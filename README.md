# ☕ Coffee Shop Sales Analysis | PostgreSQL

### Advanced SQL Business Analytics Project

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-Advanced-green?style=for-the-badge)
![Data Analytics](https://img.shields.io/badge/Data-Analytics-orange?style=for-the-badge)

---

## 📌 Project Overview

This project analyzes **149,116 coffee shop transaction records** using PostgreSQL to evaluate overall sales performance, store-level revenue, product demand, and monthly sales trends.

The objective is to transform transactional data into meaningful business insights through SQL-based analysis.

The project includes **25 business-focused SQL queries**, covering aggregations, subqueries, Common Table Expressions (CTEs), window functions, ranking, and time-series analysis.

The analysis focuses on identifying key revenue drivers, evaluating store performance, understanding product demand, and measuring business growth.

### Project Highlights

- Analyzed **149,116 transaction records**
- Evaluated **$698,812.33 in total revenue**
- Compared performance across **3 store locations**
- Analyzed **9 product categories**
- Developed **25 SQL business analysis queries**
- Applied advanced SQL techniques including CTEs and window functions
- Identified revenue growth, product performance, and store-level insights

---

## 🎯 Business Objectives

The project addresses the following business questions:

1. What is the total revenue generated?
2. How many transactions and product units were recorded?
3. Which store generates the highest revenue?
4. Which store achieves the highest average transaction value?
5. Which product categories contribute the most revenue?
6. What are the best-selling products?
7. How does revenue change month over month?
8. Which month recorded the highest revenue?
9. Which hours and weekdays experience the highest transaction volumes?
10. How can advanced SQL techniques support business performance analysis?

---

## 📊 Dataset Information

| Attribute | Details |
|---|---|
| Dataset | Coffee Shop Sales |
| Source | Maven Analytics Data Playground |
| Database | PostgreSQL |
| Records | 149,116 |
| Columns | 11 |
| Time Period | January–June 2023 |
| Store Locations | 3 |
| Product Categories | 9 |

### Dataset Schema

| Column | Data Type | Description |
|---|---|---|
| transaction_id | INTEGER | Unique transaction identifier |
| transaction_date | DATE | Date of transaction |
| transaction_time | TIME | Time of transaction |
| transaction_qty | INTEGER | Quantity purchased |
| store_id | INTEGER | Store identifier |
| store_location | VARCHAR | Store location |
| product_id | INTEGER | Product identifier |
| unit_price | NUMERIC | Price per unit |
| product_category | VARCHAR | Product category |
| product_type | VARCHAR | Product type |
| product_detail | VARCHAR | Product description |

### Revenue Calculation

Revenue is calculated using:

```sql
SELECT
    SUM(transaction_qty * unit_price) AS total_revenue
FROM coffee_sales;
```

**Note:** The dataset does not contain product cost information, so profit and profit margin analysis are outside the scope of this project.

---

## 🛠️ Tools & Technologies

| Technology | Purpose |
|---|---|
| PostgreSQL | Relational database and analytical queries |
| pgAdmin 4 | Database management and SQL execution |
| SQL | Data validation and business analysis |
| GitHub | Version control and project documentation |

---

## 🧠 SQL Skills Demonstrated

### Core SQL

- SELECT, WHERE, ORDER BY
- GROUP BY and HAVING
- COUNT, SUM, AVG, MIN, MAX
- DISTINCT
- CASE WHEN
- Date and time functions
- Aggregate functions

### Advanced SQL

- Common Table Expressions (CTEs)
- Subqueries
- Window Functions
- RANK()
- DENSE_RANK()
- ROW_NUMBER()
- LAG()
- PARTITION BY
- Running Totals
- Cumulative Revenue
- Month-over-Month Growth
- NULLIF()
- Revenue Contribution Analysis

---

# 📈 Business Analysis & Key Insights

## 1. Overall Sales Performance

The first stage of the analysis focused on calculating key business performance indicators.

### Key Performance Indicators

| KPI | Result |
|---|---:|
| Total Transactions | 149,116 |
| Total Units Sold | 214,470 |
| Total Revenue | $698,812.33 |
| Average Transaction Value | $4.69 |
| Average Units per Transaction | 1.44 |

### Key Findings

- The coffee shop generated approximately **$698.8K in total revenue**.
- A total of **214,470 units** were sold across **149,116 transactions**.
- The average transaction generated approximately **$4.69 in revenue**.
- The average number of units sold per transaction was **1.44**.

### Business Interpretation

The average transaction value provides a baseline for evaluating sales performance across different locations.

Increasing transaction volume or average transaction value could contribute to future revenue growth.

### 📸 SQL Output

![Overall Sales KPIs](screenshots/01_sales_kpis.png)

---

## 2. Store Performance Analysis

The second stage compared revenue, transaction volume, and units sold across three coffee shop locations.

### Store Revenue Comparison

| Store Location | Transactions | Units Sold | Revenue | Average Transaction Value |
|---|---:|---:|---:|---:|
| Hell's Kitchen | 50,735 | 71,737 | $236,511.17 | $4.66 |
| Astoria | 50,599 | 70,991 | $232,243.91 | $4.59 |
| Lower Manhattan | 47,782 | 71,742 | $230,057.25 | $4.81 |

### Key Findings

**Hell's Kitchen generated the highest revenue.**

- Total Revenue: **$236,511.17**
- Revenue Contribution: **33.85%**
- Total Transactions: **50,735**

**Lower Manhattan achieved the highest average transaction value.**

- Average Transaction Value: **$4.81**
- Total Revenue: **$230,057.25**

Despite recording fewer transactions than the other locations, Lower Manhattan generated the highest revenue per transaction.

### Revenue Contribution by Store

| Store | Revenue Contribution |
|---|---:|
| Hell's Kitchen | 33.85% |
| Astoria | 33.23% |
| Lower Manhattan | 32.92% |

### Business Recommendations

- Investigate the product mix contributing to Hell's Kitchen's strong revenue performance.
- Analyze why Lower Manhattan achieves a higher average transaction value.
- Compare product demand across locations to identify opportunities for improving sales.
- Use store-level sales trends to support inventory and staffing decisions.

### 📸 SQL Output

![Store Performance](screenshots/02_store_performance.png)

---

## 3. Product Category Performance Analysis

The third stage identified the categories contributing the most revenue.

### Revenue by Product Category

| Product Category | Units Sold | Total Revenue | Revenue Contribution |
|---|---:|---:|---:|
| Coffee | 89,250 | $269,952.45 | 38.63% |
| Tea | 69,737 | $196,405.95 | 28.11% |
| Bakery | 23,214 | $82,315.64 | 11.78% |
| Drinking Chocolate | 17,457 | $72,416.00 | 10.36% |
| Coffee Beans | 1,828 | $40,085.25 | 5.74% |
| Branded | 776 | $13,607.00 | 1.95% |
| Loose Tea | 1,210 | $11,213.60 | 1.60% |
| Flavours | 10,511 | $8,408.80 | 1.20% |
| Packaged Chocolate | 487 | $4,407.64 | 0.63% |

### Key Findings

**Coffee was the highest-revenue category.**

Coffee generated **$269,952.45**, contributing **38.63% of total revenue**.

**Coffee and Tea dominated overall sales.**

Combined revenue:

**$466,358.40**

Combined revenue contribution:

**66.74%**

Approximately two-thirds of total revenue came from Coffee and Tea.

**Bakery was the third-largest revenue category.**

Bakery generated **$82,315.64**, representing **11.78% of total revenue**.

**Coffee Beans generated relatively high revenue per unit.**

Coffee Beans generated **$40,085.25** from **1,828 units sold**, representing approximately **$21.93 per unit**.

### Business Recommendations

- Prioritize inventory availability for Coffee and Tea.
- Explore opportunities to promote bakery products alongside beverages.
- Evaluate Coffee Beans as a higher-priced product category.
- Review lower-revenue categories to identify opportunities for improving performance.

### 📸 SQL Output

![Product Category Analysis](screenshots/03_category_analysis.png)

---

## 4. Monthly Revenue Growth Analysis

The fourth stage evaluated monthly revenue trends and month-over-month growth from January to June 2023.

### Monthly Sales Performance

| Month | Transactions | Units Sold | Revenue | MoM Growth |
|---|---:|---:|---:|---:|
| January 2023 | 17,314 | 24,870 | $81,677.74 | — |
| February 2023 | 16,359 | 23,550 | $76,145.19 | -6.77% |
| March 2023 | 21,229 | 30,406 | $98,834.68 | +29.80% |
| April 2023 | 25,335 | 36,469 | $118,941.08 | +20.34% |
| May 2023 | 33,527 | 48,233 | $156,727.76 | +31.77% |
| June 2023 | 35,352 | 50,942 | $166,485.88 | +6.23% |

### Key Findings

**June recorded the highest monthly revenue.**

- Revenue: **$166,485.88**
- Transactions: **35,352**
- Units Sold: **50,942**

**May recorded the highest month-over-month growth.**

May revenue increased by **31.77%** compared with April.

**February experienced a revenue decline.**

Revenue declined by **6.77%** compared with January.

**Revenue more than doubled between January and June.**

January Revenue: **$81,677.74**

June Revenue: **$166,485.88**

Overall Increase: **Approximately 103.83%**

**Transaction volume also increased significantly.**

Transactions increased from **17,314 in January** to **35,352 in June**, representing approximately **104.18% growth**.

### Business Recommendations

- Investigate the factors contributing to strong revenue growth during March, April, and May.
- Examine February's performance using daily sales averages.
- Evaluate staffing requirements during periods of increasing transaction volume.
- Monitor transaction volume and average transaction value to understand revenue growth drivers.

### 📸 SQL Output

![Monthly Revenue Growth](screenshots/04_monthly_growth.png)

---

# 🔍 Advanced SQL Analysis

In addition to the four major business analyses, the project includes advanced SQL techniques for product ranking and cumulative revenue analysis.

## 5. Top 3 Products per Category Using DENSE_RANK()

This analysis identifies the highest-revenue products within each product category.

### SQL Techniques

- Common Table Expressions (CTEs)
- DENSE_RANK()
- PARTITION BY
- Aggregate functions
- Product-level revenue calculations

### Business Purpose

Identifying top-performing products within each category can support inventory planning, product assortment decisions, and targeted promotions.

### 📸 SQL Output

![Top Products Ranking](screenshots/05_top_products_ranking.png)

---

## 6. Cumulative Monthly Revenue Analysis

This analysis calculates the running total of revenue over the six-month period.

### SQL Techniques

- Common Table Expressions (CTEs)
- SUM() OVER()
- ORDER BY
- ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
- Date aggregation

### Business Purpose

Cumulative revenue analysis helps track overall business growth and monitor revenue performance over time.

The final cumulative revenue reached **$698,812.33** in June 2023.

### 📸 SQL Output

![Cumulative Revenue](screenshots/06_cumulative_revenue.png)

---

# 📂 Project Structure

```text
coffee-shop-sales-sql-analysis/
│
├── README.md
│
├── sql/
│   ├── 01_create_table.sql
│   ├── 02_data_validation.sql
│   └── 03_business_analysis.sql
│
└── screenshots/
    ├── 01_sales_kpis.png
    ├── 02_store_performance.png
    ├── 03_category_analysis.png
    ├── 04_monthly_growth.png
    ├── 05_top_products_ranking.png
    └── 06_cumulative_revenue.png
```

### SQL Files

**01_create_table.sql**

Contains the PostgreSQL table schema and data type definitions.

**02_data_validation.sql**

Contains data-quality checks for:

- Total records
- Missing values
- Duplicate transaction IDs
- Transaction date range
- Invalid quantities and prices

**03_business_analysis.sql**

Contains 25 SQL business-analysis questions covering:

- Revenue Analysis
- Store Performance
- Product Performance
- Category Analysis
- Time-Series Analysis
- CTEs and Subqueries
- Window Functions
- Ranking
- Cumulative Revenue
- Month-over-Month Growth

---

# 🚀 How to Run This Project

### Step 1: Create a PostgreSQL Database

```sql
CREATE DATABASE coffee_shop_sql;
```

Connect to the new database.

### Step 2: Create the Table

Execute:

```text
sql/01_create_table.sql
```

### Step 3: Import the Dataset

Download the Coffee Shop Sales dataset from Maven Analytics Data Playground.

Convert the Excel file to CSV format.

Import the CSV into PostgreSQL using pgAdmin's Import/Export feature.

### Step 4: Validate the Dataset

Execute:

```text
sql/02_data_validation.sql
```

Verify that the dataset contains **149,116 records**.

### Step 5: Run the Business Analysis

Execute:

```text
sql/03_business_analysis.sql
```

Review the results of all 25 SQL queries.

---

# 💡 Overall Business Findings

| Business Area | Key Finding |
|---|---|
| Overall Revenue | $698,812.33 |
| Total Transactions | 149,116 |
| Total Units Sold | 214,470 |
| Average Transaction Value | $4.69 |
| Highest-Revenue Store | Hell's Kitchen |
| Highest Store Revenue | $236,511.17 |
| Highest Average Transaction Value | Lower Manhattan ($4.81) |
| Top Product Category | Coffee |
| Coffee Revenue Contribution | 38.63% |
| Coffee + Tea Revenue Contribution | 66.74% |
| Highest-Revenue Month | June 2023 |
| Highest Monthly Revenue | $166,485.88 |
| Highest Monthly Growth | May 2023 (+31.77%) |
| January-to-June Revenue Growth | Approximately 103.83% |

---

# 📚 Key Learnings

Through this project, I strengthened my ability to:

- Translate business requirements into SQL queries.
- Perform data validation and exploratory analysis.
- Calculate business KPIs using SQL.
- Analyze store-level and product-level performance.
- Apply CTEs to organize complex SQL logic.
- Use window functions for ranking and time-series analysis.
- Calculate month-over-month growth and cumulative revenue.
- Interpret analytical results and develop business recommendations.
- Document SQL projects for reproducibility and portfolio presentation.

---

# 🎯 Conclusion

This project demonstrates the practical application of PostgreSQL and advanced SQL techniques to analyze transactional retail data.

The analysis identified approximately **$698.8K in total revenue**, with Coffee and Tea contributing **66.74% of sales**.

Hell's Kitchen was the highest-revenue store, while Lower Manhattan achieved the highest average transaction value.

Monthly revenue increased approximately **103.83% between January and June 2023**, highlighting significant growth in sales activity during the observed period.

By combining business-focused SQL queries with CTEs, subqueries, window functions, and time-series analysis, this project demonstrates how transactional data can be transformed into meaningful business insights.

---

## 👨‍💻 Project Information

**Project:** Coffee Shop Sales Analysis  
**Role:** Data Analyst  
**Database:** PostgreSQL  
**Tools:** PostgreSQL, pgAdmin 4, SQL, GitHub  
**Analysis Type:** Sales Analytics & Business Intelligence  
**SQL Queries:** 25 Business Analysis Questions  

### Core Skills

`PostgreSQL` `SQL` `CTEs` `Window Functions` `Subqueries` `Data Analysis` `Business Intelligence` `Sales Analytics` `Time-Series Analysis` `Data Validation`

---

⭐ If you found this project useful, consider starring the repository.
