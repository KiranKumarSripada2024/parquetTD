# Parquet File Comparison Tool

## Overview
This tool automates the comparison of Parquet files from two different snapshots, extracts differences, and stores the results in both JSON and CSV formats. It also inserts the comparison data into a MySQL database.

## Features
- Downloads Parquet files from a remote server.
- Extracts and compares data based on the `edited_date` column.
- Saves differences in JSON and CSV formats.
- Stores results in a MySQL database.

## Requirements
- Python 3.x
- Required libraries: `polars`, `requests`, `mysql-connector-python`, `zipfile`, `json`, `configparser`
- MySQL database with a table named `insights_comparison`.

## Usage
1. Add your credentials to `config.properties`.
2. Run the script and enter the snapshot dates when prompted.
3. The differences will be saved in the `json_master` and `csv_master` directories and inserted into the database.

## Database Table Structure
```sql
CREATE TABLE insights_comparison (
    id INT AUTO_INCREMENT PRIMARY KEY,
    folder_name VARCHAR(255),
    file1 VARCHAR(255),
    file2 VARCHAR(255),
    edited_date VARCHAR(50),
    data JSON
);
```

