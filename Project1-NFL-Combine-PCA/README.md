# Project 1 — NFL Combine RB vs WR Athleticism (PCA)

## Problem Statement
Apply Principal Component Analysis to 2025 NFL Combine measurements for
Running Backs and Wide Receivers to identify the primary athletic dimensions
that differentiate the two positions, and visualize how body frame and speed
separate players in reduced-dimensional space.

## Data
- **Source:** 2025 NFL Combine Dataset (2025 NFL Combine Dataset.csv)
- **Scope:** Filtered to RB and WR positions only
- **Samples:** 63 players after dropping rows with missing values
  (RB=24, WR=39); original filtered set was 80 players (RB=31, WR=49)
- **Features Selected:** Weight (lbs), Height (ft, numeric), Hand Size (in),
  40 Yard Dash (sec)
- **Missing Values:** Hand Size had 1 missing value (1.2%); 40 Yard Dash had
  17 missing values (21.2%); rows with any missing value in the 4 selected
  features were dropped
- **Feature Selection Rationale:** These 4 measurements are the most
  meaningful from an NFL scouting perspective for skill positions, and
  retaining them minimized data loss compared to columns such as Wingspan
  (61.3% missing) and Bench Press (80% missing)

## Data Mining Operations
- **Algorithm:** Principal Component Analysis (Unsupervised Dimensionality
  Reduction)
- **Libraries:** pandas, numpy, scikit-learn, seaborn, matplotlib
- **Preprocessing:** StandardScaler applied to all 4 features prior to PCA
  to normalize the scale differences between weight in pounds and dash time
  in seconds; all missing values resolved by row-wise deletion
- **Components Evaluated:** Full 4-component PCA for explained variance
  analysis; reduced to 2 components for visualization
- **Why PCA:** 4 scouting features with moderate inter-correlations (0.10 to
  0.40 range) are suitable for compression into interpretable principal
  components that reveal the underlying athletic structure of the data

## Model Outputs
- PC1 captures 41.4% of variance (body size axis: Weight, Height, Hand Size)
- PC2 captures 26.0% of variance (speed axis: 40 Yard Dash)
- Combined 2D variance retained: 67.4%
- All 4 components required to reach both 90% and 95% variance thresholds
- Scree plot and cumulative variance chart
- 2D PCA scatter plot colored by position (RB vs WR)
- Feature loadings heatmap across all 4 principal components
- EDA boxplots comparing feature distributions by position
- Feature correlation heatmap

## Key Findings
- RBs are heavier on average (208.6 lbs vs 196.1 lbs) and shorter (5.87 ft
  vs 6.09 ft), consistent with the lower center of gravity required at the
  position
- WRs have slightly larger hands on average (9.29 in vs 9.13 in), consistent
  with the catching demands of the position
- 40 Yard Dash times are nearly identical across positions (4.48 vs 4.46 sec),
  confirming speed is a universal baseline requirement at both skill positions
- PC1 separates positions primarily by body frame; RBs cluster at higher PC1
  values while WRs spread more broadly, reflecting the variety of receiver
  body types including boundary and slot archetypes
- Overlap in the middle of the scatter plot reflects modern NFL positionless
  players such as pass-catching RBs and receivers used in run packages

## Limitations
- 40 Yard Dash missingness of 21.2% required dropping 17 players, reducing
  the RB sample to 24, which limits the statistical power of position
  comparisons
- Only 4 of the available combine measurements were used; incorporating
  vertical jump, broad jump, and agility drills would provide a more complete
  athletic profile but would further reduce the usable sample due to high
  missingness in those columns
- PCA captures physical and speed dimensions only; football-specific skills
  such as route running, catching ability, and vision are not measurable from
  combine data

## Results
PCA reduced the 4 NFL combine measurements into 2 interpretable athletic
dimensions: body size (PC1) and speed (PC2). The 2D scatter plot shows
partial but meaningful separation between RBs and WRs along the size axis,
confirming that physical frame is the primary differentiator between the two
positions at the combine level. Speed alone does not separate positions,
as both groups demonstrate equivalent 40 Yard Dash performance.
