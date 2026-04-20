# HW4 — Linear Regression

## Problem Statement
Predict employee salary based on years of experience using Linear Regression,
demonstrating a strong positive relationship between experience and compensation.

## Data
- **Source:** Course-provided dataset (Salary_dataset.csv)
- **Samples:** 30 observations
- **Features:** YearsExperience (independent variable)
- **Target:** Salary (dependent variable)
- **Missing Values:** None

## Data Mining Operations
- **Algorithm:** Linear Regression (Supervised Learning)
- **Libraries:** pandas, numpy, scikit-learn, matplotlib, seaborn
- **Preprocessing:** Min-Max scaling applied to YearsExperience feature
- **Why Linear Regression:** Strong linear correlation (0.978) between years of
  experience and salary makes linear regression the appropriate model choice

## Model Outputs
- Correlation coefficient between YearsExperience and Salary: 0.978
- R2 Score: 0.90 (model explains 90% of salary variance)
- RMSE: $7,059
- Regression line plot, Actual vs Predicted plot, Residual plot

## Limitations
- Very small dataset of only 30 observations limits generalizability
- Single feature model does not account for other salary drivers such as
  education, industry, or job title
- Results may not generalize across different industries or regions

## Results
The Linear Regression model achieved an R2 score of 0.90, confirming a strong
positive relationship between years of experience and salary. The residual plot
showed no systematic bias, validating the model fit on unseen data.
