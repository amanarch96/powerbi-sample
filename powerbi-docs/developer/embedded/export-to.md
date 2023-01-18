---
title: Export Power BI reports API
description: Learn how to export an embedded Power BI report 
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 10/01/2020
---

# Export Power BI report to file (preview)

The `exportToFile` API enables exporting a Power BI report by using a REST call. The following file formats are supported:
* **.pptx** (PowerPoint)
* **.pdf**
* **.png**
    * When exporting to a .png, a report with multiple pages is compressed into a .zip file
    * Each file in the .zip represents a report page
    * The page names are the same as the return values of the [Get Pages](/rest/api/power-bi/reports/getpages) or [Get Pages in Group](/rest/api/power-bi/reports/getpagesingroup) APIs

## Usage examples

You can use the export feature in a variety of ways. Here are a couple of examples:

* **Send to print button** - In your application, create a button that when clicked on triggers an export job. The job can export the viewed report as a .pdf or a .pptx, and when it's complete, the user can receive the file as a download. Using bookmarks you can export the report in a specific state, including configured filters, slicers, and additional settings. As the API is asynchronous, it may take some time for the file to be available.

* **Email attachment** - Send an automated email at set intervals, with an attached .pdf report. This scenario can be useful if you want to automate sending a weekly report to executives.

## Using the API

