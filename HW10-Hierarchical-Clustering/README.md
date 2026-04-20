# HW10 — Hierarchical Clustering

## Problem Statement
Segment bank customers into distinct behavioral groups using Hierarchical
Clustering with Ward linkage, identifying profiles that could inform targeted
retention strategies for a churn prediction use case.

## Data
- **Source:** Course-provided dataset (Bank Customer Churn Prediction.csv)
- **Samples:** 10,000 customers
- **Features:** 6 clustering features — credit score, age, tenure, account
  balance, number of products, and estimated salary
- **Target:** Not used in clustering; churn label (0 = Retained, 1 = Churned)
  referenced for context only
- **Missing Values:** None
- **Class Distribution:** 7,963 retained / 2,037 churned

## Data Mining Operations
- **Algorithm:** Hierarchical Agglomerative Clustering — Ward linkage
  (Unsupervised)
- **Libraries:** pandas, numpy, scikit-learn, scipy, seaborn, matplotlib
- **Preprocessing:** Dropped non-predictive customer_id; LabelEncoder applied
  to country and gender; StandardScaler normalization applied to all 6
  clustering features
- **Dendrogram:** Plotted on a 200-row sample using Ward linkage for
  readability; full 10,000-row linkage computed for cluster assignment
- **Number of Clusters:** 3 (selected by cutting the dendrogram at maxclust=3)
- **Why Hierarchical Clustering:** Does not require pre-specifying k; Ward
  linkage minimizes within-cluster variance and produces compact, well-separated
  clusters suitable for customer segmentation

## Model Outputs
- Silhouette Score: 0.1527
- Dendrogram visualization (200-row sample)
- Age vs. Balance scatter plot colored by cluster
- Cluster mean feature profiles:
  - Cluster 1: Older customers (avg 41), high balance (~$115K), 1 product
  - Cluster 2: Mid-age customers (avg 38), high balance (~$114K), 2 products
  - Cluster 3: Younger customers (avg 37), near-zero balance (~$1.5K)

## Limitations
- The low silhouette score of 0.15 indicates overlapping clusters with limited
  separation, suggesting the selected features do not produce strongly
  distinct groupings
- Hierarchical clustering on 10,000 rows is computationally expensive; the
  full linkage matrix computation is O(n^2) and may not scale to larger datasets
- Three clusters were selected by visual inspection of the dendrogram rather
  than a quantitative criterion such as the silhouette method across multiple k

## Results
Ward linkage identified three customer segments primarily differentiated by
account balance and number of products. Cluster 3 represents a younger,
low-balance segment likely at higher churn risk, while Clusters 1 and 2
capture established customers with higher balances who differ mainly in product
engagement. These profiles offer a practical starting point for differentiated
retention outreach.
