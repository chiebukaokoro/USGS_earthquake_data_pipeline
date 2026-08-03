# Earthquake ETL Pipeline

An automated ETL pipeline that extracts earthquake data from the USGS API, transforms the data using Python, stores historical records in a SQLite database, and performs incremental data loading.

## Tools

- Python (requests, pathlib, pandas and SQLAlchemy)
- SQLite
- GitHub Actions

## Pipeline Workflow

1. Extract earthquake data from USGS API
2. Clean and tranform the data to contain US data
3. Load historical data into SQLite database
4. Perform incremental weekly updates