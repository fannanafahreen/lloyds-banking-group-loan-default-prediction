# 🏦 Lloyds Banking Group — Loan Default Prediction

![Python](https://img.shields.io/badge/Python-3.x-blue) ![Machine Learning](https://img.shields.io/badge/Machine%20Learning-XGBoost%20%7C%20Random%20Forest-green) ![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

> Virtual work experience project completed as part of the **Digdata Step Up Career Challenge** with **Lloyds Banking Group**.

---

## 📋 Project Overview

Lloyds Banking Group is launching a new loans product and needs a reliable, fair, and explainable process to decide which customers to lend money to. Using historical data of **18,324 customers**, this project analyses past loan behaviour to understand what separates customers who repaid their loans from those who defaulted — and builds a machine learning model to predict future default risk.

---

## 🎯 Objectives

- **Task 1 — Data Strategy:** Explore the dataset and produce a visual summary comparing customers who repaid their loan against those who defaulted. Identify key differences in their financial behaviour and attributes.
- **Task 2 — Data Science:** Use historical data to design a machine learning process that predicts the likelihood of a new customer not paying back their loan. The model must be accurate, explainable, and fair.

---

## 📊 Dataset

| Property | Details |
|----------|---------|
| Total Customers | 18,324 |
| Features | 31 columns |
| Fully Paid | 14,418 (79%) |
| Charged Off | 3,906 (21%) |
| Source | Lloyds Banking Group via Digdata |

The dataset was provided by Lloyds Banking Group via Digdata 
and is not included in this repository for data privacy reasons. 
Please contact Digdata to access the original dataset.

### Key Features
- `loan_amnt` — Loan amount borrowed
- `int_rate` — Interest rate on the loan
- `annual_inc` — Customer annual income
- `installment` — Monthly repayment amount
- `loan_status` — Target variable (Fully Paid / Charged Off)
- `term` — Loan duration (36 or 60 months)
- `home_ownership` — Rent / Own / Mortgage
- `purpose` — Reason for the loan

---

## 🔍 Task 1 — Key Findings

| Metric | Fully Paid | Charged Off |
|--------|-----------|-------------|
| Avg Annual Income | £81,997 | £73,451 |
| Avg Loan Amount | £15,262 | £16,482 |
| Avg Interest Rate | 13% | 16% |
| Avg Monthly Installment | £461 | £490 |

### Visualisations Produced
- Categorical bar charts (term, home ownership, loan purpose)
- Scatter plots (loan amount vs income, interest rate vs loan amount)
- Line graphs (default rate by interest rate, loan amount, income bands)
- Correlation heatmap
- KDE distribution plots
- Outlier detection box plots

---

## 🤖 Task 2 — Models Built

### Data Preparation
- Label Encoding for categorical variables
- Standard Scaler for numerical features
- 80/20 train/test split with stratified sampling
- IQR capping for outlier treatment
- Median/zero/unknown filling for missing values

### Model 1 — Random Forest
```
n_estimators    : 200
max_depth       : 15
class_weight    : {0:1, 1:4}
threshold       : 0.35
```

| Metric | Score |
|--------|-------|
| Accuracy | 67.69% |
| ROC AUC | 0.67 |
| Charged Off Recall | 52% |
| Charged Off F1 | 0.41 |

### Model 2 — XGBoost (Recommended)
```
n_estimators      : 500
learning_rate     : 0.01
max_depth         : 6
scale_pos_weight  : 3.69
```

| Metric | Score |
|--------|-------|
| Accuracy | 67.04% |
| ROC AUC | 0.69 |
| Charged Off Recall | 56% |
| Charged Off F1 | 0.42 |

### Feature Engineering
Three new features were created:
- `debt_to_income` — Monthly installment / (annual income / 12)
- `loan_to_income` — Loan amount / annual income
- `balance_to_income` — Total balance / annual income

---

## 📈 Top 15 Most Important Features

| Rank | Feature | Importance |
|------|---------|-----------|
| 1 | int_rate | 0.1280 |
| 2 | avg_cur_bal | 0.0558 |
| 3 | annual_inc | 0.0541 |
| 4 | installment | 0.0537 |
| 5 | mo_sin_old_rev_tl_op | 0.0522 |
| 6 | mo_sin_old_il_acct | 0.0484 |
| 7 | total_bal_ex_mort | 0.0482 |
| 8 | loan_amnt | 0.0422 |
| 9 | total_acc | 0.0393 |
| 10 | addr_state | 0.0374 |

---

## 🛠️ Tools & Libraries

| Category | Tools |
|----------|-------|
| Language | Python 3.x |
| Data Manipulation | Pandas, NumPy |
| Visualisation | Matplotlib, Seaborn |
| Machine Learning | Scikit-learn, XGBoost |
| Environment | Jupyter Notebook |

---

## 📁 Repository Structure

```
lloyds-banking-group-loan-default-prediction/
│
├── Loan Default Prediction.ipynb    # Main project notebook
├── LBG Step Up Data Set.xlsx        # Dataset
├── LBG Step Up Data Dictionary.xlsx # Data dictionary
├── Lloyds_Submission.pptx           # 3-slide submission deck
└── README.md                        # Project documentation
```

---

## 🚀 How to Run

1. Clone the repository:
```bash
git clone https://github.com/fannanafahreen/lloyds-banking-group-loan-default-prediction.git
```

2. Install required libraries:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost openpyxl
```

3. Open Jupyter Notebook:
```bash
jupyter notebook "Loan Default Prediction.ipynb"
```

4. Run all cells from top to bottom

---

## 💡 Key Recommendations to Lloyds

1. **Use Interest Rate as Primary Signal** — importance score of 0.128, double any other feature
2. **Assess Affordability Holistically** — combine income, installment, and total debt
3. **Flag 60-Month Term Applications** — strong proxy for financial strain
4. **Ensure Fair & Explainable Decisions** — use feature importance for every decline

---

## ⚠️ Model Limitations

Despite testing multiple algorithms and techniques, model accuracy remained in the 67-78% range. This is consistent with the correlation heatmap findings which showed no single feature has a correlation above 0.10 with loan default status. In a real world setting, additional data such as credit scores, full payment history, and employment stability records would significantly improve model performance.

---

## 👩‍💻 Author

**Fannana Fahreen Aanan**
MSc Data Science (FinTech) — University of Greenwich
_ Digdata Virtual Work Experience — Lloyds Banking Group Step Up Challenge

---

## 📜 Acknowledgements

- **Lloyds Banking Group** for providing the dataset and challenge brief
- **Digdata** for organising the virtual work experience programme
