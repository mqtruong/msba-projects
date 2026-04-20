# HW5 — Logistic Regression

## Problem Statement
Predict loan approval status (approved vs. denied) for 45,000 applicants using
Logistic Regression, identifying the most influential financial and demographic
factors driving lending decisions.

## Data
- **Source:** Course-provided dataset (loan_data.csv)
- **Samples:** 45,000 observations
- **Features:** 13 features including age, income, employment experience, home
  ownership, loan amount, loan intent, interest rate, loan percent of income,
  credit history length, credit score, and prior defaults
- **Target:** loan_status (0 = Denied, 1 = Approved)
- **Missing Values:** None
- **Class Distribution:** 35,000 denied / 10,000 approved (imbalanced)

## Data Mining Operations
- **Algorithm:** Logistic Regression (Supervised Classification)
- **Libraries:** pandas, numpy, scikit-learn, seaborn, matplotlib
- **Preprocessing:** Label encoding for categorical variables; StandardScaler
  normalization applied to all features
- **Train/Test Split:** 80/20 stratified split (random_state=42)
- **Why Logistic Regression:** Binary classification target with interpretable
  coefficient output makes logistic regression an appropriate baseline model

## Model Outputs
- Accuracy: 89.68%
- Precision: 89.56% | Recall: 89.68% | F1-Score: 89.61%
- ROC-AUC Score: 0.9514
- Confusion matrix, feature importance bar chart, ROC curve
- Top predictors: previous loan defaults (-4.54), loan percent of income
  (1.24), loan interest rate (0.98)

## Limitations
- Class imbalance (78% denied vs. 22% approved) may bias the model toward
  the majority class
- LabelEncoder applies arbitrary ordinal encoding to nominal categorical
  features such as loan intent and home ownership, which could introduce
  unintended relationships
- Logistic regression assumes a linear decision boundary, which may underfit
  complex nonlinear patterns in the data

## Results
The model correctly identified 6,572 denied and 1,499 approved loans on the
test set. Previous loan defaults on file were by far the strongest predictor,
followed by loan percent of income and loan interest rate, confirming that
repayment history and debt burden are the dominant factors in loan approval.
