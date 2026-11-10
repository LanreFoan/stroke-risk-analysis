# Stroke Risk Analysis
### Cardiovascular Risk Factors and Stroke: An Exploratory Data Analysis 


## Table of Contents
1. [Project Overview](#project-overview)
2. [Business Problem](#business-problem)
3. [Project Objectives](#project-objectives)
4. [Dataset Description](#dataset-description)
5. [Data Quality and Preparation](#data-quality-and-preparation)
6. [Feature Engineering](#feature-engineering)
7. [Exploratory Data Analysis](#exploratory-data-analysis)
8. [Statistical Analysis](#statistical-analysis)
9. [Key Findings](#key-findings)
10. [Recommendations](#recommendations)
11. [Tools and Libraries](#tools-and-libraries)
12. [Limitations and Notes](#limitations-and-notes)
13. [Author](#author)

---

## Project Overview

This project presents an exploratory data analysis (EDA) of a healthcare dataset containing demographic, clinical, and lifestyle information for **5,110 patients**.

The primary objective is to investigate patient characteristics associated with stroke occurrence, identify patterns among patients with and without stroke, and translate the findings into practical recommendations for healthcare stakeholders and decision-makers.

The analysis focuses on understanding how factors such as age, hypertension, heart disease, average glucose level, and body mass index (BMI) relate to stroke prevalence.

> **Project type:** Exploratory Data Analysis and statistical analysis  
> **Domain:** Healthcare analytics  
> **Target variable:** `stroke`  
> **Records analysed:** 5,110 patients

## Business Problem

Stroke is a major healthcare concern, and identifying patient characteristics associated with its occurrence can help healthcare providers improve screening, monitoring, and preventive care.

This project examines a patient dataset to answer the following analytical questions:

- How does stroke prevalence vary across different age groups?
- Are hypertension and heart disease associated with stroke occurrence?
- Is the average glucose level different between patients with and without stroke?
- How does BMI relate to stroke prevalence?
- Which demographic and clinical characteristics distinguish stroke patients from non-stroke patients?

The findings are intended to support data-informed healthcare decisions. They should not be interpreted as a clinical diagnostic tool or proof of causation.

## Project Objectives

- Inspect the dataset for duplicate records and missing values.
- Assess the pattern of missing BMI values across stroke groups.
- Prepare the data for exploratory and statistical analysis.
- Create meaningful categorical features from continuous variables.
- Explore individual and combined relationships between patient characteristics and stroke.
- Apply statistical tests to assess observed differences and associations.
- Communicate findings through actionable recommendations.

## Dataset Description

The dataset contains **5,110 patient records** drawn from a healthcare registry. It includes demographic, clinical, and lifestyle-related variables.

The target variable is `stroke`:

| Value | Description |
|---|---|
| `0` | No stroke |
| `1` | Stroke |

The analysis considers variables including age, hypertension, heart disease, average glucose level, and BMI.

*Dataset source: [Kaggle](https://www.kaggle.com/datasets/aouatifcherdid/healthcare-dataset-stroke-data)*

## Data Quality and Preparation

### 1. Duplicate Records

All records were inspected for duplicate entries. No duplicate rows were identified.

### 2. Missing Values

The `bmi` column was the only column identified as containing missing values.

Before imputation, missing BMI rates were compared across the target groups:

| Patient group | Missing BMI rate |
|---|---:|
| No stroke (`stroke = 0`) | Approximately 4.0% |
| Stroke (`stroke = 1`) | Approximately 19.9% |

The substantially higher missing-BMI rate among stroke patients suggests that missingness may be related to the stroke group. The original analysis interpreted this pattern as potentially **Missing at Random (MAR)**.

Using a single mean or median across the full population could obscure differences between the two groups. Therefore, BMI was imputed using the median calculated separately within each stroke group.

**Imputation strategy:** Group-wise median imputation based on the `stroke` variable.

## Feature Engineering

Three categorical features were derived from continuous variables to support clinically meaningful comparisons and visualizations.

| Engineered feature | Categories |
|---|---|
| Age category | Child, Adult, Senior |
| Glucose tier | Normal, Pre-diabetic, Diabetic |
| BMI tier | Underweight, Normal, Overweight, Obese |

These derived variables make it easier to compare stroke prevalence across interpretable patient groups.

*Note: The exact numerical cut-off values used to define these categories should be documented in the analysis notebook or added here for full reproducibility.*

## Exploratory Data Analysis

The exploratory analysis was organized into three stages:

### Univariate Analysis
Examined the distribution of individual variables to understand the characteristics of the patient population.

### Bivariate Analysis
Investigated relationships between individual patient characteristics and stroke occurrence.

### Multivariate Analysis
Explored combined patterns of risk factors to identify characteristics that co-occur in stroke cases.

The analysis included comparisons involving age, hypertension, heart disease, glucose levels, and BMI.

*Add selected charts from the analysis notebook to this section. Recommended visuals include stroke prevalence by age category, comparisons of hypertension and heart disease, glucose distributions by stroke status, and BMI category comparisons.*

## Statistical Analysis

Statistical tests were used to assess whether patterns observed during EDA were supported by evidence of statistically significant differences or associations.

| Statistical test | Application |
|---|---|
| Independent samples t-test | Tested whether continuous variables differed between stroke and non-stroke patients. |
| Chi-squared test of independence | Assessed whether categorical risk factors were associated with stroke outcome. |

The tests were used to complement the exploratory analysis rather than establish causation.

*For a fully reproducible report, include the test statistics, p-values, significance threshold, and any relevant assumptions in the notebook or an expanded results section.*

## Key Findings

### 1. Age is the Strongest Risk Indicator

Stroke prevalence increased substantially across age categories.

| Age group | Stroke prevalence |
|---|---:|
| Seniors (≥65 years) | 15.5% |
| Adults | 2.7% |
| Children | 0.2% |

The mean age of stroke patients was **67.7 years**, compared with **42.0 years** among patients without stroke.

Age was the most discriminating variable identified in the analysis.

### 2. Chronic Conditions Are Associated with Higher Stroke Prevalence

The proportion of patients with hypertension and heart disease was higher among stroke patients.

| Condition | Stroke patients | Non-stroke patients |
|---|---:|---:|
| Hypertension | 26.5% | 8.9% |
| Heart disease | 18.9% | 4.7% |

These findings highlight the importance of monitoring patients with existing cardiovascular conditions.

### 3. Elevated Blood Glucose Is Associated with Higher Stroke Prevalence

Patients in the diabetic glucose category had a stroke prevalence of **10.2%**, compared with **3.6%** among patients in the normal glucose category.

Mean glucose levels were also higher among stroke patients:

| Patient group | Mean glucose level |
|---|---:|
| Stroke | 132.5 mg/dL |
| No stroke | 104.8 mg/dL |

The findings suggest that glucose management should be considered in broader stroke-prevention efforts.

### 4. BMI and Lifestyle-Related Factors Contribute to the Observed Pattern

Stroke prevalence varied across BMI categories.

| BMI category | Stroke prevalence |
|---|---:|
| Overweight (BMI 25–30) | 7.1% |
| Obese | 5.1% |
| Normal | 2.8% |

The bivariate scatter analysis also showed clustering of combined metabolic risk, particularly elevated glucose and higher BMI, among stroke cases.

These are observed associations in this dataset and should not be interpreted as evidence that BMI or glucose levels independently cause stroke.

## Recommendations

Based on the analysis, the following actions are recommended for healthcare stakeholders:

1. **Strengthen stroke-risk screening among older patients.** The observed stroke prevalence among seniors was 15.5%, supporting targeted screening and monitoring.
2. **Improve hypertension and diabetes management programmes.** The analysis found higher prevalence of both conditions among stroke patients.
3. **Expand glucose screening and patient education.** Encourage awareness and appropriate monitoring of blood glucose levels.
4. **Promote targeted weight-management and wellness programmes.** The overweight group had a higher observed stroke prevalence than the normal-BMI group.
5. **Develop patient risk-stratification dashboards.** Combine relevant indicators such as age, blood pressure, glucose, and BMI to support clinical review.
6. **Monitor outcomes through continuous analytics.** Use dashboards and periodic analysis to evaluate screening and prevention initiatives.

These recommendations are intended to inform healthcare planning and should be evaluated alongside clinical guidelines and professional judgement.

## Tools and Libraries

| Tool / Library | Purpose |
|---|---|
| Python | Primary programming language for analysis |
| pandas | Data manipulation and aggregation |
| NumPy | Numerical operations |
| Matplotlib | Base plotting and data visualization |
| Seaborn | Statistical data visualization |
| Plotly | Interactive charts |
| SciPy | Statistical testing, including chi-squared tests |


## Limitations and Notes

- This project is an exploratory and statistical analysis; it does not build or validate a machine-learning prediction model.
- The findings describe patterns and associations in the dataset and do not establish causation.
- The dataset source, collection period, population coverage, and detailed variable definitions should be documented to provide additional context.
- The numerical thresholds used for the engineered age, glucose, and BMI categories should be included in the notebook or project documentation.
- Statistical test results, including p-values and test statistics, should be reported alongside the findings when available.
- The missing-BMI pattern suggests that missingness may be related to stroke status, but the MAR assumption is not established by group-level missingness rates alone.

## Author

**Olanrewaju Emmanuel**

Healthcare | Data | Innovation
---

If you find this project useful, feel free to explore the repository, review the analysis, and share feedback.
