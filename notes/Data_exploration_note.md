# Data Exploration

## Descriptive Analytics, Variable Profiling, and Visual Diagnostics

The data exploration phase provided a systematic understanding of the
demographic, behavioral, and water-access characteristics present in the
cleaned dataset. This stage was essential for identifying structural patterns,
validating the quality of the prepared data, and informing the modelling
decisions undertaken in subsequent notebooks.

All analyses in this section were conducted in Notebook: Data Exploration and Visualization.

## 3.1 Objectives of Data Exploration

The exploratory analysis was conducted with the following goals:

Characterize respondent demographics and socioeconomic conditions across
households, schools, and health facilities.

Understand distributions, central tendencies, and variability in key variables
related to water access, reliability, and cost.

Identify potential relationships through correlation analysis and conditional comparisons.

Detect remaining anomalies or inconsistencies that may require further cleaning
or transformation.

Generate visual evidence to support modelling hypotheses and contextualize
communities’ water-access challenges.

## 3.2 Structure of the Analytical Dataset

Following data preparation, the dataset consisted of 121 validated responses,
spanning three respondent categories:

- Households
- Schools
- Health Facilities

Due to differences in sector-specific attributes, exploratory visualizations
were designed to examine each group independently while retaining the unified
dataset structure.

## 3.3 Household-Level Exploration

Exploration of household variables focused on demographic structure,
water-collection burden, consumption patterns, and economic pressures.
Key variables assessed included:

- Age Group
- Gender
- Role in Household
- Education Level of Household Head
- Primary Income Source
- Daily Water Consumption (L/person/day)
- Household Size
- Main Drinking Water Source
- Water-Shortage Frequency (Last 12 Months)
- One-Way Distance to Water Source
- Weekly Water Cost (SSP & USD)

Visual Diagnostics Included:

Bar charts illustrating the distribution of demographic and categorical indicators.

Histograms describing numeric distributions such as household size and litres
consumed per person per day.

Outlier-filtered cost distributions, removing implausible values (e.g., extreme
scientific-notation entries).

Correlation heatmaps quantifying relationships across key numeric variables
(e.g., consumption, distance, water costs).

These visualizations enabled early identification of:

Skewed consumption patterns

High economic variability in weekly water costs

Significant reliance on unimproved water sources

Non-uniform distribution of shortage experiences across households

## 3.4 School-Level Exploration

School-specific exploration aimed to quantify institutional water-access
conditions and identify factors affecting reliability and cost.

Variables examined included:

- Student Population (numeric midpoint conversion)
- Staff Population (numeric midpoint conversion)
- Monthly Water Cost (SSP & USD)
- Daily Hours of Water Availability
- School Type (Primary/Secondary/etc.)
- Ownership (Public/Private/NGO-Supported)
- Main Water Source
- Potable Water Availability (binary)
- Hygiene-related indicators and water-use behaviors

**Visual Diagnostics Included:**

Bar charts for school type, ownership, and potable-water availability.

Histograms for monthly cost distributions (after IQR-based outlier removal).

Heatmaps showing numeric correlations among student population,
staff population, water availability hours, and cost.

Boxplots comparing cost variability across institutions.

These analyses revealed:

Strong cost variability between institutions

Low potable-water availability in certain institutional types

Moderate correlation between staffing levels and student populations

High heterogeneity in daily water availability hours

## 3.5 Residual Exploration for Health Facilities

Although the dataset contained few health-facility responses, exploratory
checks were performed where possible to ensure completeness and internal
consistency. Variables examined included:

Daily patient load

Staff count

Facility ownership

Water-reliability indicators

Monthly water-cost estimates

Given the limited sample size, visualization was minimal but descriptive
statistics were retained for completeness.

## 3.6 Cross-Cutting Observations

The exploration phase identified key structural patterns:

High reliance on manually collected water among households and certain schools.

Significant economic burden, evidenced by the wide spread in weekly and monthly
water costs.

Variability in water-availability duration, particularly among schools,
suggesting infrastructure gaps.

Strong heterogeneity in water-shortage experiences, consistent with chronic
supply and access challenges.

Presence of systematic outliers requiring removal prior to modelling
(e.g., mis-entered cost values).

These findings informed both the feature-engineering and modelling strategies
applied in Notebook 1, Notebook 2, Notebook 3, and Notebook 4.

## 3.7 Reproducibility and Automation of Visual Outputs

All figures generated during the exploration stage were programmatically saved
using the custom utility:

save_fig()

Charts were automatically exported to:

- 3_data_exploration/charts/
- This ensured that visual analytics were:
- Fully reproducible
- Version-controlled
- Available for documentation and reporting
- Consistent across all notebooks in the project
