# Juba Urban Water Access, Equity and Demand Forecasting

## MIT Emerging Talent – Data Science Capstone Project

**Author: Yool Malaak Yool Ajak**
**Year: 2025**

### Project Overview

Urban water access remains one of the biggest public-service challenges in Juba,
South Sudan. Many households and institutions depend on water vendors,
boreholes, and informal supply chains that are unreliable, unequal, and
expensive. This project applies data science and machine learning to understand
current water inequalities and to forecast future water demand
for the growing city of Juba.

**The project covers four main components:**

- Regression: Predicting weekly water costs

- Classification: Predicting which schools have potable water

- Clustering: Grouping households/institutions with similar water challenges

- Forecasting: Predicting Juba’s water demand up to 2035

The goal is to support a data-driven understanding of inequity, access,
and future needs—and to provide insights useful for policymakers, NGOs,
urban planners, and development partners.

### Project Roadmap

This roadmap outlines the complete workflow followed throughout the project.

### Phase 1: Problem Definition & Domain Understanding

Reviewed literature and reports on water access issues in Juba

**Identified systemic challenges:**

high cost of water vendors

long distances to sources

reliability issues

inconsistent quality

Defined key analysis questions:

Who has access?

Who pays more?

How can ML help identify under-served groups?

How much water will Juba need in the next decade?

Phase 2:Data Collection

**Survey data was collected from:**

Households

Schools

Health facilities

Community informants

Supplementary data:

Population estimates for Juba (2010–2025)

Contextual notes on local water sources, vendor behavior, and pricing patterns

### Phase 3: Data Preparation

Cleaned all datasets and combined them into a unified analytical dataset

Converted text-based fields into structured indicators (high cost, reliability,
access, quality, infrastructure, etc.)

Created engineered variables:

numeric encodings

binary flags

normalized cost indicators

Final dataset stored as:

2_data_preparation/final_cleaned_dataset.csv

### Phase 4: Exploratory Data Analysis (EDA)

Visualized distributions, shortages, reliability, distance to water,
and demographic patterns

Identified structural inequities in potable water access

Investigated correlations and feature importance signals

Prepared charts for storytelling and communication

### Phase 5: Regression Modeling (Weekly Water Cost)

Objective: Can we predict weekly water cost using demographic and access indicators?

Outcome:
All regression models (Random Forest, Gradient Boosting, XGBoost) achieved
negative R² after removing leakage variables.

Conclusion:
Weekly water cost cannot be predicted from household characteristics alone.
Pricing is dominated by:

vendor discretion

scarcity periods

fuel prices

informal market dynamics

This is an important policy insight:

Affordability is structurally uncontrolled and not linked to needs or household conditions.

### Phase 6: Classification Modeling (School Potable Water Access)

Objective: Predict whether a school has potable water.

Actions:

Removed leakage variables linked directly to the target

Used SMOTE to address class imbalance

Applied preprocessing, feature selection, and cross-validation

Compared Logistic Regression, Random Forest, XGBoost, and Gradient Boosting

Best Model:

Logistic Regression with ROC-AUC ≈ 0.87

Interpretation:
Potable water access in schools is driven by:

school type

ownership

hygiene infrastructure

water reliability indicators

### Phase 7: Clustering (Unsupervised Learning)

Objective: Identify natural vulnerability groups among respondents.

Methods:

K-Means clustering

Standardized numeric variables

One-hot encoded categorical variables

Selected core water-related features: shortages, cost flags, quality,
access, distance, reliability

Findings (example clusters):

Cluster A: Severe shortages, long distance, high cost

Cluster B: Moderate access, but frequent quality and contamination concerns

Cluster C: Better reliability but high dependence on vendors

Cluster D: Institutions with moderate reliability but infrastructure problems

These clusters help quantify which groups are most under-served—critical
for targeting interventions.

Phase 8: Forecasting Juba’s Water Demand (2010–2035)

Using population growth data and per-capita consumption scenarios (40, 60, 80 LPPD):

Models used:

Linear Regression

Polynomial Regression

Exponential Model

ARIMA

Prophet

Result:

By 2035, Juba’s annual water demand rises 50–80% depending on consumption scenario.

This reveals a significant infrastructure investment gap.

Phase 9: Communication & Reporting

Exported all charts to the /5_communication folder

Organized notebooks for clean execution

Prepared summary insights for an MIT Emerging Talent presentation

Ensured reproducibility for reviewers

### Repository Structure

0_domain_study/           Background materials & problem framing
1_dataset/                Raw collected dataset
2_data_preparation/       Cleaning scripts + final_cleaned_dataset.csv
3_data_exploration/       Exploratory visuals & analysis
4_data_analysis/          Regression, Classification, Clustering, Forecasting
5_communication/          Plots, charts, and report-friendly visuals
6_final_presentation/     Project slides for Emerging Talent
notes/                    meeting notes, explanation of Notebooks, and etc.

### Tools & Technologies

Python (pandas, numpy, matplotlib, seaborn)

scikit-learn (regression, classification, clustering)

xgboost

statsmodels (ARIMA)

prophet

Jupyter Notebook

Git & GitHub for version control

### Key Insights

Water cost is unpredictable driven by unregulated vendor systems

School water access is predictable → logistic regression works well

Clustering reveals hidden vulnerability groups

Future demand will exceed capacity without major infrastructure expansion

### Author

Yool Malaak Yool Ajak
MIT Emerging Talent - Data Science Track 2025
