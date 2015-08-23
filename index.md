---
title       : MPG Predictor Tool
subtitle    : An easy way to predict a car's MPG
author      : outofrhyme
job         : Developing Data Products
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## What is MPG Predictor?

MPG Predictor is a simple shiny app that can predict a car's miles per gallon.

To make a prediction, you input:
* The weight of the car (in lb/1000)
* The number of cylinders that the car has
* Whether the car has manual or automatic transmission

MPG Predictor will then plug those values into a prediction model built around the mtcars dataset.

--- .class #id

## How it works

The mtcars dataset contains fuel consumption and 10 aspects of automobile design and performance for 32 automobiles, extracted from the 1974 Motor Trend magazine.

Using the caret library, we've trained a simple glm machine learning model on weight, cylinders and transmission type.


```r
modFit <- train(mpg ~ wt + cyl + am,method="glm",data=mtcars)
```

--- 

## How it works

The MPG Predictor app then takes the user-inputted values and plugs them into this prediction model.

For example, if the user inputs these values:


```r
wt <- 3.5
cyl <- 4
am <- "automatic"
```

The model then runs the model and predict an MPG value:



```r
predict(modFit, newdata=values)
```

```
## [1] 22.43895
```


--- 

## Try it out!

You can give MPG Predictor a try at:

http://outofrhyme.shinyapps.io/MPG-Predictor

MPG Predictor is a fun and easy way to guess what MPG a car might have if you know a few stats, and hey, maybe it will save you a bit of money in gas. Of course, unless you are purchasing a 1973-74 model of car, the results should be taken with a grain of salt ;)
