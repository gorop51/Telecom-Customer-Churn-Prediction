\# 📱 Telecom Customer Churn Prediction



\## 📌 Project Overview



Telecom operator "TeleDom" aims to reduce customer churn by offering personalized promocodes and special conditions to clients planning to leave. This project develops a machine learning model to predict the probability of contract termination.



\## 🎯 Objective



Create a model that accurately predicts customer churn with:

\- ROC-AUC ≥ 0.85

\- High recall (prioritizing identifying potential churners over false positives)



\## 📊 Dataset Description



Four CSV files containing customer information as of February 1, 2020:



1\. \*\*contract\_new.csv\*\* - contract details:

&nbsp;  - `customerID`, `BeginDate`, `EndDate` (target feature)

&nbsp;  - Billing and payment information (`Type`, `PaperlessBilling`, `PaymentMethod`)

&nbsp;  - Charges (`MonthlyCharges`, `TotalCharges`)



2\. \*\*personal\_new.csv\*\* - customer demographics:

&nbsp;  - `Dependents`, `SeniorCitizen`, `Partner`



3\. \*\*internet\_new.csv\*\* - internet services:

&nbsp;  - `InternetService` (DSL/Fiber optic)

&nbsp;  - Additional services (`OnlineSecurity`, `OnlineBackup`, etc.)



4\. \*\*phone\_new.csv\*\* - phone services:

&nbsp;  - `MultipleLines`



\## 🔍 Methodology



\### Data Preparation

\- Merged datasets using `customerID`

\- Converted `EndDate` to binary target (1 = churned, 0 = active)

\- Created new feature `Months` (contract duration)

\- Handled missing values and transformed categorical features

\- Removed highly correlated `TotalCharges` feature (MSE = 103.45 with `MonthlyCharges \* Months`)



\### Modeling Approach

Tested multiple models with cross-validation and focal loss to address class imbalance (only ~26% churn rate):



\- DecisionTreeClassifier (ROC-AUC: 0.808)

\- RandomForestClassifier (ROC-AUC: 0.834)

\- LGBMClassifier with focal loss (ROC-AUC: 0.899)

\- LogisticRegression (ROC-AUC: 0.757)

\- Neural Network (ROC-AUC: 0.871)



\## 📈 Results



\*\*Best Model\*\*: LGBMClassifier with matched hyper-parameters.



\*\*Test Performance\*\*:

\- ROC-AUC: 0.913

\- Recall: 90% (correctly identifies 90% of customers planning to leave)



The model successfully identifies high-risk customers, enabling targeted retention strategies while minimizing customer loss.

