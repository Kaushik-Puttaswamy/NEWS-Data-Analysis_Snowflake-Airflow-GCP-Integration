# NEWS-Data-Analysis-Project-Snowflake-Airflow-GCP-Integration

This project demonstrates an end-to-end data pipeline that fetches news data from the News API, processes it, and stores it in Google Cloud Storage (GCS) as Parquet files. The data is then ingested into Snowflake for analysis and the generation of summary tables.

## Project Overview

### Workflow:

1.	Fetch News Data:
	
 	• News data is fetched from the News API using Python.
 
 	• The data is cleaned, transformed, and saved locally as a Parquet file.
 
 	• The Parquet file is uploaded to a GCS bucket.
 
2.	Ingest Data into Snowflake:
	
 	• The Parquet files from GCS are ingested into a Snowflake table.
 
3.	Data Analysis in Snowflake:
	
 	• Create summary tables:
	
 	• News Summary Table: Aggregates article counts and timestamps by source.
	
 	• Author Activity Table: Tracks author statistics such as article count and distinct news sources.

## Components

1. fetch_news.py
	
 	•	Python script that fetches news articles from the News API.
	
 	•	Saves the processed data as a Parquet file.
	
 	•	Uploads the Parquet file to GCS using the Google Cloud Storage library.

2. Airflow DAG: news_api_airflow_job.py
	
 	•	Orchestrates the data pipeline:
	
 	•	Fetches news data and uploads it to GCS.
	
 	•	Creates a Snowflake table for news data.
	
 	•	Copies data from GCS to Snowflake.
	
 	•	Generates summary tables in Snowflake.

3. Snowflake SQL Scripts: snowflake_commands.sql
	
 	•	Configures Snowflake resources:
	
 	•	Creates a Snowflake database, table, and file format for Parquet.
	
 	•	Sets up a stage to read files from GCS.
	
 	•	Defines SQL queries for data ingestion and analysis.

## Setup and Configuration

### Prerequisites:

1.	Google Cloud Platform:
	
 	•	GCS bucket: snowflake-projects_test

	•	Service account with appropriate permissions to upload files to GCS.

2.	Snowflake:
	
 	•	Snowflake account with access to create databases, stages, and tables.
	
 	•	Configured storage integration with GCS.

3.	Airflow:
	
 	•	Airflow environment with the following operators:
	
 	•	PythonOperator
	
 	•	SnowflakeOperator

4.	News API:
	
 	•	Obtain an API key from https://newsapi.org/

## Steps to Run:

1.	Setup GCS:
	
 	•	Create a GCS bucket named snowflake-projects_test.
	
 	•	Ensure the service account has write access to the bucket.
 
2.	Configure Snowflake:
	
 	•	Run the commands in snowflake_commands.sql to set up the database, file format, and stage.
	
3.	Install Dependencies:
	
 	•	Python: Install required libraries:

	``` pip install pandas google-cloud-storage requests apache-airflow snowflake-connector-python ```

	•	Airflow: Configure the Snowflake connection (snowflake_conn) in Airflow.
