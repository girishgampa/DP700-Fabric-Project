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

# Gold Layer Tables

## Dimension Tables

Dimension tables provide descriptive attributes used for filtering, grouping, and slicing business metrics in Power BI reports.

---

## 1. dim_customer

The **Customer Dimension** stores customer-related information required for customer segmentation and geographical analysis.

| Column | Description |
|---------|-------------|
| customer_id | Unique customer identifier |
| customer_city | Customer city |
| customer_state | Customer state |

### Business Purpose

- Analyze sales by customer location
- Customer segmentation
- Power BI slicers and filters

---

## 2. dim_product

The **Product Dimension** contains descriptive information about products.

| Column | Description |
|---------|-------------|
| product_id | Unique product identifier |
| product_category_name | Product category |
| product_description_length | Product description length |
| product_photos_qty | Number of product images |
| product_weight_g | Product weight (grams) |
| product_length_cm | Product length (cm) |
| product_height_cm | Product height (cm) |
| product_width_cm | Product width (cm) |

### Business Purpose

- Product analysis
- Product performance reporting
- Revenue by product/category

---

## 3. dim_category

The **Category Dimension** stores English translations for product categories.

| Column | Description |
|---------|-------------|
| product_category_name | Original category name |
| product_category_name_english | English category name |

### Business Purpose

- Improve report readability
- Business-friendly category names

---

## 4. dim_seller

The **Seller Dimension** contains seller information.

| Column | Description |
|---------|-------------|
| seller_id | Unique seller identifier |
| seller_city | Seller city |
| seller_state | Seller state |

### Business Purpose

- Seller performance analysis
- Revenue by seller location

---

## 5. dim_date

The **Date Dimension** supports time intelligence and date-based reporting.

| Column | Description |
|---------|-------------|
| date | Calendar date |
| day | Day of month |
| day_name | Day name |
| week | Week number |
| month | Month number |
| month_name | Month abbreviation |
| quarter | Quarter |
| year | Year |

### Business Purpose

- Monthly revenue analysis
- Time intelligence
- Year-over-Year reporting
- Dashboard filtering

---

# Fact Tables

Fact tables store measurable business transactions used for KPIs and analytical reporting.

---

## 1. fact_sales

The **Sales Fact Table** is the central fact table in the warehouse.

Each record represents **one order item**, making it the primary table for sales analytics.

### Key Columns

| Column | Description |
|---------|-------------|
| order_id | Order identifier |
| order_item_id | Order item number |
| customer_id | Customer identifier |
| product_id | Product identifier |
| seller_id | Seller identifier |
| order_purchase_timestamp | Purchase timestamp |
| order_purchase_date | Purchase date |
| order_status | Original order status |
| delivery_status | Formatted delivery status |
| price | Product price |
| freight_value | Shipping cost |
| total_item_cost | Total item cost (Price + Freight) |
| avg_review_score | Average review score per order |
| review_count | Number of reviews |
| order_approved_at | Approval timestamp |
| order_delivered_carrier_date | Carrier delivery date |
| order_delivered_customer_date | Customer delivery date |
| order_estimated_delivery_date | Estimated delivery date |
| shipping_limit_date | Shipping deadline |

### Business Purpose

- Revenue analysis
- Sales KPIs
- Customer analytics
- Product analytics
- Delivery performance
- Review analysis

---

## 2. fact_payments

The **Payments Fact Table** stores payment transaction information.

> **Design Note**
>
> This table remains independent from `fact_sales` because a single order can contain multiple payment transactions. Connecting both fact tables would introduce a many-to-many relationship, so payment analytics are performed separately.

| Column | Description |
|---------|-------------|
| order_id | Order identifier |
| payment_sequential | Payment sequence |
| payment_type | Payment method |
| payment_installments | Number of installments |
| payment_value | Payment amount |

### Business Purpose

- Payment method distribution
- Installment analysis
- Payment reporting

---

## 3. fact_reviews

The **Reviews Fact Table** stores customer review information.

Although review metrics are aggregated into `fact_sales` for interactive reporting, the original review fact table is retained for detailed review analysis.

| Column | Description |
|---------|-------------|
| review_id | Review identifier |
| order_id | Order identifier |
| review_score | Customer rating |
| review_creation_date | Review creation date |
| review_answer_timestamp | Seller response timestamp |

### Business Purpose

- Customer satisfaction analysis
- Review trends
- Review quality reporting

---

# Star Schema

The Gold layer follows a **Star Schema** optimized for analytical workloads and Power BI reporting.

```text
                    dim_customer
                          │
                    dim_seller
                          │
dim_category ── dim_product ──┐
                              │
                         fact_sales
                              │
                          dim_date

fact_payments (Standalone Fact)

fact_reviews (Source for Review Aggregation)
```

---

# Power BI Integration

The Gold layer serves as the source for the **Microsoft Fabric Semantic Model** and the **Power BI Executive Dashboard**.

Business users can analyze:

- 📈 Revenue trends
- 💰 Sales performance
- 📦 Product category performance
- 👥 Customer insights
- 🏪 Seller performance
- ⭐ Customer reviews
- 🚚 Delivery performance
- 💳 Payment method distribution

---

## Gold Layer Summary

✔️ Business-ready dimensional model

✔️ Star Schema implementation

✔️ Optimized for Microsoft Fabric Semantic Model

✔️ Interactive Power BI reporting

✔️ Supports KPI generation and executive dashboards
