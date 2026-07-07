
## Cafe Sales Data Cleaning Project

## Overview
This project involved cleaning a real-world-style cafe sales transaction dataset containing **9,859 records** with significant data quality issues — missing values, calculation errors, and invalid entries. The goal was to transform it into a fully clean, analysis-ready dataset using Microsoft Excel.

## Objective
Identify and resolve data quality issues in a transactional sales dataset while documenting the logic and assumptions behind every fix — a core skill for any data analyst working with real-world data.

## Data Quality Issues Identified

| Issue | Count | Description |
|---|---|---|
| Missing values (all columns) | 6,600+ rows | NULLs across Item, Payment Method, Location, Transaction Date |
| Math mismatches | 126 rows | `Total_Spent` did not equal `Quantity × Price_Per_Unit` |
| Single missing numeric value | 823 rows | One of Quantity/Price/Total missing (recoverable via formula) |
| Double missing numeric values | 12 rows | Two of three numeric fields missing (required manual judgment) |
| Invalid zero-quantity transactions | 479 rows | Transactions with no items purchased |
| Free/promotional items | 5 rows | Price_Per_Unit = 0, required special handling |

## 🛠️ Cleaning Process

1. **Standardized inconsistent placeholders** — converted "UNKNOWN" text entries to proper NULL values for accurate detection
2. **Fixed math mismatches** — recalculated `Total_Spent` using `Quantity × Price_Per_Unit` wherever both values were present but the total didn't match
3. **Recovered missing values via formula logic**:
   - Missing `Total_Spent` → `Quantity × Price_Per_Unit`
   - Missing `Quantity` → `Total_Spent ÷ Price_Per_Unit`
4. **Handled edge cases individually**:
   - Rows with `Price_Per_Unit = 0` (free/promotional items) → set `Total_Spent = 0`
   - Rows missing two of three numeric values → applied a documented assumption (`Quantity = 1`, the most common single-unit purchase) rather than discarding valid item/price/date data
5. **Removed invalid records** — deleted transactions with `Quantity = 0` where no valid recovery was possible, as these had no business meaning
6. **Standardized categorical fields** — filled missing `Item`, `Payment_Method`, `Location`, and `Transaction_Date` values with `"Unknown"` instead of leaving blanks

## Results

| Metric | Before | After |
|---|---|---|
| Total rows | 9,859 | 9,392 |
| Missing values | 6,600+ | 0 |
| Math mismatches | 126 | 0 |
| Invalid transactions | 479 | 0 |

## Tools Used
- Microsoft Excel (formulas, conditional formatting, filtering, Paste Special)

## Files in this Repository
- `Cafe_Sales_Data_CLEANED.xlsx` — Final cleaned dataset (Excel format)
- `Cafe_Sales_Data_CLEANED.csv` — Final cleaned dataset (CSV format)
- `Cafe_Sales_Data2.csv` — Original raw dataset (for reference/comparison)

## Key Takeaways
Data cleaning isn't just about deleting errors — it's about understanding *why* data is missing or incorrect, applying the right recovery method for each case, and making transparent, documented decisions when data can't be recovered. Every fix in this project was based on a clear business logic rationale rather than arbitrary changes.

---
**Author:** Sahoora Jamshed
**Connect with me on LinkedIn** for more data analytics projects.
