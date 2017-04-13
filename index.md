---
title       : Playing with plotly 
subtitle    : A first go with plotly for coursera assignment
author      : Simon C
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---


## Loading the data
We will use the Manchester traffic signals dataset.  
Firsly we need to load our libraries and do some basic tidying.


```r
library(plotly)
traffic <- read.csv("../TrafficSignals.csv")
```


A quick tidy.  


```r
traffic$Crossing_Facility <- gsub("P(ed|ED).*","PEDESTRIAN", traffic$Crossing_Facility)
traffic$Crossing_Facility <- gsub("P(uf|UF).*","PUFFIN", traffic$Crossing_Facility)
traffic$Crossing_Facility[traffic$Crossing_Facility==""] <- "NA"
```

---

## Let's plot!

```r
qTraffic <- qplot(Type, data = traffic, fill=Crossing_Facility, 
                  xlab="Crossing Type", ylab="Number")+
  theme(axis.text.x = element_text(angle=90))+labs(fill="Facility")

ggplotly(qTraffic)
```

![plot of chunk unnamed-chunk-3](assets/fig/unnamed-chunk-3-1.png)

---

## The interactive chart
### Using an iframe
<iframe src="https://plot.ly/~simbosky/0.embed" width="800" height="600" id="igraph" scrolling="no" seamless="seamless" frameBorder="0"> </iframe>


<iframe scrolling='no' seamless='seamless' style='border:none'
src='https://plot.ly/~simbosky/0' width='800' height='500'></iframe>
