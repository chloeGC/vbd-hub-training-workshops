# (PART) Workshop 2:  Data Wrangling with Hub Search & ohvbd {-}

# Introduction

## Learning objectives

**By the end of this workshop, you should be able to:**

1. Use VBD Hub resources to access shared VBD datasets.
2. Effectively wrangle real-world VDB datasets ready for further analysis.
3. Build collaborative, professional connections within the VBD community.


## Prerequisites

**Before participating in this workshop, you should have:**

- Foundational knowledge of programming in R and RStudio, including running code, installing packages, and working within scripts.
- Some experience of formatting datasets in R, such as importing .csv files and viewing dataframes.
- Basic understanding of VBD biology, including common vectors and pathogen transmission.


## Training Plan
### Pre- live session content
This is to be completed ahead of the **Live Session**.
Content will be available on the Hub under [Learning Resources](https://vbdhub.org/resources/learn).


The [VBD Hub Forum](https://forum.vbdhub.org/t/online-training-data-visualisations-in-r/159) is available for support and networking.


### Live session
10:00 - 13:00 on Thursday 26th March, via Teams.


Content will be made available on the Hub under [Learning Resources](https://vbdhub.org/resources/learn) on the day of the **Live Session**.


### Post- Live Session Challenge Task
Multi-stage task to be completed independently after the **Live Session**. The stages will increase in difficulty and provide an opportunity to apply what you have learnt to real VBD datasets.


Content will be posted on the VBD Hub under [Learning Resources](https://vbdhub.org/resources/learn) on the day of the Live Session.
The [VBD Hub Forum](https://forum.vbdhub.org/t/challenge-task-q-a-data-visualisations-in-r/160) will be available for support.


## Navigating Course Content
Many of the tasks in this workshop will be in a workbook-style format and will walk you through how to code specific functions and models. We encourage you to type this code yourself to practice syntax and gain the most out of the content provided, rather than copying and pasting.


All coding through this workshop will be done in Rstudio, a user friendly IDE (integrated development environment) for R language. Please ensure you have R and RStudio installed and updated ahead of the **Live Session**. If you do not already have R or RStudio installed, see [here](https://posit.co/download/rstudio-desktop/).


## Available Materials & Support
If you need a quick reminder of basic coding in R, additional materials and cheat sheets can be found here:

- [Biological Computing in R](https://vbdhub.org/MQB/notebooks/r.html)
- [Data Management (read up to Data visualization)](https://vbdhub.org/resources/learn/training-2025/data-management-and-visualisation)
- [Basic Hypothesis Testing](https://vbdhub.org/MQB/notebooks/t-f-tests.html)
-	[RStudio IDE Cheatsheet](https://rstudio.github.io/cheatsheets/rstudio-ide.pdf)
-	[Data Wrangling with dplyr Cheatsheet](https://rstudio.github.io/cheatsheets/data-transformation.pdf) 


If you need additional support through this workshop:

- The [**Forum**](http://forum.vbdhub.org) is a good place to discuss queries with fellow participants.
- Demonstrators will be available to help during the **Live Session**.
- During the **Challenge Task**, a specific discussion on the Forum will be open to ask demonstrators questions. One-to-one video support will also be available if required.
- For technical support (e.g. trouble accessing content or joining the Teams link), please contact support@vbdhub.org. This is **not** for coding or statistical support.


## Installing Packages
This workshop will use several R packages throughout, please install these ahead of the **Live Session**.


**Packages for this workshop:**

- `ohvbd`
- `tidyr`


::: {.rmdtip}
**Reminder:** To install packages in R, use the `install.packages()` command.


To install one package:
``` r
install.packages("ggplot2")
```

To install multiple packages:
``` r
install.packages(c("ggplot2", "dplyr", "tidyr"))
```
:::


# Pre- Live Session Content


## VBD Hub Overview
The **VBD Hub** is a non-profit, open-source project funded by UKRI and Defra, which aims to improve accessibility and information sharing. To do this, the project builds infrastructure and tools to allow researchers to combine knowledge and share data within the VBD research community and with policymakers.  


The hub site is home to resources to help your research, and spaces for collaboration and networking with the VBD community.


In this session, we will cover some of the key resources available through the **VBD Hub** and how to use them effectively. 


## Navigating VBD Hub
The [VBD Hub website](https://vbdhub.org/) is straightforward to navigate, but if you haven’t used it before it can be useful to know what information you can find and where.


### Home
When you first visit the site, you will see the **Home** screen with a summary of what the Hub is. 


The **Getting started** boxes provide user-friendly links to some of the key information and resources available on the Hub site:

- **Find data**
- **Share data**
- **Learn**


The **Roadmap** covers the progress of the VBD Hub since July 2024. As the Hub continues to grow, new developments will be updated here. 


![VBD Hub Home screen](images/homescreen.png "alt text"){width=100%}


### Find Data
The **Find Data** tab is where we find the **Hub Search** resource. This can be used to find open access databases from over 10,000 records within the VBD Hub system. The filter section allows you to refine your search using a number of parameters. 


You may notice this page is linked under the **Getting started** section of the **Home** page.


We will explore this resource in more detail shortly.


![VBD Hub Search](images/finddata.png "alt text"){width=100%}


### About
Under the **About** tab, you will find a more in depth overview of the **VBD Hub**, the aims of the Hub, and the critical impact of a platform like this. 


There is also a list of the **Core team**, and their involvement within the Hub.


![VBD Hub About page](images/about.png "alt text"){width=100%}


### Resources
The Resources tab offers a drop-down menu of four pages:

- **R package** - an overview of the **ohvbd package** for R developed by the Hub, and latest release patch notes. We will explore this in more detail shortly.
- **FAIR data** - this page outlines FAIR data principles (Findable, Accessible, Interoperable, Reusable), which are important to consider with open-access data.
- **How to share?** - provides guidance on standards and privacy of data sharing, and standard operating procedures for specific data types.
- **Learn** - here, you can find learning resources developed by the Hub, such as the content for this workshop!


You may notice some of these are also linked under the **Getting started** section of the **Home** page.


![VBD Hub Resources](images/resources.png "alt text"){width=100%}


### Community
The **Community** tab also has a drop-down menu, with links to:

- **Forum** - this opens a new tab to the **VBD Hub Forum**, a space to connect with the VBD community and discuss a variety of topics. We will explore this in more detail shortly.
- **Blog** - announcements will be posted in this space with details of Hub development, contributions, and upcoming opportunities, including this training.


![VBD Hub Community](images/community.png "alt text"){width=100%}


## VBD Hub Resources & How to Use Them


### Hub Search
As we have seen, the **Hub Search** can be found under the **Find Data** tab on the **VBD Hub** site. 

**Hub Search** makes discovering datasets much easier by searching multiple data sources in one place, allowing you to identify datasets relevant to your research and explore metadata before downloading several individual datasets.

On the **Find Data** page, we can find a **Filter** menu with several drop down options:

- **Category** - filter your search based on data type. Hub Search currently allows you to filter Occurrence, Abundance, Traits, Proteomics, and Epidemiological data. 
- **Database** - filter by source database - VecDyn, VecTraits, GBIF, ProteomeXchange, and VBD Hub.
- **Published** - set the start date and end date of the publications you want to search.
- **Location** - draw polygons around the geographical area you want to search.
- **Taxonomy** - search for a specific taxon.
- **Full text search** - filter your search by more specific text fields.


![Hub Search Filter](images/filter.png "alt text")


::: {.rmdnote}
**Note:** Through this workshop, we will discuss resources that search and retrieve data from several open-access VBD databases. If you are unfamiliar with these databases, they include:

- **VecDyn** - vector population dynamics, including how vector populations change over time and across locations. 
- **VecTraits** - vector trait data, such as life history, behavioural, and ecological traits. 
- **GBIF** - species occurrence records on the location and time vector species have been observed.
- **ProteomeXchange** - proteomic and molecular vector data.
- **AreaData** - environmental and geographic data. 
- **NCBI**- genetic and genomic data.

:::


Once we have searched for specific data, we can review the search results. Results typically include the dataset name, the source database, and a brief description of the dataset. 


Clicking on resulting datasets lets us explore that data in more detail, including metadata, geographic or temporal coverage, and access or download options.


After reviewing your data, you might decide to refine your search depending on:

- **Relevance** - does the resulting dataset answer your research question?
- **Coverage** - does the resulting data include the right location or time period for your research?
- **Structure** - is the data in a usable format or file type?


You can refine your search by adding more parameters, trying more specific key words, or combining terms, such as “species + country”.


::: {.rmdtip}
**Tip:** Start broad, then narrow your search by adding more parameters where necessary.


Remember, you don’t have to download everything - you should focus on datasets that are the most useful to you.
:::


### Hub Search Task
Use the **Hub Search** to find datasets on abundance of *Ixodes ricinus*. How many results did your search return?


Select one dataset from your search and identify the:

- Dataset name
- Publication date
- Source database


Use the **Response Form** at the end of the **Pre- Live Session** content to record your answers.


### ohvbd package
**ohvbd** is an R package developed by the **VBD Hub** that allows you to search for and retrieve data within R, without needing to download files from multiple sources.


It connects to several VBD database sources at once, including **VBD Hub** (vbdhub), **VecTraits** (vt), **VecDyn** (vd), **GBIF** (gbif), and **AreaData** (px), and pulls datasets directly into your R workflow.

You can install **ohvbd** from CRAN by running this code in R:



``` r
library(ohvbd)
```


**ohvbd** uses a piped workflow, which allows us to build on each step of our code. For example, if we wanted to search for data on *Ixodes ricinus* from the **VecTraits** database, we can run:


``` r
ixodes_ricinus_data <- search_hub("Ixodes ricinus") |>
  filter_db("vt") |>
  fetch(connections = 8) |>
  glean()
```


Let’s break this down a bit so we can understand what is happening:

- `search_hub()` - searches for datasets matching your criteria, here we want to search for "Ixodes ricinus".
- `filter_db()` - narrows results to a specific database, in this case “vt”, VecTraits.
- `fetch()` - retrieves the data.
- `glean()` - converts the data into a usable table format.


::: {.rmdtip}
**Tip:** We can consider a basic search with **ohvbd** as 4 stages:

- 1. **Find** the data we are looking for.
- 2. **Filter** the search field.
- 3. **Fetch** the data.
- 4. **Format** the data.

:::


The data we retrieve from **ohvbd** is often raw and its formatting depends on the original source database. After using the package, you will then need to wrangle and analyse the data yourself.


We can make our search more refined by adding more search parameters and retrieving the IDs for any datasets that match those parameters:


``` r
search_hub(
  query = "",
  db = c("vt", "vd", "gbif", "px"),
  fromdate = NULL,
  todate = NULL,
  locationpoly = NULL,
  taxonomy = NULL,
  exact = FALSE,
  withoutpublished = TRUE,
  returnlist = FALSE
)
```


Let’s also break this down so we can understand what each argument does:

- **query** - what you are searching for, such as a species name.
- **db** - which databases we want to search
- **fromdate** - the date we want to search from. 
- **todate** - the date we want to search up to. 
- **locationpoly** - set our search to a geographic area.
- **taxonomy** - advanced search by species ID.
- **exact** - whether to return exact matches only.
- **withoutpublished** - whether to return results without a publishing date when filtering by date.
- **returnlist** - return the raw output list of datasets, rather than a formatted dataframe.


::: {.rmdimportant}
**Important:** When adding parameters, you do not need to use all of these arguments at once. Start simple and build a pipeline that aligns with your search aims.
:::


::: {.rmdtip}
**Tip:** **fromdate** and **todate** use ISO format: yyyy-mm-dd.
:::


### ohvbd Task
Let’s have a go at retrieving data using ***ohvbd**. Consider what we would want to include to search for data on *Aedes aegypti* from **VecTraits**.


We first want to define our search string using `search_hub()`:


``` r
search_hub("Aedes aegypti")
```


Next, we want to filter our search so that data is only retrieved from **VecTraits**:


``` r
filter_db("vt")
```


Now we can combine these lines of code to retrieve and format the data:



``` r
aedes_aegypti_data <- search_hub("Aedes aegypti", db = "vt") |>
 filter_db("vt") |>
 fetch(connections = 8) |>
 glean()
```

Notice we also added `fetch()` and `glean()` to our pipeline. These ensure the data is downloaded and formatted for further wrangling and analysis.


Once we have searched and retrieved the data we want, we can inspect the dataset:



``` r
head(aedes_aegypti_data)
#> <ohvbd.data.frame>
#> Database: vt
#>       Id DatasetID IndividualID OriginalID
#> 1 110069       893                   SK055
#> 2 110070       893                   SK055
#> 3 110065       892                   SK056
#> 4 110066       892                   SK056
#> 5 110067       892                   SK056
#> 6 110068       892                   SK056
#>   OriginalTraitName            OriginalTraitDef
#> 1  development time mean duration of life stage
#> 2  development time mean duration of life stage
#> 3         body size            mean wing length
#> 4         body size            mean wing length
#> 5         body size            mean wing length
#> 6         body size            mean wing length
#>   StandardisedTraitName StandardisedTraitDef
#> 1                    NA                   NA
#> 2                    NA                   NA
#> 3                    NA                   NA
#> 4                    NA                   NA
#> 5                    NA                   NA
#> 6                    NA                   NA
#>   OriginalTraitValue OriginalTraitUnit OriginalErrorPos
#> 1              21.00              days               NA
#> 2              21.00              days               NA
#> 3               3.01                mm             0.12
#> 4               3.30                mm             0.10
#> 5               2.80                mm             0.10
#> 6               3.22                mm             0.03
#>   OriginalErrorNeg OriginalErrorUnit StandardisedTraitValue
#> 1               NA              <NA>                     NA
#> 2               NA              <NA>                     NA
#> 3             0.12                SE                     NA
#> 4             0.10                SE                     NA
#> 5             0.10                SE                     NA
#> 6             0.03                SE                     NA
#>   StandardisedTraitUnit StandardisedErrorPos
#> 1                    NA                   NA
#> 2                    NA                   NA
#> 3                    NA                   NA
#> 4                    NA                   NA
#> 5                    NA                   NA
#> 6                    NA                   NA
#>   StandardisedErrorNeg StandardisedErrorUnit Replicates
#> 1                   NA                    NA         NA
#> 2                   NA                    NA         NA
#> 3                   NA                    NA         NA
#> 4                   NA                    NA         NA
#> 5                   NA                    NA         NA
#> 6                   NA                    NA         NA
#>       Habitat   LabField ArenaValue ArenaUnit ArenaValueSI
#> 1 terrestrial laboratory         NA        NA           NA
#> 2 terrestrial laboratory         NA        NA           NA
#> 3 terrestrial laboratory         NA        NA           NA
#> 4 terrestrial laboratory         NA        NA           NA
#> 5 terrestrial laboratory         NA        NA           NA
#> 6 terrestrial laboratory         NA        NA           NA
#>   ArenaUnitSI AmbientTemp AmbientTempMethod AmbientTempUnit
#> 1          NA          NA                NA              NA
#> 2          NA          NA                NA              NA
#> 3          NA          NA                NA              NA
#> 4          NA          NA                NA              NA
#> 5          NA          NA                NA              NA
#> 6          NA          NA                NA              NA
#>   AmbientLight AmbientLightUnit SecondStressor
#> 1           NA               NA           <NA>
#> 2           NA               NA           <NA>
#> 3           NA               NA           <NA>
#> 4           NA               NA           <NA>
#> 5           NA               NA           <NA>
#> 6           NA               NA           <NA>
#>                                               SecondStressorDef
#> 1 estimate of total food (tetramin) provided per larvae per day
#> 2 estimate of total food (tetramin) provided per larvae per day
#> 3 estimate of total food (tetramin) provided per larvae per day
#> 4 estimate of total food (tetramin) provided per larvae per day
#> 5 estimate of total food (tetramin) provided per larvae per day
#> 6 estimate of total food (tetramin) provided per larvae per day
#>   SecondStressorValue SecondStressorUnit TimeStart TimeEnd
#> 1           0.0952381                 mg      2013    2013
#> 2           0.4761905                 mg      2013    2013
#> 3           0.0952381                 mg      2013    2013
#> 4           0.4761905                 mg      2013    2013
#> 5           0.0952381                 mg      2013    2013
#> 6           0.4761905                 mg      2013    2013
#>   TotalObsTimeValue TotalObsTimeUnit TotalObsTimeValueSI
#> 1                NA               NA                  NA
#> 2                NA               NA                  NA
#> 3                NA               NA                  NA
#> 4                NA               NA                  NA
#> 5                NA               NA                  NA
#> 6                NA               NA                  NA
#>   TotalObsTimeUnitSI TotalObsTimeNotes ResRepValue
#> 1                 NA                NA          NA
#> 2                 NA                NA          NA
#> 3                 NA                NA          NA
#> 4                 NA                NA          NA
#> 5                 NA                NA          NA
#> 6                 NA                NA          NA
#>   ResRepUnit ResRepValueSI ResRepUnitSI
#> 1         NA            NA           NA
#> 2         NA            NA           NA
#> 3         NA            NA           NA
#> 4         NA            NA           NA
#> 5         NA            NA           NA
#> 6         NA            NA           NA
#>                                                 Location
#> 1 Instituto Oswaldo Cruz Fundacao Oswaldo Cruz RJ Brazil
#> 2 Instituto Oswaldo Cruz Fundacao Oswaldo Cruz RJ Brazil
#> 3 Instituto Oswaldo Cruz Fundacao Oswaldo Cruz RJ Brazil
#> 4 Instituto Oswaldo Cruz Fundacao Oswaldo Cruz RJ Brazil
#> 5 Instituto Oswaldo Cruz Fundacao Oswaldo Cruz RJ Brazil
#> 6 Instituto Oswaldo Cruz Fundacao Oswaldo Cruz RJ Brazil
#>   LocationType OriginalLocationDate LocationDate
#> 1       colony                   NA         <NA>
#> 2       colony                   NA         <NA>
#> 3       colony                   NA         <NA>
#> 4       colony                   NA         <NA>
#> 5       colony                   NA         <NA>
#> 6       colony                   NA         <NA>
#>   LocationDatePrecision CoordinateType  Latitude Longitude
#> 1                     0        decimal -22.87736 -43.24356
#> 2                     0        decimal -22.87736 -43.24356
#> 3                     0        decimal -22.87736 -43.24356
#> 4                     0        decimal -22.87736 -43.24356
#> 5                     0        decimal -22.87736 -43.24356
#> 6                     0        decimal -22.87736 -43.24356
#>        Interactor1 Interactor1Common Interactor1Wholepart
#> 1 Aedes albopictus              <NA>                   NA
#> 2 Aedes albopictus              <NA>                   NA
#> 3 Aedes albopictus              <NA>                   NA
#> 4 Aedes albopictus              <NA>                   NA
#> 5 Aedes albopictus              <NA>                   NA
#> 6 Aedes albopictus              <NA>                   NA
#>   Interactor1WholePartType Interactor1Number
#> 1                       NA               100
#> 2                       NA                20
#> 3                       NA               100
#> 4                       NA                20
#> 5                       NA               100
#> 6                       NA                20
#>   Interactor1Kingdom Interactor1Phylum Interactor1Class
#> 1           Animalia        Arthropoda          Insecta
#> 2           Animalia        Arthropoda          Insecta
#> 3           Animalia        Arthropoda          Insecta
#> 4           Animalia        Arthropoda          Insecta
#> 5           Animalia        Arthropoda          Insecta
#> 6           Animalia        Arthropoda          Insecta
#>   Interactor1Order Interactor1Family Interactor1Genus
#> 1          Diptera         Culicidae            Aedes
#> 2          Diptera         Culicidae            Aedes
#> 3          Diptera         Culicidae            Aedes
#> 4          Diptera         Culicidae            Aedes
#> 5          Diptera         Culicidae            Aedes
#> 6          Diptera         Culicidae            Aedes
#>   Interactor1Species      Interactor1Stage Interactor1Sex
#> 1         albopictus juvenile (L1 to pupa)  indeterminate
#> 2         albopictus juvenile (L1 to pupa)  indeterminate
#> 3         albopictus                 adult         female
#> 4         albopictus                 adult         female
#> 5         albopictus                 adult         female
#> 6         albopictus                 adult         female
#>   Interactor1Temp Interactor1TempUnit Interactor1TempMethod
#> 1              25             Celsius                    NA
#> 2              25             Celsius                    NA
#> 3              25             Celsius                    NA
#> 4              25             Celsius                    NA
#> 5              25             Celsius                    NA
#> 6              25             Celsius                    NA
#>   Interactor1GrowthTemp Interactor1GrowthTempUnit
#> 1                    NA                      <NA>
#> 2                    NA                      <NA>
#> 3                    NA                      <NA>
#> 4                    NA                      <NA>
#> 5                    NA                      <NA>
#> 6                    NA                      <NA>
#>   Interactor1GrowthDur Interactor1GrowthdDurUnit
#> 1                   NA                        NA
#> 2                   NA                        NA
#> 3                   NA                        NA
#> 4                   NA                        NA
#> 5                   NA                        NA
#> 6                   NA                        NA
#>   Interactor1GrowthType Interactor1Acc Interactor1AccTemp
#> 1                    NA             NA                 NA
#> 2                    NA             NA                 NA
#> 3                    NA             NA                 NA
#> 4                    NA             NA                 NA
#> 5                    NA             NA                 NA
#> 6                    NA             NA                 NA
#>   Interactor1AccTempNotes Interactor1AccTime
#> 1                      NA                 NA
#> 2                      NA                 NA
#> 3                      NA                 NA
#> 4                      NA                 NA
#> 5                      NA                 NA
#> 6                      NA                 NA
#>   Interactor1AccTimeNotes Interactor1AccTimeUnit
#> 1                      NA                     NA
#> 2                      NA                     NA
#> 3                      NA                     NA
#> 4                      NA                     NA
#> 5                      NA                     NA
#> 6                      NA                     NA
#>   Interactor1OrigTemp Interactor1OrigTempNotes
#> 1                  NA                       NA
#> 2                  NA                       NA
#> 3                  NA                       NA
#> 4                  NA                       NA
#> 5                  NA                       NA
#> 6                  NA                       NA
#>   Interactor1OrigTime Interactor1OrigTimeNotes
#> 1                  NA                       NA
#> 2                  NA                       NA
#> 3                  NA                       NA
#> 4                  NA                       NA
#> 5                  NA                       NA
#> 6                  NA                       NA
#>   Interactor1OrigTimeUnit Interactor1EquilibTimeValue
#> 1                      NA                          NA
#> 2                      NA                          NA
#> 3                      NA                          NA
#> 4                      NA                          NA
#> 5                      NA                          NA
#> 6                      NA                          NA
#>   Interactor1EquilibTimeUnit Interactor1Size
#> 1                         NA            <NA>
#> 2                         NA            <NA>
#> 3                         NA            <NA>
#> 4                         NA            <NA>
#> 5                         NA            <NA>
#> 6                         NA            <NA>
#>   Interactor1SizeUnit Interactor1SizeType Interactor1SizeSI
#> 1                <NA>                <NA>              <NA>
#> 2                <NA>                <NA>              <NA>
#> 3                <NA>                <NA>              <NA>
#> 4                <NA>                <NA>              <NA>
#> 5                <NA>                <NA>              <NA>
#> 6                <NA>                <NA>              <NA>
#>   Interactor1SizeUnitSI Interactor1DenValue
#> 1                  <NA>                <NA>
#> 2                  <NA>                <NA>
#> 3                  <NA>                <NA>
#> 4                  <NA>                <NA>
#> 5                  <NA>                <NA>
#> 6                  <NA>                <NA>
#>   Interactor1DenUnit Interactor1DenTypeSI
#> 1           juvenile                   NA
#> 2           juvenile                   NA
#> 3              adult                   NA
#> 4              adult                   NA
#> 5              adult                   NA
#> 6              adult                   NA
#>   Interactor1DenValueSI Interactor1DenUnitSI
#> 1                    NA                   NA
#> 2                    NA                   NA
#> 3                    NA                   NA
#> 4                    NA                   NA
#> 5                    NA                   NA
#> 6                    NA                   NA
#>   Interactor1MassValueSI Interactor1MassUnitSI Interactor2
#> 1                     NA                    NA   None None
#> 2                     NA                    NA   None None
#> 3                     NA                    NA   None None
#> 4                     NA                    NA   None None
#> 5                     NA                    NA   None None
#> 6                     NA                    NA   None None
#>   Interactor2Common Interactor2Kingdom Interactor2Phylum
#> 1                NA                 NA                NA
#> 2                NA                 NA                NA
#> 3                NA                 NA                NA
#> 4                NA                 NA                NA
#> 5                NA                 NA                NA
#> 6                NA                 NA                NA
#>   Interactor2Class Interactor2Order Interactor2Family
#> 1               NA               NA                NA
#> 2               NA               NA                NA
#> 3               NA               NA                NA
#> 4               NA               NA                NA
#> 5               NA               NA                NA
#> 6               NA               NA                NA
#>   Interactor2Genus Interactor2Species Interactor2Stage
#> 1               NA                 NA               NA
#> 2               NA                 NA               NA
#> 3               NA                 NA               NA
#> 4               NA                 NA               NA
#> 5               NA                 NA               NA
#> 6               NA                 NA               NA
#>   Interactor2Sex Interactor2Temp Interactor2TempUnit
#> 1             NA              NA                  NA
#> 2             NA              NA                  NA
#> 3             NA              NA                  NA
#> 4             NA              NA                  NA
#> 5             NA              NA                  NA
#> 6             NA              NA                  NA
#>   Interactor2TempMethod Interactor2GrowthTemp
#> 1                    NA                    NA
#> 2                    NA                    NA
#> 3                    NA                    NA
#> 4                    NA                    NA
#> 5                    NA                    NA
#> 6                    NA                    NA
#>   Interactor2GrowthTempUnit Interactor2GrowthDur
#> 1                        NA                   NA
#> 2                        NA                   NA
#> 3                        NA                   NA
#> 4                        NA                   NA
#> 5                        NA                   NA
#> 6                        NA                   NA
#>   Interactor2GrowthDurUnit Interactor2GrowthType
#> 1                       NA                    NA
#> 2                       NA                    NA
#> 3                       NA                    NA
#> 4                       NA                    NA
#> 5                       NA                    NA
#> 6                       NA                    NA
#>   Interactor2Acc Interactor2AccTemp Interactor2AccTempNotes
#> 1             NA                 NA                      NA
#> 2             NA                 NA                      NA
#> 3             NA                 NA                      NA
#> 4             NA                 NA                      NA
#> 5             NA                 NA                      NA
#> 6             NA                 NA                      NA
#>   Interactor2AccTime Interactor2AccTimeNotes
#> 1                 NA                      NA
#> 2                 NA                      NA
#> 3                 NA                      NA
#> 4                 NA                      NA
#> 5                 NA                      NA
#> 6                 NA                      NA
#>   Interactor2AccTimeUnit Interactor2OrigTemp
#> 1                     NA                  NA
#> 2                     NA                  NA
#> 3                     NA                  NA
#> 4                     NA                  NA
#> 5                     NA                  NA
#> 6                     NA                  NA
#>   Interactor2OrigTempNotes Interactor2OrigTime
#> 1                       NA                  NA
#> 2                       NA                  NA
#> 3                       NA                  NA
#> 4                       NA                  NA
#> 5                       NA                  NA
#> 6                       NA                  NA
#>   Interactor2OrigTimeNotes Interactor2OrigTimeUnit
#> 1                       NA                      NA
#> 2                       NA                      NA
#> 3                       NA                      NA
#> 4                       NA                      NA
#> 5                       NA                      NA
#> 6                       NA                      NA
#>   Interactor2EquilibTimeValue Interactor2EquilibTimeUnit
#> 1                          NA                         NA
#> 2                          NA                         NA
#> 3                          NA                         NA
#> 4                          NA                         NA
#> 5                          NA                         NA
#> 6                          NA                         NA
#>   Interactor2Size Interactor2SizeUnit Interactor2SizeType
#> 1              NA                  NA                  NA
#> 2              NA                  NA                  NA
#> 3              NA                  NA                  NA
#> 4              NA                  NA                  NA
#> 5              NA                  NA                  NA
#> 6              NA                  NA                  NA
#>   Interactor2SizeSI Interactor2SizeUnitSI
#> 1                NA                    NA
#> 2                NA                    NA
#> 3                NA                    NA
#> 4                NA                    NA
#> 5                NA                    NA
#> 6                NA                    NA
#>   Interactor2DenValue Interactor2DenUnit
#> 1                  NA                 NA
#> 2                  NA                 NA
#> 3                  NA                 NA
#> 4                  NA                 NA
#> 5                  NA                 NA
#> 6                  NA                 NA
#>   Interactor2DenTypeSI Interactor2DenValueSI
#> 1                   NA                    NA
#> 2                   NA                    NA
#> 3                   NA                    NA
#> 4                   NA                    NA
#> 5                   NA                    NA
#> 6                   NA                    NA
#>   Interactor2DenUnitSI Interactor2MassValueSI
#> 1                   NA                     NA
#> 2                   NA                     NA
#> 3                   NA                     NA
#> 4                   NA                     NA
#> 5                   NA                     NA
#> 6                   NA                     NA
#>   Interactor2MassUnitSI PhysicalProcess PhysicalProcess_1
#> 1                    NA              NA                NA
#> 2                    NA              NA                NA
#> 3                    NA              NA                NA
#> 4                    NA              NA                NA
#> 5                    NA              NA                NA
#> 6                    NA              NA                NA
#>   PhysicalProcess_2 FigureTable
#> 1                NA    figure 1
#> 2                NA    figure 1
#> 3                NA    figure 1
#> 4                NA    figure 1
#> 5                NA    figure 1
#> 6                NA    figure 1
#>                                                                                                                                                   Citation
#> 1 Lima-Camara et al 2022. Body size does not affect locomotor activity of Aedes aegypti and Aedes albopictus females (Diptera:Culicidae). Acta Tropica 231
#> 2 Lima-Camara et al 2022. Body size does not affect locomotor activity of Aedes aegypti and Aedes albopictus females (Diptera:Culicidae). Acta Tropica 231
#> 3 Lima-Camara et al 2022. Body size does not affect locomotor activity of Aedes aegypti and Aedes albopictus females (Diptera:Culicidae). Acta Tropica 231
#> 4 Lima-Camara et al 2022. Body size does not affect locomotor activity of Aedes aegypti and Aedes albopictus females (Diptera:Culicidae). Acta Tropica 231
#> 5 Lima-Camara et al 2022. Body size does not affect locomotor activity of Aedes aegypti and Aedes albopictus females (Diptera:Culicidae). Acta Tropica 231
#> 6 Lima-Camara et al 2022. Body size does not affect locomotor activity of Aedes aegypti and Aedes albopictus females (Diptera:Culicidae). Acta Tropica 231
#>                                                                                                                                                       CuratedByCitation
#> 1 Brass et al. 2024. Role of vector phenotypic plasticity in disease transmission as illustrated by the spread of dengue virus by Aedes albopictus. Nat Commun 15: 7823
#> 2 Brass et al. 2024. Role of vector phenotypic plasticity in disease transmission as illustrated by the spread of dengue virus by Aedes albopictus. Nat Commun 15: 7823
#> 3 Brass et al. 2024. Role of vector phenotypic plasticity in disease transmission as illustrated by the spread of dengue virus by Aedes albopictus. Nat Commun 15: 7823
#> 4 Brass et al. 2024. Role of vector phenotypic plasticity in disease transmission as illustrated by the spread of dengue virus by Aedes albopictus. Nat Commun 15: 7823
#> 5 Brass et al. 2024. Role of vector phenotypic plasticity in disease transmission as illustrated by the spread of dengue virus by Aedes albopictus. Nat Commun 15: 7823
#> 6 Brass et al. 2024. Role of vector phenotypic plasticity in disease transmission as illustrated by the spread of dengue virus by Aedes albopictus. Nat Commun 15: 7823
#>                 CuratedByDOI
#> 1 10.1038/s41467-024-52144-5
#> 2 10.1038/s41467-024-52144-5
#> 3 10.1038/s41467-024-52144-5
#> 4 10.1038/s41467-024-52144-5
#> 5 10.1038/s41467-024-52144-5
#> 6 10.1038/s41467-024-52144-5
#>                                 DOI SubmittedBy
#> 1 10.1016/j.actatropica.2022.106430 Sarah Kelly
#> 2 10.1016/j.actatropica.2022.106430 Sarah Kelly
#> 3 10.1016/j.actatropica.2022.106430 Sarah Kelly
#> 4 10.1016/j.actatropica.2022.106430 Sarah Kelly
#> 5 10.1016/j.actatropica.2022.106430 Sarah Kelly
#> 6 10.1016/j.actatropica.2022.106430 Sarah Kelly
#>         ContributorEmail Notes   DefaultChartXaxis
#> 1 s.kelly@imperial.ac.uk  <NA> SecondStressorValue
#> 2 s.kelly@imperial.ac.uk  <NA> SecondStressorValue
#> 3 s.kelly@imperial.ac.uk  <NA> SecondStressorValue
#> 4 s.kelly@imperial.ac.uk  <NA> SecondStressorValue
#> 5 s.kelly@imperial.ac.uk  <NA> SecondStressorValue
#> 6 s.kelly@imperial.ac.uk  <NA> SecondStressorValue
#>   DefaultChartCategory
#> 1             Location
#> 2             Location
#> 3             Location
#> 4             Location
#> 5             Location
#> 6             Location
```


Remember, data retrieved using **ohvbd** can be raw and depends on the format of the source database. When inspecting the data, it is useful to consider:

- What type of data has the search returned?
- How many columns are there?
- Are there any missing values?


Let’s save our data, we will use this later in the workshop:


``` r
write.csv(aedes_aegypti_data, "aedes_aegypti_data.csv", row.names = FALSE)
```


::: {.rmdnote}
**Note:** If you want to practice more examples of using the **ohvbd package**, try looking at these vignettes:

- [Retrieving data from VectorByte](https://cran.rstudio.com/web/packages/ohvbd/vignettes/use-areadata.html)
- [Sourcing climatic data from AREAdata](https://cran.rstudio.com/web/packages/ohvbd/vignettes/use-areadata.html)

:::


### VBD Hub Forum
Earlier in this content, we found the **Hub Forum** under the **Community** tab. The **VBD Hub Forum** is a space to ask questions and share knowledge with the VBD community. 


Discussions on the **Forum** are organised using categories and tags so you can easily find topics relevant to you. When you post in a discussion, this contributes to an ongoing thread with other users. 


You can engage with the **Forum** by:

- Following discussions that interest you.
- Posting a new question or conversation prompt.
- Sharing resources and opportunities.
- Responding to existing threads. 


### VBD Hub Forum Task
Log in or sign up to the [VBD Hub Forum](https://forum.vbdhub.org/) and find the workshop discussion under the Training topic. 


Create a short post to introduce yourself, including your name, research interests, and what you hope to gain from this workshop.


You might want to reply to each others' posts to network with your fellow participants.


## Data Wrangling Principles
Data wrangling is the process of cleaning, transforming, and organising raw data into a format that is suitable for your analysis. 


Data retrieved through the **Hub Search** or the **ohvbd package** will often be raw, with missing values or messy data formats. Understanding data wrangling principles will help you organise your data into usable formats to make further statistical analysis smoother and easier.


### Do’s and Don’ts of Data Wrangling
**1. Understand your data first.**

- **Do:** Explore your data before making any changes. We can look at the first few rows of our dataset using `head()`, which allows us to better understand our data, including checking the column names and data types. 
- **Don’t:** Jump straight into cleaning the data without fully understanding how it is formatted. Without understanding the data, you risk misinterpreting variables and accidentally removing useful data.


**2. Save your raw data.**

- **Do:** Keep an unchanged version of the raw dataset so you can access a previous version if something goes wrong, reproduce your work, and verify your results.
- **Don’t:** Overwrite your original data. When wrangling your data in R, assign your cleaned data to a new object: `clean_data <- raw_data`.


**3. Use clear & consistent naming.**

- **Do:** Use informative column, model, and object names so you know what your object is explicitly. Clear naming makes your R workflow easier for others (and yourself) to understand.
- **Don’t:** Use unclear names or names with messy formatting. Try to avoid spaces, special characters, or specific abbreviations.


**4. Reformat your data.**

- **Do:** Convert your data to long format for analysis, using `pivot_longer()`. In this format, each row represents a single observation, which can make the data easier to filter and analyse.
- **Don’t:** Use data in wide format, where values are spread across multiple columns. This can limit data wrangling and processing, such as grouping across different years and generating effective visualisations.


**5. Record what you do.**

- **Do:** Keep track of your progress by recording what changes you made and why you used that approach. It is good practice to note these changes as comments in your code.
- **Don’t:** Rely on memory alone. It is easy to forget what analytical methods you used, why you chose that approach, and what order you processed your data in. Keeping clear records of your workflow contributes to better reproducibility.


::: {.rmdcaution}
**Frequent Mistake:** R cannot handle spaces in object names. There are a few options for alternative syntax, we would recommend using camelCase where letters are capitalised to indicate new words (e.g. specificModelName), or using an underscore to connect words (e.g. specific_model_name).


If using camelCase, remember that R is case sensitive - if your object is named specificModelName, but you call specificmodelname, R will show an error:


`Error: object ‘specificmodelname’ not found`
:::


### Data Wrangling Task
Let’s have a go at applying these data wrangling principles to the dataset we retrieved using **ohvbd**. 


**1. Understand your data first** - run `head()` before making any changes to your data:



``` r
head(aedes_aegypti_data)
#> <ohvbd.data.frame>
#> Database: vt
#>       Id DatasetID IndividualID OriginalID
#> 1 110069       893                   SK055
#> 2 110070       893                   SK055
#> 3 110065       892                   SK056
#> 4 110066       892                   SK056
#> 5 110067       892                   SK056
#> 6 110068       892                   SK056
#>   OriginalTraitName            OriginalTraitDef
#> 1  development time mean duration of life stage
#> 2  development time mean duration of life stage
#> 3         body size            mean wing length
#> 4         body size            mean wing length
#> 5         body size            mean wing length
#> 6         body size            mean wing length
#>   StandardisedTraitName StandardisedTraitDef
#> 1                    NA                   NA
#> 2                    NA                   NA
#> 3                    NA                   NA
#> 4                    NA                   NA
#> 5                    NA                   NA
#> 6                    NA                   NA
#>   OriginalTraitValue OriginalTraitUnit OriginalErrorPos
#> 1              21.00              days               NA
#> 2              21.00              days               NA
#> 3               3.01                mm             0.12
#> 4               3.30                mm             0.10
#> 5               2.80                mm             0.10
#> 6               3.22                mm             0.03
#>   OriginalErrorNeg OriginalErrorUnit StandardisedTraitValue
#> 1               NA              <NA>                     NA
#> 2               NA              <NA>                     NA
#> 3             0.12                SE                     NA
#> 4             0.10                SE                     NA
#> 5             0.10                SE                     NA
#> 6             0.03                SE                     NA
#>   StandardisedTraitUnit StandardisedErrorPos
#> 1                    NA                   NA
#> 2                    NA                   NA
#> 3                    NA                   NA
#> 4                    NA                   NA
#> 5                    NA                   NA
#> 6                    NA                   NA
#>   StandardisedErrorNeg StandardisedErrorUnit Replicates
#> 1                   NA                    NA         NA
#> 2                   NA                    NA         NA
#> 3                   NA                    NA         NA
#> 4                   NA                    NA         NA
#> 5                   NA                    NA         NA
#> 6                   NA                    NA         NA
#>       Habitat   LabField ArenaValue ArenaUnit ArenaValueSI
#> 1 terrestrial laboratory         NA        NA           NA
#> 2 terrestrial laboratory         NA        NA           NA
#> 3 terrestrial laboratory         NA        NA           NA
#> 4 terrestrial laboratory         NA        NA           NA
#> 5 terrestrial laboratory         NA        NA           NA
#> 6 terrestrial laboratory         NA        NA           NA
#>   ArenaUnitSI AmbientTemp AmbientTempMethod AmbientTempUnit
#> 1          NA          NA                NA              NA
#> 2          NA          NA                NA              NA
#> 3          NA          NA                NA              NA
#> 4          NA          NA                NA              NA
#> 5          NA          NA                NA              NA
#> 6          NA          NA                NA              NA
#>   AmbientLight AmbientLightUnit SecondStressor
#> 1           NA               NA           <NA>
#> 2           NA               NA           <NA>
#> 3           NA               NA           <NA>
#> 4           NA               NA           <NA>
#> 5           NA               NA           <NA>
#> 6           NA               NA           <NA>
#>                                               SecondStressorDef
#> 1 estimate of total food (tetramin) provided per larvae per day
#> 2 estimate of total food (tetramin) provided per larvae per day
#> 3 estimate of total food (tetramin) provided per larvae per day
#> 4 estimate of total food (tetramin) provided per larvae per day
#> 5 estimate of total food (tetramin) provided per larvae per day
#> 6 estimate of total food (tetramin) provided per larvae per day
#>   SecondStressorValue SecondStressorUnit TimeStart TimeEnd
#> 1           0.0952381                 mg      2013    2013
#> 2           0.4761905                 mg      2013    2013
#> 3           0.0952381                 mg      2013    2013
#> 4           0.4761905                 mg      2013    2013
#> 5           0.0952381                 mg      2013    2013
#> 6           0.4761905                 mg      2013    2013
#>   TotalObsTimeValue TotalObsTimeUnit TotalObsTimeValueSI
#> 1                NA               NA                  NA
#> 2                NA               NA                  NA
#> 3                NA               NA                  NA
#> 4                NA               NA                  NA
#> 5                NA               NA                  NA
#> 6                NA               NA                  NA
#>   TotalObsTimeUnitSI TotalObsTimeNotes ResRepValue
#> 1                 NA                NA          NA
#> 2                 NA                NA          NA
#> 3                 NA                NA          NA
#> 4                 NA                NA          NA
#> 5                 NA                NA          NA
#> 6                 NA                NA          NA
#>   ResRepUnit ResRepValueSI ResRepUnitSI
#> 1         NA            NA           NA
#> 2         NA            NA           NA
#> 3         NA            NA           NA
#> 4         NA            NA           NA
#> 5         NA            NA           NA
#> 6         NA            NA           NA
#>                                                 Location
#> 1 Instituto Oswaldo Cruz Fundacao Oswaldo Cruz RJ Brazil
#> 2 Instituto Oswaldo Cruz Fundacao Oswaldo Cruz RJ Brazil
#> 3 Instituto Oswaldo Cruz Fundacao Oswaldo Cruz RJ Brazil
#> 4 Instituto Oswaldo Cruz Fundacao Oswaldo Cruz RJ Brazil
#> 5 Instituto Oswaldo Cruz Fundacao Oswaldo Cruz RJ Brazil
#> 6 Instituto Oswaldo Cruz Fundacao Oswaldo Cruz RJ Brazil
#>   LocationType OriginalLocationDate LocationDate
#> 1       colony                   NA         <NA>
#> 2       colony                   NA         <NA>
#> 3       colony                   NA         <NA>
#> 4       colony                   NA         <NA>
#> 5       colony                   NA         <NA>
#> 6       colony                   NA         <NA>
#>   LocationDatePrecision CoordinateType  Latitude Longitude
#> 1                     0        decimal -22.87736 -43.24356
#> 2                     0        decimal -22.87736 -43.24356
#> 3                     0        decimal -22.87736 -43.24356
#> 4                     0        decimal -22.87736 -43.24356
#> 5                     0        decimal -22.87736 -43.24356
#> 6                     0        decimal -22.87736 -43.24356
#>        Interactor1 Interactor1Common Interactor1Wholepart
#> 1 Aedes albopictus              <NA>                   NA
#> 2 Aedes albopictus              <NA>                   NA
#> 3 Aedes albopictus              <NA>                   NA
#> 4 Aedes albopictus              <NA>                   NA
#> 5 Aedes albopictus              <NA>                   NA
#> 6 Aedes albopictus              <NA>                   NA
#>   Interactor1WholePartType Interactor1Number
#> 1                       NA               100
#> 2                       NA                20
#> 3                       NA               100
#> 4                       NA                20
#> 5                       NA               100
#> 6                       NA                20
#>   Interactor1Kingdom Interactor1Phylum Interactor1Class
#> 1           Animalia        Arthropoda          Insecta
#> 2           Animalia        Arthropoda          Insecta
#> 3           Animalia        Arthropoda          Insecta
#> 4           Animalia        Arthropoda          Insecta
#> 5           Animalia        Arthropoda          Insecta
#> 6           Animalia        Arthropoda          Insecta
#>   Interactor1Order Interactor1Family Interactor1Genus
#> 1          Diptera         Culicidae            Aedes
#> 2          Diptera         Culicidae            Aedes
#> 3          Diptera         Culicidae            Aedes
#> 4          Diptera         Culicidae            Aedes
#> 5          Diptera         Culicidae            Aedes
#> 6          Diptera         Culicidae            Aedes
#>   Interactor1Species      Interactor1Stage Interactor1Sex
#> 1         albopictus juvenile (L1 to pupa)  indeterminate
#> 2         albopictus juvenile (L1 to pupa)  indeterminate
#> 3         albopictus                 adult         female
#> 4         albopictus                 adult         female
#> 5         albopictus                 adult         female
#> 6         albopictus                 adult         female
#>   Interactor1Temp Interactor1TempUnit Interactor1TempMethod
#> 1              25             Celsius                    NA
#> 2              25             Celsius                    NA
#> 3              25             Celsius                    NA
#> 4              25             Celsius                    NA
#> 5              25             Celsius                    NA
#> 6              25             Celsius                    NA
#>   Interactor1GrowthTemp Interactor1GrowthTempUnit
#> 1                    NA                      <NA>
#> 2                    NA                      <NA>
#> 3                    NA                      <NA>
#> 4                    NA                      <NA>
#> 5                    NA                      <NA>
#> 6                    NA                      <NA>
#>   Interactor1GrowthDur Interactor1GrowthdDurUnit
#> 1                   NA                        NA
#> 2                   NA                        NA
#> 3                   NA                        NA
#> 4                   NA                        NA
#> 5                   NA                        NA
#> 6                   NA                        NA
#>   Interactor1GrowthType Interactor1Acc Interactor1AccTemp
#> 1                    NA             NA                 NA
#> 2                    NA             NA                 NA
#> 3                    NA             NA                 NA
#> 4                    NA             NA                 NA
#> 5                    NA             NA                 NA
#> 6                    NA             NA                 NA
#>   Interactor1AccTempNotes Interactor1AccTime
#> 1                      NA                 NA
#> 2                      NA                 NA
#> 3                      NA                 NA
#> 4                      NA                 NA
#> 5                      NA                 NA
#> 6                      NA                 NA
#>   Interactor1AccTimeNotes Interactor1AccTimeUnit
#> 1                      NA                     NA
#> 2                      NA                     NA
#> 3                      NA                     NA
#> 4                      NA                     NA
#> 5                      NA                     NA
#> 6                      NA                     NA
#>   Interactor1OrigTemp Interactor1OrigTempNotes
#> 1                  NA                       NA
#> 2                  NA                       NA
#> 3                  NA                       NA
#> 4                  NA                       NA
#> 5                  NA                       NA
#> 6                  NA                       NA
#>   Interactor1OrigTime Interactor1OrigTimeNotes
#> 1                  NA                       NA
#> 2                  NA                       NA
#> 3                  NA                       NA
#> 4                  NA                       NA
#> 5                  NA                       NA
#> 6                  NA                       NA
#>   Interactor1OrigTimeUnit Interactor1EquilibTimeValue
#> 1                      NA                          NA
#> 2                      NA                          NA
#> 3                      NA                          NA
#> 4                      NA                          NA
#> 5                      NA                          NA
#> 6                      NA                          NA
#>   Interactor1EquilibTimeUnit Interactor1Size
#> 1                         NA            <NA>
#> 2                         NA            <NA>
#> 3                         NA            <NA>
#> 4                         NA            <NA>
#> 5                         NA            <NA>
#> 6                         NA            <NA>
#>   Interactor1SizeUnit Interactor1SizeType Interactor1SizeSI
#> 1                <NA>                <NA>              <NA>
#> 2                <NA>                <NA>              <NA>
#> 3                <NA>                <NA>              <NA>
#> 4                <NA>                <NA>              <NA>
#> 5                <NA>                <NA>              <NA>
#> 6                <NA>                <NA>              <NA>
#>   Interactor1SizeUnitSI Interactor1DenValue
#> 1                  <NA>                <NA>
#> 2                  <NA>                <NA>
#> 3                  <NA>                <NA>
#> 4                  <NA>                <NA>
#> 5                  <NA>                <NA>
#> 6                  <NA>                <NA>
#>   Interactor1DenUnit Interactor1DenTypeSI
#> 1           juvenile                   NA
#> 2           juvenile                   NA
#> 3              adult                   NA
#> 4              adult                   NA
#> 5              adult                   NA
#> 6              adult                   NA
#>   Interactor1DenValueSI Interactor1DenUnitSI
#> 1                    NA                   NA
#> 2                    NA                   NA
#> 3                    NA                   NA
#> 4                    NA                   NA
#> 5                    NA                   NA
#> 6                    NA                   NA
#>   Interactor1MassValueSI Interactor1MassUnitSI Interactor2
#> 1                     NA                    NA   None None
#> 2                     NA                    NA   None None
#> 3                     NA                    NA   None None
#> 4                     NA                    NA   None None
#> 5                     NA                    NA   None None
#> 6                     NA                    NA   None None
#>   Interactor2Common Interactor2Kingdom Interactor2Phylum
#> 1                NA                 NA                NA
#> 2                NA                 NA                NA
#> 3                NA                 NA                NA
#> 4                NA                 NA                NA
#> 5                NA                 NA                NA
#> 6                NA                 NA                NA
#>   Interactor2Class Interactor2Order Interactor2Family
#> 1               NA               NA                NA
#> 2               NA               NA                NA
#> 3               NA               NA                NA
#> 4               NA               NA                NA
#> 5               NA               NA                NA
#> 6               NA               NA                NA
#>   Interactor2Genus Interactor2Species Interactor2Stage
#> 1               NA                 NA               NA
#> 2               NA                 NA               NA
#> 3               NA                 NA               NA
#> 4               NA                 NA               NA
#> 5               NA                 NA               NA
#> 6               NA                 NA               NA
#>   Interactor2Sex Interactor2Temp Interactor2TempUnit
#> 1             NA              NA                  NA
#> 2             NA              NA                  NA
#> 3             NA              NA                  NA
#> 4             NA              NA                  NA
#> 5             NA              NA                  NA
#> 6             NA              NA                  NA
#>   Interactor2TempMethod Interactor2GrowthTemp
#> 1                    NA                    NA
#> 2                    NA                    NA
#> 3                    NA                    NA
#> 4                    NA                    NA
#> 5                    NA                    NA
#> 6                    NA                    NA
#>   Interactor2GrowthTempUnit Interactor2GrowthDur
#> 1                        NA                   NA
#> 2                        NA                   NA
#> 3                        NA                   NA
#> 4                        NA                   NA
#> 5                        NA                   NA
#> 6                        NA                   NA
#>   Interactor2GrowthDurUnit Interactor2GrowthType
#> 1                       NA                    NA
#> 2                       NA                    NA
#> 3                       NA                    NA
#> 4                       NA                    NA
#> 5                       NA                    NA
#> 6                       NA                    NA
#>   Interactor2Acc Interactor2AccTemp Interactor2AccTempNotes
#> 1             NA                 NA                      NA
#> 2             NA                 NA                      NA
#> 3             NA                 NA                      NA
#> 4             NA                 NA                      NA
#> 5             NA                 NA                      NA
#> 6             NA                 NA                      NA
#>   Interactor2AccTime Interactor2AccTimeNotes
#> 1                 NA                      NA
#> 2                 NA                      NA
#> 3                 NA                      NA
#> 4                 NA                      NA
#> 5                 NA                      NA
#> 6                 NA                      NA
#>   Interactor2AccTimeUnit Interactor2OrigTemp
#> 1                     NA                  NA
#> 2                     NA                  NA
#> 3                     NA                  NA
#> 4                     NA                  NA
#> 5                     NA                  NA
#> 6                     NA                  NA
#>   Interactor2OrigTempNotes Interactor2OrigTime
#> 1                       NA                  NA
#> 2                       NA                  NA
#> 3                       NA                  NA
#> 4                       NA                  NA
#> 5                       NA                  NA
#> 6                       NA                  NA
#>   Interactor2OrigTimeNotes Interactor2OrigTimeUnit
#> 1                       NA                      NA
#> 2                       NA                      NA
#> 3                       NA                      NA
#> 4                       NA                      NA
#> 5                       NA                      NA
#> 6                       NA                      NA
#>   Interactor2EquilibTimeValue Interactor2EquilibTimeUnit
#> 1                          NA                         NA
#> 2                          NA                         NA
#> 3                          NA                         NA
#> 4                          NA                         NA
#> 5                          NA                         NA
#> 6                          NA                         NA
#>   Interactor2Size Interactor2SizeUnit Interactor2SizeType
#> 1              NA                  NA                  NA
#> 2              NA                  NA                  NA
#> 3              NA                  NA                  NA
#> 4              NA                  NA                  NA
#> 5              NA                  NA                  NA
#> 6              NA                  NA                  NA
#>   Interactor2SizeSI Interactor2SizeUnitSI
#> 1                NA                    NA
#> 2                NA                    NA
#> 3                NA                    NA
#> 4                NA                    NA
#> 5                NA                    NA
#> 6                NA                    NA
#>   Interactor2DenValue Interactor2DenUnit
#> 1                  NA                 NA
#> 2                  NA                 NA
#> 3                  NA                 NA
#> 4                  NA                 NA
#> 5                  NA                 NA
#> 6                  NA                 NA
#>   Interactor2DenTypeSI Interactor2DenValueSI
#> 1                   NA                    NA
#> 2                   NA                    NA
#> 3                   NA                    NA
#> 4                   NA                    NA
#> 5                   NA                    NA
#> 6                   NA                    NA
#>   Interactor2DenUnitSI Interactor2MassValueSI
#> 1                   NA                     NA
#> 2                   NA                     NA
#> 3                   NA                     NA
#> 4                   NA                     NA
#> 5                   NA                     NA
#> 6                   NA                     NA
#>   Interactor2MassUnitSI PhysicalProcess PhysicalProcess_1
#> 1                    NA              NA                NA
#> 2                    NA              NA                NA
#> 3                    NA              NA                NA
#> 4                    NA              NA                NA
#> 5                    NA              NA                NA
#> 6                    NA              NA                NA
#>   PhysicalProcess_2 FigureTable
#> 1                NA    figure 1
#> 2                NA    figure 1
#> 3                NA    figure 1
#> 4                NA    figure 1
#> 5                NA    figure 1
#> 6                NA    figure 1
#>                                                                                                                                                   Citation
#> 1 Lima-Camara et al 2022. Body size does not affect locomotor activity of Aedes aegypti and Aedes albopictus females (Diptera:Culicidae). Acta Tropica 231
#> 2 Lima-Camara et al 2022. Body size does not affect locomotor activity of Aedes aegypti and Aedes albopictus females (Diptera:Culicidae). Acta Tropica 231
#> 3 Lima-Camara et al 2022. Body size does not affect locomotor activity of Aedes aegypti and Aedes albopictus females (Diptera:Culicidae). Acta Tropica 231
#> 4 Lima-Camara et al 2022. Body size does not affect locomotor activity of Aedes aegypti and Aedes albopictus females (Diptera:Culicidae). Acta Tropica 231
#> 5 Lima-Camara et al 2022. Body size does not affect locomotor activity of Aedes aegypti and Aedes albopictus females (Diptera:Culicidae). Acta Tropica 231
#> 6 Lima-Camara et al 2022. Body size does not affect locomotor activity of Aedes aegypti and Aedes albopictus females (Diptera:Culicidae). Acta Tropica 231
#>                                                                                                                                                       CuratedByCitation
#> 1 Brass et al. 2024. Role of vector phenotypic plasticity in disease transmission as illustrated by the spread of dengue virus by Aedes albopictus. Nat Commun 15: 7823
#> 2 Brass et al. 2024. Role of vector phenotypic plasticity in disease transmission as illustrated by the spread of dengue virus by Aedes albopictus. Nat Commun 15: 7823
#> 3 Brass et al. 2024. Role of vector phenotypic plasticity in disease transmission as illustrated by the spread of dengue virus by Aedes albopictus. Nat Commun 15: 7823
#> 4 Brass et al. 2024. Role of vector phenotypic plasticity in disease transmission as illustrated by the spread of dengue virus by Aedes albopictus. Nat Commun 15: 7823
#> 5 Brass et al. 2024. Role of vector phenotypic plasticity in disease transmission as illustrated by the spread of dengue virus by Aedes albopictus. Nat Commun 15: 7823
#> 6 Brass et al. 2024. Role of vector phenotypic plasticity in disease transmission as illustrated by the spread of dengue virus by Aedes albopictus. Nat Commun 15: 7823
#>                 CuratedByDOI
#> 1 10.1038/s41467-024-52144-5
#> 2 10.1038/s41467-024-52144-5
#> 3 10.1038/s41467-024-52144-5
#> 4 10.1038/s41467-024-52144-5
#> 5 10.1038/s41467-024-52144-5
#> 6 10.1038/s41467-024-52144-5
#>                                 DOI SubmittedBy
#> 1 10.1016/j.actatropica.2022.106430 Sarah Kelly
#> 2 10.1016/j.actatropica.2022.106430 Sarah Kelly
#> 3 10.1016/j.actatropica.2022.106430 Sarah Kelly
#> 4 10.1016/j.actatropica.2022.106430 Sarah Kelly
#> 5 10.1016/j.actatropica.2022.106430 Sarah Kelly
#> 6 10.1016/j.actatropica.2022.106430 Sarah Kelly
#>         ContributorEmail Notes   DefaultChartXaxis
#> 1 s.kelly@imperial.ac.uk  <NA> SecondStressorValue
#> 2 s.kelly@imperial.ac.uk  <NA> SecondStressorValue
#> 3 s.kelly@imperial.ac.uk  <NA> SecondStressorValue
#> 4 s.kelly@imperial.ac.uk  <NA> SecondStressorValue
#> 5 s.kelly@imperial.ac.uk  <NA> SecondStressorValue
#> 6 s.kelly@imperial.ac.uk  <NA> SecondStressorValue
#>   DefaultChartCategory
#> 1             Location
#> 2             Location
#> 3             Location
#> 4             Location
#> 5             Location
#> 6             Location
```


Notice what the columns represent, what the data types are, and whether there are any missing values.


**2. Save your raw data** - save your data as a new object. Any changes you make will use this new object, rather than the raw data:



``` r
clean_aedes_data <- aedes_aegypti_data
```


**3. Use clear and consistent naming** - rename at least two columns with more informative names:



``` r
library(dplyr)
#> 
#> Attaching package: 'dplyr'
#> The following objects are masked from 'package:stats':
#> 
#>     filter, lag
#> The following objects are masked from 'package:base':
#> 
#>     intersect, setdiff, setequal, union

clean_aedes_data <- clean_aedes_data |>
  rename(
    original_trait_name = OriginalTraitName,
    original_trait_def = OriginalTraitDef
  )
```


**4. Reformat your data** - check whether your dataset is in wide or long format. Remember, we typically want each row to represent a single observation. If our variables are spread across several columns we can reformat our data using `pivot_longer()`. FOr this dataset, we can see the data is already in long format.


**5. Record what you do** - add comments to your code explaining what changes you made and why:


`# Convert data from wide to long format so it is easier to filter and analyse.`


::: {.rmdnote}
**Note:** Don’t worry if you weren’t able to retrieve a dataset from **ohvbd**, we will recap this in the **Live Session**.
:::


## Response Form 
Please complete this [Response Form](https://docs.google.com/forms/d/e/1FAIpQLSdshvuPxVUR1-87qeZgfGI0fIigrJthmS4S1IzHen3DjggiLQ/viewform?usp=publish-editor) after finishing the tasks above.


This form is anonymous and is not an assessment. Your responses will help us to understand which areas may require more support during the **Live Session**. We aim to tailor the content to the group's needs, so you gain the most from this workshop.


## Conclusion & Preparation for Live Session
Ahead of the live session, ensure you keep R and RStudio installed on your device, as well as the packages we prepared earlier. 


Please make sure you have Teams set up on your device and that your microphone is working. We will aim to send the link 48 hours before the live session. Please be aware that the live session will be recorded. 


# Live Session


## Schedule
10:00 - Introduction
10:10 - Recap Pre- Live Session Content
10:20 - Data Wrangling (Broad)
10:25 - Replicate/Merging
10:40 - Fix Species Name
11:00 - BREAK
11:10 - Real-World Data is Messy
11:25 - Collaborative Task
12:10 - BREAK
12:20 - Share Results from Collaborative Task
12:35 - Collaboration (Forum)
12:50 - Prepare for Challenge Task & Conclusion


## Introduction (10 mins)
Introduce myself


Introduce demonstrators


Recap Learning Objectives


Reiterate where to find support:
Forum
Demonstrators
Technical difficulties - (email)


## Recap Pre- Live Session Content (10 mins)
What went well?


Common mistakes


Strong anonymous examples?


## Data Wrangling (Broad) (5 mins)
Lots of ways to wrangle data, depends on field, data collected, etc.


We will focus on two methods key to VBD data.


## Replicate/Merging (15 mins)
Similar columns across two datasets


Merge by common column


Useful functions


Common mistakes


## Fix Species Name (20 mins)
Find and remove a misnamed species


Remove underscore or spp. Etc. at the end of the species name


Make a column all lowercase


Useful functions


Common mistakes


Combine merging - merge by species


RGBIF for those wanting extra


## Real World Data is Messy (15 mins)
Common trip-ups in “messy” data sets


What to look out for


## Collaborative Task (45 mins)
Find a specified dataset through ohvbd


Identify what makes it messy


Wrangle data


Try to use datasets with multiple messy elements:
Mixed data types
Messy columns (merge)
Messy species names
Wide to long


## Share Results from Collaborative Task (15 mins)
4 groups


What went wrong?


How did you fix it?


Why?


## What Does Collaboration Mean to You? (15 minutes)
Why do you want to collaborate?


What makes a good collaboration?


What makes a bad collaboration?


How could you use the Forum in your own research context for collaboration?


Whiteboard


## Prepare for Challenge Task & Conclusion (10 mins)
Outline Challenge Task


Where to find support


Conclusion


# Challenge Task


## Level 1
Find a dataset using Hub Search or VBD Hub (participant choice)


## Level 2
What data types?


Does it need converting from wide to long?


## Level 3
Do any columns need merging? (second dataset? TBC?)


## Level 4
Check species names


Variable/trait names?


## Level 5
Share your wrangling process in the Forum, feedback to each other


You might choose to pair up with someone using similar data and give peer feedback



::: {.rmdtip}
**Tip:** This is a tip.
:::

::: {.rmdnote}
**Note:** This is a note.
:::

::: {.rmdimportant}
**Important:** This is important.
:::

::: {.rmdcaution}
**Caution:** This is a caution.
:::

::: {.rmdwarning}
**Warning:** This is a warning.
:::


