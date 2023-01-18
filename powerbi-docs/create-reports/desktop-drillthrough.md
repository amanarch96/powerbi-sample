---
title: Set up drill through in Power BI reports
description: Learn how to use drill through to drill down into data, on a new report page, in Power BI reports
author: maggiesMSFT
ms.reviewer: ''

ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 03/12/2020
ms.author: maggies

LocalizationGroup: Create reports
---
# Set up drill through in Power BI reports
With *drill through* in Power BI reports, you can create a page in your report that focuses on a specific entity such as a supplier, customer, or manufacturer. When your report readers use drill through, they right-click a data point in other report pages, and drill through to the focused page to get details that are filtered to that context. You can also [create a button that drills through](desktop-drill-through-buttons.md) to details when they click it.

You can set up drill through in your reports in Power BI Desktop or the Power BI service.

![Using drill through](media/desktop-drillthrough/power-bi-drill-through-right-click.png)

## Set up the drill-through destination page
1. To set up drill through, create a report page that has the visuals you want for the type of entity that you're going to provide drill through for. 

    For example, suppose you want to provide drill through for manufacturers. For this case, you might create a drill-through page with visuals that show total sales, total units shipped, sales by category, sales by region, and so on. That way, when you drill through to that page, the visuals are specific to the manufacturer you selected.

2. Then, on that drill-through page, in the **Fields** section of the **Visualizations** pane, drag the field for which you want to enable drill through into the **Drill-through filters** well.

    ![Drill-through well](media/desktop-drillthrough/drillthrough_02.png)

    When you add a field to the **Drill-through filters** well, Power BI automatically creates a *back* button visual. That visual becomes a button in published reports. Users who consume your report in the Power BI service use this button to get back to the report page from which they came.

    ![Drill-through image](media/desktop-drillthrough/drillthrough_03.png)

> [!IMPORTANT]
> You can configure and perform drillthrough to a page in the same report, however, you cannot drillthrough to a page in a different report.  



## Use your own image for a back button    
 Because the back button is an image, you can replace the image of that visual with any image you want. It still operates as a back button so that report consumers can go back to their original page. 

To use your own image for a back button, follow these steps:

1. On the **Home** tab, select **Image**. Then, locate your image and place it on the drill-through page.

2. Select your new image on the drill-through page. Under the **Format image** pane, set the **Action** slider to **On**, and  then set the **Type** to **Back**. Your image now functions as a back button.

    ![Load image and set Type to Back](media/desktop-drillthrough/drillthrough_05.png)

    
     Now users can right-click a data point in your report and get a context menu that supports drill through to that page. 

    ![Drill-through menu](media/desktop-drillthrough/drillthrough_04.png)

    When report consumers choose to drill through, the page is filtered to show information about the data point on which they right-clicked. For example, suppose they right-clicked on a data point about Contoso, a manufacturer, and selected to drill through. The drill-through page they go to is filtered to Contoso.

## Pass all filters in drill through

You can pass all applied filters to the drill-through window. For example, you can select only a certain category of products and the visuals filtered to that category, and then select drill through. You might be interested in what that drill through would look like with all those filters applied.

To keep all applied filters, in the **Drill-through** section of the **Visualizations** pane, set **Keep all filters** to **On**. 

![Keep all filters](media/desktop-drillthrough/drillthrough_06.png)

When you then drill through on a visual, you can see which filters were applied as a result of the source visual having temporary filters applied. In the **Drill-through** section of the **Visualization** pane, those transient filters are shown in italics. 

![Transient filters in italics](media/desktop-drillthrough/drillthrough_07.png)

Although you could do this with tooltips pages, that would be an odd experience because the tooltip wouldn't appear to be working properly. For this reason, so doing so with tooltips isn't recommended.

## Add a measure to drill through

Besides passing all filters to the drill-through window, you can also add a measure or a summarized numeric column to the drill-through area. Drag the drill-through field to the **Drill-through** card to apply it. 

![Add a measure to drill through](media/desktop-drillthrough/drillthrough_08.png)

When you add a measure or summarized numeric column, you can drill through to the page when the field is used in the *Value* area of a visual.

That's all there is to using drill through in your reports. It's a great way to get an expanded view of the entity information that you selected for your drill-through filter.

## Next steps

You might also be interested in the following articles:

* [Use cross-report drill through in Power BI reports](desktop-cross-report-drill-through.md)
* [Using slicers Power BI Desktop](../visuals/power-bi-visualization-slicers.md)
