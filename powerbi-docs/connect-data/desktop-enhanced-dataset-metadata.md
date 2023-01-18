---
title: Using enhanced dataset metadata in Power BI Desktop
description: This article describes how to use enhanced dataset metadata in Power BI.
author: davidiseminger
ms.reviewer: ''

ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/22/2020
ms.author: davidi

LocalizationGroup: Connect to data
---
# Using enhanced dataset metadata

When Power BI Desktop creates reports, it also creates dataset metadata in the corresponding PBIX and PBIT files. Previously the metadata was stored in a format that was specific to Power BI Desktop. It used base-64 encoded M expressions and data sources, and assumptions were made about how that metadata was stored.

With the release of the **enhanced dataset metadata** feature, many of these limitations are removed. PBIX files are automatically upgraded to enhanced metadata upon opening the file. With **enhanced dataset metadata**, metadata created by Power BI Desktop uses a format similar to what is used for Analysis Services tabular models, based on the [Tabular Object Model](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).


The **enhanced dataset metadata** feature is strategic and foundational, because future Power BI functionality will be built upon its metadata. Some additional capabilities that stand to benefit from enhanced dataset metadata include [XMLA read/write](/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite) for management of Power BI datasets, and the migration of Analysis Services workloads to Power BI to benefit from next-generation features.


## Next steps

You can do all sorts of things with Power BI Desktop. For more information on its capabilities, check out the following resources:

* [What is Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [What's new in Power BI Desktop?](../fundamentals/desktop-latest-update.md)
* [Query overview with Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Data types in Power BI Desktop](desktop-data-types.md)
* [Shape and combine data with Power BI Desktop](desktop-shape-and-combine-data.md)
* [Common query tasks in Power BI Desktop](../transform-model/desktop-common-query-tasks.md)