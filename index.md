---
title       : Developing Data Products Class Project
subtitle    : Predicting Child Heights Using Galton Data
author      : Michael Green
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

<style type="text/css">
body, td {
   font-size: 14px;
}
code.r{
  font-size: 14px;
}
pre {
  font-size: 16px
}
</style>

## Overview
<br/>
The Child Height Predictor App allows users to input parents heights to get a prediction
of a child's fully grown height.<br/>
<br/>

The app uses the Galton dataset from the HistData package.

<br/>
The dataset was compiled by Galton in the 1880, and was part of milestone breakthroughs
in statistics including the discovery of the regression to the mean.

---

## The Data

The dataset consists of 928 rows of child and parent heights.

The parents height is the mid-parent height which is the father's height plus the mother's height multiplied by 1.08.

Galton multiplied female heights by 1.08. This includes the calcultion of the mid-parent height and in recording female children's heights.


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

---

## Using the App

The user can change the parents heights using a slider for the mother's height and a slider for the father's height.

The child's sex is entered via a dropdown box.

The results panel shows the the calculated mid-parent height and the predicted child's height.

The mid-parent height is calulated as the father's height + the mother's height * 1.08.

The child's height is calculated using a regression model. 
A child's predicted height is the intercept + the slope * the mid-parent height.

For female children the result is divided by 1.08

---

## Regression on Galton to get Prediction

<font size="4">

```r
modelFit <- lm(Galton$child ~ Galton$parent)
summary(modelFit) 
```

```
## 
## Call:
## lm(formula = Galton$child ~ Galton$parent)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -7.8050 -1.3661  0.0487  1.6339  5.9264 
## 
## Coefficients:
##               Estimate Std. Error t value Pr(>|t|)    
## (Intercept)   23.94153    2.81088   8.517   <2e-16 ***
## Galton$parent  0.64629    0.04114  15.711   <2e-16 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 2.239 on 926 degrees of freedom
## Multiple R-squared:  0.2105,	Adjusted R-squared:  0.2096 
## F-statistic: 246.8 on 1 and 926 DF,  p-value: < 2.2e-16
```

</font>

---


## Regression Plot

<img src="assets/fig/simple-plot1-1.png" title="plot of chunk simple-plot1" alt="plot of chunk simple-plot1" style="display: block; margin: auto;" />

---


## Plot 2

<img src="assets/fig/simple-plot2-1.png" title="plot of chunk simple-plot2" alt="plot of chunk simple-plot2" style="display: block; margin: auto;" />

---

