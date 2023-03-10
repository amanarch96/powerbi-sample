---
title: Use Shape maps in Power BI Desktop (Preview)
description: Create relative comparisons to regions using Shape maps in Power BI Desktop
author: msftrien
ms.reviewer: 'sujata'
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 03/18/2020
ms.author: rien
LocalizationGroup: Transform and shape data
---

# Create Shape Map visualizations in Power BI Desktop (preview)

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Create a **Shape Map** visual to compare regions on a map using color. Unlike the **Map** visual, **Shape Map** can't show precise geographical locations of data points on a map. Instead,  its main purpose is to show relative comparisons of regions on a map by coloring them differently.

**Shape Map** visuals are based on TopoJSON maps, which have the compelling ability to use custom maps that you can create. Examples of custom maps are: geographical, seating arrangements, floor plans, and others. The ability to use custom maps is not available in this Preview release of **Shape Map**.

> [!NOTE]
> Sharing your report with a Power BI colleague requires that you both have individual Power BI Pro licenses or that the report is saved in Premium capacity.

## Creating Shape Maps
You can test the **Shape Map** control with the maps that are shipping with this Preview release, or you can use your own custom map as long as it meets the requirements outlined in the following section called **Use Custom Maps**.

The **Shape Map** visual is in Preview, and must be enabled in Power BI Desktop. To enable **Shape Map**, select **File > Options and Settings > Options > Preview Features**, then select the **Shape Map Visual** checkbox. You'll need to restart Power BI Desktop after you make the selection.

![enable the Shape map preview feature](media/desktop-shape-map/power-bi-preview-features.png)

Once **Shape Map** is enabled, select the **Shape Map** icon from the **Visualizations** pane.

![select the template for shape map](media/desktop-shape-map/power-bi-shape-map-template2.png)

Power BI Desktop creates an empty **Shape Map** visual design canvas.

![an empty shape map appears on your canvas](media/desktop-shape-map/shape-map-3.png)

Take the following steps to create a **Shape Map**:

