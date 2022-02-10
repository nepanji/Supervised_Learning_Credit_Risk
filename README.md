# Supervised_Machine_Learning
## Overview
In this assignment, the task is to build a machine learning model that attempts to predict whether a loan from LendingClub 
will become high risk or not. 

## Data Preparation
The initial step is to retrieve the data. We are provided with the GenerateData.ipynb notebook file in the Generator folder in the Resources that
will download data from LendingClub and output two CSVs: (1) 2019loans.csv (2) 2020Q1loans.csv.

The entire year's worth of data (2019) to predict the credit risk of loans from the first quarter of the next year (2020).

## Preprocessing
I'll create a training set from the 2019 loans using pd.get_dummies() to convert the categorical data to numeric columns. I will also create a 
testing set from the 2020 loans, also using pd.get_dummies(). To fit a model I will need to use code to fill in the missing categories in the testing set.

## Consider the Models
When I think about identifying default risk of loans, I am immediately drawn to the concept of classificaiton. I will be using a LogisticRegression and a 
RandomForestClassifier model to make predictions on this data. In this assignment, because I am creating comparing models to predict credit risk, I believe 
that the logistic regression model will provide the best results since it is used to predict a discrete set of classes or categories.

Measuring success of how well each model predicts the probability that a borrower is high-risk or low risk depends on the amount of revenue that can be 
generated from the financial decision to lend or not to lend based on the model observations. This can be accomplished by finding a model that will yield the
highest recall rate (% of bad credit classified as bad) with the least amount of false negatives (# of bad credit misclassified as good). 

## LogisticRegression model and RandomForestClassifier Model 
### Model Comparisons (Unscaled data)
The LogisticRegression model of unscaled data produces an accuracy score of 52%. The precision score for high risk is 53% and low risk is 51%. 
The sensitivity score for high risk is 30% and low risk is 73%. This model is not ideal based on the fact that the percentage of correct predictions is at 52%, 
the percentage of correct positive predictions for both risk types is between 51%-53% which is less than ideal , and the percentage of correct actual positive 
results is low for high risk. This model produced the second highest number of false negatives at 1640. 

The RandomForestClassifier model of unscaled data produces an accuracy score of 64%. The precision score for high risk is 61% and low risk is 71%. 
The sensitivity score for high risk is 80% and low risk is 48%. This model is a better option than LogisticRegression based on the fact that the percentage of 
correct predictions is at 64% and better than 52%, the percentage of correct positive predictions for high risk types is 80% which is more ideal than 
the LogisticRegression model. This model produced the least number of false negatives at 463.

### Model Comparisons (Unscaled data)
The LogisticRegression model of scaled data produces an accuracy score of 77%. The precision score for high risk is 77% and low risk is 76%. The sensitivity score 
for high risk is 76% and low risk is 77%. This model is ideal based on the fact that the percentage of correct predictions is at 77%, the percentage of correct 
positive predictions for both risk types is between 76%-77% which is also better, and this model produced a low Type II error of 562; therefore, reducing the 
costly number of bad credit misclassifications as good.

The RandomForestClassification model of scaled data produces an accuracy score of 50%. The precision score for both high and low risk is 50%. The sensitivity score 
for high risk is 21% and low risk is 79%. This model is not ideal based on the fact that the percentage of correct predictions is at 50%, the percentage of correct 
positive predictions for both risk types is between 50% which is not ideal , and the percentage of correct actual positive results is very low for high risk. 
This model produced the highest number of false negatives at 1848; whereby, creating the most costly number of bad credit misclassification as good.

## Conclusion
Examing the above results showed that the LogisticRegression model of scaled data has a accuracy of 77%, meaning 7.7 out of 10 risks were identified correctly. This
model was also 77% precise when labeling high risk and low risk borrowers and 77% sensitive, meaning that 2.3 out of every 10 risks were missed by the model and 23%
of high and low risks are miss labeled. Additionally, this model produced a low number of false negatives and false positives, meaning there is a low occurance of
bad credit misclassifications as good and a low number of good credit misclassifications as bad. 