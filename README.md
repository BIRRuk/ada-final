# ADA Final Project

## Overview

This project analyzes **NHANES 2021 data** to explore the relationship between **saturated fat intake** and **DSM-V depression status**, adjusting for demographic and socioeconomic factors. It demonstrates:

*   Data acquisition from CDC NHANES
*   Data cleaning and transformation
*   Descriptive statistics (Table 1)
*   Visualization (histograms, boxplots)
*   Statistical tests (t-test, ANOVA)
*   Logistic regression modeling
*   Multiple imputation using `mice`
*   Exporting results for reporting

***

## Data Sources

*   **Demographics**: NHANES DEMO\_L
*   **Depression Screener**: NHANES DPQ\_L
*   **Dietary Intake**: NHANES DR1TOT\_L

***

## Key Steps

### 1. **Data Preparation**

*   Read XPT files using `haven::read_xpt()`
*   Merge demographics, depression screener, and nutrient data
*   Apply DSM-V criteria for depression (≥5 symptoms + core symptom)
*   Factorize categorical variables (gender, ethnicity, education)
*   Handle missing values and impute using `mice`

### 2. **Descriptive Analysis**

*   Create **Table 1** stratified by depression status using `table1`
*   Variables: Age, Gender, Ethnicity, Education, Saturated Fat Intake

### 3. **Visualization**

*   Histograms of saturated fat intake by depression status
*   Boxplots comparing fat intake between groups
*   Age distribution plots

### 4. **Statistical Tests**

*   **t-test**: Compare mean saturated fat intake by depression status
*   **ANOVA**: Test differences in fat intake across age groups

### 5. **Modeling**

*   Logistic regression: `glm(dsmv_depression ~ DR1TSFAT + RIDAGEYR + RIDRETH3 + DMDEDUC2)`
*   Check linearity assumption (Box-Tidwell)
*   Report odds ratios and confidence intervals

### 6. **Multiple Imputation**

*   Use `mice` for missing data
*   Specify methods: `logreg` for binary, `polyreg` for categorical
*   Exclude outcome from imputation via `predictorMatrix`

### 7. **Export Results**

*   Tidy pooled model output with `broom::tidy()`
*   Save as CSV: `write.csv(tidy_res, "model_results.csv")`

***

## 📊 Example Outputs

*   **Table 1**: Demographics and nutrient intake by depression status
*   **Plots**: Histograms, boxplots, age distribution
*   **Model Summary**: Odds ratios for predictors

***

## 🛠️ Packages Used

```r
pacman::p_load(haven, ggplot2, nhanesA, table1, broom, mice, TinyTeX)
```

***

## How to Run

1.  Clone the repo:
    ```bash
    git clone https://github.com/yourusername/ADA-Final-Project.git
    ```
2.  Open `data_management+analysis.Rmd` in R-Studio and 🟩`Run All`
    ```r
    Ctrl + Alt + R
    ```


***

## Outputs

*   `table1` – Descriptive Table 1
*   `model_results.csv` – Logistic regression results (OR + CI)
*   `plots` – Visualizations

***

## Key Findings

*   No significant association between saturated fat intake and depression.
*   Age >65 and higher education levels were negatively associated with depression prevalence.

***
