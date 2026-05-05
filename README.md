# Multi-Source Sales Data Pipeline

The project simulates a renewable fuels company tracking sales transactions, customers, and products across four global regions (EMEA, NA, LATAM, APAC).

## Project Goal

Clean data in different formats (Excel and CSV) using Python, so data from different sources can be unified, cleaned, and loaded into Delta tables. After this, data can be queried with SQL.

## Process

1. Reading raw CSV and Excel files with Python
2. Cleaning inconsistencies with pandas in Python
3. Loading cleaned data into Catalog as Delta tables

## Cleaning Techniques Used

- **String normalization**: `.str.strip().str.upper()` / `.str.title()`
- **Currency parsing**: `.str.replace("€", "").str.replace(",", "")` then `pd.to_numeric()`
- **Type coercion**:  `pd.to_numeric(errors="coerce")`
- **Outlier flagging**: `df.loc[df[col] > threshold, col] = pd.NA`
- **Duplicate removal**: `.drop_duplicates()`
- **Date parsing**: `parse_dates=[...]` in `read_csv` / `read_excel`

## Tech Stack

- **Python (pandas)**: data cleaning and transformation
- **SQL**: double-check tables after they are loaded into Catalog as Delta tables
- **Databricks**: notebook environment + Unity Catalog

## Result

### Sales Transactions
![Sales cleaning](Clean%20dataset%20images/Sales%20transactions.png)

### Customers
![Customers cleaning](Clean%20dataset%20images/Customers.png)

### Products
![Products cleaning](Clean%20dataset%20images/Products.png)

## Repo Structure

- **`Notebooks/`**: notebooks for cleaning customers, products, and sales datasets
- **`Clean dataset images/`**: screenshots of the data after being loaded into SQL
- **`README.md`**: project summary

## Repo Structure

- **`Notebooks`**: notebooks for cleaning customers, products, and sales datasets
- **`Clean dataset images`**: screenshots of the data after being loaded into SQL
- **`README.md`**: project summary

## Caveat

Data is fabricated for demonstration purposes.
