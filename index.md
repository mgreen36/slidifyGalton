---
title       : Developing Data Products Class Project
subtitle    : Predicting Child Heights Using Galton Data
author      : Michael Green
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : mathjax, quiz, bootstrap            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---




## Overview


- The Child Height Predictor Shiny App <a href="https://mgreen70.shinyapps.io/ChildHeightPredictor">https://mgreen70.shinyapps.io/ChildHeightPredictor</a> allows users to get a prediction of a child's height based on the height of the child's parents.


- The app is based on Francis Galton's famous study of child heights in the 1880's.


- Galton's height study made milestone breakthroughs
in statistics including the development of the idea of the regression to the mean.

- <a href="https://select-statistics.co.uk/blog/regression-to-the-mean-as-relevant-today-as-it-was-in-the-1900s">More info about Galton's study</a>

--- .class #id1

## The Data

- The app is using the Galton dataset from HistData.

- The dataset consists of 928 rows of child and parent heights.

- Galton multiplied female heights by 1.08. 

- The heights of female children were multiplied by 1.08.

- The parents height in the dataset is the mid-parent height which is the father's height plus the mother's height multiplied by 1.08.


<style type="text/css">

code.r{
  font-size: 12px;
}
pre {
  font-size: 12px
}
</style>


```r
library(HistData)

summary(Galton)
```

```
##      parent          child      
##  Min.   :64.00   Min.   :61.70  
##  1st Qu.:67.50   1st Qu.:66.20  
##  Median :68.50   Median :68.20  
##  Mean   :68.31   Mean   :68.09  
##  3rd Qu.:69.50   3rd Qu.:70.20  
##  Max.   :73.00   Max.   :73.70
```

--- .class #id2


## Using the App
- The app's sidepanel has fields to enter the father's height, the mother's height and the child's sex. All heights are in inches.

- The user can change the parents heights using a slider for the mother's height and a slider for the father's height.

- The child's sex is entered via a dropdown box.

- The results panel shows the the calculated mid-parent height and the predicted child's height.

- The sliders and the dropdown box are reactive fields in shiny. Changes to any of these fields are immediately reflected in the results data.

- The mid-parent height is the father's height + the mother's height * 1.08.

- The child's height is calculated using a regression model. 
A child's predicted height is the intercept + the slope * the mid-parent height.For female children the result is divided by 1.08


--- .class #id3

<style type='text/css'>
img {
    max-height: 760px;
    max-width: 960px;
}
</style>

## Regression Model


```r
lm(Galton$child ~ Galton$parent)
```

```
## 
## Call:
## lm(formula = Galton$child ~ Galton$parent)
## 
## Coefficients:
##   (Intercept)  Galton$parent  
##       23.9415         0.6463
```


<img src="assets/fig/simple-plot1-1.png" title="plot of chunk simple-plot1" alt="plot of chunk simple-plot1" style="display: block; margin: auto;" />

