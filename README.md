# Automobile & Clothing Sales Performance Analytics

## 🏗️ End-to-End Medallion Architecture | SQL Server & Power BI



[![SQL Server](https://img.shields.io/badge/SQL_Server-CC2927?style=for-the-badge&logo=microsoft-sql-server&logoColor=white)](https://www.microsoft.com/en-us/sql-server)

[![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=power-bi&logoColor=black)](https://powerbi.microsoft.com/)



---



### 🚀 Project Overview



This project presents a full-cycle Data Engineering and Business Intelligence solution built to analyze global automobile and clothing sales performance. The goal was to design a scalable, production-style data pipeline that transforms raw, siloed CSV data into a clean, queryable warehouse — and finally into an executive-ready Power BI dashboard.



The core challenge this project solves: **raw sales data across multiple domains (products, customers, geography) was unstructured and unusable for business decisions.** By implementing a Medallion Architecture, I ensured data integrity at every stage — from ingestion to final visualization — providing stakeholders with a reliable "Single Source of Truth."



---



### 📊 Executive Dashboard Insights

![Dashboard Screenshot](Reports/automobiles_&_clothing_sales_report.png)

*Figure 1: Interactive Dashboard — 2013 Sales Performance Analysis*



**Key Features:**

- **Metric Selector (Tabs):** Custom navigation bar to switch the entire report view between Sales, Cost, Profit, Customers, Orders, and Quantity

- **KPI Scorecard:** Tracks Total Sales ($15M), Profit Margin (40.78%), and Total Customers (17K) with automated Year-over-Year (YoY) growth indicators

- **Trend Analysis:** Monthly Sales Trend combining bar and line charts to visualize revenue vs. cost across the fiscal year

- **Demographic Segmentation:** Breakdowns by Gender, Age Group, and Customer Segment (New, VIP, Regular)



---

### 🔍 Deep Data Analysis & Executive Report (FY 2013 vs. FY 2012)

**Active Context Filter:** Fiscal Year 2013 (January 1, 2013 – December 31, 2013)  
**Comparison Benchmark:** Fiscal Year 2012 (Prior Year / "vs PY")

#### 1. Executive Performance Cards (High-Level Snapshot)
*   **Total Sales Card:** **$15M** | 🟢 **+164.8% vs. 2012**
    *   *Data Meaning:* Top-line revenue more than doubled compared to 2012, proving massive product adoption and successful territory expansion.
*   **Profit Margin Card:** **40.78%** | 🟢 **+5.6% vs. 2012**
    *   *Data Meaning:* The business didn't just sell more; it became more efficient. A 5.6% jump in margin means profitability outpaced cost scaling.
*   **Total Cost Card:** **$9.16M** | 🔴 **+141.9% vs. 2012**
    *   *Data Meaning:* While costs rose significantly to support expansion, this growth stayed below our revenue growth curve (+164.8%), unlocking positive operating leverage.
*   **Total Customers Card:** **17K** | 🟢 **+426.2% vs. 2012**
    *   *Data Meaning:* Our active buying ecosystem grew more than 5x, expanding the customer footprint massively from 2012's baseline.
*   **Total Orders Card:** **21K** | 🟢 **+551.2% vs. 2012**
    *   *Data Meaning:* Order frequency grew faster than the customer acquisition rate, indicating strong repeat-buying behavior.
*   **Total Quantity Card:** **59K Units** | 🟢 **+311.4% vs. 2012**
    *   *Data Meaning:* High product movement across warehouses, driven primarily by low-ticket accessory items.

#### 2. Deep-Dive Trend Analysis & Strategic Metrics Correlation
*   **Revenue vs. Cost Variance (Scale Efficiency):** Moving into FY 2013, monthly trends showcase strong business performance. Monthly sales built momentum from $0.8M in January up to $1.5M in June. Profitability surged in H2. In December, sales reached a peak of $1.8M while costs were capped at $1.1M, securing an outstanding $1.06M in net profit for a single month, indicating optimized overhead as volume scaled up.
*   **Customer Acquisition vs. Ticket Size:** Total Orders jumped +551.2%, but Total Sales increased by a lower +164.8%. This divergence highlights a structural pivot. In 2012, the business focused on high-ticket, low-volume sales. In 2013, the brand successfully entered high-volume, mainstream consumer channels, anchored by **Tires and Tubes** moving a massive 21,000 units.

#### 3. Demographics & Geographic Market Insights
*   **Demographic Concentrations:** Revenue generation is split evenly down the middle by gender (~$7.6M Male vs. ~$7.7M Female), but the **50 and above age cohort** controls a dominant 71.92% ($11M) of entire global operations.
*   **Segment Value Structure:** New Customers expanded to 13.3K users, contributing $6.9M in sales, which directly validates the massive +426.2% customer growth card. VIP Customers, while representing a small pool of 1,600 users, generated an astounding $5.3M in sales and $2.2M in net profit, proving elite per-capita value.
*   **International Market Performance:** The **United States ($49.26M)** and **Australia ($41.53M)** anchored the global expansion, acting as the primary engines for the revenue jump. Conversely, **Canada ($9.75M)** and **France ($15.04M)** underperformed, showing higher relative operational costs and compressed profit margins.

#### 4. Strategic Recommendations for the Business
*   **Protect and Monetize the VIP Cohort:** Establish a dedicated loyalty and cross-selling framework tailored to the 50+ age demographic to keep lifetime value high.
*   **Optimize Regional Cost Structures:** Conduct a thorough logistics audit to lower supply chain costs in underperforming European regions (Germany and France).
*   **Execute an Attachment Rate Strategy for Accessories:** Leverage the high-demand volume of Tires and Tubes (21K units) by creating automated cross-sell bundles directly into premium Bike sales.

---


### 🏗️ Data Architecture: Medallion Approach



Data flows through three distinct layers within SQL Server:



| Layer | Purpose |

|-------|---------|

| **Bronze (Raw)** | Initial ingestion of source CSVs (Sales, Products, Customers, Geography) with no transformation |

| **Silver (Cleansed)** | Deduplication, null handling, schema enforcement, and data type standardization |

| **Gold (Curated)** | Star Schema fact and dimension tables optimized for Power BI — includes aggregated sales metrics |



---



### 💡 DAX Engineering Highlights



The dashboard's flexibility is powered by a custom `Select Metric` field parameter:



```dax

Select Metric = {

    ("Sales", NAMEOF([Sales (Latest Year)]), 0),

    ("Cost", NAMEOF([Total Cost]), 1),

    ("Profit", NAMEOF([Profit (Latest Year)]), 2),

    ("Customers", NAMEOF([Customers (Latest Year)]), 3),

    ("Orders", NAMEOF([Orders (Latest Year)]), 4),

    ("Quantity", NAMEOF([Total Quantity]), 5)

}

```



**Time Intelligence:** Custom DAX measures automatically lock visuals to the Latest Complete Year (FY 2013) while maintaining YoY growth context — avoiding the common mistake of mixing partial-year data with full-year comparisons.



---



### 🛠️ Tech Stack



| Tool | Usage |

|------|-------|

| Microsoft SQL Server | Database engine and pipeline execution |

| T-SQL | ETL scripting — CTEs, Window Functions, DDL/DML |

| Medallion Architecture | Data Lakehouse-style layering pattern |

| Star Schema | Dimensional modeling for analytics optimization |

| Power BI | Dashboard and DAX engineering |



---



### 📂 Repository Structure



```

├── Reports/                        # Power BI files and dashboard screenshots

│   ├── automobiles_sales_report.pbix

│   └── automobiles_clothing_sales_report.png

├── Sql_data_Warehouse/             # Core data engineering pipeline

│   ├── datasets/                   # Source CSV files

│   ├── docs/                       # Architecture documentation

│   ├── scripts/                    # Bronze → Silver → Gold T-SQL scripts

│   └── tests/                      # SQL unit tests and data quality checks

├── data_analysis/                  # Supplementary analysis

│   ├── docs/                       # Business logic documentation

│   ├── gold_layer-csv-files/       # Exported curated data

│   └── scripts/                    # Ad-hoc analysis scripts

└── README.md

```



---



### ⚙️ How to Run This Project



1. **Environment:** Ensure Microsoft SQL Server is installed and running

2. **Build the Warehouse:** Execute scripts in `Sql_data_Warehouse/scripts/` in sequence — Bronze → Silver → Gold

3. **Open Dashboard:** Launch `Reports/automobiles_sales_report.pbix` in Power BI Desktop

4. **Connect Data Source:** Update Data Source Settings to point to your SQL Server instance

5. **Refresh:** Click Refresh in Power BI to propagate the Medallion data through the model



---



### 📌 What I Learned



- Designing a production-style data warehouse from scratch using industry-standard Medallion Architecture

- Writing advanced T-SQL including Window Functions, CTEs, and stored procedures for ETL automation

- Dimensional modeling (Star Schema) and why it matters for query performance in BI tools

- DAX engineering for dynamic, time-intelligent dashboards in Power BI

- Data quality testing at each pipeline layer before promoting to the next"with this report 



