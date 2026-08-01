# Lab Assignment: Clustering Urban Mobility Patterns Using Bike-Sharing Data

## Objective

The objective of this assignment is to:

- Perform data preprocessing and feature engineering for mobility-pattern analysis.
- Apply and compare different clustering algorithms, excluding link-based clustering methods.
- Evaluate cluster quality and stability.
- Interpret the discovered clusters in the context of urban transport planning.
- Demonstrate theoretical understanding of clustering techniques.

---

# Dataset

## Bike Sharing Dataset – UCI Machine Learning Repository

Dataset URL:

https://archive.ics.uci.edu/dataset/275/bike+sharing+dataset

Use the **hourly dataset (`hour.csv`)**, which contains hourly bike rental records from the Capital Bikeshare system in Washington, D.C.

## Important Attributes

| Attribute | Description |
|---|---|
| `dteday` | Date |
| `hr` | Hour of the day |
| `season` | Season |
| `yr` | Year |
| `mnth` | Month |
| `holiday` | Whether the day is a public holiday |
| `weekday` | Day of the week |
| `workingday` | Whether it is a working day |
| `weathersit` | Weather condition |
| `temp` | Normalized temperature |
| `atemp` | Normalized apparent temperature |
| `hum` | Normalized humidity |
| `windspeed` | Normalized wind speed |
| `casual` | Number of casual users |
| `registered` | Number of registered users |
| `cnt` | Total number of rentals |

> **Important:** The clustering unit is a **day**, not an individual hourly record.

---

# Part 1: Data Preparation and Feature Engineering

## 1.1 Inspect and Clean the Data

Perform the following:

- Check for:
  - Missing values
  - Invalid values
  - Duplicate records

- Convert the date column into an appropriate date format.

- Verify that each date contains a reasonable number of hourly observations.

- Identify unusual or incomplete days.

- Explain how incomplete or invalid observations were handled.

---

## 1.2 Generate Daily Mobility Features

Aggregate hourly records by date and construct a daily feature vector.

The feature vector must include at least:

| Feature | Description |
|---|---|
| Total daily rentals | Sum of rentals per day |
| Average hourly rentals | Mean hourly rentals |
| Maximum hourly rentals | Highest hourly rental count |
| Standard deviation of hourly rentals | Daily rental variability |
| Morning peak share | Proportion of rentals between 6:00 AM and 9:00 AM |
| Evening peak share | Proportion of rentals between 4:00 PM and 7:00 PM |
| Off-peak rental share | Rentals outside peak periods |
| Casual-user proportion | Casual users / total users |
| Registered-user proportion | Registered users / total users |
| Average temperature | Daily average temperature |
| Average humidity | Daily average humidity |
| Average wind speed | Daily average wind speed |

Additional meaningful features may be introduced.

### Restrictions

- Do not include date identifiers.
- Do not include duplicate information directly in the clustering feature set.

---

## 1.3 Prepare the Clustering Data

Perform:

### Feature Distribution Analysis

- Examine feature distributions.
- Identify highly skewed features.
- Apply suitable transformations where necessary.

### Correlation Analysis

- Investigate highly correlated or redundant features.
- Remove unnecessary features.
- Clearly justify removed features.

### Feature Scaling

Standardize selected clustering features before applying algorithms.

---

## 1.4 Exploratory Visualisation

Include suitable visualisations:

- Histograms of daily mobility features.
- Boxplots of daily mobility features.
- Correlation heatmap.
- Daily rental pattern plots.
- Two-dimensional visualisation using PCA.

Briefly describe:

- Major trends.
- Patterns.
- Possible groups before clustering.

---

# Part 2: Apply and Analyse Clustering Methods

Apply clustering algorithms on the daily feature vectors.

---

# 2.1 K-Means Clustering

## Cluster Number Selection

Use multiple methods:

- Elbow Method.
- Silhouette Score.

Report:

- Selected number of clusters.
- Reason for selecting the final value.

---

## Cluster Analysis

Report and interpret:

- Cluster centroids.
- Centroids converted back to original feature scale.

Visualise clusters using:

- PCA.
- Another suitable dimensionality reduction method.

---

## Cluster Interpretation

Provide meaningful descriptions such as:

- Commuting-dominated days.
- Leisure-oriented days.
- Low-demand days.
- High-demand days.

---

# 2.2 Hierarchical Clustering Using AGNES

Apply agglomerative hierarchical clustering using:

1. Single linkage
2. Complete linkage
3. Average linkage

---

## For Each Linkage Method

Include:

- Dendrogram.
- Suitable cluster cuts.
- Cluster evaluation results.

Discuss:

- Differences between cluster structures.
- Strengths and weaknesses of each linkage method.

The final clustering decision should **not** be based only on dendrogram inspection.

Use evaluation metrics to support the decision.

