---
layout: post
title: Machine Learning with Python
feature-img: "assets/img/posts/ml_python/ml_python.webp"
categories: datascience
tags: [Pandas, Data Science, Python]
---

Notes about the IBM course "Machine Learning with Python"

# Machine Learning with Python

## Linear Regression

In linear regression, the dependant values (target) should be continuous and cannot be discrete value. However, the independant variables can be measured on either a categorical or continuous measurement scale.
Linear Regression is used to predict continuous values, for example it can be used to predict :
* Sales forecasting ( Target : total yearly sales. Independant variables : Age, Education, Years of experience )
* Satisfaction analysis ( Target : Individual satisfaction. Independant variables : Demographic ans psychological factors )
* Price estimation ( Target : Price of a house in an area. Independant variables : Size, number of bedrooms, ...)
* Employment income ( Target : Income. Independant variables : Hours of work, education, occupation, sex, age, years of experience, ...)

There are many Regression Algorithms, to name a few :
* Ordinal regression
* Poisson regression
* Fast forest quantile regression
* Linear, polynomial, Lasso, Stepwise, Ridge regression
* Bayesian linear regression
* Neural network regression
* Decision forest regression
* Boosted decision tree regression
* KNN ( K-nearest Neighbors )

## Simple Linear Regression
Simple Linear Regression is when 1 independant variable is used to estimate a dependant variable. As you can guess, when more than one independant variable is used, the process is called Multiple Linear Regression.

$$ \hat{y} $$ = dependant variable  or the predicted value  
$$ x_1 $$ = independant variable  
  
=> $$ \boxed{\hat{y} = \overbrace{\theta_0 + \theta_1}^{\text{parameters}}\underbrace{x_1}_{\text{predictor}}} $$  
  
$$ \bar{x} $$ = moyenne des parametres independants (features)  
$$ \bar{y} $$ = moyenne des parametres dependants (target)  
$$ i = $$ same calcul pour chaque valeur  
$$ \theta_1 = \cfrac{\sum_{i}^s = 1(x_i - \bar{x})(y_i - \bar{y})}{\sum_{i}^s = 1(x_i - \bar{x})^2}  $$  (slope)
  
$$ \theta_0 = \bar{y} - \theta_1\bar{x} $$ (Bias Coefficient ?)  
  
  
With $$ \theta_0 $$ being the intercept and $$ \theta_1 $$ being the slope.  

### Error and Accuracy
#### Evaluation metrics
##### Mean Absolute Error (MAE)
MAE = $$ \cfrac{1}{n} \sum_{j=1}^n |y_j - \hat{y}_j| $$  
  
MAE = $$ \cfrac{(y_{j1} - \hat{y}_{j1}) + (y_{j2} - \hat{y}_{j2}) + (y_{j3} - \hat{y}_{j3}) + ... + (y_{jn} - \hat{y}_{jn})}{n} $$
##### Mean Squared Error (MSE)
MSE = $$ \cfrac{1}{n}\sum_{i=1}^n(y_i - \hat{y}_i)^2 $$

##### Root Meaned Squared Error (RMSE)
RMSE = $$ \sqrt{\cfrac{1}{n}\sum_{j=1}^n(y_j - \hat{y}_j)^2} $$
##### Relative Absolute Error (RAE)
RAE = $$ \cfrac{\sum_{j=1}^n|y_j - \hat{y}_j|}{\sum_{j=1}^n|y_j - \bar{y}|} $$
##### Relative Squared Error (RSE)
RSE = $$ \cfrac{\sum_{j=1}^n(y_j - \hat{y}_j)^2}{\sum_{j=1}^n(y_j - \bar{y})^2} $$  
  
The RSE is often used in Data Science as it is necessary to obtain the $$ R^2 $$ value, used to evaluate the performance. The higher it is, the better it fits the data.  
$$ R^2 = 1 - RSE $$


## Classification

### Binary Classification VS Mutliclass Classification

### K-Nearest Neighbours

### Evaluation Metrics in Classification
#### Jaccard Index / Jaccard Similarity Coefficient
#### F1-Score
#### Log Loss
