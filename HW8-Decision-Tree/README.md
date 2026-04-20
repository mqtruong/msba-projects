# HW8 — Decision Tree Classification

## Problem Statement
Predict whether a bank customer will accept a personal loan offer using a
Decision Tree classifier, and determine whether Gini Index or Entropy
produces better classification performance.

## Data
- **Source:** Course-provided dataset (Bank_Personal_Loan_Modelling.csv)
- **Samples:** 5,000 customers
- **Features:** 12 features including age, experience, income, family size,
  credit card average spend, education level, mortgage, and account holdings
- **Target:** Personal Loan (0 = Rejected, 1 = Accepted)
- **Missing Values:** None
- **Class Distribution:** 4,520 rejected / 480 accepted (highly imbalanced)

## Data Mining Operations
- **Algorithm:** Decision Tree Classifier (Supervised Classification)
- **Libraries:** pandas, numpy, scikit-learn, seaborn, matplotlib
- **Preprocessing:** Dropped non-predictive ID and ZIP Code columns;
  stratified 80/20 train/test split to preserve class balance
- **Split Criterion Comparison:** Gini (98.20%) vs. Entropy (99.20%)
- **Final Model:** Entropy criterion, max_depth=5 (random_state=42)
- **Why Decision Tree:** Interpretable tree structure is well-suited for a
  business decision use case; max_depth=5 constrains the model to avoid
  overfitting on the imbalanced dataset

## Model Outputs
- Accuracy: 99.1%
- Precision: Rejected 0.99, Accepted 0.96
- Recall: Rejected 1.00, Accepted 0.95
- F1-Score: Rejected 1.00, Accepted 0.95
- ROC-AUC Score: 0.993
- Decision tree visualization, ROC curve

## Limitations
- Severe class imbalance (90.4% rejected) means the model can achieve high
  accuracy by predominantly predicting rejection; the minority class F1 of
  0.95 should be the primary evaluation metric
- A shallow max_depth=5 tree may underfit complex interactions; deeper trees
  were not evaluated via cross-validation
- Decision trees are prone to overfitting when retrained on different data
  splits, so reported performance should be interpreted with caution

## Results
The Decision Tree using Entropy achieved 99.1% accuracy and an AUC of 0.993.
Income, CCAvg (credit card average spend), and Education emerged as the most
important splitting features, indicating that a customer's financial behavior
and educational background are the primary drivers of personal loan acceptance.
