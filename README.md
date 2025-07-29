# 🧠 Customer Churn Prediction – Machine Learning Project

## 📌 Project Overview
This project aims to predict customer churn in a telecom company using supervised machine learning models. The objective is to help the company proactively identify customers likely to leave, so they can take action to retain them

The workflow follows the standard data science lifecycle:
- Data understanding and cleaning
- Exploratory Data Analysis (EDA)
- Feature engineering and encoding
- Model training and evaluation
- Insights and business recommendations

---

## 📂 Dataset
**Source:** [Kaggle – Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)  
**Rows:** 7,043  
**Columns:** 21

---

## 🔍 Problem Statement
**Goal:** Predict whether a customer will churn (leave) or not, based on service details and demographic data

---

## 🔬 EDA Highlights
- Customers on **month-to-month contracts** and **with higher monthly charges** are more likely to churn
- **New users (tenure < 1 year)** show the highest churn rates
- Customers with **long-term contracts or longer tenure** are more loyal

Visualizations included:
- Churn distribution
- Churn by contract type
- Churn by tenure group
- Monthly charges vs churn (box plot)

---

## 🧹 Data Preprocessing
- Handled non-numeric values in `TotalCharges`
- Encoded categorical variables using:
  - Label Encoding for binary features
  - One-Hot Encoding for multi-class features
- Scaled numerical features (`tenure`, `MonthlyCharges`, `TotalCharges`)
- Train-test split using stratification on the churn variable

---

## 🤖 Models Used & Results

| Model                | Accuracy | Churn Recall | ROC-AUC |
|----------------------|----------|--------------|---------|
| Logistic Regression  | **80%**  | **57%**      | **0.836**|
| Random Forest        | 79%      | 51%          | 0.821   |
| XGBoost              | 77%      | 52%          | 0.808   |

> ✅ **Final Model Selected:** Logistic Regression – due to the highest recall on churners and best ROC-AUC

---

## 🧠 Insights & Learnings

For a detailed walkthrough of the decisions made during the project, including data understanding, cleaning steps, exploratory insights, model evaluation comparisons, and final conclusions. Refer to the separate file:

📄 [`INSIGHTS_AND_LEARNINGS.md`](./INSIGHTS_AND_LEARNINGS.md)

This file reflects the thought process behind the project and serves as a technical and business summary of the entire workflow

---


## 🧠 Key Takeaways

- Churn is strongly associated with pricing, contract flexibility, and early tenure
- Logistic Regression performed best in identifying potential churners
- Business can take proactive steps for at-risk customers based on these predictions
