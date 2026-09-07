# ceo_360_dashboard
CEO-level executive dashboard built with SQL (MySQL) and Power BI — tracks revenue, cost, profit, growth trends, and regional/product performance for data-driven business decisions.
# CEO Business 360 Dashboard

## Problem Statement

Leadership at growing SMEs and startups typically tracks revenue, cost, and profit 
across scattered Excel sheets and disconnected reports, with no single, unified view 
of business health. Without consolidated visibility into growth trends, margin 
performance, or regional/product-level drivers, strategic decisions on pricing, cost 
control, and market focus are often made reactively — based on gut feeling rather 
than data.

Leadership can't answer a basic question — "are we growing, where, and why" — in 
under 5 minutes. Delayed visibility into cost spikes or margin erosion means problems 
are caught late, after they've already impacted profitability.

## Solution

A CEO Business 360 Dashboard built on a structured SQL data model (star schema) and 
visualized in Power BI, consolidating financial and operational data into a single 
decision-intelligence system. It surfaces revenue, cost, and profit trends, YoY/MoM 
growth, regional and product-level performance, and customer insights.

## Dashboard Structure

**Page 1 — Executive Overview**
- KPI cards: Total Revenue, Total Profit, Total Cost, Total Transactions
- Monthly revenue trend
- MoM growth % trend
- Top insights panel

**Page 2 — Financial Analysis**
- Gross margin % trend by quarter (surfaces a real Q3 2024 cost spike)
- Profit by product category
- Category-level financial summary table

**Page 3 — Sales Performance**
- Revenue by region
- Top 10 customers by revenue
- Region × category revenue matrix (drill-down view)

## Dataset

Synthetic dataset generated in Python — 12,466 transactions across 3 years (2023–2025), 
with realistic trend, seasonality, and margin patterns built in intentionally (including 
a Q3 2024 cost-spike anomaly used to validate the analysis).

**Schema (star schema, 5 tables):**
- `fact_sales` — transactions (revenue, cost, profit, quantity)
- `dim_date`, `dim_product`, `dim_region`, `dim_customer`

## Tech Stack

Python (Pandas, Faker) · MySQL · SQL (CTEs, Window Functions) · Power BI · DAX

## Key SQL Techniques

- Window functions: `LAG()`, `RANK()` for YoY/MoM growth and regional ranking
- CTEs for multi-step aggregation
- Cohort analysis for customer retention
- Running totals and quarterly margin analysis

## Key DAX Measures

- Time intelligence: `SAMEPERIODLASTYEAR`, `DATEADD` for YoY/MoM growth
- Calculated columns for chronological quarter sorting
- Gross margin %, revenue per customer, running totals

## Key Insight

Gross margin dropped sharply in Q3 2024 (26% → 16%) due to a cost spike, fully 
recovering by Q4 — identified directly through SQL and DAX analysis, not assumed.

## Repository Structure

\```
ceo-business-360-dashboard/
├── README.md
├── data/                          # Source CSVs (5-table star schema)
├── sql/
│   ├── 01_create_tables.sql
│   ├── 02_load_data.sql
│   └── 03_business_queries.sql    # 11 queries, commented
├── scripts/
│   └── generate_dataset.py
└── dashboard/
    └── CEO_Business_360_Dashboard.pbix
\```

## Status

✅ Complete — SQL data model, business queries, and full 3-page Power BI dashboard.