Before using the API, verify that the following [admin tenant settings](../../admin/service-admin-portal.md#tenant-settings) are enabled:
* **Export reports as PowerPoint presentations or PDF documents** - Enabled by default.
* **Export reports as image files** - Required only for *.png* and disabled by default.

The API is asynchronous. When the [exportToFile](/rest/api/power-bi/reports/exporttofile) API is called, it triggers an export job. After triggering an export job, use [polling](/rest/api/power-bi/reports/getexporttofilestatus) to track the job, until it's complete.

During polling, the API returns a number that represents the amount of work completed. The work in each export job is calculated based on the number of pages the report has. All pages have the same weight. If for example you're exporting a report with 10 pages, and the polling returns 70, it means that the API has processed seven out of the 10 pages in the export job.

When the export is complete, the polling API call returns a [Power BI URL](/rest/api/power-bi/reports/getfileofexporttofile) for getting the file. The URL will be available for 24 hours.

## Supported features

### Selecting which pages to print

Specify the pages you want to print according to the [Get Pages](/rest/api/power-bi/reports/getpages) or [Get Pages in Group](/rest/api/power-bi/reports/getpagesingroup) return value. You can also specify the order of the pages you're exporting.

### Bookmarks

[Bookmarks](../../consumer/end-user-bookmarks.md) can be used to save a report in a specific configuration, including applied filters and the state of the report's visuals. You can use the [exportToFile](/rest/api/power-bi/reports/exporttofile) API to programmatically export a report's bookmark, in two ways:

* **Export an existing bookmark**

    To export an existing [report bookmark](../../consumer/end-user-bookmarks.md#report-bookmarks), use the `name` property, a unique (case sensitive) identifier which you can get using the [bookmarks JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bookmarks).

* **Export the report's state**

    To export the current state of the report, use the `state` property. For example, you can use the bookmark's `bookmarksManager.capture` method to capture the changes a specific user made to a report, and then export it in its current state using `capturedBookmark.state`.

>[!NOTE]
>[Personal bookmarks](../../consumer/end-user-bookmarks.md#personal-bookmarks) and [persistent filters](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) are not supported.

### Authentication

You can authenticate using a user (or master user) or a [service principal](embed-service-principal.md).

### Row Level Security (RLS)

With [Row Level Security (RLS)](embedded-row-level-security.md), you can export a report showing data that's only visible to certain users. For example, if you're exporting a sales report that's defined with regional roles, you can programmatically filter the report so that only a certain region is displayed.

To export using RLS, you must have the following permissions:
* Write and reshare permissions for the dataset the report is connected to
* If the report resides on a v1 workspace, you need to be the workspace admin
* If the report resides on a v2 workspace, you need to be a workspace member or admin

### Data protection

The .pdf and .pptx formats support [sensitivity labels](../../admin/service-security-sensitivity-label-overview.md). If you export a report with a sensitivity label to a .pdf or a .pptx, the exported file will display the report with its sensitivity label.

A report with a sensitivity label cannot be exported to a .pdf or a .pptx using a [service principal](embed-service-principal.md).

### Localization

When using the `exportToFile` API, you can pass your desired local. The localization settings affect the way the report is displayed, for example by changing formatting according to the selected local.

## Concurrent requests

`exportToFile` supports concurrent export job requests. The table below shows the number of jobs you can run at the same time, depending on the SKU your report resides on. Concurrent requests refer to report pages. For example, 20 pages in one export request on an A6 SKU, will be processed concurrently. This will take roughly the same time as sending 20 export requests with one page each.

A job that exceeds its number of concurrent requests doesn't terminate. For example, if you export three pages in an A1 SKU, the first job will run, and the latter two will wait for the next two execution cycles.

|Azure SKU  |Office SKU  |Maximum concurrent report pages  |
|-----------|------------|-----------|
|A1         |EM1         |1          |
|A2         |EM2         |2          |
|A3         |EM3         |3          |
|A4         |P1          |6          |
|A5         |P2          |12         |
|A6         |P3          |24         |

## Limitations

* The report you're exporting must reside on a Premium or Embedded capacity.
* The dataset of the report you're exporting must reside on a Premium or Embedded capacity.
* For public preview, the number of Power BI report pages exported per hour is limited to 50 per capacity.
* Exported reports cannot exceed a file size of 250 MB.
* When exporting to .png, sensitivity labels are not supported.
* The number of pages that can be included in an exported report is 50. If the report includes more pages, the API returns an error and the export job is canceled.
* [Personal bookmarks](../../consumer/end-user-bookmarks.md#personal-bookmarks) and [persistent filters](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) are not supported.
* The Power BI visuals listed below are not supported. When a report containing these visuals is exported, the parts of the report that contain these visuals will not render, and will display an error symbol.
    * Uncertified Power BI visuals
    * R visuals
    * Power Apps
    * Python visuals
    * Visio

## Code examples

When you create an export job, there are three steps to follow:

1. [Sending an export request](#step-1---sending-an-export-request).
2. [Polling](#step-2---polling).
3. [Getting the file](#step-3---getting-the-file).
4. [Using the file stream](#step-4---using-the-file-stream).

This section provides examples for each step.

### Step 1 - sending an export request

The first step is sending an export request. In this example, an export request is sent for a specific page.

```csharp
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    IList<string> pageNames = null /* Get the page names from the GetPages REST API */)
{
    var powerBIReportExportConfiguration = new PowerBIReportExportConfiguration
    {
        Settings = new ExportReportSettings
        {
            Locale = "en-us",
        },
        // Note that page names differ from the page display names
        // To get the page names use the GetPages REST API
        Pages = pageNames?.Select(pn => new ExportReportPage(Name = pn)).ToList(),
    };

    var exportRequest = new ExportReportRequest
    {
        Format = format,
        PowerBIReportConfiguration = powerBIReportExportConfiguration,
    };

    // The 'Client' object is an instance of the Power BI .NET SDK
    var export = await Client.Reports.ExportToFileInGroupAsync(groupId, reportId, exportRequest);

    // Save the export ID, you'll need it for polling and getting the exported file
    return export.Id;
}
```

### Step 2 - polling

After you've sent an export request, use polling to identify when the export file you're waiting for is ready.

```csharp
private async Task<HttpOperationResponse<Export>> PollExportRequest(
    Guid reportId,
    Guid groupId,
    string exportId /* Get from the PostExportRequest response */,
    int timeOutInMinutes,
    CancellationToken token)
{
    HttpOperationResponse<Export> httpMessage = null;
    Export exportStatus = null;
    DateTime startTime = DateTime.UtcNow;
    const int c_secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations 
            return null;
        }

        // The 'Client' object is an instance of the Power BI .NET SDK
        httpMessage = await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
        exportStatus = httpMessage.Body;

        // You can track the export progress using the PercentComplete that's part of the response
        SomeTextBox.Text = string.Format("{0} (Percent Complete : {1}%)", exportStatus.Status.ToString(), exportStatus.PercentComplete);
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is not always populated
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;
            await Task.Delay(retryAfterInSec * c_secToMillisec);
        }
    }
    // While not in a terminal state, keep polling
    while (exportStatus.Status != ExportState.Succeeded && exportStatus.Status != ExportState.Failed);

    return httpMessage;
}
```

### Step 3 - getting the file

Once polling returns a URL, use this example to get the received file.

```csharp
private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the PollExportRequest response */)
{
    if (export.Status == ExportState.Succeeded)
    {
        // The 'Client' object is an instance of the Power BI .NET SDK
        var fileStream = await Client.Reports.GetFileOfExportToFileAsync(groupId, reportId, export.Id);
        return new ExportedFile
        {
            FileStream = fileStream,
            FileSuffix = export.ResourceFileExtension,
        };
    }
    return null;
}

public class ExportedFile
{
    public Stream FileStream;
    public string FileSuffix;
}
```

### Step 4 - Using the file stream

When you have the file stream, you can handle it in the way that best fits your needs. For example, you can email it or use it to download the exported reports.

### End-to-end example

This is an end-to-end example for exporting a report. This example includes the following stages:
1. [Sending the export request](#step-1---sending-an-export-request).
2. [Polling](#step-2---polling).
3. [Getting the file](#step-3---getting-the-file).

```csharp
private async Task<ExportedFile> ExportPowerBIReport(
	Guid reportId,
	Guid groupId,
	FileFormat format,
	int pollingtimeOutInMinutes,
	CancellationToken token,
	IList<string> pageNames = null  /* Get the page names from the GetPages REST API */)
{
	const int c_maxNumberOfRetries = 3; /* Can be set to any desired number */
	const int c_secToMillisec = 1000;
	try
	{
		Export export = null;
		int retryAttempt = 1;
		do
		{
			var exportId = await PostExportRequest(reportId, groupId, format, pageNames);
			var httpMessage = await PollExportRequest(reportId, groupId, exportId, pollingtimeOutInMinutes, token);
			export = httpMessage.Body;
			if (export == null)
			{
				// Error, failure in exporting the report
				return null;
			}
			if (export.Status == ExportState.Failed)
			{
				// Some failure cases indicate that the system is currently busy. The entire export operation can be retried after a certain delay
				// In such cases the recommended waiting time before retrying the entire export operation can be found in the RetryAfter header
				var retryAfter = httpMessage.Response.Headers.RetryAfter;
				if(retryAfter == null)
				{
				    // Failed state with no RetryAfter header indicates that the export failed permanently
				    return null;
                }

                var retryAfterInSec = retryAfter.Delta.Value.Seconds;
                await Task.Delay(retryAfterInSec * c_secToMillisec);
            }
        }
        while (export.Status != ExportState.Succeeded && retryAttempt++ < c_maxNumberOfRetries);

        if (export.Status != ExportState.Succeeded)
        {
            // Error, failure in exporting the report
            return null;
        }

        var exportedFile = await GetExportedFile(reportId, groupId, export);

        // Now you have the exported file stream ready to be used according to your specific needs
        // For example, saving the file can be done as follows:
        /*
            var pathOnDisk = @"C:\temp\" + export.ReportName + exportedFile.FileSuffix;

            using (var fileStream = File.Create(pathOnDisk))
            {
                exportedFile.FileStream.CopyTo(fileStream);
            }
        */

        return exportedFile;
    }
    catch
    {
        // Error handling
        throw;
    }
}
```

## Next steps

Review how to embed content for your customers and your organization:

> [!div class="nextstepaction"]
>[Export paginated report to file](export-paginated-report.md)

> [!div class="nextstepaction"]
>[Embed for your customers](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Embed for your organization](embed-sample-for-your-organization.md)