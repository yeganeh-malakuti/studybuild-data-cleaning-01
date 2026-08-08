# Project 01: Data Cleaning on an E-commerce Dataset

## 📊 Overview

This project is part of the **StudyBuild** program. The goal is to clean a
real-world e-commerce customer dataset and prepare it for further analysis.

The dataset contains customer demographics, purchase behavior, and
satisfaction metrics. The raw data contained several quality issues that
needed to be resolved before it could be used reliably.

---

## 🔍 Issues Identified

| # | Issue | Description |
|---|-------|-------------|
| 1 | **Duplicate Records** | Rows fully duplicated across all columns except `customer_id` |
| 2 | **Gender Inconsistencies** | Several rows had a `gender` value that didn't match the customer's `first_name` |
| 3 | **Missing / Invalid Age** | Missing values in `age`, plus unrealistic ages (> 110) |
| 4 | **Calculation Errors** | `total_spending` did not always equal `purchase_count * avg_order_value` |
| 5 | **Invalid Returns** | `returned_items` was sometimes greater than `purchase_count`, which is impossible |
| 6 | **Incorrect Data Types** | Categorical columns, `first_name`, `signup_date`, and `returned_items` were stored with the wrong dtype |

---

## 🛠 Cleaning Steps Performed

| Step | Action | Reason |
|------|--------|--------|
| 1 | **Duplicates** | Dropped rows that were fully duplicated (ignoring `customer_id`), keeping the first occurrence. |
| 2 | **Gender Correction** | Built a name → gender reference map and overwrote mismatched `gender` values. |
| 3 | **Age Cleaning** | Filled missing ages with the median; replaced ages above 110 with a reasonable fallback (45). |
| 4 | **Spending Recalculation** | Recomputed `total_spending` as `purchase_count * avg_order_value` for every row. |
| 5 | **Invalid Returns** | Set `returned_items` to missing (`NA`) wherever it exceeded `purchase_count`, since the true value couldn't be inferred safely. |
| 6 | **Data Types** | Converted categorical columns to `category`, `first_name` to `string`, `signup_date` to `datetime`, and `returned_items` to nullable `Int64`. |

---

## 🛠 Tools Used

- **Python 3.11** with pandas, numpy
- **Jupyter Notebook** for development
- **openpyxl** for Excel file I/O

---

## 📂 Files

- `data_cleaning_yeganeh-malakuti.ipynb` – Full, commented cleaning workflow
- `cleaned_dataset_yeganeh-malakuti.xlsx` – Cleaned dataset
- `analysis_report_yeganeh-malakuti.pdf` – Supporting analysis report

---

## ✅ Conclusion

The dataset is now clean and consistent, with duplicates removed, invalid
values corrected or nulled out, and proper data types applied throughout.
It is ready for further analysis, visualization, and modeling.

---

**Prepared by:** Yeganeh Malakuti
**Project:** StudyBuild – Project 01
