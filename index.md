---
title       : Earthquake Data Visualizer
subtitle    : JHU Coursera - Developing Data Products
author      : suttonbm
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Introduction
The earthquake visualization tool was developed for the Developing Data Products course offered by Johns Hopkins University on Coursera.  The purpose of the tool is to allow a user to explore historical earthquake data by magnitude, date, and location.  A map is drawn for a selected region, and earthquakes are overlaid on the map with scale and color corresponding to earthquake magnitude.

<div style='text-align: center;'>
    <img src='assets/img/worldpic.png' />
</div>

--- &twocol

## User Interface
The user interface for the earthquake visualization tool was built using Shiny from RStudio. The interface allows the user to customize and explore earthquake data.

*** =left

![UI](assets/img/UI_inputs.png)

*** =right

Using the inputs displayed to the left, a user can customize:

  * The date range for which seismic events are displayed
  * The range of magnitudes to be shown on the image
  * The scale of the circles representing seismic events
  * A color scheme to personalize aesthetic taste
  * A target location to explore seismic data

---

## Data Import
Earthquake data is a combination of two data sources:

  * The Global Historical Earthquake Archive (see [GEM](https://www.globalquakemodel.org/what/seismic-hazard/historical-catalogue/))
  * The International Seismological Centre (see [ISC](http://www.isc.ac.uk/iscgem/))

All the source code for the tool is available on [Github](github.com/suttonbm/datasciencecoursera/tree/master/Developing_Data_Products/Project/DDP_Final_Project).

While the tool was developed to be used through a Shiny UI, all the features are also available as standalone R scripts.  To load the earthquake dataset at the console, run the following:




```r
source(paste0(pathToRepo, 'loadEarthquakeData.R'))
```





Data files will be dynamically loaded from the web if they are not available.  Note that ISC data, although freely available, must be requested at the link above.

--- &twocol

## Plot Generation
Earthquake plots are generated using the `maps` package in combination with R base graphics.  A plot can be generated using the source package as follows:

*** =left



![plot of chunk unnamed-chunk-6](figure/unnamed-chunk-6-1.png)

*** =right


```r
source(paste0(pathToRepo, 'generateMap.R'))
generateMap(rawData.M,
            colorMap = "inferno",
            circleScale = 3.5,
            xlim = c(-80, 80),
            ylim = c(0, 80))
```

