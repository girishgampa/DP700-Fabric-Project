# Silver Layer Documentation

## Overview

The Silver Layer is responsible for cleaning, validating, and standardizing the raw Bronze data while preserving business meaning. Each table was analyzed individually before applying transformations.

---

# Silver Layer Progress

| Table | Status |
|--------|--------|
| Customers | ✅ Completed |
| Orders | ✅ Completed |
| Order Items | ✅ Completed |
| Products | ✅ Completed |
| Order Payments | ✅ Completed |
| Reviews | ✅ Completed |
| Sellers | ✅ Completed |
| Categories | ✅ Completed |
| Geolocation | ✅ Completed |

---

# 1. Customers

## Primary Key
- customer_id

## Transformations
- customer_city → Standardized using InitCap()
- customer_zip_code_prefix → Converted from String to Integer
- customer_state → Kept as String (already standardized)

## Validation
- Verified Primary Key uniqueness
- Checked NULL values
- Verified schema after transformation

---

# 2. Orders

## Primary Key
- order_id

## Transformations

Converted date columns from String to Timestamp:

- order_purchase_timestamp
- order_approved_at
- order_delivered_carrier_date
- order_delivered_customer_date
- order_estimated_delivery_date

Created derived columns:

- approval_days
- carrier_pickup_days
- shipping_days
- total_delivery_days

Created delivery_status:

- Early
- Late
- On Time

## Validation

- Verified timestamp conversion
- Investigated NULL values
- Verified delivery calculations
- Checked row count

---

# 3. Order Items

## Composite Primary Key

(order_id, order_item_id)

## Transformations

Converted:

- shipping_limit_date → Timestamp
- price → Decimal(10,2)
- freight_value → Decimal(11,2)

Created:

- total_item_cost = price + freight_value

## Validation

- Verified composite key
- Checked NULL values
- Verified monetary precision
- Verified schema

---

# 4. Products

## Primary Key

product_id

## Transformations

Converted numeric columns to Integer:

- product_name_length
- product_description_length
- product_photos_qty
- product_weight_g
- product_length_cm
- product_height_cm
- product_width_cm

Standardized:

- product_category_name → Replaced "_" with spaces + InitCap()

## Validation

- Verified uniqueness
- Checked NULL values
- Investigated products without category
- Verified schema

---

# 5. Order Payments

## Composite Primary Key

(order_id, payment_sequential)

## Transformations

Converted:

- payment_sequential → Integer
- payment_installments → Integer
- payment_value → Decimal(10,2)

Standardized:

- payment_type
- Replaced "_" with spaces
- Applied InitCap()

Examples:

credit_card → Credit Card

debit_card → Debit Card

## Validation

- Verified composite key
- Checked NULL values
- Verified payment values
- Verified schema

---

# 6. Reviews

## Business Investigation

Initially assumed:

review_id

was the Primary Key.

Investigation revealed:

- review_id is NOT unique
- One review_id may relate to multiple order_id values
- Duplicate review_id values represent valid business relationships
- No deduplication was performed

## Transformations

Converted:

- review_score → Integer
- review_creation_date → Timestamp
- review_answer_timestamp → Timestamp

Kept unchanged:

- review_comment_title
- review_comment_message

NULL review comments were preserved because customers are not required to leave written feedback.

## Validation

Investigated:

- Duplicate review IDs
- Duplicate rows
- Unique Orders
- Unique Reviews

Final Decision:

No records removed.

---

# 7. Sellers

## Primary Key

seller_id

## Transformations

Converted:

- seller_zip_code_prefix → Integer

Standardized:

- seller_city → InitCap()

Preserved:

- seller_state

## Validation

- Verified uniqueness
- Checked NULL values
- Verified schema

---

# 8. Categories

## Business Key

product_category_name

## Transformations

Both columns:

- Replaced "_" with spaces
- Applied InitCap()

Examples:

beleza_saude

↓

Beleza Saude

health_beauty

↓

Health Beauty

## Validation

- Verified uniqueness
- Checked NULL values

---

# 9. Geolocation

## Business Key

geolocation_zip_code_prefix

## Transformations

Converted:

- geolocation_zip_code_prefix → Integer
- geolocation_lat → Double
- geolocation_lng → Double

Standardized:

- geolocation_city → InitCap()

Preserved:

- geolocation_state

## Validation

- Verified schema
- Checked NULL values

---

# General Validation Performed

Every Silver table followed the same validation process:

✔ Verified Primary/Business Key

✔ Checked Duplicate Records

✔ Checked NULL Values

✔ Converted Correct Data Types

✔ Standardized Text Columns

✔ Verified Schema

✔ Verified Row Counts

✔ Saved as Delta Tables

---

# Data Engineering Lessons Learned

## 1. Never Assume Primary Keys

Always validate uniqueness before deciding a Primary Key.

---

## 2. Understand Business Meaning Before Cleaning Data

Not every duplicate is a bad record.

Example:

Review IDs were intentionally linked to multiple Orders.

---

## 3. Financial Columns Should Use Decimal

Money values should never use Float or Double because of precision issues.

---

## 4. Free Text Should Not Be Standardized

Customer comments were preserved exactly as entered.

---

## 5. Controlled Business Values Should Be Standardized

Examples:

Cities

Categories

Payment Types

---

## 6. Preserve Business Meaning

The Silver Layer improves data quality without changing business logic.

---

# Silver Layer Completed

```
Bronze
   │
   ▼
Silver ✅
   │
   ▼
Gold (Next Phase)
```

The Silver Layer now provides clean, validated, and analytics-ready data that will be used to build Gold Layer business models and Power BI reports.
