🚀 🗄️ ADLS → ⚙️ Microsoft Fabric → 🧭 Microsoft Purview
<p align="center">
















</p>
🧠 Business Problem

Modern organizations struggle with:

❌ Data scattered across systems
❌ No visibility into sensitive data (PII)
❌ Lack of governance & catalog
❌ No standardized data pipeline

👉 This project solves it by building a governed data platform.

🏗️ Solution Architecture
🧰 Tech Stack
Layer	Technology
Storage	Azure Data Lake Storage Gen2
Processing	Microsoft Fabric (PySpark)
Format	Delta Lake
Governance	Microsoft Purview
Visualization	Power BI
📂 Repository Structure
project/
│
├── data/
│   └── sales_transactions.csv
│
├── notebooks/
│   └── data_transformation.ipynb
│
├── screenshots/
│   ├── step1_upload.png
│   ├── step2_fabric.png
│   ├── step3_purview_scan.png
│   ├── step4_classification.png
│
└── README.md
🪜 Implementation Steps
🟢 Step 1: Data Ingestion (ADLS)

📌 Created storage account with hierarchical namespace

📌 Containers:

rawlayer
curatedlayer

📌 Uploaded dataset

<p align="center"> <img src="screenshots/step1_upload.png" width="800"/> </p>
🟡 Step 2: Data Processing in Fabric

📌 Read CSV using PySpark

df = spark.read.format("csv") \
.option("header", "true") \
.load("Files/sales/sales_transactions.csv")

📌 Preview data

<p align="center"> <img src="screenshots/step2_fabric.png" width="800"/> </p>
🔵 Step 3: Data Cleaning
df_clean = df.filter("amount > 0 AND email IS NOT NULL")

✔ Removed invalid & incomplete records
✔ Ensured data quality

🟣 Step 4: Curated Layer (Delta)
df_clean.write.format("delta") \
.mode("overwrite") \
.saveAsTable("sales_curated")

✔ Stored optimized analytics dataset
✔ Enabled ACID transactions

🟠 Step 5: Register in Purview

📌 Registered ADLS Gen2 as data source

📌 Authentication:

Managed Identity (MSI)
<p align="center"> <img src="screenshots/step3_purview_scan.png" width="800"/> </p>
🔴 Step 6: Scan Configuration
Scan name: scan-sales-raw
Rule set: AdlsGen2
Scope:
rawlayer
curatedlayer

✔ Full metadata extraction

🟢 Step 7: Data Discovery

✔ Assets discovered automatically
✔ Schema inferred

<p align="center"> <img src="screenshots/step4_classification.png" width="800"/> </p>
🔐 Step 8: PII Classification

Purview identified sensitive data:

Column	Classification
customer_name	Full Name
email	Email Address
city	Geographic Location

✔ No manual tagging required

🔗 Step 9: Lineage

⚠️ Current limitation:

No lineage visible

📌 Reason:

Fabric lineage not yet integrated with Purview

📌 Fix (future):

Use Data Factory / Fabric pipelines
📊 Power BI Integration

✔ Connect to sales_curated
✔ Build dashboards:

Revenue trends
Sales by city
Customer insights
🧠 Key Concepts Demonstrated
Data Lake Architecture (Raw → Curated)
Medallion Architecture
Delta Lake ACID properties
Data Governance & Cataloging
Automated Data Classification
Enterprise Data Engineering Design
⚡ Performance & Optimization
Column pruning via Spark
Delta storage for fast queries
Incremental scans supported
🚀 Future Enhancements
🔗 End-to-end lineage tracking
🏷️ Business glossary in Purview
🔐 Sensitivity labels & policies
⚡ Streaming ingestion
📊 Advanced Power BI dashboards
💼 Resume Bullet

Designed and implemented an enterprise-grade data platform using ADLS, Microsoft Fabric, and Purview enabling data ingestion, transformation, governance, and automated PII classification.

🌟 Why This Project Stands Out

✅ Covers Data Engineering + Governance
✅ Real-world architecture
✅ Uses modern Microsoft ecosystem
✅ Demonstrates end-to-end ownership
