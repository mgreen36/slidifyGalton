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

## Predict Child Height Using the Galton Dataset

1. Edit YAML front matter
2. Write using R Markdown
3. Use an empty line followed by three dashes to separate slides!

--- .class #id 

## Plot

<img src="assets/fig/simple-plot1-1.png" title="plot of chunk simple-plot1" alt="plot of chunk simple-plot1" style="display: block; margin: auto;" />


---



## Plot 2

<img src="assets/fig/simple-plot2-1.png" title="plot of chunk simple-plot2" alt="plot of chunk simple-plot2" style="display: block; margin: auto;" />

---

## Test Slide 2

This is test slide 2

---

## Using Regression on Galton to get Prediction


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
<img src="assets/fig/simple-plot3-1.png" title="plot of chunk simple-plot3" alt="plot of chunk simple-plot3" style="display: block; margin: auto;" />
---

## plot 4
Lets create a simple plot

```r
require(ggplot2)
qplot(parent, child, data = Galton)
```
![plot of chunk simple-plot](figure/simple-plot.png) 
---






