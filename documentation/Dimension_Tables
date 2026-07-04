# Dimension Tables

## dim_customer

Purpose:
Stores customer information used for customer segmentation and geographical analysis.

Grain:
One row per customer.

Primary Key:
customer_id

Columns

- customer_id
- customer_unique_id
- customer_zip_code_prefix
- customer_city
- customer_state

Business Questions

- Customers by State
- Customers by City
- Repeat Customers

---

## dim_product

Purpose:
Stores descriptive information about products.

Grain:
One row per product.

Primary Key:
product_id

Columns

- product_id
- product_category_name
- product_name_lenght
- product_description_lenght
- product_photos_qty
- product_weight_g
- product_length_cm
- product_height_cm
- product_width_cm

Business Questions

- Top Selling Products
- Revenue by Category
- Product Size Analysis
- Product Weight Analysis

---

## dim_seller

Purpose:
Stores seller information.

Grain:
One row per seller.

Primary Key

seller_id

Columns

- seller_id
- seller_zip_code_prefix
- seller_city
- seller_state

Business Questions

- Top Sellers
- Revenue by Seller
- Sellers by State

---

## dim_category

Purpose

Maps Portuguese product categories to English.

Grain

One row per category.

Primary Key

product_category_name

Columns

- product_category_name
- product_category_name_english

---

## dim_geography

Purpose

Stores geographical information.

Grain

One row per geographical location.

Columns

- geolocation_zip_code_prefix
- geolocation_city
- geolocation_state
- geolocation_lat
- geolocation_lng

Business Questions

- Sales by State
- Sales by City
- Customer Distribution

---

## dim_date

Purpose

Provides calendar attributes for time intelligence.

Columns

- Date
- Day
- Month
- Month Name
- Quarter
- Year
- Week
- Day Name

Business Questions

- Monthly Sales
- Quarterly Sales
- Yearly Trends
