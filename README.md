# 📊 Medical Data Visualizer

This project visualizes and analyzes data from medical examinations using `pandas`, `matplotlib`, and `seaborn`.

## Dataset

The dataset (`medical_examination.csv`) contains information collected during medical checkups. Each row represents a patient, and each column contains a feature such as body measurements, blood test results, and lifestyle choices.

### Features

| Feature                         | Variable Type         | Variable   | Value Type                                           |
|---------------------------------|------------------------|------------|------------------------------------------------------|
| Age                             | Objective Feature      | `age`      | int (in days)                                        |
| Height                          | Objective Feature      | `height`   | int (in cm)                                          |
| Weight                          | Objective Feature      | `weight`   | float (in kg)                                        |
| Gender                          | Objective Feature      | `gender`   | categorical code                                     |
| Systolic blood pressure         | Examination Feature    | `ap_hi`    | int                                                  |
| Diastolic blood pressure        | Examination Feature    | `ap_lo`    | int                                                  |
| Cholesterol                     | Examination Feature    | `cholesterol` | 1: normal, 2: above normal, 3: well above normal  |
| Glucose                         | Examination Feature    | `gluc`     | 1: normal, 2: above normal, 3: well above normal     |
| Smoking                         | Subjective Feature     | `smoke`    | binary                                               |
| Alcohol intake                  | Subjective Feature     | `alco`     | binary                                               |
| Physical activity               | Subjective Feature     | `active`   | binary                                               |
| Cardiovascular disease          | Target Variable        | `cardio`   | binary                                               |

---

## Project Instructions

### 1. Data Import
Import the data from `medical_examination.csv` and assign it to a DataFrame called `df`.

### 2. Add Overweight Column
Calculate the BMI using:
BMI = weight (kg) / (height (m))^2

Add a new column `overweight`:
- `1` if BMI > 25
- `0` otherwise

### 3. Normalize Data
Make `0` always good and `1` always bad:
- For `cholesterol` and `gluc`, values of `1` become `0`, and values of `2` or `3` become `1`.

### 4. Categorical Plot (`draw_cat_plot`)
- Create a melted DataFrame from `cholesterol`, `gluc`, `smoke`, `alco`, `active`, `overweight`.
- Group by `cardio`, `variable`, and `value` to count occurrences.
- Plot using `sns.catplot()` with `kind="bar"`.

### 5. Heatmap (`draw_heat_map`)
Clean the data by:
- Keeping rows where `ap_lo <= ap_hi`
- Removing height and weight outliers (outside 2.5th and 97.5th percentiles)

Steps:
- Compute correlation matrix
- Create a mask for the upper triangle
- Plot heatmap using `sns.heatmap()`

---