1. In the **Fields** pane, drag a data field that has the region names (or abbreviations) onto the **Location** bucket, and a data measure field into the **Color saturation** bucket (you won't see a map yet).

   > [!NOTE]
   > See the section titled **Getting Map Data**, below, for information on how to quickly get map data to test **Shape Map**.
   > 
   > 

   ![build your shape map](media/desktop-shape-map/shape-map-3a.png)
2. In the **Format** settings pane, expand **Shape**, and select from the **Standard Maps** drop-down to show your data. At this point, the rendering appears, as shown in the following image.

   ![open the Formatting pane and select Shape](media/desktop-shape-map/shape-map-3b-new.png)

   > [!NOTE]
   > In the **Region Keys** section at the end of this article is a collection of tables that have map regions keys you can use to test the **Shape Map** visual.
   > 
   > 
3. You can then modify the map using the Formatting options such as **Default color**, **Zoom**, and more. And, you can also add a category data column to the **Legend** bucket, and classify the map regions based on categories.

## Use custom maps
You can use custom maps with **Shape Map** as long as they are in the **TopoJSON** format. If your map is in another format, you can use online tools such as [**Map Shaper**](https://mapshaper.org/) to convert your *shapefiles* or your *GeoJSON* maps into the **TopoJSON** format.

To use your **TopoJSON** map file, add a ShapeMap visual to your report and add some data to the *Location* and *Color saturation* buckets. Then, in the **Visualizations** pane with the **Format** section selected (shown as (1) in the following image), expand the **Shape** section and select **+ Add Map**.

![open Formatting pane and select Add Map](media/desktop-shape-map/shape-map-6-new.png)

## Sample custom map
The *Offices of the United States Attorneys* release an annual fiscal report on their litigation and caseload data.  All of their reports can be found in the link below,

https://www.justice.gov/usao/resources/annual-statistical-reports

Since states can be divided into multiple districts, we have to use a custom shape map.  By importing the **TopoJSON** map of the U.S. judicial districts into **Power BI Desktop**, we can then visualize the annual fiscal district attorney data.  The image below shows an example of this map.

![custom shape map](media/desktop-shape-map/shape-map-7a.png)

You can do interesting things with the individual state maps as well, and show more detail based on the districts it contains. 

![Texas shape map](media/desktop-shape-map/shape-map-7b.png)

If you'd like to experiment with this dataset and visualization, you can download the original PBIX file that was used to generate this report using the following link.

* [Custom shape map demo .PBIX file](https://download.microsoft.com/download/1/2/8/128943FB-9231-42BD-8A5D-5E2362C9D589/DistrictAttorneyFiscalReport.pbix)

## Getting map data
To quickly get data into a model so you can test **Shape Map**, you can copy one of the tables at the end of this article, then select **Enter Data** from the **Home** ribbon.

![In Desktop, select Enter Data](media/desktop-shape-map/shape-map-4-new.png)

If your data has multiple columns, you will need to use an editor like Excel to paste the data, then copy each data column separately. You can then paste the data into Power BI Desktop. The top row is automatically identified as a header.

![Create Table pane](media/desktop-shape-map/shape-map-5.png)

You can enter a new column simply by typing a new column name (in the blank column to the right), then add values in each cell, just like you can do in Excel. When finished, select **Load** and the table is added to the data model for Power BI Desktop.

> [!NOTE]
> When working with countries or regions, use the three-letter abbreviation to ensure that geocoding works properly in map visualizations. Do *not* use two-letter abbreviations, as some countries or regions may not be properly recognized.
> 
> If you only have two-letter abbreviations, check out [this external blog post](https://blog.ailon.org/how-to-display-2-letter-country-data-on-a-power-bi-map-85fc738497d6#.yudauacxp) for steps on how to associate your two-letter country/region abbreviations with three-letter country/region abbreviations.
> 
> 

## Preview behavior and requirements
There are a few considerations and requirements for this Preview release of **Shape Map**:

* The **Shape Map** visual is in Preview, and must be enabled in Power BI Desktop. To enable **Shape Map**, select **File > Options and Settings > Options > Preview Features**, then select the **Shape Map Visual** checkbox.
* Currently, you must also have the **Color saturation** bucket set in order for the **Legend** classification to work properly.
* The final release version of **Shape Map** will have a user interface that shows the map keys of the currently selected map (there is no date set for final release, and **Shape Map** is still in Preview). In this Preview release, you can reference the map region keys in the tables found in the following **Region Keys** section of this article.
* The **Shape Map** visual will plot up to a maximum of 1,500 data points.

## Region keys

Use the following **Region keys** in this Preview release to test **Shape map**.

### Australia: States

| ID | abbr | iso | name | postal |
| --- | --- | --- | --- | --- |
| au-wa |WA |AU-WA |Western Australia |WA |
| au-vic |Vic |AU-VIC |Victoria |VIC |
| au-tas |Tas |AU-TAS |Tasmania |TAS |
| au-sa |SA |AU-SA |South Australia |SA |
| au-qld |Qld |AU-QLD |Queensland |QLD |
| au-nt |NT |AU-NT |Northern Territory |NT |
| au-nsw |NSW |AU-NSW |New South Wales |NSW |
| au-act |ACT |AU-ACT |Australian Capital Territory |ACT |

### Austria: States

| ID | iso | name | name-en | postal |
| --- | --- | --- | --- | --- |
| at-wi |AT-9 |Wien |Vienna |WI |
| at-vo |AT-8 |Vorarlberg |Vorarlberg |VO |
| at-tr |AT-7 |Tirol |Tyrol |TR |
| at-st |AT-6 |Steiermark |Styria |ST |
| at-sz |AT-5 |Salzburg |Salzburg |SZ |
| at-oo |AT-4 |Ober??sterreich |Upper Austria |OO |
| at-no |AT-3 |Nieder??sterreich |Lower Austria |NO |
| at-ka |AT-2 |K??rnten |Carinthia |KA |
| at-bu |AT-1 |Burgenland |Burgenland |BU |

### Brazil: States

| ID |
| --- |
| Tocantins |
| Pernambuco |
| Goias |
| Sergipe |
| Sao Paulo |
| Santa Catarina |
| Roraima |
| Rondonia |
| Rio Grande do Sul |
| Rio Grande do Norte |
| Rio de Janeiro |
| Piaui |
| Parana |
| Paraiba |
| Para |
| Minas Gerais |
| Mato Grosso |
| Maranhao |
| Mato Grosso do Sul |
| Distrito Federal |
| Ceara |
| Espirito Santo |
| Bahia |
| Amazonas |
| Amapa |
| Alagoas |
| Acre |
| Litigated Zone 1 |
| Litigated Zone 2 |
| Litigated Zone 3 |
| Litigated Zone 4 |

### Canada: Provinces

| ID | iso | name | postal |
| --- | --- | --- | --- |
| ca-nu |CA-NU |Nunavut |NU |
| ca-nt |CA-NT |Northwest Territories |NT |
| ca-yt |CA-YT |Yukon |YT |
| ca-sk |CA-SK |Saskatchewan |SK |
| ca-qc |CA-QC |Quebec |QC |
| ca-pe |CA-PE |Prince Edward Island |PE |
| ca-on |CA-ON |Ontario |ON |
| ca-ns |CA-NS |Nova Scotia |NS |
| ca-nl |CA-NL |Newfoundland and Labrador |NL |
| ca-nb |CA-NB |New Brunswick |NB |
| ca-mb |CA-MB |Manitoba |MB |
| ca-bc |CA-BC |British Columbia |BC |
| ca-ab |CA-AB |Alberta |AB |

### France: Regions

| ID | name | name-en |
| --- | --- | --- |
| Auvergne-Rhone-Alpes |  |  |
| Bourgogne-Franche-Comte |  |  |
| Bretagne |Bretagne |Brittany |
| Centre-Val de Loire |Centre-Val de Loire |Centre-Val de Loire |
| Corse |Corse |Corsica |
| Grand Est |  |  |
| Guadeloupe | |   |
| Hauts-de-France |  |  |
| Ile-de-France |??le-de-France |Ile-de-France |
| La Reunion |  |  |
| Mayotte  |  |  |
| Normandie |Normandie |  |
| Nouvelle-Aquitaine |  |  |
| Occitanie  |  |  |
| Pays de la Loire |Pays de la Loire |Pays de la Loire |
| Provence-Alpes-Cote d'Azur |Provence-Alpes-C??te d'Azur |Provence-Alpes-Cote d'Azur |
|  |  |  |

### Germany: States

| ID | iso | name | name-en | postal |
| --- | --- | --- | --- | --- |
| de-be |DE-BE |Berlin |Berlin |BE |
| de-th |DE-TH |Th??ringen |Thuringia |TH |
| de-st |DE-ST |Sachsen-Anhalt |Saxony-Anhalt |ST |
| de-sn |DE-SN |Sachsen |Saxony |SN |
| de-mv |DE-MV |Mecklenburg-Vorpommern |Mecklenburg-Vorpommern |MV |
| de-bb |DE-BB |Brandenburg |Brandenburg |BB |
| de-sh |DE-SH |Schleswig-Holstein |Schleswig-Holstein |SH |
| de-sl |DE-SL |Saarland |Saarland |SL |
| de-rp |DE-RP |Rheinland-Pfalz |Rhineland-Palatinate |RP |
| de-nw |DE-NW |Nordrhein-Westfalen |North Rhine-Westphalia |NW |
| de-ni |DE-NI |Niedersachsen |Lower Saxony |NI |
| de-he |DE-HE |Hessen |Hesse |HE |
| de-hh |DE-HH |Hamburg |Hamburg |HH |
| de-hb |DE-HB |Bremen |Bremen |HB |
| de-by |DE-BY |Bayern |Bavaria |BY |
| de-bw |DE-BW |Baden-W??rttemberg |Baden-Wurttemberg |BW |

### Ireland: Counties

| ID |
| --- |
| Wicklow |
| Wexford |
| Westmeath |
| Waterford |
| Sligo |
| Tipperary |
| Roscommon |
| Offaly |
| Monaghan |
| Meath |
| Mayo |
| Louth |
| Longford |
| Limerick |
| Leitrim |
| Laoighis |
| Kilkenny |
| Kildare |
| Kerry |
| Galway |
| Dublin |
| Donegal |
| Cork |
| Clare |
| Cavan |
| Carlow |

### Italy: Regions

| ID | iso | name | name-en | postal |
| --- | --- | --- | --- | --- |
| it-vn |IT-34 |Veneto |Veneto |VN |
| it-vd |IT-23 |Valle d'Aosta |Aosta Valley |VD |
| it-um |IT-55 |Umbria |Umbria |UM |
| it-tt |IT-32 |Trentino-Alto Adige |Trentino-South Tyrol |TT |
| it-tc |IT-52 |Toscana |Tuscany |TC |
| it-sc |IT-82 |Sicilia |Sicily |SC |
| it-sd |IT-88 |Sardegna |Sardinia |SD |
| it-pm |IT-21 |Piemonte |Piedmont |PM |
| it-ml |IT-67 |Molise |Molise |ML |
| it-mh |IT-57 |Marche |Marche |MH |
| it-lm |IT-25 |Lombardia |Lombardy |LM |
| it-lg |IT-42 |Liguria |Liguria |LG |
| it-lz |IT-62 |Lazio |Lazio |LZ |
| it-fv |IT-36 |Friuli-Venezia Giulia |Friuli-Venezia Giulia |FV |
| it-er |IT-45 |Emilia-Romagna |Emilia-Romagna |ER |
| it-cm |IT-72 |Campania |Campania |CM |
| it-lb |IT-78 |Calabria |Calabria |LB |
| it-bc |IT-77 |Basilicata |Basilicata |BC |
| it-pu |IT-75 |Apulia |Puglia |PU |
| it-ab |IT-65 |Abruzzo |Abruzzo |AB |

### Mexico: States

| ID | abreviatura | iso | name | name-en | postal |
| --- | --- | --- | --- | --- | --- |
| mx-zac |Zac. |MX-ZAC |Zacatecas |Zacatecas |ZA |
| mx-yuc |Yuc. |MX-YUC |Yucat??n |Yucatan |YU |
| mx-ver |Ver. |MX-VER |Veracruz |Veracruz |VE |
| mx-tla |Tlax. |MX-TLA |Tlaxcala |Tlaxcala |TL |
| mx-tam |Tamps. |MX-TAM |Tamaulipas |Tamaulipas |TM |
| mx-tab |Tab. |MX-TAB |Tabasco |Tabasco |TB |
| mx-son |Son. |MX-SON |Sonora |Sonora |SO |
| mx-sin |Sin. |MX-SIN |Sinaloa |Sinaloa |SI |
| mx-slp |S.L.P. |MX-SLP |San Luis Potos?? |San Luis Potosi |SL |
| mx-roo |Q.R. |MX-ROO |Quintana Roo |Quintana Roo |QR |
| mx-que |Qro. |MX-QUE |Quer??taro |Queretaro |QE |
| mx-pue |Pue. |MX-PUE |Puebla |Puebla |PU |
| mx-oax |Oax. |MX-OAX |Oaxaca |Oaxaca |OA |
| mx-nle |N.L. |MX-NLE |Nuevo Le??n |Nuevo Leon |NL |
| mx-nay |Nay. |MX-NAY |Nayarit |Nayarit |NA |
| mx-mor |Mor. |MX-MOR |Morelos |Morelos |MR |
| mx-mic |Mich. |MX-MIC |Michoac??n |Michoacan |MC |
| mx-mex |M??x. |MX-MEX |Estado de M??xico |Mexico State |MX |
| mx-jal |Jal. |MX-JAL |Jalisco |Jalisco |JA |
| mx-hid |Hgo. |MX-HID |Hidalgo |Hidalgo |HI |
| mx-gro |Gro. |MX-GRO |Guerrero |Guerrero |GR |
| mx-gua |Gto. |MX-GUA |Guanajuato |Guanajuato |GT |
| mx-dur |Dgo. |MX-DUR |Durango |Durango |DU |
| mx-dif |CDMX. |MX-DIF |Ciudad de M??xico |Mexico City |DF |
| mx-col |Col. |MX-COL |Colima |Colima |CL |
| mx-coa |Coah. |MX-COA |Coahuila |Coahuila |CA |
| mx-chh |Chih. |MX-CHH |Chihuahua |Chihuahua |CH |
| mx-chp |Chis. |MX-CHP |Chiapas |Chiapas |CP |
| mx-cam |Camp. |MX-CAM |Campeche |Campeche |CM |
| mx-bcs |B.C.S. |MX-BCS |Baja California Sur |Baja California Sur |BS |
| mx-bcn |B.C. |MX-BCN |Baja California |Baja California |BN |
| mx-agu |Ags. |MX-AGU |Aguascalientes |Aguascalientes |AG |

### Netherlands: Provinces

| ID | iso | name | name-en |
| --- | --- | --- | --- |
| nl-zh |NL-ZH |Zuid-Holland |South Holland |
| nl-ze |NL-ZE |Zeeland |Zeeland |
| nl-ut |NL-UT |Utrecht |Utrecht |
| nl-ov |NL-OV |Overijssel |Overijssel |
| nl-nh |NL-NH |Noord-Holland |North Holland |
| nl-nb |NL-NB |Noord-Brabant |North Brabant |
| nl-li |NL-LI |Limburg |Limburg |
| nl-gr |NL-GR |Groningen |Groningen |
| nl-ge |NL-GE |Gelderland |Gelderland |
| nl-fr |NL-FR |Frysl??n |Friesland |
| nl-fl |NL-FL |Flevoland |Flevoland |
| nl-dr |NL-DR |Drenthe |Drenthe |

### UK: Countries

| ID | iso | name |
| --- | --- | --- |
| gb-wls |GB-WLS |Wales |
| gb-sct |GB-SCT |Scotland |
| gb-nir |GB-NIR |Northern Ireland |
| gb-eng |GB-ENG |England |

### USA: States

| ID | name | postal |
| --- | --- | --- |
| us-mi |Michigan |MI |
| us-ak |Alaska |AK |
| us-hi |Hawaii |HI |
| us-fl |Florida |FL |
| us-la |Louisiana |LA |
| us-ar |Arkansas |AR |
| us-sc |South Carolina |SC |
| us-ga |Georgia |GA |
| us-ms |Mississippi |MS |
| us-al |Alabama |AL |
| us-nm |New Mexico |NM |
| us-tx |Texas |TX |
| us-tn |Tennessee |TN |
| us-nc |North Carolina |NC |
| us-ok |Oklahoma |OK |
| us-az |Arizona |AZ |
| us-mo |Missouri |MO |
| us-va |Virginia |VA |
| us-ks |Kansas |KS |
| us-ky |Kentucky |KY |
| us-co |Colorado |CO |
| us-md |Maryland |MD |
| us-wv |West Virginia |WV |
| us-de |Delaware |DE |
| us-dc |District of Columbia |DC |
| us-il |Illinois |IL |
| us-oh |Ohio |OH |
| us-ca |California |CA |
| us-ut |Utah |UT |
| us-nv |Nevada |NV |
| us-in |Indiana |IN |
| us-nj |New Jersey |NJ |
| us-ri |Rhode Island |RI |
| us-ct |Connecticut |CT |
| us-pa |Pennsylvania |PA |
| us-ny |New York |NY |
| us-ne |Nebraska |NE |
| us-ma |Massachusetts |MA |
| us-ia |Iowa |IA |
| us-nh |New Hampshire |NH |
| us-or |Oregon |OR |
| us-mn |Minnesota |MN |
| us-vt |Vermont |VT |
| us-id |Idaho |ID |
| us-wi |Wisconsin |WI |
| us-wy |Wyoming |WY |
| us-sd |South Dakota |SD |
| us-nd |North Dakota |ND |
| us-me |Maine |ME |
| us-mt |Montana |MT |
| us-wa |Washington |WA |

## Next steps

* [Matrix visual in Power BI](desktop-matrix-visual.md)

* [Visualization types in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
