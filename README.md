# Pune-Weather-AQI-Data-Pipeline
End-to-end Data Engineering pipeline using Databricks &amp; PySpark. Implements Medallion Architecture (Bronze-Silver-Gold) with automated hourly scheduling via Databricks Jobs to monitor real-time Pune Weather &amp; AQI data.


Pune Weather and AQI Data Pipeline

In this project, I built an automated data pipeline to monitor real-time weather and air quality for Pune city. I used the Medallion Architecture (Bronze, Silver, Gold) in Databricks to make sure the data is clean, reliable, and ready for analytics.

Architecture Details:
1. Bronze Layer (Raw):
I fetched raw JSON data from the Open-Meteo API. I saved this into Delta tables and added an 'ingestion_timestamp' to every record so I can track exactly when the data arrived.

2. Silver Layer (Cleaned):
In this stage, I cleaned the raw data by flattening nested fields and assigning proper data types like Float and Timestamp. This makes the data much easier to query.

3. Gold Layer (Final):
I joined the weather and AQI tables together. To make the join work perfectly, I used 'date_trunc' to round the timestamps to the nearest hour. I also added business logic to categorize air quality as 'Good', 'Moderate', or 'Unhealthy' based on PM2.5 levels.

Automation and Monitoring:
I didn't just write the code; I scheduled it. The pipeline is set up as a Databricks Job that runs every hour. You can see in the screenshots that all runs have a 100% success rate, which proves the pipeline is stable.

Tech Stack:
PySpark (Python)

Databricks

Delta Lake

REST APIs (Open-Meteo)

Project Files:
01_Ingest_Pune_Data.ipynb: Contains the full ETL logic.

Screenshots: Shows the job success history and the final table output.

Feel free to reach out to me on LinkedIn if you have any questions about this implementation.
