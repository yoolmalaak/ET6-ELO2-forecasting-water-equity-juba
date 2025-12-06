# Forecasting Future Water Demand for Juba (2010–2035)

Population-Based Urban Water Demand Modelling

## 1. Introduction

This notebook presents a structured and data-driven approach to forecasting
potable water demand for the city of Juba, South Sudan.
Using historical population statistics from 2010 to 2025, combined with
scenario-based per-capita consumption estimates, the analysis generates
forward-looking projections up to the year 2035. Multiple forecasting models
are evaluated to establish reliable estimates that can support strategic
planning, water infrastructure development, and urban policy formulation.

## 2. Data Sources

### 2.1 Historical Population Data (2010–2025)

The forecast is built on a population time series representing estimated annual
population figures for Juba. The dataset covers the period 2010 to 2025,
during which the population increases from 255,000 to approximately 500,000
residents.
These values reflect rapid demographic expansion linked to urbanisation and migration.

A sample of the dataset is provided below:

|Year |Population|
|-----|----------|
|2010 |255,000   |
|2011 |267,000   |
|2012 |279,000   |
|2013 |293,000   |
|2014 |307,000   |
|.....|.......   |
|2025 |500,000   |

The dataset was validated for chronological consistency and used without
interpolation for the observed period.

## 3. Scenario Development

Three water consumption scenarios were defined to account for uncertainty in
future per-capita water use:

|Scenario Consumption |(L/person/day)|
|---------------------|--------------|
|Low                  |40 L|
|Medium |60 L|
|High |80 L|

These were selected based on typical consumption ranges in urban centres with
varying levels of infrastructure reliability.

## 3.1 Conversion to Annual Water Demand

Annual demand (m³/year) was computed as:

Annual Demand = (LPPD × Population × 365)/1000

 ​

Daily demand (m³/day) was also calculated for operational relevance.

Example (2010):

|Year| Population| Low Demand (m³/yr)| Medium Demand (m³/yr)| High Demand (m³/yr)|
|-----|---------|-------------------|----------------------|--------------------|
|2010| 255,000| 3,723,000| 5,584,500| 7,446,000|

These values form the basis for model training across all scenarios.

## 4. Forecasting Methodology

Four forecasting approaches were applied to predict future annual water demand:

Linear Regression
Assumes steady, non-accelerating growth over time.

Polynomial Regression (Degree = 2)
Captures curvature in long-term demand trends.

Exponential Growth Model
Reflects accelerated demand growth consistent with rapidly urbanising cities.

ARIMA (Auto-Regressive Integrated Moving Average)
Employed where the underlying time series showed adequate structure
for stochastic modelling.

Each model was trained using historical annual demand (2010–2025) and evaluated
for its predictive stability.

The forecast horizon extends to 2035, resulting in 10 years of forward projections.

## 5. Visual Exploration

### 5.1 Population and Historical Demand Trends

A combined figure illustrates:

Population Growth (2010–2025): A steady upward trajectory from 255,000
to 500,000 people.

Historical Water Demand: Rising demand across Low, Medium, and High consumption scenarios.

This figure was saved as:
historical_population_and_demands.png

These trends confirm the strong influence of demographic pressure on
water-resource requirements.

## 6. Forecast Results

Forecasts were generated for each scenario and model. The table below summarises
 annual demand estimates at two key planning horizons: 2030 and 2035.

### 6.1 Low Consumption Scenario (40 LPPD)

|Year| Linear (m³/yr)| Polynomial (m³/yr)| Exponential (m³/yr)|
|----|---------------|-------------------|--------------------|
|2030| 8.34 million| 8.93 million| 9.20 million|
|2035 |9.53 million| 10.79 million| 11.53 million|

## 6.2 Medium Consumption Scenario (60 LPPD)

|Year| Linear| Polynomial| Exponential|
|----|-------|-----------|------------|
|2030 |12.50M| 13.40M| 13.81M|
|2035 |14.29M |16.18M| 17.30M|

## 6.3 High Consumption Scenario (80 LPPD)

|Year| Linear |Polynomial| Exponential|
|----|--------|----------|------------|
|2030| 16.67M |17.86M |18.41M|
|2035| 19.06M |21.57M| 23.06M|

## 7. Interpretation of Forecasting Outputs

### 7.1 Model Behaviour

Linear Regression
Produces conservative estimates, suitable for lower-risk planning assumptions.

Polynomial Regression
Reflects moderate acceleration in demand; often aligns well with urban growth patterns.

Exponential Model
Gives the highest projections and is most appropriate for stress testing
infrastructure under rapid expansion.

ARIMA (where applicable)
Aligns closely with linear trends; best used when long historical records are available.

## 7.2 Implications for Water System Planning

Demand will continue to rise sharply across all scenarios.

By 2035, annual water demand is expected to range between:

9.5–11.5 million m³ (Low scenario)

14.3–17.3 million m³ (Medium scenario)

19.0–23.1 million m³ (High scenario)

These findings highlight the urgency of:

Expanding treatment capacity

Upgrading transmission and distribution pipelines

Enhancing water storage infrastructure

Strengthening demand management programs

## 8. Generated Outputs

The notebook automatically exports several deliverables:

## 8.1 Charts (saved to 5_communication/charts/)

Population and demand trends

Forecast plots for Low, Medium, High scenarios

8.2 Data Tables (saved to notebook4_outputs/)

juba_population_and_scenarios.csv

forecast_scenario.csv

scenario_summary_horizons.csv

forecast_metadata.csv

These files support further analysis, reporting, and integration into dashboard
or models.

## 9. Conclusion

Notebook 4 provides a comprehensive, scenario-based forecasting framework for
estimating future water demand in Juba. The results offer valuable insights for
policy makers, engineers, and planners responsible for designing resilient
water infrastructure systems.
By employing multiple forecasting models and transparently documenting all
assumptions, the methodology ensures robustness, reproducibility, and practical
applicability in long-term urban water management
