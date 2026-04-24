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
| **City** | Customer location | Standardized casing and mapped variations (e.g., "Munchen" to "Munich") |
| **OrderDate** | Date of transaction | Resolved multiple date formats (ISO, US, and text-based) |
| **Product** | Item purchased | Cleaned leading/trailing whitespace and inconsistent casing |
| **Quantity** | Number of items | Fixed negative values and missing entries |
| **Email** | Customer contact | Validated email formats and handled invalid placeholders |

---

## Project Workflow
### 1️⃣ Initial Dataset Check
The initial dataset check was performed to understand if there is any cleaning in need, as follows:
* **Structure Check**: Used "df.info()" to identify data types and non-null counts.
* **Missing Value Check**: Used "df.isna().sum()" to find the total number of missing values across all columns.
* **Statistical Profiling**: Used "df.describe()" to see statistical overview of data.

### 2️⃣ Data Cleaning Operations
The cleaning process followed column-specific logic to preserve data integrity:

#### Numeric Cleaning (Age, Price, Quantity)
* **df["column"] = pd.to_numeric(df["column"], errors="coerce")**: Converted the column's Data Type to numeric, forcing non-numeric values to `NaN`.
* **df["column"] = df["column"].fillna(df["column"].median())**: Filled missing values (in "Age" and "Price" columns) with the **Median**.
* **df["column"] = df["column"].abs()**: Converted negative values (in "Quantity" and "Age" columns) to positive ones.

#### Categorical & String Standardization
* **df["column"] = df["column"].str.lower().str.strip()**: Converted names to lowercase and removed leading/trailing spaces (in "Product" and "City" columns).
* **df["City"] = df["City"].replace({"Munchen" : "munich", "München" : "munich"})**: Used to replace "Munchen" with "munich" and "München" with "munich". (*Dictionary '{}' is used when you want to rename specific words or numbers inside a column - 'City')
* **df = df[df["Email"].str.contains("@", na = False)]**: Validated strings to ensure only records with proper email formats remained.

#### Date Uniformity
* **df["DateColumn"] = pd.to_datetime(df["DateColumn"], errors = "coerce")**: recognized that "March 5 2023" and "2023-03-05" are the same day and interpreted numerical dates as Month-First (US standard) (YYYY/MM/DD) and lastly, any invalid date format (e.g., 'Yesterday' or 'N/A' etc) will be NaT (Not a Time) so as to not crash.

---

## Key Transformations & Results
* **Data Reduction**: Refined the dataset from **10,000 raw records** down to **420 clean, validated rows**.
* **Feature Engineering**: Added a new **'Revenue'** column ("Price" * "Quantity") to enable financial reporting.
* **Data Integrity**: Removed all 'NaN' values and invalid entries (negative values) for the final cleaned dataset.
