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



### 🔍 Key Business Insights



After building the pipeline and analyzing the Gold layer data, here are the findings:



1. **The 50+ age group is the dominant revenue driver**, contributing the highest share of total sales — suggesting marketing spend should prioritize this demographic over younger segments.

2. **Profit margin holds consistently above 40%** across both product categories, indicating healthy pricing strategy and low cost leakage in the supply chain.

3. **Q4 shows the strongest sales spike** in the 2013 monthly trend, pointing to seasonal demand that can be leveraged for inventory and campaign planning.

4. **VIP customers, while fewer in number, generate disproportionately higher revenue per order** — a clear signal for a loyalty retention program.

5. **Clothing outperforms Automobiles in order volume** but lags in revenue per order, highlighting a cross-sell opportunity for premium product lines.



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



