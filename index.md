---
title       : Predicting Automobile Fuel Consumption
author      : doctorpacket
framework   : deckjs   # {io2012, html5slides, shower, dzslides, ...}
deckjs      : {theme: swiss, transition: fade}
widgets     : [mathjax]      # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Automobile Fuel Consumption Predictor

When purchasing an automobile, it would be valuable for consumers to have an independent evaluation of fuel consumption,
in addition to manufacturer's stated figures.

Using the fuel consumption data provided by Motor Trend, I hereby present a predictive model using just three simple predictors:

- Horsepower
- Weight
- Transmission Type

---

## Model Fitting

Using the R caret package, we apply linear regression to Motor Trend's dataset:




```r
library(datasets)
data(mtcars)

df <- mtcars
df$cyl <- as.factor(df$cyl)
df$am <- as.factor(df$am)
df$gear <- as.factor(df$gear)

fit <- train(mpg ~ hp + wt + am, data=df, method='lm')
```

---

## Explained Variances

Running summary on the fitted model, we see that the 3 predictors combine to explain 83% of the variances:


```r
summary(fit)
```

```
## 
## Call:
## lm(formula = .outcome ~ ., data = dat)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -3.4221 -1.7924 -0.3788  1.2249  5.5317 
## 
## Coefficients:
##              Estimate Std. Error t value Pr(>|t|)    
## (Intercept) 34.002875   2.642659  12.867 2.82e-13 ***
## hp          -0.037479   0.009605  -3.902 0.000546 ***
## wt          -2.878575   0.904971  -3.181 0.003574 ** 
## am1          2.083710   1.376420   1.514 0.141268    
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 2.538 on 28 degrees of freedom
## Multiple R-squared:  0.8399,	Adjusted R-squared:  0.8227 
## F-statistic: 48.96 on 3 and 28 DF,  p-value: 2.908e-11
```

---

## UI Demonstration

Predicting fuel consumption is easy!

![width](assets/img/demo.png)

---

## Conclusion

Using the predictor, consumers now have an independent, unbiased evaluation of fuel consumption, which can be used when comparing different car models and making purchasing decisions.

https://doctorpacket.shinyapps.io/FuelConsumption

---


