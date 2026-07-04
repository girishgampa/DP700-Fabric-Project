# Gold Layer

## Overview

The Gold layer represents the business-ready data warehouse built on top of the Silver layer following the Medallion Architecture.

Unlike the Silver layer, where the focus was on data cleaning and transformation, the Gold layer focuses on dimensional modeling by creating Fact and Dimension tables. These tables are optimized for reporting, analytics, and Power BI dashboards.

---

## Objectives

- Build a Star Schema
- Create Dimension tables
- Create Fact tables
- Prepare data for Power BI
- Enable business reporting and KPI generation

---

# Gold Layer Architecture

Silver Layer
      │
      ▼
Dimension Tables
- dim_customer
- dim_product
- dim_seller
- dim_category
- dim_geography
- dim_date

Fact Tables
- fact_sales
- fact_payments
- fact_reviews

      │
      ▼
Power BI

---

# Design Principles

- Gold layer performs business modeling, not data cleaning.
- All cleansing and datatype conversions were completed in the Silver layer.
- Dimension tables store descriptive attributes.
- Fact tables store measurable business events.
- Relationships are implemented using a Star Schema.
