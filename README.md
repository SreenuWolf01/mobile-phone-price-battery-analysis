# Mobile Phone Price vs. Battery Capacity Analysis 📈🔋

## Project Overview

This project investigates the relationship between the price of mobile phones and their battery capacity using simple linear regression. Our goal was to determine if there is a statistically significant correlation between these two variables, as higher battery capacity is often perceived as a desirable feature influencing a phone's value. [cite: 22, 24, 43]

## Problem Statement

Does the capacity of a smartphone's battery significantly affect its price? We aimed to model this relationship and test for its statistical significance. [cite: 8, 12, 25]

## Data

The dataset used for this analysis contains information on prices of several mobile phones from various brands. [cite: 8, 23]
* **Source:** The data was sourced from various business channels, including stores, e-commerce websites, showrooms, and more. [cite: 8] A Kaggle dataset was also utilized. [cite: 23]
* **Sampling:** Simple Random Sampling was employed to collect data on mobile phone prices. [cite: 9]
* **Variables:** Key attributes collected include Brand, Model, Storage, RAM, Screen Size, Camera (MP), Battery Capacity, and Price. These variables define the pricing structure in the dataset. [cite: 10, 11]

## Hypothesis

* **Null Hypothesis ($H_0$):** The battery capacity and price of the mobile phone are independent variables. ($\rho = 0$) [cite: 13, 14, 26]
* **Alternative Hypothesis ($H_a$):** The battery capacity and price of the mobile phone are dependent variables. ($\rho \neq 0$) [cite: 14, 26]

## Methodology

We employed a simple linear regression model to test our hypotheses. [cite: 27, 33]

### Conditions for Linear Regression:

Before modeling, we checked the necessary conditions for simple linear regression:

1.  **Linearity of the Data:** We assumed a linear relationship between the predictor (Battery Capacity) and the outcome (Price). Initial scatter plots indicated a positive linearity. [cite: 15, 29, 30, 33] As battery capacity tends to increase, the price also tends to rise, suggesting a positive correlation due to higher battery capacity being a desirable feature. [cite: 30, 31, 32]

2.  **Normality of Residuals:** The residual errors are assumed to be normally distributed. [cite: 16, 37] Initially, the residuals did not exhibit normality. To address this, we applied a **logarithmic transformation to the `Price` variable**, which successfully satisfied the normality assumption. [cite: 38, 39]

3.  **Homoscedasticity:** We assumed that the residuals have a constant variance, meaning the spread of residuals should remain roughly constant across all levels of battery capacity. [cite: 17, 35, 36]

4.  **Independence of Residual Error Terms:** We checked for independence, assuming observations are independent and the value of battery for one observation does not predict the price for another. [cite: 18, 34] The correlogram of residuals was used to confirm this.

## Results & Findings

### Exploratory Data Analysis (EDA)

* A scatter plot of price vs. battery capacity (before log transformation) visually suggested a positive linear relationship, with more expensive phones generally having higher battery capacity. [cite: 29, 30]

### Simple Linear Regression Model Summary

After transforming the `Price` variable to `log_price` to meet the normality assumption, the simple linear regression model was run with `log_price` as the dependent variable and `battery` as the independent variable.

```r
Call:
lm(formula = log_price ~ battery, data = Mobile_price)

Residuals:
      Min        1Q    Median        3Q       Max
-1.29091 -0.36587 -0.04193  0.27679  1.74318

Coefficients:
              Estimate Std. Error t value Pr(>|t|)
(Intercept)  7.514e+00  1.694e-01   44.36   <2e-16 ***
battery     -3.682e-04  3.571e-05  -10.31   <2e-16 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.5736 on 405 degrees of freedom
Multiple R-squared:  0.2079, Adjusted R-squared:  0.2059
F-statistic: 106.3 on 1 and 405 degrees of freedom,  p-value: < 2.2e-16
```
## Decision and Conclusion
**Decision:** We rejected the null hypothesis because the calculated p-value ($< 2.2e-16$) is significantly less than the predetermined alpha value (0.05). 

**Conclusion:** There is sufficient evidence to state that a statistically significant relationship exists between the price and battery capacity of a mobile phone. Therefore, the price of the mobile phone is indeed dependent on its battery capacity. 

## Tools and Technologies
**Language:** R

**Libraries:** alr4, dplyr, ggplot2, readr

**Tools:** RStudio, Jupyter (implied, as Rmd can be run in Jupyter too)

**Limitations and Future Work**
Our study had some limitations. For instance, some phones with different specifications had the same battery capacity, which could affect the accuracy of our results. 

Future studies should consider controlling for other factors that may influence mobile phone price and battery performance, such as:

Brand reputation
Processor speed (RAM, Storage)
Camera quality (MP)
Screen size and type
Operating system
Release date 
