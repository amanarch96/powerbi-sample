---
title: View on-premises reports and KPIs in the Power BI Windows app
description: The Power BI mobile app for Windows 10 offers live, touch-enabled mobile access to your important on-premises business information.
author: paulinbar

ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 05/19/2020
ms.author: painbar

---
# View on-premises reports and KPIs in the Power BI Windows app
The Power BI app for Windows 10 offers live, touch-enabled mobile access to your important on-premises business information in SQL Server 2016 Reporting Services. 

![Reporting Services mobile reports](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## First things first
[Create Reporting Services mobile reports](/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher) with SQL Server 2016 Enterprise Edition Mobile Report Publisher and publish them to the [Reporting Services web portal](/sql/reporting-services/web-portal-ssrs-native-mode). Create KPIs right in the web portal. Organize them in folders and mark your favorites, so you can find them easily. 

Then in the Power BI app for Windows 10, view the KPS, mobile reports, and Power BI reports, organized in folders or collected as favorites. 

> [!NOTE]
> Your device needs to be running Windows 10. The app works best on devices with at least 1 GB RAM and 8 GB internal storage.

>[!NOTE]
>Power BI mobile app support for **phones using Windows 10 Mobile** will be discontinued on March 16, 2021. [Learn more](/legal/powerbi/powerbi-mobile/power-bi-mobile-app-end-of-support-for-windows-phones)

## Explore samples without a SQL Server 2016 Reporting Services server
Even if you don't have access to a Reporting Services web portal, you can still explore the features of Reporting Services mobile reports.

1. In your Windows 10 device, open the Power BI app.
2. Tap the global navigation button ![Global navigation button](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) in the upper-left corner.
3. Tap **Settings** icon ![Settings icon](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png), right-click or tap and hold **Connect to server**, then tap **View samples**.
   
   ![View SSRS samples](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-connect-ssrs-samples.png)
4. Open the Retail Reports or Sales Reports folder to explore their KPIs and mobile reports.
   
   ![Sample KPIs and mobile reports](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-ssrs-sample-kpis.png)

Browse the samples to interact with KPIs and mobile reports.

## Connect to a Reporting Services report server
1. At the bottom of the nav pane, tap **Settings** ![Settings icon](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png)
2. Tap **Connect to server**.
3. Fill in the server address and your user name and password. Use this format for the server address:
   
     `https://<servername>/reports`
     OR
     `https://<servername>/reports`
   
   > [!NOTE]
   > Include **http** or **https** at the beginning of the connection string.
   > 
   > 
   
    Tap **Advanced option** to give the server a name, if you'd like.
4. Tap the check mark to connect. 
   
   Now you see the server in the nav pane.
   
   ![Server in nav pane](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-server.png)
   
   >[!TIP]
   >Tap the global navigation button ![Global navigation button](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) anytime to go between your Reporting Services mobile reports and your dashboards in the Power BI service. 
   > 

   >[!NOTE]
   >Report Servers configured with custom ports are not supported and cannot be accessed from the Power BI Windows app. 

## View Reporting Services KPIs and mobile reports in the Power BI app
Reporting Services KPIs, mobile reports, and Power BI reports (preview) are displayed in the same folders they're in on the Reporting Services web portal.

![Report folders](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-folders.png)

* Tap a KPI to see it in focus mode.
  
    ![KPI in focus mode](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-kpis.png)
* Tap a mobile report to open and interact with it in the Power BI app.
  
    ![Reporting Services mobile report](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## View your favorite KPIs and reports
You can mark KPIs, mobile reports, and Power BI reports as favorites on your Reporting Services web portal, and then view them in one convenient folder on your Windows 10 device, along with your Power BI favorite dashboards and reports.

* Tap **Favorites**.
  
   ![Favorites icon](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-favorite-menu.png)
  
   Your favorites from the web portal are all on this page.
  
Read more about [favorites in the Power BI mobile apps](mobile-apps-favorites.md).

## Remove a connection to a report server
You can only be connected to one report server at a time from your Power BI mobile app. If you want to connect to a different server, you need to disconnect from the current one.

1. At the bottom of the nav pane, tap **Settings** ![Settings icon](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png).
2. Tap and hold the server name you don't want to be connected to.
3. Tap **Remove server**.
   
    ![Remove server](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-windows-10-ssrs-remove-server-menu.png)

## Create Reporting Services mobile reports and KPIs
You don't create Reporting Services KPIs and mobile reports in the Power BI mobile app. You create them in SQL Server Mobile Report Publisher and a SQL Server 2016 Reporting Services web portal.

* [Create your own Reporting Services mobile reports](/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher), and publish them to a Reporting Services web portal.
* Create [KPIs on a Reporting Services web portal](/sql/reporting-services/working-with-kpis-in-reporting-services)

## Next steps
* [Get started with the Power BI mobile app for Windows 10](mobile-windows-10-phone-app-get-started.md)  
* [What is Power BI?](../../fundamentals/power-bi-overview.md)  
* Questions? [Try asking the Power BI Community](https://community.powerbi.com/)