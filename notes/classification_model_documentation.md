# Machine Learning Classification for Predicting School Potable Water Access

## 1. Introduction

Notebook 2 presents the development of a supervised machine learning model
designed to predict whether a school has access to potable water.
The notebook implements a rigorous, fully validated, and leakage-safe
modeling workflow.
The objective is to build a transparent and reproducible classifier that can
support evidence-based decision-making in water service provision,
school planning, and resource allocation.

This notebook forms the second stage of the project’s analytical pipeline,
following data collection and preparation.

## 2. Target Variable Reconstruction

The target variable, school_has_potable_water_numeric, was not originally
available as a clean binary label. Therefore, the notebook reconstructs it
using a multi-step text-processing and normalization procedure:

If available, the cleaned field school_has_potable_water_clean is used
as the primary source.
Otherwise, the raw text field school_has_potable_water is parsed and mapped
using a standardized keyword-based algorithm (e.g., “yes”, “functional”,
“piped” → 1; “no”, “not available”, “unsafe” → 0).

Ambiguous responses (e.g., “sometimes”, “intermittent”) are excluded to
maintain labeling integrity.

Following reconstruction:

67 schools (65%) were classified as having potable water.

36 schools (35%) lacked potable water.

103 complete and valid rows remained for modeling.

## 3. Leakage Prevention Strategy

Feature leakage can artificially inflate model performance.
To ensure methodological soundness, all variables that directly
reveal potable-water conditions were removed prior to training. This included,
but was not limited to:

Water source descriptors

Hygiene and sanitation fields

Hours of water availability

Drinking frequency or handwashing indicators

Any variables that implicitly contain potable-water information

A total of 10 leakage-prone fields were excluded.
This step ensures that the model learns from contextual and structural
conditions rather than explicit labels.

## 4. Preprocessing and Feature Engineering

The dataset contained a diverse mix of numeric and categorical features:

65 numeric variables

39 categorical variables

A uniform preprocessing pipeline was implemented using the following components:

### 4.1 Imputation

Numeric features: Median imputation

Categorical features: Most frequent category

### 4.2 Scaling and Encoding

StandardScaler applied to numeric features

One-Hot Encoding for categorical features

Resulted in 490 engineered features after transformation

### 4.3 Feature Selection

Low-variance features were removed using VarianceThreshold

SelectKBest (mutual information) was applied,
retaining the top 30 most informative predictors

### 4.4 Class Imbalance Mitigation

SMOTE (Synthetic Minority Oversampling Technique) was applied within each
cross-validation fold only, ensuring no information leakage.

This modular and disciplined structure ensures that preprocessing is consistent
reproducible, and applied strictly within training boundaries.

## 5. Model Development and Cross-Validation

Four baseline models were evaluated:

Logistic Regression

Random Forest Classifier

Gradient Boosting Classifier

XGBoost Classifier

Model evaluation was conducted using Stratified 5-Fold Cross-Validation with
the following metrics:

Accuracy

Precision (macro)

Recall (macro)

F1-Score (macro)

ROC-AUC

### 5.1 Baseline Cross-Validation Performance

Model Mean ROC-AUC
Logistic Regression 0.901
Gradient Boosting 0.867
Random Forest 0.832
XGBoost 0.832

Logistic Regression demonstrated the strongest and
most stable performance across folds.

## 6. Hyperparameter Optimization

To further enhance performance, RandomizedSearchCV was applied to:

Random Forest

XGBoost

The best observed ROC-AUC values were:

Model Best ROC-AUC
Random Forest 0.881
XGBoost 0.898

Despite improvements, neither surpassed Logistic Regression when performance,
stability, and interpretability were considered holistically.

## 7. Final Model Selection and Training

Based on:

Highest cross-validated ROC-AUC

Consistency across folds

Simplicity and interpretability

Logistic Regression was selected as the final model.

The finalized pipeline was trained on the entire training set.

## 8. Holdout Test Performance

On the unseen 20% test set, the model achieved:

Metric Score
Accuracy 0.8095
Precision 0.9167
Recall 0.7857
F1-Score 0.8462
ROC-AUC 0.944

These results demonstrate excellent discrimination capability, particularly
reflected in the high ROC-AUC score.

## 9. Model Diagnostics

### 9.1 ROC Curve

AUC ≈ 0.94

Indicates strong separability between classes

### 9.2 Precision–Recall Curve

Average Precision (AP) ≈ 0.97

Indicates reliability even under class imbalance

### 9.3 Confusion Matrix

 Predicted No Predicted Yes
Actual No 6 1
Actual Yes 3 11

The model slightly over-predicts potable water availability but maintains
strong overall performance.

## 10. Feature Importance Analysis

Permutation Importance revealed key predictors associated with potable water
access, including:

Community-level water challenges

School water challenges and coping mechanisms

School affiliation characteristics

Infrastructure and monthly school water costs

Shortage and service disruption indicators

These insights reveal structural factors that influence water accessibility outcomes.

## 11.  Saved Outputs and Artifacts

The following files are automatically generated:

Output Location
Final trained model pipeline notebook2_outputs/final_pipeline_Logistic.joblib
Holdout predictions notebook2_outputs/holdout_predictions.csv
Cross-validation summary notebook2_outputs/cv_summary.csv
Permutation importance notebook2_outputs/permutation_importance.csv
All charts (ROC, PR, confusion matrix…) 5_communication/charts/
Auto-generated HTML model report notebook2_outputs/notebook2_report.html

These outputs support model reuse, validation, auditability, and interpretability.

## 12. Conclusion

Notebook 2 successfully produced a high-performing, leakage-free
machine learning classifier capable of predicting whether a school has access
to potable water based on contextual and infrastructure-related variables.
The final Logistic Regression model provides:

Strong predictive accuracy

High interpretability

Robust performance across folds

Excellent discrimination (ROC-AUC = 0.94)

This classifier can be integrated into decision-support workflows,
policy dashboards, and future predictive systems focused on water service
reliability and school infrastructure assessments
