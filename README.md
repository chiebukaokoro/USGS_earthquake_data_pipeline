# GeoVolt Energy Earthquake Monitoring ETL Pipeline

## Project Overview

GeoVolt Energy is a fictional geothermal energy company focused on identifying potential locations for future geothermal projects across the United States.

Because geothermal resources are closely associated with tectonic activity, monitoring earthquake activity provides valuable geological insights for evaluating exploration areas.

This project was developed to replace a manual weekly earthquake data collection process where employees retrieved earthquake records from the USGS Earthquake API, filtered relevant events, and maintained historical data in spreadsheets.

The solution implements an automated ETL pipeline that extracts earthquake data from the USGS API, transforms and validates the data using Python, stores the results in a SQLite database, and automatically updates new earthquake events through GitHub Actions.

---

## Business Problem

The previous manual process created several challenges:

- Time-consuming weekly data collection
- Increased risk of human error
- Difficulty maintaining historical records
- Limited ability to analyze earthquake trends
- Lack of an automated data refresh process

---

## Solution

The pipeline automates the complete data engineering lifecycle:

- **Extract:** Retrieves earthquake data from the USGS Earthquake API
- **Transform:** Cleans, validates, and standardizes earthquake records using Python and Pandas
- **Load:** Stores processed earthquake data in a SQLite database
- **Automate:** Uses GitHub Actions to execute weekly incremental updates

---

## Implementation Details

### Historical Load

The historical ETL pipeline established the initial earthquake database by extracting data from January 2026 through August 2026.

The extraction was performed in monthly batches to improve reliability and simplify troubleshooting.

The historical process:

- Extracted earthquake records from the USGS API
- Flattened nested JSON responses
- Standardized timestamps and location information
- Applied data quality checks
- Loaded 70,516 earthquake records into SQLite

### Incremental Load

After the initial historical load, the pipeline performs automated weekly updates.

The incremental pipeline:

- Runs every Monday at 12:00 AM Pacific Time
- Retrieves the previous 14 days of earthquake activity
- Uses a two-week lookback window to account for delayed USGS updates
- Compares incoming earthquake IDs against existing records
- Inserts only new earthquake events into the database

---

## Technologies Used

- Python
- Pandas
- SQLAlchemy
- SQLite
- GitHub Actions
- USGS Earthquake API

---

## Future Improvements

Potential enhancements include:

- Migrating from SQLite to a more scalable database solution such as PostgreSQL, Azure SQL Database, or DuckDB
- Adding pipeline monitoring, data quality checks, and failure notifications
- Transitioning to enterprise workflow orchestration tools such as Apache Airflow, Prefect, or Azure Data Factory

---

## Project Outcome

The GeoVolt Energy Earthquake Monitoring ETL Pipeline transformed a manual weekly data collection process into an automated and reliable data engineering workflow.

The project established a centralized earthquake database, automated weekly updates, improved data consistency through validation and duplicate prevention, and created a foundation for future reporting and geothermal analytics.

This project demonstrates the complete data engineering lifecycle:

**Data Generation → Data Ingestion → Data Transformation → Data Storage → Data Serving**
