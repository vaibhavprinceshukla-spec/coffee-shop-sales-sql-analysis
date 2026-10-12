# ☕ Coffee Shop Sales Analysis | PostgreSQL

### Advanced SQL Business Analytics Project

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-SQL-blue)
![SQL](https://img.shields.io/badge/SQL-Advanced-green)
![Project](https://img.shields.io/badge/Project-Data%20Analytics-orange)

## 📌 Project Overview

This project analyzes **149,116 coffee shop transaction records** using PostgreSQL to explore sales performance, customer purchasing patterns at the transaction level, product demand, and revenue trends.

The objective is to transform raw transactional data into meaningful business insights through SQL-based exploratory analysis, aggregations, common table expressions (CTEs), subqueries, and window functions.

The analysis covers **25 business questions**, ranging from foundational sales KPIs to advanced time-series and product-ranking analysis.

## 🎯 Business Objectives

The project focuses on answering important business questions:

* How much revenue does the coffee shop generate?
* Which store locations contribute the most revenue?
* What are the best-selling products and categories?
* How does revenue change month over month?
* Which hours and weekdays experience the highest transaction volumes?
* Which products perform best within each category?
* How does each category contribute to overall revenue?
* What are the cumulative sales trends over time?

## 📊 Dataset Information

**Dataset:** Coffee Shop Sales
**Source:** Maven Analytics Data Playground
**Total Records:** 149,116
**Total Columns:** 11
**Database:** PostgreSQL

### Dataset Schema

| Column           | Description                   |
| ---------------- | ----------------------------- |
| transaction_id   | Unique transaction identifier |
| transaction_date | Date of transaction           |
| transaction_time | Time of transaction           |
| transaction_qty  | Number of units purchased     |
| store_id         | Store identifier              |
| store_location   | Store location                |
| product_id       | Product identifier            |
| unit_price       | Price per unit                |
| product_category | Product category              |
| product_type     | Product type                  |
| product_detail   | Product description           |

### Revenue Calculation

Revenue is calculated using:

`Revenue = Transaction Quantity × Unit Price`

The dataset does not contain product costs, so profit and profit margin are outside the scope of this analysis.

## 🛠️ Tools & Technologies

* **PostgreSQL:** Relational database and SQL analysis
* **pgAdmin 4:** Database management and query execution
* **SQL:** Data validation, aggregation, and analytical queries
* **GitHub:** Version control and project documentation

## 🧠 SQL Skills Demonstrated

### Core SQL

* SELECT, WHERE, ORDER BY
* GROUP BY and HAVING
* COUNT, SUM, AVG, MIN, MAX
* DISTINCT
* CASE WHEN
* Date and time functions

### Advanced SQL

* Common Table Expressions (CTEs)
* Nested subqueries
* Window functions
* RANK()
* DENSE_RANK()
* ROW_NUMBER()
* LAG()
* Running totals
* PARTITION BY
* NULLIF()
* Revenue growth calculations

## 📈 Business Analysis

### 1. Sales Performance Analysis

Calculated key sales metrics, including total revenue, transaction volume, quantity sold, and average transaction value.

Compared sales performance across store locations and product categories.

### 2. Product Performance Analysis

Identified top-performing products based on revenue and quantity sold.

Applied SQL ranking functions to identify leading products within individual categories.

### 3. Time-Series Analysis

Analyzed monthly revenue trends and month-over-month revenue growth.

Used the `LAG()` window function to compare current-month performance with the previous month.

Calculated cumulative revenue using `SUM() OVER()`.

### 4. Store Performance Analysis

Compared revenue across store locations.

Identified the highest-revenue products at each store using `ROW_NUMBER()`.

### 5. Customer Purchasing Behavior at the Transaction Level

Analyzed transaction quantities, average transaction value, and purchasing patterns by time of day and day of week.

**Note:** The dataset does not include customer identifiers, so individual customer retention and repeat-customer analysis are not possible.

## 🔍 Featured Advanced SQL Queries

### Month-over-Month Revenue Growth

```sql
WITH monthly_sales AS (
    SELECT
        DATE_TRUNC('month', transaction_date)::DATE AS month,
        SUM(transaction_qty * unit_price) AS revenue
    FROM coffee_sales
    GROUP BY 1
)

SELECT
    month,
    ROUND(revenue, 2) AS revenue,
    ROUND(
        100.0 * (
            revenue - LAG(revenue) OVER (ORDER BY month)
        ) / NULLIF(
            LAG(revenue) OVER (ORDER BY month), 0
        ),
        2
    ) AS mom_growth_percentage
FROM monthly_sales
ORDER BY month;
```

**Business purpose:** Evaluate monthly revenue performance and identify growth or decline trends.

### Top 3 Products Within Each Category

```sql
WITH product_sales AS (
    SELECT
        product_category,
        product_detail,
        SUM(transaction_qty * unit_price) AS revenue
    FROM coffee_sales
    GROUP BY product_category, product_detail
),

ranked_products AS (
    SELECT
        product_category,
        product_detail,
        revenue,
        DENSE_RANK() OVER (
            PARTITION BY product_category
            ORDER BY revenue DESC
        ) AS product_rank
    FROM product_sales
)

SELECT
    product_category,
    product_detail,
    ROUND(revenue, 2) AS revenue,
    product_rank
FROM ranked_products
WHERE product_rank <= 3
ORDER BY product_category, product_rank;
```

**Business purpose:** Identify category-leading products to support inventory and merchandising decisions.

## 💡 Key Business Insights

The analysis is designed to reveal:

* Store locations contributing the highest share of revenue.
* Products and categories driving sales performance.
* Monthly revenue growth patterns.
* Peak transaction hours and weekdays.
* Category-level revenue contribution.
* Top-performing products within each store.

Specific numerical findings can be added after reviewing the final SQL query outputs.

## 📂 Project Structure

```text
coffee-shop-sales-sql-analysis/
│
├── README.md
│
└── sql/
    ├── 01_create_table.sql
    ├── 02_data_validation.sql
    └── 03_business_analysis.sql
```

### SQL Files

**01_create_table.sql**

Creates the PostgreSQL table with appropriate data types.

**02_data_validation.sql**

Performs data-quality checks, including missing values, duplicates, and invalid quantities or prices.

**03_business_analysis.sql**

Contains 25 SQL business-analysis questions covering revenue, product performance, store comparison, and advanced analytical functions.

## 🚀 How to Run This Project

1. Install PostgreSQL and pgAdmin.
2. Create a database named `coffee_shop_sql`.
3. Execute `01_create_table.sql`.
4. Download the Coffee Shop Sales dataset from Maven Analytics.
5. Convert the Excel worksheet to CSV and import it into the `coffee_sales` table using pgAdmin.
6. Execute `02_data_validation.sql` to verify the data.
7. Execute `03_business_analysis.sql` to reproduce the analysis.

## 📚 Key Learnings

Through this project, I strengthened my ability to:

* Translate business questions into SQL queries.
* Validate transactional datasets.
* Calculate and analyze sales KPIs.
* Use CTEs to organize complex queries.
* Apply window functions for ranking and time-series analysis.
* Analyze revenue growth and cumulative performance.
* Present SQL-based business analysis in a structured, reproducible project.

## 📌 Conclusion

This project demonstrates the practical application of PostgreSQL and advanced SQL techniques to transactional retail data.

By combining business-focused analytical questions with CTEs, subqueries, and window functions, the project illustrates how SQL can support performance monitoring and data-driven business decisions.

---

**Project Type:** SQL Data Analytics
**Database:** PostgreSQL
**Focus Areas:** Sales Analytics | Business Intelligence | Advanced SQL | Time-Series Analysis
