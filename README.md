# NEWS-Data-Analysis-Project-Snowflake-Airflow-GCP-Integration

This project demonstrates an end-to-end data pipeline that fetches news data from the News API, processes it, and stores it in Google Cloud Storage (GCS) as Parquet files. The data is then ingested into Snowflake for analysis and the generation of summary tables.

## Project Overview

### Workflow:

1.	Fetch News Data:
	
 •	News data is fetched from the News API using Python.
 
 •	The data is cleaned, transformed, and saved locally as a Parquet file.
 
 •	The Parquet file is uploaded to a GCS bucket.
 
2.	Ingest Data into Snowflake:
	
 •	The Parquet files from GCS are ingested into a Snowflake table.
 
3.	Data Analysis in Snowflake:
	
 •	Create summary tables:
	
 •	News Summary Table: Aggregates article counts and timestamps by source.
	
 •	Author Activity Table: Tracks author statistics such as article count and distinct news sources.
