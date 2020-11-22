## Introduction

For banks, it's an interesting and challenging problem to predict how likely client(s) are going to default on loan(s) when they only have a handful of information

## About the dataset

Historical financial transactions 

## Data pre-processing

Our dataset was dirty. Having missing values, outliers, and incorrect data types. We imputed nan values, treated outliers and corrected variables, name type suite and region rating client to string types

## Feature extraction

Since predicting the loan default is a binary classification problem, we first need to know how many instances in each class. By looking at the target variable in the Loan table, there are 2 distinct values: 0 and 1

* 0: Are good loans

* 1: Are bad loans

There are approximately 246K loans that fal into the "good" class and 21K that fall into the "bad" class

With the two distinct classes defined, we have looked into the variables and plotted graphs to preview they correspondence to different distributions

## Feature transformation

After features were extracted, we transformed the data so that they could be fed into ML models in an organic way. In our case, we have two types of variables. Numerical, such as total income, credit amount, and annuity amunt. The other being categorical, such as code gender, region rating client, etc

We scaled numeric variables using scikit-learn option RobustScaler. On the other hand, the strategy for dealing with categorical variables was dummy encoding

## Modeling

The first step in training ML models is to split the data into training and testing sets. It's tricky in our dataset because it is not balanced: there are almost 12 times more "good" loans than "bad" loans. A stratified split is a good option here because it preserves the ratio between classes in both train and test sets

Random forest classifier, Decision tree, and Gradient Boosting classifier algorithms were used in our ***test_code_22_11_220 notebook*** 

F1 score is the harmonic mean between precision and recall, and ROC-AUC is the area under the ROC curve. These two are better metrics for evaluating the model performance for imbalanced data

With the models built, we ranked the features based on their importance, i.e features having the most predictive powers


