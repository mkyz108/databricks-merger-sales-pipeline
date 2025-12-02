Post-Merger Sales Data Pipeline – Databricks | PySpark | Medallion Architecture

This project simulates a real-world post-merger data unification scenario where a
startup with messy sales data is merged into a mature enterprise system.

I designed and built an end-to-end data pipeline on Databricks using the Medallion
Architecture (Bronze, Silver, Gold) to unify both companies’ sales data into a
single analytics-ready layer.

Technology Stack:
- Databricks
- PySpark
- Spark SQL
- Delta Lake
- AWS S3

Pipeline Layers:
- Bronze: Raw data ingestion from S3
- Silver: Data cleaning, standardization, validation
- Gold: Sales aggregation, upserts, BI-ready tables

All credentials are loaded via environment variables and are not stored in this repo.

