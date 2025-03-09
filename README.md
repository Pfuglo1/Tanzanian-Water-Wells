# Tanzania Water Wells Classification Project

## Overview

This project builds a predictive classifier to determine the condition of water wells in Tanzania. By using well characteristics such as pump type, installation date, geographic coordinates, and other factors, the model classifies wells into three groups:
- **Functional**
- **Needs Repair**
- **Non-functional**

This is a ternary classification task that can later be re-engineered into a binary task if needed. The insights derived from this project help stakeholders optimize resource allocation and guide future water infrastructure investments.

## Business and Data Understanding

### Business Problem

Tanzania faces a significant challenge in providing clean water to its 57+ million citizens. Many wells are either non-functional or require repair, leading to inefficient resource allocation and negative impacts on public health.  
**Stakeholders:**
- **NGOs (e.g., WaterAid):** Require data-driven guidance to prioritize repair efforts.
- **Government Agencies:** Need information on well failures to inform new water project planning and policy-making.

### Data Sources

The project uses two primary datasets:
- **Features Dataset:** Contains detailed information about each well (e.g., pump type, installation date, funder, GPS coordinates, etc.).
- **Labels Dataset:** Contains the target variable (`status_group`), which specifies the well condition (e.g., *functional*, *non functional*, *functional needs repair*).

The datasets consist of approximately 59,400 records each.

## Data Preparation

Key steps in data preparation include:
- **Cleaning:** Dropping non-predictive columns (such as unique IDs and recording dates), replacing implausible zero values with `NaN` to indicate missing data, and converting date fields into datetime objects.
- **Feature Engineering:** Creating new features such as "well_age" (derived from the installation date) and consolidating rare categories (e.g., grouping low-frequency funders under "Other").
- **Target Recoding:** Converting text labels for well condition into numerical codes (e.g., mapping *non functional* to 0, *functional* to 1, and *functional needs repair* to 2).

These steps are implemented in our Jupyter Notebook to ensure reproducibility.

## Modeling Approach

The project follows an iterative modeling strategy:
1. **Baseline Model:** A Logistic Regression classifier is built as a simple, interpretable benchmark.
2. **Advanced Model:** A Random Forest classifier is tuned using RandomizedSearchCV to improve performance, capturing more complex relationships in the data.

Key aspects include:
- Splitting data into training and testing sets.
- Using scikit-learn pipelines to preprocess numeric, categorical, and binary features.
- Evaluating models using metrics such as Accuracy, Precision, Recall, and F1-Score.

## Model Evaluation

A custom evaluation framework is used to:
- Summarize training and validation metrics.
- Perform cross-validation.
- Visualize confusion matrices for detailed error analysis.

This evaluation ensures that the model’s performance is communicated clearly and actionably for stakeholders.

## Conclusions and Recommendations

**Key Findings:**
- The baseline Logistic Regression model provided a straightforward benchmark.
- The tuned Random Forest model significantly improved classification performance, yielding higher F1 scores and balanced class recall.

**Stakeholder Implications:**
- **For NGOs (e.g., WaterAid):** The model can help identify and prioritize wells that need urgent repair.
- **For Government Agencies:** Insights from the analysis can inform long-term water infrastructure planning and resource allocation.

**Next Steps:**
- Further refine feature engineering (e.g., incorporating spatial interactions).
- Experiment with alternative or ensemble modeling techniques.
- Develop an interactive dashboard for real-time monitoring and decision support.

## Reference
Pump It Up: Data Mining the Water Table
Scikit-learn documentation for pipelines, imputation, and model evaluation.
yaml
Copy
Edit
