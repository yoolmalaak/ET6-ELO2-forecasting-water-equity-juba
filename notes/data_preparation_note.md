# Data Preparation

## Standardization, Validation, and Construction of Analytical Variables

The data preparation phase transformed the raw Google Form responses into a
structured, coherent, and analytically reliable dataset suitable for statistical
analysis and machine-learning modelling. Owing to the unregulated nature of
self-reported survey data, this stage required extensive validation, correction
of inconsistencies, and systematic recoding of variables to ensure
methodological rigor.

All procedures described below were implemented in Notebook – Data Preparation.

## 2.1 Objectives of the Data Preparation Process

The preparation workflow was designed to achieve the following:

Ensure data integrity by correcting formatting errors, eliminating invalid
entries, and resolving inconsistencies.

Standardize heterogeneous response formats (numerical, categorical,
and text-based) into analytically tractable structures.

Engineer derived variables required for modelling tasks, such as numeric
conversions, binary indicators, and scenario-dependent metrics.

Prevent data leakage by identifying and removing fields that directly imply
the outcome variable.

Produce a unified analytical dataset encompassing households, schools, and
health facilities, despite differences in their respective attributes.

## 2.2 Treatment of Missing, Invalid, and Ambiguous Responses

The raw survey data contained missing observations, incomplete fields,
and responses that did not conform to prescribed formats. The following
systematic procedures were applied:

Conversion of blank entries and whitespace-only strings to NaN.

Coercion of non-numeric inputs within numeric fields to NaN using controlled
parsing rules.

Removal or imputation (where justified) of invalid responses, including
malformed ranges, inconsistent units, or logically impossible values.

Exclusion of rows without a determinable potable-water indicator during
supervised learning tasks.

These steps ensured that subsequent analytical procedures operated on
internally consistent and interpretable data.

## 2.3 Standardization of Text-Based Numerical Ranges

Several variables—particularly those relating to population counts, staffing
levels, and consumption ranges—were provided in various text formats such as:

"1,001–2,000"

"Less than 50"

"More than 500"

"50–100"

To convert these into continuous numeric values:

All dash encodings (–, —) were normalized to a standard hyphen.

Commas and non-numeric characters were removed safely.

Ranges were mapped to their midpoints.

Upper- or lower-bounded statements (e.g., “Less than 50”) were mapped to
reasonable numeric approximations based on demographic scaling heuristics.

This recoding allowed consistent quantitative analysis across all modelling tasks.

## 2.4 Cleaning and Normalization of Water-Cost Variables

Water-cost indicators were among the most heterogeneous fields in the dataset.
To derive analytically valid cost metrics:

Textual cost values were converted to numeric format through coercive parsing.

All unrealistic or scientifically implausible outliers (e.g., values exceeding
5,000,000 SSP) were replaced with NaN to prevent distortion of statistical modelling.

Costs were normalized into both South Sudanese Pounds (SSP) and United States
Dollars (USD) using a fixed exchange rate of 1 USD = 4,500 SSP.

Final standardized cost variables included:

weekly_water_cost_ssp

weekly_water_cost_usd

school_monthly_water_cost_ssp

school_monthly_water_cost_usd

These transformations enabled valid comparison across respondents and
facilitated downstream forecasting and regression tasks.

## 2.5 Recoding Behavioral and Ordinal Indicators

Several survey responses described behavioral frequencies, access conditions,
or hygiene practices through qualitative categories such as:

“Always”, “Often”, “Sometimes”, “Rarely”, “Never”

“Functional”, “Not Functional”, “Intermittent”

These were systematically mapped to ordered numeric scales. The mapping was
designed to preserve ordinal structure and enable statistical learning methods
that require numeric input.

For example:

Qualitative Category Numeric Encoding
Never 0
Sometimes 1
Often 2
Always 3

This transformation was essential for clustering and feature-importance interpretation.

## 2.6 Standardization of Distance, Time, and Availability Variables

Respondents provided distance and time-based measures in various free-text
formats, including units such as “km,” “minutes,” “hrs,” and mixed forms
(e.g., “3–4 km”). To impose uniformity:

All distances were converted to kilometres.

Time-availability variables were standardized to hours per day.

Ambiguous hybrid responses were parsed using rule-based extraction models.

The resulting variables—such as distance_to_water_source_numeric and
school_hours_water_available_numeric—became essential predictors in clustering
and classification analyses.

## 2.7 Construction of the Binary Target Variable for Potable Water Access

The primary supervised-learning target, school_has_potable_water_numeric,
required careful reconstruction because self-reported responses appeared in
numerous textual variants, including:

“Yes”, “No”, “Functional”, “Not Available”, “Safe”, “Unsafe”, “Intermittent”,
“Partial Access”

To derive a valid binary label:

All responses were normalized using a multi-stage parsing algorithm.

Affirmative indicators (e.g., Yes, Available, Functional, Potable)
were mapped to 1.

Negative indicators (e.g., No, Not functional, Unsafe, Unavailable)
were mapped to 0.

Ambiguous categories (e.g., Sometimes, Intermittent, Partial) were excluded to
prevent mislabeling.

This step ensured a reliable target variable for Notebook 2 (classification).

## 2.8 Identification and Removal of Leakage Variables

Fields that directly or indirectly disclosed potable-water access were removed
prior to model training to prevent data leakage. Examples include:

Raw potable-water fields (school_has_potable_water)

Cleaned but overlapping indicators (school_has_potable_water_clean)

Hygiene facilities directly correlated with safe water access

Behavioral indicators strongly tied to the outcome (e.g., washing practices)

This ensured that model evaluation metrics reflected genuine predictive ability
rather than inadvertent disclosure.

## 2.9 Integration Across Respondent Groups

Although the survey instrument was designed as a unified Google Form,
respondents belonged to different sectors: households, schools,
and health facilities. The final dataset retained all rows in a unified
structure, with group segmentation performed in Notebook 3 using rule-based heuristics.

## 2.10 Final Output of the Data Preparation Phase

The final deliverable of this process is the fully cleaned, standardized dataset:

final_cleaned_dataset.csv

This file represents the authoritative dataset used in:
Notebook 1 — Regression
Notebook 2 — Classification

Notebook 3 — Clustering

Notebook 4 — Forecasting

Data Exploration Notebooks

## 2.11 Reproducibility and Auditability

All cleaning procedures were implemented programmatically to ensure:

End-to-end reproducibility

Full transparency of methodological decisions

Audit-ready transformation logs

Clear traceability from raw inputs to final cleaned dataset
