# Walmart Sales Analysis

This repository contains an exploratory data analysis (EDA) and basic data engineering steps for a Walmart sales dataset. The work is done in a Jupyter Notebook and includes a cleaned CSV export and a set of SQL queries for analysis.

## Contents

- `project.ipynb` - Main Jupyter notebook with data cleaning, exploration, and SQL Server upload examples.
- `Walmart.csv` - Original raw dataset used for analysis.
- `walmart_clean_data.csv` - Cleaned dataset exported from the notebook.
- `walmart_sql.sql` - A collection of SQL queries that answer common business questions (top categories, busiest days, revenue trends, preferred payment methods, profits by category, etc.).

## Overview

The notebook performs the following high-level steps:

1. Load the raw CSV into a pandas DataFrame.
2. Inspect and clean the data (drop duplicates, handle missing values, convert types, compute new columns such as `total`).
3. Normalize column names to lower case.
4. Convert currency fields and calculate aggregated metrics.
5. (Optional) Upload the cleaned DataFrame to a SQL Server database.
6. Export the cleaned DataFrame to `walmart_clean_data.csv`.

## How to run

Prerequisites
- Python 3.8+ (a recent 3.x is recommended)
- Jupyter or JupyterLab

Recommended: create and activate a virtual environment

On Windows (PowerShell):

```powershell
python -m venv .venv; .\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
jupyter lab
```

If you do not have a `requirements.txt`, the notebook uses the following Python packages:

- pandas
- sqlalchemy
- pymysql (if connecting to MySQL)
- pyodbc (if connecting to SQL Server)

You can install them with:

```powershell
pip install pandas sqlalchemy pymysql pyodbc
```

Open `project.ipynb` in Jupyter and run the cells in order. The notebook is designed to be linear: first run the data-cleaning cells, then the export/upload cells.

## About `walmart_sql.sql`

The provided SQL file contains many useful queries to run against the cleaned `walmart` table in a relational database. Examples include:

- Count transactions by payment method
- Top category by average rating per branch
- Busiest day per branch
- Revenue decrease analysis between years

The SQL file contains T-SQL constructs and functions such as `RANK()`, `TRY_CONVERT`, and `DATEPART` intended for SQL Server. Minor adjustments may be required for other RDBMS (MySQL, PostgreSQL).

## Notes and assumptions

- The notebook drops rows with missing values. If you prefer imputation or partial retention, update the notebook accordingly before export.
- Currency strings are cleaned by removing `$` and converting to float; this assumes `unit_price` values uniformly use `$` as a prefix.
- Date/time parsing in SQL queries assumes the `date` field is in a format compatible with `TRY_CONVERT` in SQL Server.

