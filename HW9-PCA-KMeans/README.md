# HW9 — PCA and K-Means Clustering

## Problem Statement
Apply Principal Component Analysis for dimensionality reduction and K-Means
for unsupervised clustering on the Heart Disease Cleveland dataset, evaluating
how well each method preserves or uncovers the underlying binary diagnostic
signal.

## Data
- **Source:** UCI Machine Learning Repository — Heart Disease Cleveland
  (processed.cleveland.data)
- **Samples:** 297 observations (after dropping 6 rows with missing values)
- **Features:** 13 clinical features including age, sex, chest pain type,
  resting blood pressure, cholesterol, fasting blood sugar, resting ECG,
  max heart rate, exercise-induced angina, ST depression, slope, number of
  vessels, and thalassemia type
- **Target:** Binarized diagnosis (0 = No Disease, 1 = Disease present)
- **Missing Values:** 6 rows dropped (ca and thal columns)
- **Class Distribution:** 164 No Disease / 139 Disease

## Data Mining Operations
- **Algorithms:** PCA (dimensionality reduction) + KNN classifier for
  evaluation; K-Means (unsupervised clustering)
- **Libraries:** pandas, numpy, scikit-learn, scipy, seaborn, matplotlib
- **Preprocessing:** Dropped rows with missing values; binarized target;
  StandardScaler applied (fit on training data only); 80/20 train/test split
- **Why PCA:** 13 correlated clinical features benefit from compression into
  uncorrelated components before downstream classification
- **Why K-Means:** Unsupervised evaluation of whether clinical features
  naturally separate healthy from diseased patients without label supervision

## Model Outputs
**PCA**
- Components retained: 12 (capturing 97.5% of variance)
- KNN accuracy on PCA-transformed data: 81.67%
- Precision: No Disease 0.80, Disease 0.84
- Recall: No Disease 0.88, Disease 0.75
- Explained variance per component bar chart

**K-Means**
- Optimal k: 2 (selected via elbow method; aligns with binary target)
- Accuracy (label-aligned): 85.00%
- Precision: No Disease 0.79, Disease 0.95
- Recall: No Disease 0.97, Disease 0.71

## Limitations
- PCA retains 12 of 13 original components at the 95% variance threshold,
  offering minimal compression on this dataset; a lower threshold such as
  90% would yield more aggressive reduction
- K-Means cluster labels require post-hoc alignment to true class labels via
  majority vote, which is an approximation and not a guaranteed optimal mapping
- KNN was used as a proxy classifier to evaluate PCA quality; a different
  classifier may produce different accuracy results on the same components

## Results
PCA reduced the feature space while retaining 97.5% of variance, and KNN on
the transformed components achieved 81.67% accuracy. K-Means with k=2
outperformed the PCA-KNN pipeline at 85% accuracy, suggesting the clinical
features naturally cluster into two groups that closely correspond to the
presence or absence of heart disease.
