# Multi-Source Sales Data Pipeline

## About The Project

A data pipeline that simulates a renewable fuels company tracking sales transactions, customers, and products across 4 global regions (EMEA, NA, LATAM, APAC). Below is the project breakdown:

- Built a Python pipeline to ingest, unify, and clean sales data in different formats (Excel and CSV)
- Loaded the cleaned data into structured SQL tables. 
- Designed as the preparation layer for Power BI, where Power BI can read table from SQL directly. This reduces refresh time compared to connecting Power BI to the raw source files.

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

- **`Notebooks`**: notebooks for cleaning customers, products, and sales datasets
- **`Clean dataset images`**: screenshots of the data after being loaded into SQL
- **`README.md`**: project summary

## Repo Structure

- **`Notebooks`**: notebooks for cleaning customers, products, and sales datasets in Python
- **`Clean dataset images`**: screenshots of the data after being loaded into SQL
- **`README.md`**: project summary

## Caveat

Data is fabricated for demonstration purposes.
