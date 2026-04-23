# 🏢 Enterprise Data Governance Platform
**Building a Modern Data Lake with ADLS, Microsoft Fabric & Purview**

---

## 📊 Project Badges

![Architecture](https://img.shields.io/badge/Architecture-Modern%20Data%20Lake-blue?style=flat-square&logo=microsoft-azure)
![Framework](https://img.shields.io/badge/Framework-Microsoft%20Fabric-0078D4?style=flat-square&logo=microsoft)
![Language](https://img.shields.io/badge/Language-PySpark%20%7C%20SQL-FF6B35?style=flat-square&logo=apache-spark)
![Cloud](https://img.shields.io/badge/Cloud-Azure-0078D4?style=flat-square&logo=microsoft-azure)
![Storage](https://img.shields.io/badge/Storage-ADLS%20Gen2-4CAF50?style=flat-square&logo=microsoft-azure)
![Governance](https://img.shields.io/badge/Governance-Purview-8B7D6B?style=flat-square&logo=microsoft)
![Data Format](https://img.shields.io/badge/Format-Delta%20Lake-004687?style=flat-square&logo=databricks)
![Status](https://img.shields.io/badge/Status-Production%20Ready-success?style=flat-square)
![GitHub](https://img.shields.io/badge/GitHub-livinvincentDE-181717?style=flat-square&logo=github)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

---

## 🔗 Quick Links

📂 **Repository:** [azure-de-21days-journey-Day4](https://github.com/livinvincentDE/azure-de-21days-journey-Day4)  
👤 **Author:** [livinvincentDE](https://github.com/livinvincentDE)  
⭐ **Star this repo** if you found it helpful!  
📖 **Full documentation** available in the repository  

---

## 🎯 Executive Summary

This project demonstrates **enterprise-grade data engineering** practices by building a fully governed data platform that:

✅ **Ingests** raw data from various sources into Azure Data Lake Storage Gen2  
✅ **Transforms** data using PySpark within Microsoft Fabric (Medallion Architecture)  
✅ **Catalogs** all assets using Microsoft Purview for discovery & governance  
✅ **Classifies** sensitive PII automatically (GDPR/HIPAA compliant)  

**Problem Solved:** Organizations lose visibility over scattered data and struggle with governance. This solution provides unified cataloging, automated classification, and enterprise-grade data lineage.

---

## 🏗️ Architecture Overview

```
┌─────────────────────────────────────────────────────────────────────┐
│                     DATA FLOW ARCHITECTURE                          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                       │
│  SOURCE DATA                                                         │
│  (CSV, APIs, DBs)                                                    │
│        │                                                              │
│        ▼                                                              │
│  ┌──────────────────────────────────────────────────┐               │
│  │  Azure Data Lake Storage Gen2 (ADLS)            │               │
│  │  ├─ rawlayer/        (Bronze)                   │               │
│  │  ├─ curatedlayer/    (Silver)                   │               │
│  │  └─ consumerlayer/   (Gold)                     │               │
│  └──────────────────────────────────────────────────┘               │
│        │                                                              │
│        ▼                                                              │
│  ┌──────────────────────────────────────────────────┐               │
│  │  Microsoft Fabric (PySpark / Delta Lake)         │               │
│  │  ├─ Data transformation                          │               │
│  │  ├─ Quality checks & validation                  │               │
│  │  └─ ACID transactions                            │               │
│  └──────────────────────────────────────────────────┘               │
│        │                                                              │
│        ├─────────────────┬──────────────────┐                       │
│        ▼                 ▼                  ▼                        │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐              │
│  │ Power BI     │  │  Purview     │  │ SQL Endpoint │              │
│  │ Dashboards   │  │  Governance  │  │  Analytics   │              │
│  └──────────────┘  └──────────────┘  └──────────────┘              │
│                                                                       │
│  OUTPUTS: Insights, Governance, Compliance                          │
│                                                                       │
└─────────────────────────────────────────────────────────────────────┘
```

### 🛠️ Technology Stack

| Layer | Technology | Purpose |
|-------|-----------|---------|
| **Storage** | Azure Data Lake Storage Gen2 | Scalable, hierarchical data lake |
| **Compute** | Microsoft Fabric (PySpark) | Distributed data transformation |
| **Format** | Delta Lake | ACID transactions, time travel |
| **Governance** | Microsoft Purview | Data cataloging & lineage |
| **Visualization** | Power BI | Business intelligence & analytics |
| **Language** | Python, SQL, Spark SQL | Data engineering workflows |

---

## 📸 Step-by-Step Implementation

### **Step 0: Welcome Screen**

![Welcome Screen](https://raw.githubusercontent.com/livinvincentDE/azure-de-21days-journey-Day4/main/screenshot/welcomescreen.png)

**Overview:** Microsoft Purview portal landing page showing unified governance capabilities across Microsoft 365, Azure, AWS, Snowflake, and other cloud platforms.

**Key Points:**
- Single platform for data discovery across multi-cloud environments
- Integrated governance for sensitive information protection
- Modern, unified user experience across compliance solutions

---

### **Step 1: Data Source Registration**

![Data Sources Overview](https://raw.githubusercontent.com/livinvincentDE/azure-de-21days-journey-Day4/main/screenshot/step1.png)

**What's Shown:**
- **Data Map** section displaying registered data sources in both Map View and Table View
- Currently shows **2 data sources**:
  1. **purview-gov-demo** (default container)
  2. **adls-sales-source** (Azure Data Lake Storage Gen2)
  3. **Fabric-R2x** (Microsoft Fabric workspace)

**Technical Details:**
```
Data Source: adls-sales-source
├─ Type: Azure Data Lake Storage Gen2
├─ Credential: Microsoft Purview MSI (system)
├─ Scope: rawlayer, curatedlayer
└─ Status: Active & discoverable
```

**Why This Matters:**
- Establishes single source of truth for data assets
- Enables unified search across all data sources
- Prepares metadata for automatic discovery

---

### **Step 2: Register Data Source Dialog**

![Register Data Source](https://raw.githubusercontent.com/livinvincentDE/azure-de-21days-journey-Day4/main/screenshot/step2.png)

**What's Shown:**
Complete dialog for registering new data sources with multiple connector options:

**Supported Data Sources:**
```
Azure                          Database                Services
├─ Azure Cosmos DB             ├─ Amazon RDS           ├─ Amazon Redshift
├─ Azure Blob Storage          ├─ Azure Arc SQL        ├─ Amazon S3
├─ Azure Data Lake Storage     ├─ Azure DB MySQL       ├─ Azure Data Explorer
├─ Azure Database              ├─ Azure DB PostgreSQL  ├─ Azure Databricks
├─ Azure Synapse               ├─ Fabric Lakehouse     └─ (15+ more)
└─ (8+ more)
```

**Selection Process:**
1. Filter by keyword or tab
2. Choose data source type
3. Configure authentication
4. Set scan parameters
5. Deploy scan rule set

---

### **Step 3: Source Details View**

![Data Source Details](https://raw.githubusercontent.com/livinvincentDE/azure-de-21days-journey-Day4/main/screenshot/step3.png)

**What's Shown:**
Detailed view of the **adls-sales-source** data source after registration:

**Configuration:**
```yaml
Name: adls-sales-source
Type: Azure Data Lake Storage Gen2
Container: purview-gov-demo
Status: Registered & Active
Lineage: Visual map showing relationships
```

**Available Actions:**
- **View details** - Full configuration review
- **Edit** - Modify settings
- **Delete** - Remove from catalog
- **Scan** - Trigger metadata extraction

**Data Lineage Preview:**
Shows upstream container connection in visual graph format

---

### **Step 4: Scan Configuration**

![Scan Configuration Dialog](https://raw.githubusercontent.com/livinvincentDE/azure-de-21days-journey-Day4/main/screenshot/step4.png)

**What's Shown:**
Configuration wizard for scanning the ADLS data source

**Critical Configuration Steps:**

```python
Scan Parameters:
├─ Name: scan-sales-raw
├─ Integration Runtime: Azure AutoResolveIntegrationRuntime ✓
├─ Credential: Microsoft Purview MSI (system) ✓
├─ Scan Level: Auto-detect (highest level supported)
├─ Domain: purview-gov-demo
├─ Collection: (Select domain only)
└─ Status: Ready for execution
```

**Authentication Method:**
```
Managed Identity (MSI):
├─ No API keys needed
├─ Automatic token refresh
├─ Secure credential handling
└─ Best practice for Azure services
```

**Key Insight:**
Before scan setup, the managed identity must have:
- Reader access to ADLS
- List & Read permissions on containers
- No explicit credential management required

---

### **Step 5: Scan Scope Selection**

![Scope Configuration](https://raw.githubusercontent.com/livinvincentDE/azure-de-21days-journey-Day4/main/screenshot/step5.png)

**What's Shown:**
Asset selection dialog for defining scan boundaries

**Scan Scope Configuration:**

```
adls-sales-source (ADLS Gen2)
├─ curatedlayer/ ✓ (checked)
│  └─ Contains processed delta tables
├─ rawlayer/ ✓ (checked)
│  └─ Contains raw CSV uploads
└─ Settings:
   ├─ Refresh: Full rescan on each run
   ├─ Add new assets: Enabled (future assets auto-included)
   └─ Incremental: Second run onwards
```

**Configuration Options:**
- **Full Scan:** Initial discovery of all metadata
- **Incremental Scan:** Subsequent scans (delta only)
- **Auto-include:** New assets automatically discovered
- **Refresh:** Toggle periodic updates

**Why This Matters:**
- Controls which assets get cataloged
- Optimizes scan performance
- Enables automatic discovery of new data

---

### **Step 6: Scan Trigger Configuration**

![Scan Trigger Setup](https://raw.githubusercontent.com/livinvincentDE/azure-de-21days-journey-Day4/main/screenshot/step6.png)

**What's Shown:**
Options for when and how often scans execute

**Scan Schedule Options:**

```
Option 1: RECURRING (Scheduled)
├─ Frequency: Daily, Weekly, Monthly
├─ Time: User-specified
└─ Use Case: Continuous data discovery

Option 2: ONCE (Manual)
├─ Runs: Immediately after setup
├─ Recurrence: None
└─ Use Case: One-time initial catalog [SELECTED]
```

**Configuration Choice:**
For this project, **"Once"** is selected because:
1. Initial discovery of existing assets
2. Subsequent scans can be triggered manually
3. Incremental mode for future runs
4. Avoids unnecessary cloud compute costs

**Best Practice:** Set to recurring (daily) in production for continuous asset discovery

---

### **Step 7: Scan Review & Confirmation**

![Scan Review](https://raw.githubusercontent.com/livinvincentDE/azure-de-21days-journey-Day4/main/screenshot/step7.png)

**What's Shown:**
Final review of all scan configurations before execution

**Complete Scan Configuration Summary:**

```yaml
BASICS:
  Name: scan-sales-raw
  Collection: purview-gov-demo

CREDENTIAL:
  Type: Managed identity
  Provider: Microsoft Purview MSI

SCAN SCOPE:
  Scope: Full
  Rule Set: AdlsGen2 (System ruleset)

SCAN TRIGGER:
  Start At: Immediately
  Recurrence: Once
```

**Action:**
- ✅ **Save and run** - Executes scan immediately
- 📋 **Back** - Modify configuration
- ❌ **Cancel** - Discard changes

**Test Connection:**
Button available to validate ADLS connectivity before scan

---

### **Step 8: Domains & Collections**

![Domains View](https://raw.githubusercontent.com/livinvincentDE/azure-de-21days-journey-Day4/main/screenshot/step8.png)

**What's Shown:**
Domain management interface showing the default governance container

**Domain Structure:**

```
purview-gov-demo (Default Domain)
├─ Description: The default container
├─ Type: Organization domain
├─ Assets Discovered: 1
├─ Collections: 0 (can create sub-collections)
└─ Metadata:
   ├─ Assets: 1
   ├─ Data Sources: 1
   ├─ Scans: 1
   └─ Last Updated: April 23, 2026

Actions Available:
├─ New Collection (hierarchy)
├─ Edit (modify domain settings)
├─ Refresh (re-scan assets)
└─ View other objects
```

**Organizational Structure:**
```
Enterprise Root
└─ purview-gov-demo
   ├─ Collection: Finance
   │  ├─ Collection: GL Accounts
   │  └─ Collection: Receivables
   └─ Collection: Sales
      └─ Collection: Transactions
```

**Why This Matters:**
- Organizes assets by business domains
- Enables role-based access control (RBAC)
- Supports governance across teams

---

### **Step 9: Data Assets Discovery**

![Assets Discovered](https://raw.githubusercontent.com/livinvincentDE/azure-de-21days-journey-Day4/main/screenshot/step9.png)

**What's Shown:**
Comprehensive list of all discovered assets from the scan

**Discovered Assets (6 items):**

```
Asset Name              │ Asset Type                    │ Collection
─────────────────────────────────────────────────────────────────────
curatedlayer            │ ADLS Gen2 Folder              │ -
rawlayer                │ ADLS Gen2 Folder              │ -
rgdatagovernancedemo    │ Azure Storage Account         │ -
rgdatagovernancedemo    │ ADLS Gen2 Service            │ -
sales                   │ ADLS Gen2 Path               │ -
sales_transactions.csv  │ ADLS Gen2 Path               │ -
```

**Asset Details:**
- **Folders** - Containers for organizing data
- **Storage Account** - Parent Azure resource
- **Paths** - Individual CSV files
- **CSV Files** - Actual data assets

**Metadata Captured:**
```python
For each asset:
├─ Name & Type
├─ Full path in ADLS
├─ Creation timestamp
├─ Last modified date
├─ File size (if applicable)
├─ Storage account details
└─ Hierarchy relationships
```

**View Columns:**
- Asset name (clickable for details)
- Asset type (folder, file, service)
- Collection (governance grouping)

---

### **Step 10: Data Catalog & Schema**

![Unified Catalog View](https://raw.githubusercontent.com/livinvincentDE/azure-de-21days-journey-Day4/main/screenshot/step10.png)

**What's Shown:**
Detailed asset view in Microsoft Purview Unified Catalog showing schema and classification

**Asset Details: sales_transactions.csv**

```
Location: Azure Data Lake Storage Gen2 | File
Source: purview-gov-demo > Assets in domain
Status: Updated on April 23, 2026, 11:48 AM
Scan Reference: scan-sales-raw (automated)
```

**Schema Inference (8 Columns):**

```sql
Column Name          │ Data Type │ Classifications
─────────────────────────────────────────────────────────
order_id             │ string    │ -
customer_id          │ string    │ -
customer_name        │ string    │ ⚡ All Full Names
email                │ string    │ ⚡ Email Address
product              │ string    │ -
amount               │ string    │ -
order_date           │ string    │ -
city                 │ string    │ ⚡ World Cities
```

**Auto-Classification Details:**

| Column | Classification | Standard | Risk Level |
|--------|---------------|----|-----------|
| customer_name | All Full Names | PII | High |
| email | Email Address | PII | High |
| city | World Cities | Location Data | Medium |

**Features:**
- **Lineage** - Shows upstream sources
- **Contacts** - Data stewards & producers
- **Related** - Connected assets
- **History** - Change tracking
- **Glossary** - Business terminology

---

### **Step 11: Welcome Portal**

![Portal Welcome Screen](https://raw.githubusercontent.com/livinvincentDE/azure-de-21days-journey-Day4/main/screenshot/datalineage_check.png)

**What's Shown:**
Microsoft Purview portal home with multi-cloud integration overview

**Supported Cloud Platforms:**

```
Connected Platforms (✓ = Connected):
├─ Microsoft 365 (✓)
├─ Microsoft Azure (✓)
├─ AWS (Amazon Web Services)
├─ Snowflake
└─ Other cloud platforms & apps
```

**Portal Features:**

1. **Data Governance**
   - Unified catalog across clouds
   - Asset discovery & classification
   - Lineage tracking

2. **Data Security**
   - Sensitivity label automation
   - Compliance monitoring
   - Data risk analytics

3. **Compliance Solutions**
   - GDPR, HIPAA, SOX support
   - Audit trails
   - Policy enforcement

4. **Data Quality**
   - Quality metrics
   - Issue tracking
   - Remediation workflows

**Portal Advantages:**
- Single pane of glass for all data governance
- Cross-cloud visibility (Azure, AWS, Snowflake)
- Unified compliance management

---

## 🔐 Data Governance & Classification

### **Automated PII Classification**

Microsoft Purview automatically classifies sensitive data:

```yaml
CLASSIFICATION RESULTS:

Column: customer_name
├─ Classifier: Pattern-based (Full Name)
├─ Confidence: High (95%+)
├─ Classification: "All Full Names"
├─ Risk Level: High
├─ Standard: Personal Identifiable Information (PII)
└─ Remediation: Apply sensitivity labels, restrict access

Column: email
├─ Classifier: Pattern-based (Email regex)
├─ Confidence: High (99%+)
├─ Classification: "Email Address"
├─ Risk Level: High
├─ Standard: Personal Identifiable Information (PII)
└─ Remediation: Apply sensitivity labels, restrict access

Column: city
├─ Classifier: Glossary lookup (World Cities)
├─ Confidence: Medium (80%+)
├─ Classification: "World Cities"
├─ Risk Level: Medium
├─ Standard: Geographic Location Data
└─ Remediation: Optional tagging
```

### **Governance Policies**

```yaml
Sensitive Data Handling:

Policy 1: PII Access Control
├─ Assets: customer_name, email, phone
├─ Action: Require MFA + approval
├─ Audit: Log all access
└─ Retention: 90 days

Policy 2: Data Minimization
├─ Assets: email addresses
├─ Action: Mask in dev/test environments
├─ Format: xxxxx@example.com
└─ Frequency: Daily

Policy 3: Deletion on Schedule
├─ Assets: Transactional logs older than 1 year
├─ Action: Automatic purge
├─ Approval: Manager review
└─ Schedule: Monthly batch job
```

---


### **Microsoft Purview Best Practices**

```yaml
1. Metadata Governance:
   ├─ Define domain taxonomy upfront
   ├─ Enforce consistent naming conventions
   ├─ Establish data owner responsibilities
   └─ Version control metadata changes

2. Classification Strategy:
   ├─ Customize classifications for your org
   ├─ Use glossary terms for consistency
   ├─ Automate classification where possible
   └─ Review classifications quarterly

3. Access Control:
   ├─ Implement least-privilege model
   ├─ Use roles for team assignments
   ├─ Audit all data access
   └─ Rotate service principal secrets

4. Compliance & Retention:
   ├─ Map regulations to data classifications
   ├─ Define retention periods
   ├─ Automate deletion policies
   └─ Generate compliance reports
```

---

## 📚 Project Artifacts

**📂 Repository:** [azure-de-21days-journey-Day4](https://github.com/livinvincentDE/azure-de-21days-journey-Day4)

```
project-root/
├── README.md (this file)
├── screenshot/
│   ├── welcomescreen.png
│   ├── step1.png
│   ├── step2.png
│   ├── step3.png
│   ├── step4.png
│   ├── step5.png
│   ├── step6.png
│   ├── step7.png
│   ├── step8.png
│   ├── step9.png
│   ├── step10.png
│   └── datalineage_check.png
├── data/
│   └── sales_transactions.csv
├── notebooks/
│   └── data_transformation.ipynb
├── iac/
│   └── infrastructure.bicep
├── sql/
│   └── analytics_queries.sql
└── config/
    └── purview_classification_rules.json
```

