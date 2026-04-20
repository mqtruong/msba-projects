# HW6 — Naive Bayes

## Problem Statement
Classify patients as diabetic or non-diabetic based on glucose level and blood
pressure measurements using Gaussian Naive Bayes.

## Data
- **Source:** Course-provided dataset (Naive-Bayes-Classification-Data.csv)
- **Samples:** 995 observations
- **Features:** glucose, bloodpressure
- **Target:** diabetes (0 = No Diabetes, 1 = Diabetes)
- **Missing Values:** None
- **Class Distribution:** Nearly balanced (50/50 split)

## Data Mining Operations
- **Algorithm:** Gaussian Naive Bayes (Supervised Classification)
- **Libraries:** pandas, numpy, scikit-learn, seaborn, matplotlib
- **Preprocessing:** No scaling required; Gaussian NB assumes features follow
  a normal distribution and handles raw numeric values directly
- **Train/Test Split:** 80/20 (random_state=42)
- **Why Gaussian Naive Bayes:** Continuous numeric features with an
  approximately normal distribution make Gaussian NB a natural fit; the
  dataset is small and the feature space is low-dimensional

## Model Outputs
- Training Accuracy: 93.97%
- Test Accuracy: 90.95%
- Precision: 0.91 | Recall: 0.91 | F1-Score: 0.91 (both classes)
- ROC-AUC Score: 0.976
- Confusion matrix (training and test), ROC curve

## Limitations
- Only two features are used; additional clinical indicators such as BMI,
  insulin level, and age could substantially improve predictive power
- The Gaussian assumption may not perfectly capture the true feature
  distributions, particularly for blood pressure which can be multimodal
- Small dataset of 995 observations limits the robustness of performance
  estimates

## Results
The Gaussian Naive Bayes model achieved 90.95% test accuracy with symmetric
precision and recall across both classes, indicating well-balanced
classification performance. The high AUC of 0.976 confirms strong
discriminative ability between diabetic and non-diabetic patients using only
two clinical features.