---

# 2.3 DBSCAN

## Parameter Selection

Perform:

- Nearest-neighbour distance plot to determine `eps`.
- Justify selected `min_samples`.

---

## DBSCAN Analysis

Report:

- Number of clusters.
- Number of noise points.

Investigate sensitivity using:

- At least two alternative parameter settings.

Visualise:

- DBSCAN clusters.
- Noise observations.

Discuss:

- Whether noise points are:
  - Data errors.
  - Genuine unusual mobility days.

---

# Part 3: Clustering Evaluation and Comparison

Evaluate each meaningful clustering result using:

## Required Metrics

### 1. Silhouette Score

Measures cluster separation and cohesion.

### 2. Davies–Bouldin Index

Measures cluster similarity and compactness.

### 3. Distance Analysis

Compare:

- Intra-cluster distances.
- Inter-cluster distances.

### 4. Cluster Size Distribution

Analyse balance between clusters.

---

## DBSCAN Evaluation

Clearly state:

- How noise observations were handled during metric calculation.

---

# Method Comparison

Compare clustering methods based on:

| Criteria | Description |
|---|---|
| Cluster separation | How clearly groups are separated |
| Cluster compactness | Similarity within clusters |
| Parameter sensitivity | Stability under parameter changes |
| Cluster size balance | Distribution of observations |
| Interpretability | Meaningfulness of discovered groups |
| Treatment of unusual observations | Handling of rare mobility patterns |

---

## Final Selection

Select the most suitable clustering method.

Justify the choice.

> The clustering algorithm with the highest value for a single metric should not automatically be considered the best.

---

# Part 4: Cluster Interpretation and Validation

For the selected clustering result:

## Cluster Profiling

Produce cluster profiles using:

- Original non-standardized features.

---

## Compare Cluster Characteristics

Analyse:

- Weekday distribution.
- Weekend distribution.
- Holiday distribution.
- Season distribution.
- Weather distribution.

---

## Cluster Naming

Assign meaningful names.

Example:

- High-demand commuting days.
- Low-demand adverse weather days.
- Weekend leisure cycling days.

---

## Mobility Behaviour Explanation

Explain:

- User behaviour represented by each cluster.
- Differences between clusters.

---

## Practical Insights

Provide at least two insights supporting:

- Bike availability planning.
- Station rebalancing.
- Maintenance scheduling.
- Demand forecasting.

---

# Part 5: Theoretical Understanding

Answer the following questions concisely.

---

## 1. K-Means Assumptions

What assumptions does K-means make about:

- Cluster shape?
- Cluster size?
- Distance?

---

## 2. Linkage Criterion

How does the choice of linkage criterion affect hierarchical clustering?

---

## 3. Single Linkage Chaining Effect

Why is single linkage particularly vulnerable to the chaining effect?

---

## 4. DBSCAN Noise Detection

Why can DBSCAN identify noise points while K-means assigns every observation to a cluster?

---

## 5. Feature Scaling

Why was feature scaling necessary for this analysis?

---

## 6. Correlated Features

How can highly correlated features influence distance-based clustering?

---

## 7. PCA Usage

Advantages and disadvantages of using PCA only for visualisation instead of clustering directly on PCA components.

---

## 8. Distance Metrics

How would Manhattan distance potentially change clustering results compared with Euclidean distance?

---

## 9. Evaluation Metrics

Why should clustering quality not be judged using a single evaluation metric?

---

## 10. Valid Unusual Days vs Data Outliers

What is the difference between:

- An unusual but valid mobility day.
- A data-quality outlier.

---

# Submission Requirements

---

# 1. Python Implementation

Submit a well-organised and commented Jupyter Notebook containing:

- Data cleaning.
- Feature engineering.
- Exploratory analysis.
- Clustering implementations.
- Parameter selection.
- Evaluation.
- Visualisations.
- Cluster profiling.

Requirements:

- Notebook must execute from beginning to end.
- Use fixed random seeds where relevant.

---

# 2. Short Report

Submit an IEEE Conference Format report.

Maximum length:

**4 pages excluding references**

The report should include:

- Data preparation and feature engineering.
- Exploratory findings.
- Clustering methods.
- Parameter selection.
- Evaluation and comparison.
- Selected cluster interpretation.
- Practical mobility insights.
- Answers to theoretical questions.

Avoid including large blocks of source code.

---

# 3. Reproducibility

Include:

## Python Libraries and Versions

Document:

- Main libraries.
- Versions used.

Example:

- Python
- NumPy
- Pandas
- Scikit-learn
- Matplotlib
- Seaborn

---

## Documentation

Clearly document:

- Data cleaning decisions.
- Feature transformations.
- Removed features.
- Clustering parameters.

---

## Important Rule

Do **not manually remove observations** only to improve clustering scores.