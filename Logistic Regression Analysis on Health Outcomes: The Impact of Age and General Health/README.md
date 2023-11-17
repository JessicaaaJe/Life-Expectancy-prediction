# R-Project

# Logistic Regression Analysis on Regular Exercise Probability

**Author:** Jessica Chen

## Abstract

This project investigates factors contributing to health-related risk behaviors and chronic health conditions, focusing on the probability of individuals exercising regularly. Using data from the Behavioral Risk Factor Surveillance System (BRFSS), we analyze the influence of various predictors on exercise frequency.

## Introduction

Our primary research questions aim to understand the relationship between individuals' weight loss goals, their general health, and the probability of regular exercise. We also seek to determine the predictability of exercise regularity using demographic variables.

## Data

The dataset from BRFSS comprises 20,000 respondents, with variables including general health, exercise frequency, health plan status, smoking habits, and demographic information. A subset `cdc_new` was created to focus on individuals whose weight exceeds their desired weight, adding a `weightLoss` variable for analysis.

## Exploratory Data Analysis (EDA)

We performed EDA on the response variable `exerany` to understand the number of respondents who exercised in the past month. Further EDA was conducted on potential predictors, including smoking habits (`smoke100`), gender, and height, to prepare for model building.

## Modeling

A logistic regression model was constructed to evaluate the relationship between the probability of regular exercise and predictors such as age, general health, health plan, weight loss, and height. Three models were compared for best fit.

## Predictive Ability

We assessed the model's predictive ability using overall accuracy, sensitivity, and specificity. Our model showed high accuracy and sensitivity but indicated a need for improvement in predicting true negatives.

## Discussion

The final model highlights a negative relationship between the probability of exercising regularly and expected weight loss, and a positive relationship with general health conditions, health plan, and height. Future research may include additional BRFSS variables to improve model specificity.

---

For more detailed analysis and methodology, please refer to the full report in this repository.
