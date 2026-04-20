# HW3 — Principal Component Analysis (PCA)

## Problem Statement
Apply PCA to the UCI Iris dataset to reduce its 4-dimensional feature space 
into 2 principal components while preserving maximum variance, enabling 
visual separation of the three Iris species.

## Data
- **Source:** UCI Machine Learning Repository — Iris Dataset (via scikit-learn)
- **Samples:** 150 (50 per species)
- **Features:** Sepal length, sepal width, petal length, petal width
- **Target:** Iris species (Setosa, Versicolor, Virginica)

## Data Mining Operations
- **Algorithm:** Principal Component Analysis (PCA)
- **Libraries:** numpy, scikit-learn, matplotlib
- **Preprocessing:** StandardScaler applied before PCA to normalize feature scale
- **Why PCA:** Reduces 4 correlated measurements into 2 components for 
  visualization while retaining 95.8% of total variance

## Model Outputs
- PC1 explained 73.0% of variance, PC2 explained 22.9%
- Combined 2-component retention: 95.8%
- 2D scatter plot shows clear separation between Setosa and the other two species

## Limitations
- Only 2 components visualized — remaining 4.2% of variance is discarded
- PCA is unsupervised and does not use class labels during transformation
- Iris is a simple, well-separated dataset and may not reflect real-world complexity

## Results
PCA successfully reduced 4 features to 2 principal components retaining 95.8% 
of variance. Setosa was clearly separated from Versicolor and Virginica, 
while the latter two showed partial overlap in the reduced space.
