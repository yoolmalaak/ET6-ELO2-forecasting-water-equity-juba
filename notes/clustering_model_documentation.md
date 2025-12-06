# Clustering Analysis

## 1. Introduction

Notebook 3 focuses on applying unsupervised machine learning techniques to
identify underlying structural patterns within the dataset, specifically
among school records. The goal of this stage was to determine whether schools
could be meaningfully grouped based on similarities in infrastructure,
water access, and operational characteristics. Such clustering provides
valuable insights for targeted policy interventions,
resource allocation, and infrastructure planning.

Due to the characteristics of the collected dataset, only school-level data met
the minimum sample size threshold required for robust clustering. Household and
health facility records were excluded because they did not contain enough valid
observations to support reliable unsupervised learning.

## 2. Data Preparation for Clustering

A subset of variables relevant to school characteristics was selected.
These features represent important aspects of water accessibility and
institutional operations, and were chosen based on domain knowledge
and exploratory analysis.

Selected Features

school_student_population

school_staff_population

school_monthly_water_cost_ssp

school_hours_water_available_numeric

school_type

school_ownership

These variables include both numerical and categorical attributes. Standard
preprocessing steps were applied:

Numeric variables were standardized.

Categorical variables were encoded using One-Hot Encoding.

Combined feature matrix shape after transformation: (121 observations × 22 features).

## 3. Clustering Methodology

The analysis implemented K-Means as the primary clustering algorithm.
In order to determine the most appropriate number of clusters (k),
three diagnostic approaches were used:

### 3.1 Elbow Method (Inertia)

The Elbow plot demonstrated a clear point of diminishing returns around k = 2,
where further increases yielded only marginal reductions in within-cluster variation.

### 3.2 Silhouette Score

Silhouette analysis indicated the highest cohesion and separation at k = 2,
with a silhouette score of:

0.6661, representing a strong cluster structure.

## 3.3 Calinski–Harabasz Index

The Calinski–Harabasz index peaked at k = 5, but the gain relative to k = 2
did not justify the added complexity.
Considering interpretability and silhouette strength, k = 2 was selected
as the final model.

## 4. Clustering Result

### 4.1 Final Model

Algorithm: K-Means

Optimal number of clusters: 2

Cluster quality metrics:

Silhouette Score: 0.6661

Calinski–Harabasz Score: 28.82

### 4.2 Cluster Interpretation

Principal Component Analysis (PCA) was used to project high-dimensional data
into a 2-dimensional space for visualization. The clusters were clearly
separable in the PCA plot, suggesting substantial
structural differences between groups.

Cluster-Level Characteristics (Numeric Variables)
Feature Cluster 0 (Lower-Cost Schools) Cluster 1 (High-Cost Outliers)
Monthly Water Cost (SSP) 9.32 × 10⁶ 4.00 × 10¹¹
Water Availability (Hours/Day) 5.33 hours 4.00 hours

Cluster 1 contains extreme outliers with extraordinarily high reported
costs—likely reflecting inconsistent data entry or currency format issues.
Cluster 0 represents the majority of schools, with plausible cost
and operational characteristics.

## 5. Visualization Outputs

The notebook generated several diagnostic and interpretive visualizations:

Elbow Curve — showing cost reduction across different values of k.

Silhouette and Calinski–Harabasz Scores — supporting k = 2.

PCA 2-Dimensional Scatter Plot — visual separation of clusters.

Boxplots of Key Numerical Features — highlighting differences in water-related
expenditures and availability.

All visual outputs were exported to:

/5_communication/charts/

## 6. Limitations

Household and Health Facility Clustering:
These groups had fewer than 8 valid observations and were excluded,
as clustering would have produced unstable and non-generalizable results.

Presence of Extreme Outliers:
Some values—particularly for monthly water costs—were several orders of
magnitude larger than expected, potentially affecting cluster boundaries.

Interpretation Constraints:
Although clusters were statistically separable, their practical implications
require careful contextual investigation to avoid misinterpretation.

## 7. Conclusion

Notebook 3 successfully delivered a structured unsupervised learning workflow
for school-level clustering. The analysis established that the dataset supports
a two-cluster solution, revealing substantial differences in cost structures
and water availability patterns across schools.
These findings provide a foundation for deeper investigation and can help
identify institutions requiring prioritized water-infrastructure support
