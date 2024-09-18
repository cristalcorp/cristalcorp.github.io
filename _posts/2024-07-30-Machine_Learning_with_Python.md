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
$$ \bar{x} $$ = moyenne des parametres independants (features)  
$$ \bar{y} $$ = moyenne des parametres dependants (target)  
$$ i = $$ same calcul pour chaque valeur  
$$ \theta_1 = \cfrac{\sum_{i}^s = 1(x_i - \bar{x})(y_i - \bar{y})}{\sum_{i}^s = 1(x_i - \bar{x})^2}  $$  (slope)
  
$$ \theta_0 = \bar{y} - \theta_1\bar{x} $$ (Bias Coefficient ?)  
  
=> $$ \boxed{\hat{y} = \overbrace{\theta_0 + \theta_1}^{\text{parameters}}\underbrace{x_1}_{\text{predictor}}} $$  
  
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

## Multiple Linear Regression


## Classification

### Binary Classification VS Mutliclass Classification

### K-Nearest Neighbours

### Evaluation Metrics in Classification
#### Jaccard Index / Jaccard Similarity Coefficient
#### F1-Score
#### Log Loss
