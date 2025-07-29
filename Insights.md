# Data Understanding Report – Telco Customer Churn

## Overview
This dataset contains information about 7043 customers of a telecom company. The goal is to predict whether a customer is likely to churn based on their demographics, service usage, contract type, and billing information

## Target Variable
- **Churn**: Whether the customer left the company (Yes/No)
- Imbalanced dataset: 26.5% churned

## Column Overview
- **Numerical Features**: `tenure`, `MonthlyCharges`, `TotalCharges` (currently object), `SeniorCitizen` (binary)
- **Categorical Features**: Gender, Partner, PhoneService, InternetService, Contract type, etc

## Observations
- Most customers are not senior citizens
- Many customers are on month-to-month contracts - this might correlate with higher churn
- `TotalCharges` is incorrectly typed as object - to be fixed during data cleaning

## Data Cleaning Summary
- Converted `TotalCharges` from object to float and dropped 11 rows with missing values
- Replaced values like "No internet service" and "No phone service" with "No" for consistency across binary features
- Changed `SeniorCitizen` from 0/1 to "No"/"Yes" to align with other categorical columns

## Key Insights from EDA
- **Churn Rate**: 26.5% of customers churned. The dataset is imbalanced
- **Contract Type**: Month-to-month users are far more likely to churn than those on annual contracts
- **Tenure**: New users churn much more. Loyalty improves sharply after 1–2 years
- **Monthly Charges**: Higher monthly bills are associated with greater churn

## Visual EDA Insights
- **Churn is heavily concentrated** among customers with month-to-month contracts
- **New customers (under 1 year)** are most at risk of leaving
- **Higher monthly charges** are often seen in churned customers - pricing sensitivity may contribute
- **Customers with long tenure or 1–2 year contracts** are more loyal, indicating retention programs or contract incentives are effective

 ## Feature Engineering
- Dropped `customerID`, as it can't be used for predicting
- Encoded:
  - Binary variables using Label Encoding (`Yes`/`No` → `1`/`0`)
  - Multi-class variables using One-Hot Encoding
- Scaled numerical columns (`tenure`, `MonthlyCharges`, `TotalCharges`) using StandardScaler
- Split data into training (80%) and testing (20%) while maintaining class balance using stratified sampling

## Logistic Regression (Baseline)
- **Accuracy:** 80%
- **ROC-AUC:** 0.836
- The model is better at predicting retained customers than churners
- Precision (65%) is medium, but Recall (57%) indicates some missed churns
- This sets a baseline to compare more complex models like Random Forest or XGBoost

## Random Forest
- **Accuracy:** 79%
- **ROC-AUC:** 0.821
- Slightly lower recall for churn class compared to Logistic Regression
- Shows stronger performance for non-churn class but may underperform on finding actual churners

## XGBoost
- **Accuracy:** 77%
- **ROC-AUC:** 0.808
- **Recall for Churn:** 52%
- The XGBoost model performed similarly to Random Forest in terms of overall accuracy but did not significantly outperform the simpler logistic regression model.
- While it captured churned customers slightly better than Random Forest (52% vs 51%), it still missed many churn cases compared to Logistic Regression (57%).
- These results highlight that more complex models don't always lead to better performance, especially in moderately imbalanced datasets without heavy tuning.
