## Introduction

Bank loan default is a classic use case where ML models can be deployed to predict risky clients and hence minimize losses of the lender. The financial industry is highly regulated, thus any model(s) deployed or classification of clients based on their behavior, demographics etc. is highly regulated and must be explained to authorities to ensure unbiased operations

Loans are risky but at the same time it's also a product that generates profits for the institution through differential borrowing/ lending rates

The ML model should be explainable and be able to balance between risk and profits

For banks, it's an interesting and challenging problem to predict how likely client(s) are going to default on loan(s) when they only have a handful of information

## About the dataset

Historical financial transactions. This dataset contains ~ 308k line items, with a mix of numerical and categorical columns 

## Data pre-processing

Our dataset was dirty. Having missing values, outliers, and incorrect data types. We imputed nan values, treated outliers and corrected variables, name type suite and region rating client to string types

## Feature extraction

Since predicting the loan default is a binary classification problem, we first need to know how many instances in each class. By looking at the target variable in the Loan table, there are 2 distinct values: 0 and 1

* good loans (labeled as 0)

* bad loans (labeled as 1)

There are ~ 246k loans that fal into the "good" class and ~ 21k that fall into the "bad" class

With the two distinct classes defined, we have looked into the variables and plotted graphs to preview they correspondence to different distributions

## Feature transformation

After features were extracted, we transformed the data so that they could be fed into ML models in an organic way. In our case, we have two types of variables. Numerical, such as total income, credit amount, and annuity amunt. The other being categorical, such as code gender, region rating client, etc

We scaled numeric variables using scikit-learn option RobustScaler. On the other hand, the strategy for dealing with categorical variables was dummy encoding

## Modeling

The first step in training ML models is to split the data into training and testing sets. It's tricky in our dataset because it is not balanced: there are almost 12 times more "good" loans than "bad" loans. A stratified split is a good option here because it preserves the ratio between classes in both train and test sets

Our baseline modeel used was a Random Forest Classifier

Random forest classifier, Decision tree, and Gradient Boosting classifier algorithms were used in our ***test_code_XX_11_220 notebook*** 

F1 score is the harmonic mean between precision and recall, and ROC-AUC is the area under the ROC curve. These two are better metrics for evaluating the model performance for imbalanced data

With the models built, we ranked the features based on their importance, i.e features having the most predictive powers

For hamdling the imbalanced data we used SMOTE technique. SMOTE (Synthetic Minority Over-sampling Technique) is a type of over-sampling procedure that is used to correct the imbalances in our classes. This technique created new data instances of the minority class "bad loans" by copying existing minority instances and making small changes to them

Oversampling’s purpose is for us to feel confident the data we generate are real examples of already existing data. This inherently comes with the issue of creating more of the same data we currently have, without adding any diversity to our dataset, and producing effects such as overfitting

## Conclusion

Random Forest predicts better than Logistic Regression, however, in the banking industry, as per the government regulations and compliance requirements, one should be able to interpret the model results and clearly explain the reason for declining the loan(s) to the customer(s). Hence, Logistic Regression should be used to build the real model for deploying the same in production. Logistic Regression is simple which is a score that is a combination of coefficients multiplied by features. It can be interpreted as probabilities. If users are declined the features where their scores were low can be identified and the account holder can be told how to improve their score(s)
