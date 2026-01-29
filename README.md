# Credit Risk Scoring System

## Overview
This project focuses on building a **credit risk scoring system** using machine learning to predict whether a loan applicant is likely to **default or repay** a loan.

The main goal of the project is to understand how financial institutions use historical loan data to make **loan approval decisions**, and how machine learning models can support those decisions in a practical way.

Instead of only predicting outcomes, the project also converts model predictions into **risk levels and approval decisions**, similar to real banking systems.

---

## Problem Statement
Loan defaults are a major risk for banks and FinTech companies.  
Approving a risky borrower can result in financial loss, while rejecting a good borrower affects customer trust.

This project aims to:
- Predict the probability of loan default
- Identify high-risk borrowers
- Support loan approval, rejection, or manual review decisions

---

## Dataset
- **Lending Club Loan Dataset** (from Kaggle)
- Contains historical loan applications and repayment outcomes
- Includes borrower information, loan details, and financial indicators

Due to the large size of the dataset, it is **not included** in this repository.

---

## Features Used
To keep the model efficient and meaningful, only important financial and borrower features were selected:

- Loan amount  
- Loan term  
- Interest rate  
- Installment amount  
- Grade and sub-grade  
- Employment length  
- Home ownership  
- Annual income  
- Loan purpose  
- Debt-to-income ratio (DTI)  

Target variable:
- `loan_status`
  - `0` → Fully Paid  
  - `1` → Charged Off (Default)

---

## Data Preparation
The following preprocessing steps were applied:

- Filtered loans with clear outcomes (Fully Paid, Charged Off)
- Handled missing values using median imputation
- Converted categorical variables using one-hot encoding
- Reduced dataset size for faster training
- Cleaned feature names for model compatibility

---

## Models Used
### 1. SGDClassifier (Baseline Model)
- Used as a scalable baseline classifier
- Suitable for large datasets
- Helped establish initial performance

### 2. XGBoost (Final Model)
- Used for final predictions
- Performed better on tabular financial data
- Provided stronger ROC-AUC results

---

## Model Evaluation
The model was evaluated using:
- ROC-AUC score
- Recall for default cases
- Confusion matrix

Accuracy was not used as the main metric because the dataset is imbalanced and default detection is more important.

---

## Risk Scoring & Decision Logic
The model outputs a **probability of default**, which is converted into business-friendly decisions:

| Default Probability | Risk Level | Decision |
|--------------------|------------|----------|
| < 0.40 | Low Risk | Approve |
| 0.40 – 0.70 | Medium Risk | Manual Review |
| ≥ 0.70 | High Risk | Reject |

This approach reflects how credit risk models are actually used in banks.

---

## Real-Time Prediction
The trained model can score **new loan applications one at a time**, simulating a real-time credit approval system.

The system returns:
- Default probability
- Risk category
- Loan decision

Model files are saved using `joblib` for reuse.

---

## Key Learnings
- Working with large real-world financial datasets
- Feature selection for credit risk modeling
- Handling class imbalance
- Choosing business-relevant evaluation metrics
- Translating ML predictions into real decisions

---

## Technologies Used
- Python  
- Pandas & NumPy  
- Scikit-learn  
- XGBoost  
- Joblib  
- Google Colab  

---

## Project Structure
credit-risk-scoring-system/
│
├── notebooks/
│ └── credit_risk_model.ipynb
│
├── models/
│ ├── credit_risk_model.pkl
│ └── model_features.pkl
│
├── README.md
└── requirements.txt

## Acknowledgment
Dataset provided by **Lending Club** through Kaggle.

## Author
**Rahul Bisht**  
