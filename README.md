# Multi-Source Sales Data Pipeline

The project simulates a renewable fuels company tracking sales transactions, customers, and products across four global regions (EMEA, NA, LATAM, APAC).

## Project Goal

Take messy data from different sources and turn it into a clean dataset so that data could be queried with SQL. This is the preparation step before loading data to Power BI.

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

## Notebooks

| Notebook | Purpose |
|---|---|
| `Customers.ipynb` | Clean and load customer data |
| `Sales_transactions.ipynb` | Clean and load transaction data |
| `clean_products.ipynb` | Clean and load product data |

## Caveat

Data is fabricated for demonstration purposes.
