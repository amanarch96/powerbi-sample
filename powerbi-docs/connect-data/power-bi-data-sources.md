---
title: Power BI data sources
description: This article lists the data sources that Power BI supports, including information about DirectQuery and the on-premises data gateway.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/07/2020
ms.author: davidi
---

# Power BI data sources

The following table shows the data sources that Power BI supports for datasets, including information about DirectQuery and the on-premises data gateway. For information about dataflows, see [Connect to data sources for Power BI dataflows](../transform-model/dataflows/dataflows-configure-consume.md).

| Data source | Connect from Desktop | Connect and refresh from service | DirectQuery / Live connection | Gateway (supported) | Gateway (required) | Power BI Dataflows |
|---|---|---|---|---|---|---|---|
| Access database | Yes | Yes | No | Yes <sup>1</sup> | Yes | Yes |
| ActiveDirectory | Yes | Yes | No | Yes | Yes | Yes |
| Adobe Analytics | Yes | Yes | No | No | No | No |
| Amazon Redshift | Yes | Yes | Yes | Yes | No | Yes |
| appFigures | Yes | Yes | No | No | No | No |
| AtScale cubes | Yes | Yes | Yes | Yes | No | No |
| Azure Analysis Services | Yes | Yes | Yes | No | No | No |
| Azure Blob Storage | Yes | Yes | No | Yes | No | Yes |
| Azure Cosmos DB | Yes | Yes | No | No | No | No |
| Azure Cost Management | Yes | Yes | No | No | No | No |
| Azure Data Explorer (kusto) | Yes | Yes | Yes | Yes | No | Yes |
| Azure Data Lake Storage Gen1 | Yes | Yes | No | No | No | No |
| Azure Data Lake Storage Gen2 | Yes | Yes | No | Yes | No | Yes |
| Azure DevOps | Yes | Yes | No | No | No | No |
| Azure DevOps Server | Yes | Yes | No | Yes | Yes | No |
| Azure HDInsight (HDFS) | Yes | Yes | No | No | No | No |
| Azure HDInsight Spark | Yes | Yes | Yes | No | No | Yes |
| Azure SQL Database | Yes | Yes | Yes | Yes | No | Yes |
| Azure SQL Data Warehouse | Yes | Yes | Yes | Yes | No | Yes |
| Azure Table Storage | Yes | Yes | No | Yes | No | Yes |
| BI Connector | Yes | Yes | Yes | Yes | Yes | No |
| BI360 - Budgeting & Financial Reporting | Yes | Yes | No | No | No | No |
| Common Data Service | Yes | Yes | No | No | No | Yes |
| Data.World - Get Dataset | Yes | Yes | No | No | No | No |
| Denodo | Yes | Yes | Yes | Yes | Yes | No |
| Dremio | Yes | Yes | Yes | Yes | Yes | No |
| Dynamics 365 (online) | Yes | Yes | No | No | No | No |
| Dynamics 365 Business Central | Yes | Yes | No | No | No | No |
| Dynamics 365 Business Central (on-premises) | Yes | Yes | No | No | No | No |
| Dynamics 365 Customer Insights | Yes | Yes | No | No | No | No |
| Dynamics NAV | Yes | Yes | No | No | No | No |
| Emigo Data Source | Yes | Yes | No | No | No | No |
| Entersoft Business Suite | Yes | Yes | No | No | No | No |
| Essbase | Yes | Yes | Yes | Yes | Yes | No |
| Exasol | Yes | Yes | Yes | Yes | Yes | No |
| Excel | Yes <sup>3</sup> | Yes <sup>3</sup> | No | Yes <sup>3</sup> | No <sup>4</sup> | Yes |
| Facebook | Yes | Yes | No | No | No | No |
| File | Yes | Yes | No | Yes | Yes | Yes |
| Folder | Yes | Yes | No | Yes | Yes | Yes |
| GitHub | Yes | Yes | No | No | No | No |
| Google Analytics | Yes | Yes | No | No | No | No |
| Google BigQuery | Yes | Yes | Yes | No | No | Yes |
| Hadoop File (HDFS) | Yes | No | No | No | No | No |
| Hive LLAP | Yes | Yes | Yes | Yes | No | No |
| HDInsight Interactive Query | Yes | Yes | Yes | No | No | No |
| IBM DB2 | Yes | Yes | Yes | Yes | No | Yes |
| IBM Informix Database | Yes | Yes | No | Yes | No | No |
| IBM Netezza | Yes | Yes | Yes | Yes | Yes | No |
| Impala | Yes | Yes | Yes | Yes | Yes | Yes |
| Indexima | Yes | Yes | Yes | Yes | Yes | No |
| Industrial App Store | Yes | Yes | No | No | No | No |
| Information Grid | Yes | Yes | No | No | No | No |
| Intersystems IRIS | Yes | Yes | Yes | Yes | Yes | No |
| Intune Data Warehouse | Yes | Yes | No | No | No | No |
| Jethro ODBC | Yes | Yes | Yes | Yes | Yes | No |
| JSON | Yes | Yes | No | Yes** | No <sup>4</sup> | Yes |
| Kyligence Enterprise | Yes | Yes | Yes | Yes | Yes | No |
| MailChimp | Yes | Yes | No | No | No | No |
| Marketo | Yes | Yes | No | No | No | No |
| MarkLogic ODBC | Yes | Yes | Yes | Yes | Yes | No |
| Microsoft Azure Consumption Insights | Yes | Yes | No | No | No | No |
| Microsoft Exchange | Yes | Yes | No | Yes | No | No |
| Microsoft Exchange Online | Yes | Yes | No | No | No | Yes |
| Microsoft Graph Security | Yes | Yes | No | Yes | No | No |
| Mixpanel | Yes | Yes | No | No | No | No |
| MySQL | Yes | Yes | No | Yes | Yes | Yes |
| OData | Yes | Yes <sup>7</sup> | No | Yes | No | Yes |
| ODBC | Yes | Yes | No | Yes | Yes | Yes |
| OleDb | Yes | Yes | No | Yes | Yes | No |
| Oracle | Yes | Yes | Yes | Yes | Yes | Yes |
| Paxata <sup>8</sup> | Yes | Yes | No | Yes | No | No |
| PDF | Yes | Yes | No | Yes | No <sup>4</sup> | Yes |
| Planview Enterprise One - CTM | Yes | Yes | No | No | No | No |
| Planview Enterprise One - PRM | Yes | Yes | No | No | No | No |
| Planview Projectplace | Yes | Yes | No | No | No | No |
| PostgreSQL | Yes | Yes | Yes | Yes | No | Yes |
| Power BI dataflows | Yes | Yes | No | No | No | Yes |
| Power BI datasets | Yes | Yes | Yes | No | No | No |
| Power platform dataflows | Yes | Yes | No | No | No | Yes |
| Python script | Yes | Yes <sup>5</sup> | No | Yes <sup>5</sup> | Yes | No |
| QubolePresto | Yes | Yes | Yes | Yes | Yes | No |
| Quick Base | Yes | Yes | No | Yes | Yes | No |
| QuickBooks Online | Yes | Yes | No | No | No | No |
| R script | Yes | Yes <sup>5</sup> | No | Yes <sup>5</sup> | No | No |
| Roamler | Yes | Yes | No | Yes | No | No |
| Salesforce Objects | Yes | Yes | No | No | No | Yes |
| Salesforce Reports | Yes | Yes | No | No | No | Yes |
| SAP Business Warehouse Message Server | Yes | Yes | Yes | Yes | Yes | Yes |
| SAP Business Warehouse Server | Yes | Yes | Yes | Yes | Yes | Yes |
| SAP HANA | Yes | Yes | Yes | Yes | Yes | Yes |
| SharePoint Folder | Yes | Yes | No | Yes | No <sup>4</sup> | Yes |
| SharePoint List | Yes | Yes | No | Yes | No <sup>4</sup> | Yes |
| SharePoint Online List | Yes | Yes | No | Yes | No | Yes |
| Smartsheet | Yes | Yes | No | No | No | Yes |
| Snowflake | Yes | Yes | Yes | Yes | No | Yes |
| Spark | Yes | Yes | Yes | Yes | No | Yes |
| SparkPost | Yes | Yes | No | No | No | No |
| SQL Server | Yes | Yes | Yes | Yes | Yes | Yes |
| SQL Server Analysis Services | Yes | Yes | Yes | Yes | Yes | No |
| Stripe | Yes | Yes | No | No | No | No |
| SurveyMonkey | Yes | Yes | No | Yes | No | No |
| SweetIQ | Yes | Yes | No | No | No | No |
| Sybase | Yes | Yes | No | Yes | Yes | Yes |
| TeamDesk | Yes | Yes | No | Yes | No | No |
| Tenforce | Yes | Yes | No | No | No | No |
| Teradata | Yes | Yes | Yes | Yes | Yes | Yes |
| Text/CSV | Yes | Yes | No | Yes | No <sup>4</sup> | Yes |
| Twilio | Yes | Yes | No | No | No | No |
| tyGraph | Yes | Yes | No | No | No | No |
| Vertica | Yes | Yes | Yes | Yes | Yes | Yes |
| Web | Yes | Yes | No | Yes | Yes <sup>6</sup> | Yes |
| Webtrends | Yes | Yes | No | No | No | No |
| Workforce Dimensions | Yes | Yes | No | Yes | No | No |
| XML | Yes | Yes | No | Yes | No <sup>4</sup> | Yes |
| Zendesk | Yes | Yes | No | No | No | No |
| | | | | | | | |

