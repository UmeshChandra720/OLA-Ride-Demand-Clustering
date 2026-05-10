# OLA Driver Churn Prediction

## Overview
This project analyzes driver attrition patterns and builds a machine learning model to identify drivers at high risk of leaving the platform.

The objective was to understand why drivers churn, identify the most important business factors behind attrition, and generate actionable retention recommendations.

---

## Problem Statement
Driver churn directly impacts operational stability, recruitment cost, and service quality.

The goal of this project was to:

- Analyze historical driver data
- Identify key churn drivers
- Build a predictive model for early risk detection

---

## Dataset
The dataset contains 2,300+ driver records with information such as:

- Driver ID
- Quarterly Rating
- Monthly Income
- Total Business Value
- Grade
- Joining Designation
- City
- Joining Date
- Target (Churn / Retained)

---

## Project Workflow

### 1. Exploratory Data Analysis (EDA)

Performed analysis to understand:

- churn distribution
- joining trends
- rating patterns
- income growth
- city-level differences
- grade-level performance

### Key findings

- Drivers with Quarterly Rating = 1 showed the highest churn.
- No rating increase and no income increase strongly increased churn risk.
- Grade 1 drivers were more likely to leave.
- Some high-volume cities generated lower business value per driver.

---

### 2. Feature Engineering

Created additional features to improve predictive performance:

- Joining Month
- Joining Year
- Rating Increase Indicator
- Income Increase Indicator
- One-hot encoding for City

---

### 3. Hypothesis Testing

Used Chi-square tests to identify statistically significant features.

### Significant churn drivers

- Quarterly Rating
- Rating Increase
- Income Increase
- Grade
- Joining Designation
- City
- Reportings

### Non-significant features

- Gender
- Education Level

---

### 4. Data Preparation

- Removed irrelevant columns
- Train-test split (80:20)
- Standard scaling
- Handled class imbalance using SMOTE

---

## Modeling

### Models Used

- Random Forest
- LightGBM

### Hyperparameter Tuning

Used GridSearchCV for parameter optimization.

---

## Model Performance

### LightGBM (Best Model)

| Metric | Value |
|--------|-------|
| Training Accuracy | 96% |
| Test Accuracy | 92% |
| ROC-AUC | 0.96 |
| PR-AUC | 0.98 |

### Classification Report

| Class | Precision | Recall | F1-score |
|------|-----------|--------|----------|
| 0 | 0.89 | 0.87 | 0.88 |
| 1 | 0.94 | 0.95 | 0.94 |

---

## Confusion Matrix

| Actual / Predicted | 0 | 1 |
|--------------------|---|---|
| 0 | 133 | 20 |
| 1 | 17 | 307 |

The model correctly identified most churned and retained drivers with relatively low misclassification.

---

## Important Features

Top predictors of churn:

- Quarterly Rating
- Year
- Month
- Total Business Value
- Reportings
- Income
- Rating Increase

---

## Business Insights

- Churn is mainly driven by performance and career stagnation rather than demographics.
- Low-rated drivers form the highest-risk group.
- Lack of growth in rating and income is strongly associated with attrition.
- Early-stage drivers require focused retention support.

---

## Recommendations

- Create early intervention programs for low-rating drivers
- Provide rating improvement coaching
- Introduce income progression incentives
- Focus retention efforts on Grade 1 and new drivers
- Use the model as an early churn warning system

---

## Tech Stack

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- LightGBM
- Statsmodels

---

## Repository Structure

OLA-Driver-Churn-Prediction/
│
├── data/
├── notebooks/
├── images/
├── README.md
└── requirements.txt

---

## Future Improvements

- SHAP-based model explainability
- Time-based validation
- Deployment as a churn monitoring dashboard
