# Project 2 — World Happiness Report K-Means Clustering

## Problem Statement
Apply K-Means clustering to the 2021 World Happiness Report to group 143
countries into distinct happiness segments based on six socioeconomic factors,
and identify which factors most strongly differentiate high, moderate, and low
happiness nations.

## Data
- **Source:** Kaggle (World Happiness Report dataset)
- **Samples:** 143 countries (full dataset); 140 usable rows after accounting
  for missing values in feature columns
- **Features Used:** Log GDP per capita, Social support, Healthy life
  expectancy, Freedom to make life choices, Generosity, Perceptions of
  corruption, Dystopia + residual
- **Target:** None (unsupervised); Ladder score used post-hoc to validate
  cluster labels
- **Missing Values:** 3 countries missing values across the 6 factor columns
  and dystopia + residual; minimal impact on clustering
- **Dataset Structure:** 143 rows, 12 columns (2 object, 10 float64); each
  row represents one country's average survey scores

## Data Mining Operations
- **Algorithm:** K-Means Clustering (Unsupervised Learning)
- **Libraries:** pandas, numpy, scikit-learn, seaborn, matplotlib
- **Preprocessing:** StandardScaler applied to all numeric clustering features
  prior to K-Means to prevent high-magnitude features such as GDP from
  dominating distance calculations
- **Optimal k Selection:** Elbow method evaluated k=1 through k=10; inertia
  curve showed a clear inflection point at k=3
- **Final Model:** K-Means with k=3 (n_init=10, random_state=42)
- **Why K-Means:** Countries with continuous socioeconomic scores are well
  suited for centroid-based clustering; k=3 produces interpretable high,
  moderate, and low happiness segments aligned with real-world policy
  categories

## Model Outputs
- 3 clusters identified via elbow method
- Cluster 1 (High happiness): avg ladder score ~6.95; strong economies,
  high social support, good healthcare, high freedom scores
- Cluster 0 (Moderate happiness): avg ladder score ~5.95; mixed quality
  of life and moderate scores across all factors
- Cluster 2 (Low happiness): avg ladder score ~4.25; lower incomes, weaker
  healthcare, reduced social support
- GDP vs Social Support scatter plot colored by cluster assignment
- Average Happiness Score by Cluster bar chart
- Elbow method inertia plot (Optimal K)

## Key Findings
- GDP per capita and social support are the primary differentiating factors
  between clusters, as shown by the GDP vs Social Support scatter plot where
  clusters separate cleanly along both axes
- The bar chart validates cluster labels without supervision; average ladder
  scores follow a monotonic ordering across the three clusters confirming
  the clustering captured a meaningful happiness gradient
- Cluster 1 nations concentrate in the upper right of the GDP vs Social
  Support space, while Cluster 2 nations concentrate in the lower left,
  indicating that economic output and community support move together
  as joint drivers of national happiness

## Limitations
- K-Means assumes spherical, equally sized clusters, which may not reflect
  the true shape of happiness distributions across geopolitically diverse
  nations
- The dataset represents a single year (2021); happiness rankings shift year
  to year and longitudinal clustering would provide more robust country
  profiles
- Generosity and perceptions of corruption had 3 missing values each; while
  minimal, countries with missing data were excluded from full feature
  analysis
- Cluster label interpretation (high, moderate, low) is applied post-hoc
  based on average ladder scores and is not guaranteed by the algorithm

## Results
K-Means with k=3 successfully segmented 143 countries into three happiness
tiers. GDP per capita and social support emerged as the strongest
differentiators between clusters. The cluster validation via average ladder
scores confirms that the unsupervised groupings align with meaningful
real-world differences in national wellbeing, demonstrating that happiness
outcomes are closely tied to economic prosperity and social infrastructure.
