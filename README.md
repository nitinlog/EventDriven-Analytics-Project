# EventDriven-Analytics-Project

This is formaula one event drivent pipeline. 


DATASET DETAILS -

Dataset - https://openf1.org/#introduction
High granularity: Lap-by-lap and sector-level telemetry lets you build advanced analytics (beyond just race results)
Raw data ready for ingestion (JSON files or API?)
Open data means fewer restrictions than proprietary APIs
Supports building:
Event-driven pipelines (e.g., ingest live telemetry)
Historical analyses (SCD Type 2 tracking for driver performance changes)
Advanced metrics (lap time consistency, pit stop efficiency)



Tech Stack:

Snowflake (Data Warehouse)

dbt (Data Transformation & Modeling)

Python (for orchestration and ingestion)

GitHub Actions (for CI/CD)

Optional: Airflow or Prefect (for orchestration), Kafka (for real-time ingestion), Streamlit (for dashboards)



Key metrics:

1)
2) 
3) 
4)

Project Architecture -

+-----------------------+
|     External API      |  <-- Ergast / other F1 API (race, driver, lap data)
+----------+------------+
           |
           v
+-----------------------+
|      Airflow DAGs     |  <-- Orchestrate API calls, retries, full & incremental loads
+----------+------------+
           |
           v
+-----------------------+
|   Snowflake Raw Layer |  <-- Store raw JSON or parsed data + ingestion metadata
+----------+------------+
           |
           v
+-----------------------+
|  DBT Staging Models   |  <-- Flatten & clean raw data
+----------+------------+
           |
           v
+-----------------------+
|  DBT Snapshots (SCD2) |  <-- Track historical changes in dimensions
+----------+------------+
           |
           v
+-----------------------+
| DBT Curated Models    |  <-- Business metrics, facts & dimensions
+----------+------------+
           |
           v
+-----------------------+
|     BI / Analytics    |  <-- Dashboards & reports (Looker/Tableau)
+-----------------------+


