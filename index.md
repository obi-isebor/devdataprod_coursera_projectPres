---
title       : Prediction of Car Braking Distance
subtitle    : Developing data products coursera project
author      : Obi Isebor
job         : Data science enthusiast
framework   : io2012       # {io2012, html5slides, shower, dzslides, deckjs, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # zenburn, tomorrow
widgets     : [mathjax]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft, selfcontained}
knit        : slidify::knit2slides
---

## Motivation

* There is a relationship between speed of moving cars and the stopping distance 
  of the car once the driver hits the brakes
* It would be useful to be able to quantify this relationship and predict
  stopping distances for cars moving at certain speeds. This information is useful
  for:
  * Public safety
  * Car and tire manufacturers
  * Driver training and testing
* Now available: a web application to predict stopping distances given car speeds

--- .class #id 

## Details

* Web application is based on linear model regression of the `cars` dataset available in R

```
## 'data.frame':	50 obs. of  2 variables:
##  $ speed: num  4 4 7 7 8 9 10 10 10 11 ...
##  $ dist : num  2 10 4 22 16 10 18 26 34 17 ...
```
* The two variables in the dataset are `speed` of the car and `dist`, the stopping distance
* The dataset includes stopping distances for speeds up to 25 mph, however in 
order to extrapolate the stopping distance to higher speeds, a linear model is used
* The model: `dist = slope*speed + intercept`
* The web application has two purposes (separated into two panels): 
    * linear model calibration to determine parameters `slope` and `intercept`
      that best fit the `cars` data
    * the stopping distance prediction, given a specified car speed


--- &twocolfull

## Calibration Section

In the **Linear Model Calibration Panel**, the user has two options to calibrate the linear model:

*** =left

Manual calibration by varying slope and intercept values to find a linear
  regression line that best fits the `cars` data, i.e., modifying the parameters
  for the red line in the figure shown to the right
  
*** =right

<img src="assets/fig/unnamed-chunk-2-1.png" title="plot of chunk unnamed-chunk-2" alt="plot of chunk unnamed-chunk-2" width="300px" height="250px" />

*** =fullwidth

Automatic calibration (recommended), where the following R code is run in the background to 
determine the regression coefficients (slope & intercept):


```r
data(cars)
coef(lm(dist ~ speed, data = cars))
```

---

## Prediction Section

* When satisfied with the calibration, in the **Prediction Panel**, the user can now begin to predict braking distances based on speeds he/she can input in this panel
* Predictions are based on the calibration performed in the calibration panel
* Enjoy!


