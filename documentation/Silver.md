# Silver Layer Documentation

## Purpose

The Silver layer stores cleansed, standardized, and validated data from the Bronze layer. It prepares raw data for business analysis by applying data quality checks, standardization, and business transformations.

---

# Customers

## Business Purpose

Stores cleaned customer information used for customer analytics and reporting.

## Source

Bronze → customers

## Primary Key

customer_id

## Transformations

- Preserved customer_id as String.
- Preserved customer_zip_code_prefix as String to avoid losing leading zeros.
- Standardized customer_city using InitCap().
- Retained customer_state as String.

## Validation

- Verified customer_id uniqueness.
- Verified row count remained unchanged.
- Verified schema after transformation.
- Checked city names after applying InitCap().

## Business Questions Supported

- Customers by City
- Customers by State
- Customer Distribution
- Regional Customer Analysis

## Lessons Learned

- ZIP codes should always be stored as String.
- IDs should never be converted into numeric values.
- Standardized city names improve reporting consistency.

---

# Orders

## Business Purpose

Stores cleaned order information used for logistics, delivery and SLA reporting.

## Source

Bronze → orders

## Primary Key

order_id

## Transformations

Converted the following columns from String to Timestamp:

- order_purchase_timestamp
- order_approved_at
- order_delivered_carrier_date
- order_delivered_customer_date
- order_estimated_delivery_date

Created new business columns:

- approval_days
- carrier_pickup_days
- shipping_days
- total_delivery_days
- delivery_status

Delivery Status Logic

- Early
- On Time
- Late

Initially, delivery_status compared complete timestamps.

Later the logic was improved to compare only the date portion using to_date(), since businesses usually consider deliveries made on the promised date as "On Time" regardless of the delivery time.

## Validation

- Verified timestamp conversion.
- Checked for NULL timestamps.
- Verified row count remained unchanged.
- Verified delivery status counts.

Final Delivery Status Distribution

- Early : 88,649
- On Time : 1,292
- Late : 9,500

Verified

- No duplicate order IDs.
- Delivery calculations produced expected results.
- Business KPIs were successfully created.

## Business Questions Supported

- Average Approval Time
- Average Delivery Time
- Warehouse Processing Time
- Shipping Time
- Late Delivery Percentage
- On Time Delivery Percentage

## Lessons Learned

- Never assume timestamp formats.
- Always inspect sample data before parsing timestamps.
- NULL values are not always bad data.
- Compare Dates instead of Timestamps when implementing SLA reporting.
- Silver Layer should contain business-ready columns rather than raw operational fields.

---

# Order Items

## Business Purpose

Stores every individual product purchased in an order.

Acts as the Fact Table connecting:

- Orders
- Products
- Sellers

## Source

Bronze → order_items

## Composite Primary Key

(order_id, order_item_id)

## Foreign Keys

- order_id
- product_id
- seller_id

## Planned Transformations

- Convert shipping_limit_date → Timestamp
- Convert price → Decimal(10,2)
- Convert freight_value → Decimal(10,2)
- Create total_item_cost

## Business Questions Supported

- Revenue by Product
- Revenue by Seller
- Freight Cost Analysis
- Total Sales
- Product Sales Performance

## Data Investigation

While exploring the dataset we discovered:

order_item_id has:

Maximum Value = 21

Distinct Values = 21

This proves:

- order_item_id is NOT globally unique.
- order_item_id restarts from 1 for every order.
- (order_id + order_item_id) forms a Composite Primary Key.

Further investigation revealed:

Example:

order_id = cfe9a2c324eefb180663116644e4f171

contained

order_item_id

1
2
3

with the SAME

- product_id
- seller_id
- price
- freight_value

This strongly suggests that the dataset represents multiple quantities of the same product by creating multiple rows instead of maintaining a quantity column.

Each row therefore represents ONE purchased item.

The dataset does not contain a quantity field.

## Lessons Learned

- Composite Primary Keys are common in transactional databases.
- Every row represents one purchased item.
- Quantity is represented using multiple rows instead of a quantity column.
- Revenue calculations should sum the price column rather than multiplying by quantity.
- Money columns should be stored as Decimal instead of Integer to preserve precision.

