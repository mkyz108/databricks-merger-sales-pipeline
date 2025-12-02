# Post-Merger Sales Data Pipeline  
### Databricks | PySpark | Spark SQL | AWS S3 | Medallion Architecture

This project simulates a real-world **post-merger data integration problem** in the **sales domain**.

A mature company (**Atlon**) acquires a fast-growing startup (**Sports Bar**).  
Atlon has clean ERP-driven data, while Sports Bar has messy CSV-based sales data with:
- Inconsistent schemas
- Missing months
- Typos in cities & customer names
- Invalid and negative prices
- Duplicate records

Leadership needed a **single trusted sales dataset** for forecasting and inventory planning.

This repository contains the **end-to-end Databricks data pipeline** I built to solve that problem using the **Medallion Architecture (Bronze → Silver → Gold).**

---

## 🧱 Architecture

- **Storage:** AWS S3 (raw CSV files)
- **Compute:** Databricks
- **Processing:** PySpark & Spark SQL
- **Storage Format:** Delta Lake

**Layers**
- **Bronze:** Raw ingestion from S3 (no transformations)
- **Silver:** Data cleaning & standardization
- **Gold:** Monthly sales aggregation & unified fact tables

> Add your architecture image here once uploaded:  
> `architecture/medallion_architecture.png`

---

## 🥉 Bronze Layer – Raw Ingestion
Location: `notebooks/bronze/`

- Ingest raw CSV files from AWS S3
- Preserve original schema for audit & reprocessing
- No transformations applied

---

## 🥈 Silver Layer – Data Cleaning & Standardization
Location: `notebooks/silver/`

Key transformations:
- City name standardization using mapping logic
- Customer name normalization using `trim()` and `initcap()`
- Negative & invalid prices corrected
- Duplicate customer records removed
- Schema alignment across both companies

---

## 🥇 Gold Layer – Aggregation & Unification
Location: `notebooks/gold/`

- Daily sales aggregated to **monthly sales**
- Sports Bar sales **merged (upserted)** into Atlon fact tables
- Created **BI-ready denormalized view** for analytics

---

## ⚙️ Technologies Used

- Databricks (Lakehouse Platform)
- PySpark
- Spark SQL
- Delta Lake
- AWS S3
- Python

---

## 🔐 Configuration & Security

All AWS credentials and secrets are loaded using **environment variables**.  
No sensitive data is stored in this repository.

Required environment variables:
- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `S3_BUCKET_NAME`
- `AWS_REGION`

---

## ▶️ How to Run (High Level)

1. Upload raw CSV files to your S3 bucket
2. Run Bronze notebooks for ingestion
3. Run Silver notebooks for cleaning
4. Run Gold notebooks for aggregation & merge
5. Query the Gold tables for reporting

---

## 🎯 Purpose of This Project

This project demonstrates:
- Real-world **ETL pipeline design**
- Practical **data cleaning under messy business conditions**
- Use of **Medallion Architecture**
- Hands-on experience with **Databricks + PySpark for analytics engineering**

---

## 👤 Author

**Mudasir Khan**  
Targeting: Data Engineer / Analytics Engineer roles (US, Canada, Remote)

