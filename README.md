# DataCleaning_Exercise (Python)
This project demonstrates a comprehensive data cleaning workflow designed to handle "dirty" data scenarios. The goal was to transform a raw dataset of 10,000 rows with missing values, inconsistent formatting, outliers, and invalid entries into a clean and structured dataset ready for statistical analysis.

## Project Overview
The objective was to take a raw, messy dataset and apply the systematic transformation to ensure data integrity. By addressing issues like negative numbers in Age, invalid prices (e.g., 9999), and mixed date formats, the data was refined from a chaotic state into a structured format suitable for any possible business intelligence.

---

## Dataset and Structure
The data used in this project was artificially generated to simulate common data quality issues that can be found in any databases.

| Column | Description | Issues Addressed |
| :--- | :--- | :--- |
| **OrderID / CustomerID** | Unique identifiers | Checked for range and type consistency |
| **Age** | Customer age data | Handled negatives (e.g., -10) and missing values |
| **Price** | Product price | Addressed extreme outliers (e.g., 9999) and nulls |
| **City** | Customer location | Standardized casing and mapped variations (e.g., 'Munchen' to 'Munich') |
| **OrderDate** | Date of transaction | Resolved multiple date formats (ISO, US, and text-based) |
| **Product** | Item purchased | Cleaned leading/trailing whitespace and inconsistent casing |
| **Quantity** | Number of items | Fixed negative values and missing entries |
| **Email** | Customer contact | Validated email formats and handled invalid placeholders |