<sup>1</sup> Supported with the [ACE OLEDB provider](https://www.microsoft.com/download/details.aspx?id=54920), installed on the same machine as the gateway.

<sup>3</sup> Excel 1997-2003 files (.xls) require the [ACE OLEDB provider](https://www.microsoft.com/download/details.aspx?id=54920).

<sup>4</sup> Required for the on-premises version of the technology.

<sup>5</sup> Supported only with the [personal gateway](service-gateway-personal-mode.md).

<sup>6</sup> Required for .html, .xls, and Access Databases

<sup>7</sup> Power BI service doesn't support OData feeds that require authentication.

<sup>8</sup> Paxata is supported in the version of Power BI Desktop optimized for Power BI Report Server. It isn't supported in Power BI reports published to Power BI Report Server. See [Power BI report data sources in Power BI Report Server](../report-server/data-sources.md) for the list of supported data sources.

## Considerations and limitations

- Many data connectors for Power BI Desktop require Internet Explorer 10 (or newer) for authentication. 
- Some data sources are available in Power BI Desktop optimized for Power BI Report Server, but aren't supported when published to Power BI Report Server. See [Power BI report data sources in Power BI Report Server](../report-server/data-sources.md) for the list of supported data sources.

## Single sign-on (SSO) for DirectQuery sources

When the SSO option is enabled and your users access reports built atop the data source, Power BI sends their authenticated Azure AD credentials in the queries to the underlying data source. This enables Power BI to respect the security settings that are configured at the data source level.
The SSO option takes effect across all datasets that use this data source. It does not affect the authentication method used for import scenarios. The following data sources support SSO for connections through DirectQuery:

- Azure SQL Database
- Azure SQL Data Warehouse
- Impala
- SAP HANA
- SAP BW
- SAP BW Message Server
- Snowflake
- Spark
- SQL Server
- Teradata

## Next steps

[Connect to data in Power BI Desktop](desktop-quickstart-connect-to-data.md)  
[Using DirectQuery in Power BI](desktop-directquery-about.md)  
[SQL Server Analysis Services live data in Power BI](sql-server-analysis-services-tabular-data.md)  
[What is an on-premises data gateway?](service-gateway-onprem.md)  
[Power BI report data sources in Power BI Report Server](../report-server/data-sources.md)