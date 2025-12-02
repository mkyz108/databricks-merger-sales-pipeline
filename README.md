# Post-Merger Sales Data Pipeline  
### Databricks | PySpark | Spark SQL | AWS S3 | Medallion Architecture | Incremental Loads | Dashboards

This project simulates a real-world **post-merger data integration problem** in the **sales domain**.

A mature enterprise (**Atlon**) acquired a fast-growing startup (**Sports Bar**).  
Their data environments were completely different:

- Atlon → Clean ERP-driven structured data  
- Sports Bar → Messy CSV-based startup data with:
  - Missing months
  - Duplicates
  - Typos in city & customer names
  - Invalid and negative prices
  - Inconsistent schemas

Leadership required a **single trusted analytics layer** for unified sales and inventory planning.

I built a **production-style end-to-end data pipeline on Databricks** using the **Medallion Architecture (Bronze → Silver → Gold)** with **incremental loading and scheduled execution**.

---

## 🧱 Architecture

- **Cloud Storage:** AWS S3  
- **Compute:** Databricks  
- **Processing:** PySpark & Spark SQL  
- **Storage Format:** Delta Lake  
- **Orchestration:** Databricks Jobs (Scheduled Runs)

### Layers
- **Bronze:** Raw incremental ingestion from S3
- **Silver:** Data cleansing, validation & standardization
- **Gold:** Monthly aggregation, upserts, BI-ready fact tables

> Add your architecture image here:  
> `architecture/medallion_architecture.png`

---

## 🥉 Bronze Layer – Incremental Raw Ingestion
Location: `notebooks/bronze/`

- Ingest raw CSV files from AWS S3
- Load only **new or changed data (incremental strategy)**
- Preserve original schema for audit & replay
- No transformations applied

---

## 🥈 Silver Layer – Data Cleaning & Standardization
Location: `notebooks/silver/`

Key transformations:
- City name standardization using mapping logic
- Customer name normalization using `trim()` and `initcap()`
- Invalid price correction (negative & non-numeric values)
- Removal of duplicate customer records
- Schema alignment across both companies

---

## 🥇 Gold Layer – Aggregation & Unification
Location: `notebooks/gold/`

- Daily sales aggregated into **monthly sales**
- **Upsert (MERGE)** into unified sales fact table
- Creation of **denormalized BI-ready views**
- Supports incremental refresh instead of full reloads

---

## ⏱️ Orchestration & Scheduling

- All pipeline stages are executed using **Databricks Jobs**
- Pipeline supports:
  - Incremental Bronze ingestion
  - Incremental Silver transformation
  - Incremental Gold aggregation & merge
- Can run on:
  - Daily
  - Weekly
  - Or custom schedules

---

## 📊 Databricks SQL Dashboard

A business-facing **Databricks SQL Dashboard** was created on the Gold layer:

Key KPIs:
- Total Revenue: **105.34B**
- Total Quantity Sold: **34.13M**
- Unique Customers: **54**
- Average Selling Price: **4043.16**

Visuals include:
- Monthly revenue trend
- Revenue share by channel
- Top products by revenue
- Top customers by revenue
- Variant-level performance
- Product price vs quantity analysis

---

## ⚙️ Technologies Used

- Databricks
- PySpark
- Spark SQL
- Delta Lake
- AWS S3
- Python
- Databricks SQL Dashboards
- Databricks Jobs (Scheduling)

---

## 🔐 Configuration & Security

All AWS credentials and secrets are managed using **environment variables**.  
No sensitive data is stored in this repository.

Required environment variables:
- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `S3_BUCKET_NAME`
- `AWS_REGION`

---

## ▶️ How to Run (High Level)

1. Upload raw CSV sales files to AWS S3
2. Trigger Databricks Job for Bronze incremental ingestion
3. Execute Silver transformations
4. Run Gold aggregation & merge job
5. Refresh Databricks SQL Dashboard on Gold tables

---

## 🎯 Purpose of This Project

This project demonstrates:
- Real-world **ETL / ELT pipeline design**
- **Incremental data processing**
- **Job scheduling & orchestration**
- Practical **data cleaning at scale**
- **Medallion Architecture implementation**
- End-to-end **analytics engineering on Databricks**

---

## 👤 Author

**Mudasir Khan**  
Targeting: Data Engineer | Analytics Engineer  
Location: US | Canada | Remote
