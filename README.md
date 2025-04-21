# Data Cleaning and Preprocessing Task

## Overview
This repository contains the code, datasets, and documentation for cleaning and preprocessing the `messy_marketing_campaign.xlsx` dataset as part of a data science task. The objective was to transform a raw dataset with missing values, duplicates, inconsistent formats, and outliers into a clean, structured dataset ready for analysis or modeling. The cleaning was performed using Python (Pandas), following best practices for data preprocessing.

The dataset resembles the "Customer Personality Analysis" dataset from Kaggle, containing customer demographics, spending behavior, and campaign response data. The cleaned dataset is suitable for further analysis, such as customer segmentation or predictive modeling.

## Task Objectives
- **Identify and handle missing values** using `.isnull()` and `.fillna()`.
- **Remove duplicates** using `.drop_duplicates()`.
- **Standardize text values** (e.g., `education`, `marital_status`).
- **Convert date formats** to a consistent datetime type.
- **Rename column headers** to be uniform (lowercase, no spaces).
- **Fix data types** (e.g., numeric, datetime, categorical).
- **Handle outliers** and ensure data consistency.

## Repository Contents
- **`messy_marketing_campaign.xlsx`**: The original raw dataset with issues like missing values, duplicates, and inconsistent formats.
- **`cleaned_marketing_campaign.xlsx`**: The cleaned dataset after preprocessing.
- **`data_cleaning_script.py`**: Python script that performs the cleaning process.
- **`README.md`**: This file, providing an overview, instructions, and summary of changes.

## Cleaning Steps and Summary of Changes
The raw dataset was cleaned to address common data quality issues. Below is a summary of the changes made:

1. **Standardized Column Names**:
   - Converted to lowercase with underscores (e.g., `Year Birth` → `year_birth`).
2. **Fixed Data Types**:
   - Converted `income` and numerical columns to numeric, handling "unknown" and empty strings.
   - Standardized `dt_customer` to datetime, parsing multiple formats (e.g., "2012/09/04", "Sep 04, 2012").
   - Set `education` and `marital_status` as strings.
3. **Standardized Categorical Values**:
   - Unified `education` and `marital_status` to title case (e.g., "graduation" → "Graduation").
   - Mapped unusual `marital_status` values: "YOLO" and "Absurd" to "Unknown", "Alone" to "Single".
4. **Handled Missing Values**:
   - Imputed missing `income`, `recency`, and `dt_customer` with their respective medians to preserve data distribution.
5. **Handled Outliers**:
   - Capped extreme values in `income` (e.g., 666666) and `mntmeatproducts` (e.g., 1725) at the 99th percentile.
6. **Removed Duplicates**:
   - Dropped duplicate rows and duplicate `id` entries, keeping the first occurrence.
7. **Ensured Data Consistency**:
   - Clipped negative values to 0 in numerical columns.
   - Restricted `year_birth` to 1900–2000 for realistic customer ages.
   - Filtered `dt_customer` to exclude dates after April 21, 2025.
   - Dropped constant columns (`z_costcontact`, `z_revenue`) as they provided no value.
8. **Saved Cleaned Dataset**:
   - Exported the cleaned dataset as `cleaned_marketing_campaign.xlsx`.

The resulting dataset is clean, consistent, and ready for downstream tasks like analysis or modeling.

## Prerequisites
- **Python 3.x**
- **Libraries**: Install required packages using:
  ```bash
  pip install pandas matplotlib seaborn openpyxl
