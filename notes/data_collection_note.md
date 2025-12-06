# Data Collection

## 1. Overview

The dataset used in this project was collected through a single, consolidated
digital survey designed to capture water access, reliability, affordability,
and service-level indicators across households, schools, and health facilities
in Juba, South Sudan. The instrument was developed to support machine learning
clustering, and forecasting tasks within this research project.

## 2. Data Collection Method

### 2.1 Digital Administration

Data were collected entirely online using a single Google Form containing
dynamic sections. Respondents were automatically directed to the relevant
question set based on their selected group:

- Household respondents

- School representatives

- Health facility staff

Branching logic ensured that each respondent only completed items
relevant to their category.

## 3. Distribution Strategy

## 3.1 Social Media Dissemination

The survey link was disseminated across multiple social media platforms to reach
diverse respondents within Juba:

- Facebook

- WhatsApp

- LinkedIn

- Instagram

This approach prioritized accessibility and broad coverage without requiring
physical interaction.

## 3.2 Engagement Challenges

Despite extensive outreach, data collection presented significant challenges:

Many potential respondents lacked stable internet access.

Some users were unfamiliar with online survey tools.

Mobile data costs and connectivity issues limited participation.

Several recipients viewed but did not complete the form.

As a result, the final dataset comprised approximately 120 valid responses,
significantly below the initial target of 400 responses.

## 4. Target Population

The intended respondents included:

Households residing within Juba

Schools (public, private, community, faith-based)

Health facilities (hospitals, clinics, PHCCs)

The actual sample size skewed toward school responses due to the higher
likelihood of institutional staff completing the online form

## 5. Survey Instrument Design

### 5.1 Structure

A single Google Form was designed with:

Required fields to enforce completeness of key variables

Multiple-choice options for categorical consistency

Numeric fields with input constraints

Conditional sections using Google Forms’ “Go to section based on answer” logic

Minimal free-text fields to reduce ambiguity during analysis

### 5.2 Key Themes Captured

Household Section: water sources, consumption, affordability, reliability,
shortages, demographics
School Section: student/staff populations, potable water access, reliability,
costs, WASH indicators
Health Facility Section: patient volumes, staffing, water reliability,
operational disruptions, costs.

## 6. Ethical Considerations

- Participation was voluntary, and respondents could withdraw at any time.

- The form did not collect personally identifiable information (PII).

- Data were handled confidentially and used solely for research and academic purposes.

## 7. Export and Storage

Responses were exported from Google Forms in CSV format and stored in:

1_data_collection/
    raw_dataset.csv
