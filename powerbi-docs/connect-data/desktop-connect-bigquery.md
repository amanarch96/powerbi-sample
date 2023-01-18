---
title: Connect to a Google BigQuery database in Power BI Desktop
description: Easily connect to and use Google BigQuery in Power BI Desktop
author: davidiseminger
ms.reviewer: ''

ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi

LocalizationGroup: Connect to data
---
# Connect to a Google BigQuery database in Power BI Desktop
In Power BI Desktop, you can connect to a Google **BigQuery** database and use the underlying data just like any other data source in Power BI Desktop.

## Connect to Google BigQuery
To connect to a Google **BigQuery** database select **Get Data** from the **Home** ribbon in Power BI Desktop. Select **Database** from the categories on the left, and you see **Google BigQuery**.

![Get Data dialog for Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_01.png)

In the **Google BigQuery** window that appears, sign in to your Google BigQuery account and select **Connect**.

![Sign in to Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_02.png)

When you're signed in, you see the following window indicated you've been authenticated. 

![Signed in to Google](media/desktop-connect-bigquery/connect_bigquery_02b.png)

Once you successfully connect, a **Navigator** window appears and displays the data available on the server, from which you can select one or multiple elements to import and use in **Power BI Desktop**.

![Data from Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_03.png)

## Considerations and Limitations
There are a few limits and considerations to keep in mind with the Google **BigQuery** connector:

* The Google BigQuery connector is available in Power BI Desktop and in the Power BI service. In the Power BI service, the connector can be accessed using the Cloud-to-Cloud connection from Power BI to Google BigQuery.

* You can use Power BI with the Google BigQuery **Billing Project**. By default, Power BI uses the first project from the list returned for the user. 

  To customize the behavior of the Billing Project when you use it with Power BI, specify the following option in the underlying M in the Source step, which can be customized by using **Power Query Editor** in Power BI Desktop:

  ```
  Source = GoogleBigQuery.Database([BillingProject="Include-Billing-Project-Id-Here"])
  ```

  Beginning in the September 2020 release, we enabled support for the [Google BigQuery Storage API](https://cloud.google.com/bigquery/docs/reference/storage). This feature is enabled by default and is controlled by the optional boolean argument called "UseStorageApi". Some customers might encounter issues with this feature if they use granular permissions. In this scenario, you might see the following error message:

  `ERROR [HY000] [Microsoft][BigQuery] (131) Unable to authenticate with Google BigQuery Storage API. Check your account permissions`

  You can resolve this issue by adjusting the user permissions for Storage API. Assign these Storage API permissions:

  - `bigquery.readsessions.create` - Creates a new read session via the BigQuery Storage API.
  - `bigquery.readsessions.getData` - Reads data from a read session via the BigQuery Storage API.
  - `bigquery.readsessions.update` - Updates a read session via the BigQuery Storage API.

  These permissions typically are provided in the BigQuery.User role. For more information, see [Google BigQuery Predefined roles and permissions](https://cloud.google.com/bigquery/docs/access-control).
  
  If the above steps do not resolve the problem or if you want to disable the support for Storage API, change your query to the following:
  ```
  Source = GoogleBigQuery.Database([UseStorageApi=false])
  ```
  Or if you are already using a billing project, change the query to the following:
  ```
  Source = GoogleBigQuery.Database([BillingProject="Include-Billing-Project-Id-Here", UseStorageApi=false])
  ```

## Next steps
There are all sorts of data you can connect to using Power BI Desktop. For more information on data sources, check out the following resources:

* [What is Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Data Sources in Power BI Desktop](desktop-data-sources.md)
* [Shape and Combine Data with Power BI Desktop](desktop-shape-and-combine-data.md)
* [Connect to Excel workbooks in Power BI Desktop](desktop-connect-excel.md)   
* [Enter data directly into Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
