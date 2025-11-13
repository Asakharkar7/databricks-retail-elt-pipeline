#🛍️ Retail Analytics Pipeline — Databricks PySpark (Bronze → Silver → Gold)

An end-to-end ELT pipeline built in Databricks using PySpark and the Delta Lake Bronze/Silver/Gold architecture.
This project ingests raw retail data, cleans and transforms it, produces business-ready analytics tables, and visualizes insights using Databricks Notebook Dashboards.

##🚀 Architecture

<img width="1536" height="1024" alt="Architecture" src="https://github.com/user-attachments/assets/7fe8c940-7de1-4a77-93fc-d2da2ce27047" />




# 🧱 Pipeline Overview

## Bronze Layer — Raw Ingestion

1. Loaded CSV file into Databricks

2. Enforced schema & cleaned minimal fields

3. Stored as Bronze Delta Table

## Silver Layer — Data Cleaning

1. Performed full data fixes:

2. Handled mixed timestamp formats

3. Removed negative quantities / prices

4. Standardized CustomerID

5. Added revenue column

6. Removed corrupted rows

7. Ensured clean timestamp conversion

## Gold Layer — Business Metrics

1. Created analytical Delta Tables:

2. Revenue by Country

3. Monthly Revenue Trend

4. Total Orders

5. Unique Customers

6. Returning Customer %

7. Top 10 Customers

8. Average Order Value

# 📊 Dashboard (Notebook Dashboard View)

## Since Databricks notebook dashboards cannot be exported, screenshots are provided

<img width="1277" height="757" alt="Dashboard Part 1" src="https://github.com/user-attachments/assets/29849e6e-d404-4905-b538-27516b1d6c3a" />


<img width="1022" height="501" alt="Dashboard Part 2" src="https://github.com/user-attachments/assets/5c8cd1ec-f01f-452c-b075-c9752a34f636" />

## Included KPIs visualized:

Total Orders

Total Revenue

Revenue by Country

Unique Customers

Returning Customer %

Average Order Value (AOV)

Monthly Revenue

Top 10 Customers


#🛠️ Technologies Used

1. Databricks (Free Community Edition)

2. PySpark

3. Delta Lake

4. Notebook Dashboard UI

5. Bronze/Silver/Gold Architecture

6. ETL/ELT Pipeline Design

7. Data Visualization

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



# 🏁 Future Enhancements

1. Automate ingestion with Auto Loader

2. Add Databricks Jobs for scheduling

3. Implement unit tests with pytest

Add CDC support for incremental updates

Convert Gold Layer into a star schema (fact + dims)

