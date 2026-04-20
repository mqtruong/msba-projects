# HW7 — SVM Classification

## Problem Statement
Classify breast tumor diagnoses as benign or malignant using Support Vector
Machines, and determine which kernel function produces the best classification
performance on high-dimensional medical data.

## Data
- **Source:** UCI Machine Learning Repository — Wisconsin Diagnostic Breast
  Cancer (WDBC) dataset
- **Samples:** 569 observations
- **Features:** 30 numeric features derived from digitized images of fine
  needle aspirates, measuring properties such as radius, texture, perimeter,
  area, smoothness, and concavity across mean, standard error, and worst-case
  measurements
- **Target:** diagnosis (0 = Benign, 1 = Malignant)
- **Missing Values:** None
- **Class Distribution:** 357 Benign / 212 Malignant

## Data Mining Operations
- **Algorithm:** Support Vector Machine (SVC) — Supervised Classification
- **Libraries:** pandas, numpy, scikit-learn, seaborn, matplotlib
- **Preprocessing:** Dropped non-predictive ID column; LabelEncoder applied
  to diagnosis column; StandardScaler applied to all 30 features (fit on
  training data only to prevent data leakage)
- **Train/Test Split:** 80/20 stratified split (random_state=42)
- **Kernel Comparison:** Linear (96.49%), RBF (97.37%), Polynomial (88.60%),
  Sigmoid (94.74%)
- **Why SVM:** High-dimensional feature space with relatively few samples is
  a classic use case for SVMs, which maximize the margin between classes

## Model Outputs
- Final Model Kernel: RBF (best performing)
- Accuracy: 97.37%
- Precision: Benign 0.96, Malignant 1.00
- Recall: Benign 1.00, Malignant 0.93
- F1-Score: Benign 0.98, Malignant 0.96
- ROC-AUC Score: 0.995
- Confusion matrix, ROC curve

## Limitations
- Small test set of 114 samples means individual misclassifications have
  an outsized effect on reported metrics
- RBF kernel results are sensitive to the choice of C and gamma hyperparameters,
  which were not tuned via grid search
- The dataset is relatively clean and balanced, so reported performance may
  not generalize to noisier real-world clinical data

## Results
The RBF kernel achieved the highest accuracy of 97.37% and an AUC-ROC of
0.995, outperforming linear, polynomial, and sigmoid kernels. Zero false
positives for malignant predictions on the test set confirms the model's
clinical reliability for ruling in malignancy.
