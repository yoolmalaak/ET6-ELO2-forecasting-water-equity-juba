# Regression Modeling Documentation

## Predicting Weekly Household Water Expenditure (SSP)

### 1. Introduction

Notebook 1 presents the regression analysis conducted to model and predict
weekly household water expenditure in South Sudan (measured in SSP).
The notebook establishes a complete supervised-learning pipeline,
encompassing data preparation, leakage mitigation, model development,
evaluation, and interpretability. This component forms the foundation of
the machine-learning workflow within the broader project.

### 2. Purpose and Scope

The primary objective of this notebook is to assess whether weekly water
expenditure can be reliably predicted using the demographic, socioeconomic, and
water-access characteristics collected through the survey. Specifically,
the notebook seeks to:

Construct a clean, leakage-free feature set suitable for regression analysis.

Train and compare multiple machine-learning regression models.

Examine prediction accuracy using robust evaluation metrics.

Analyze error patterns to understand model limitations.

Identify the most influential predictors via permutation feature importance.

Generate interpretable outputs for reporting and communication.

### 3. Dataset and Target Variable

The regression pipeline uses the cleaned dataset derived in the data-preparation
stage. The final modeling dataset contains:

- 121 observations

- 103 non-leakage input features

- Target variable: weekly_water_cost_ssp

To prevent predictive contamination, all variables containing direct or
indirect cost information were removed based on pattern matching including:
"weekly_water_cost", "monthly_water_cost", "ssp", "usd", "cost", and "high_cost".

This systematic filtering ensured that cost-related information was not
inadvertently used as a predictor of itself.

### 4. Data Partitioning

The dataset was split into distinct subsets for model development:

Training set: 96 samples

Test set: 25 samples

Split ratio: 80/20

Random seed: 42

This approach facilitates unbiased evaluation of model generalization performance.

### 5. Preprocessing Pipeline

A unified preprocessing architecture was implemented using ColumnTransformer,
consisting of:

5.1 Numeric Features

Median imputation for missing values

Standard scaling

5.2 Categorical Features

Most-frequent imputation

One-hot encoding

This preprocessing ensures that all models receive clean, consistent,
and numerically stable features.

### 6. Regression Models Evaluated

The notebook evaluates three widely used machine-learning regression algorithms:

Model Description
Random Forest Regressor Ensemble method using bootstrap-aggregated decision trees
Gradient Boosting Regressor Sequentially built trees optimizing residual errors
XGBoost Regressor Regularized gradient boosting optimized for performance

Each model is trained using an identical, standardized preprocessing pipeline.

### 7. Model Performance

Model performance was evaluated using Mean Absolute Error (MAE),
Root Mean Squared Error (RMSE), and R-squared (R²).
The results are summarized below:

|Model| MAE (SSP)| RMSE (SSP)| R²|
|-----|----------|-----------|---|
|Random Forest| 96,710| 158,955| –0.1417|
|Gradient Boosting| 111,238| 165,137| –0.2323|
|XGBoost| 100,709| 165,755| –0.2415|

Interpretation

All models produced negative R² values, indicating performance
below that of a mean-only baseline.

This outcome reflects the inherent limitations of the available dataset, including:

Small sample size

High variability in reported water costs

Presence of noise and outliers

Sparse socioeconomic signals

Although predictive performance is limited, the analysis remains valuable for
understanding influential factors and for building
the infrastructure for future modeling.

## 8. Residual Diagnostics

### 8.1 Residual Distribution

Residuals displayed strong right-skewness and heavy tails, suggesting the
presence of high-cost outliers and nonlinear relationships not captured by the models.

### 8.2 Residuals vs. Predictions

Visual analysis showed:

Wide dispersion of errors across predicted values

Systematic underprediction at higher cost levels

No clear homoscedastic pattern

These diagnostics reinforce the conclusion that the current dataset does not
support reliable regression modeling of weekly water expenditure.

## 9. Feature Importance Analysis

Permutation feature importance was used to quantify the predictive contribution
of each feature.
The most influential predictors included:

Need for additional taps

Sleep-without-bathing frequency

Dependence on boreholes

Household water shortage indicators

Distance to water source

These relationships provide meaningful insights into the dynamics influencing
household water expenditure, even though model accuracy is limited.

## 10. Outputs Saved

Notebook 1 automatically generates a number of reproducible artifacts for
analysis and communication.

### 10.1 Visualizations (Saved to 5_communication/charts/)

Residual distribution

Residuals vs. predictions

Model performance comparison

Permutation importance rankings

10.2 Data & Model Artifacts

Saved in the notebook directory:

predictions_clean.csv — Actual vs predicted values with residuals

best_model_RandomForest.joblib — Serialized best-performing model pipeline

permutation_importance_clean.csv — Importance ranking of top features

These outputs support downstream reporting and reproducibility.

## 11. Conclusions

The regression analysis demonstrates that the prediction of weekly household
water expenditure is not currently feasible with the available dataset.
While the modeling pipeline is technically robust, the data itself
does not contain sufficient signal for accurate forecasting.

However, the notebook:

Establishes a high-quality modeling framework

Highlights key drivers of water expenditure

Provides clear direction for improved future data collection

## 12. Recommendations

To improve regression performance in future iterations, the following actions
are recommended:

Increase sample size significantly (≥ 300 responses).

Enhance socioeconomic data collection (income ranges, expenditure categories,
household assets).

Capture geographic context (neighborhoods, GPS clusters).

Introduce structured cost categories (fixed tariff, variable tariff, vendor pricing).

Apply controlled sampling techniques to minimize population imbalance
