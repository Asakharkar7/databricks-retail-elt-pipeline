🛍️ Retail Analytics Pipeline — Databricks PySpark (Bronze → Silver → Gold)

An end-to-end ELT pipeline built in Databricks using PySpark and the Delta Lake Bronze/Silver/Gold architecture.
This project ingests raw retail data, cleans and transforms it, produces business-ready analytics tables, and visualizes insights using Databricks Notebook Dashboards.

🚀 Architecture

<img width="1536" height="1024" alt="Architecture" src="https://github.com/user-attachments/assets/7fe8c940-7de1-4a77-93fc-d2da2ce27047" />




🧱 Pipeline Overview

Bronze Layer — Raw Ingestion

Loaded CSV file into Databricks

Enforced schema & cleaned minimal fields

Stored as Bronze Delta Table

Silver Layer — Data Cleaning

Performed full data fixes:

Handled mixed timestamp formats

Removed negative quantities / prices

Standardized CustomerID

Added revenue column

Removed corrupted rows

Ensured clean timestamp conversion

Gold Layer — Business Metrics

Created analytical Delta Tables:

Revenue by Country

Monthly Revenue Trend

Total Orders

Unique Customers

Returning Customer %

Top 10 Customers

Average Order Value

📊 Dashboard (Notebook Dashboard View)

Since Databricks notebook dashboards cannot be exported, screenshots are provided

<img width="1277" height="757" alt="Dashboard Part 1" src="https://github.com/user-attachments/assets/29849e6e-d404-4905-b538-27516b1d6c3a" />


<img width="1022" height="501" alt="Dashboard Part 2" src="https://github.com/user-attachments/assets/5c8cd1ec-f01f-452c-b075-c9752a34f636" />

Included KPIs visualized:

Total Orders

Total Revenue

Revenue by Country

Unique Customers

Returning Customer %

Average Order Value (AOV)

Monthly Revenue

Top 10 Customers


🛠️ Technologies Used

Databricks (Free Community Edition)

PySpark

Delta Lake

Notebook Dashboard UI

Bronze/Silver/Gold Architecture

ETL/ELT Pipeline Design

Data Visualization

📥 Input Data

Dataset used:

📌 Online Retail Dataset


## 🔍 Example Code Snippets

### **Silver Layer Timestamp Fixing**

from pyspark.sql.functions import coalesce, to_timestamp

df_silver = df_bronze.withColumn(
    "InvoiceDate",
    coalesce(
        to_timestamp("InvoiceDate", "MM/d/yy HH:mm"),
        to_timestamp("InvoiceDate", "M/d/yy HH:mm"),
        to_timestamp("InvoiceDate", "MM/dd/yy HH:mm"),
        to_timestamp("InvoiceDate", "dd/MM/yy HH:mm")
    )
)



🏁 Future Enhancements

Automate ingestion with Auto Loader

Add Databricks Jobs for scheduling

Implement unit tests with pytest

Add CDC support for incremental updates

Convert Gold Layer into a star schema (fact + dims)

