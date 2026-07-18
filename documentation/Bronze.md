# Bronze Layer

## Overview

The Bronze layer is the first stage of the Medallion Architecture, responsible for ingesting and storing raw data in Microsoft Fabric Lakehouse.

At this stage, the source data is loaded without applying business rules, transformations, or calculations. The goal is to preserve the original dataset and create a reliable foundation for downstream processing in the Silver layer.

---

## Objectives

- Load raw CSV files into Microsoft Fabric Lakehouse
- Preserve the original source data
- Create Bronze Delta tables
- Validate successful data ingestion
- Provide input for the Silver layer

---

## Source Dataset

The project uses the **Brazilian E-Commerce Public Dataset by Olist**, containing customer, order, product, seller, payment, review, and geolocation data.

---

## Bronze Tables

The following raw tables were created in the Bronze layer:

| Table | Description |
|--------|-------------|
| customers | Customer information |
| geolocation | Geographic information |
| order_items | Order item details |
| order_payments | Payment information |
| order_reviews | Customer reviews |
| orders | Order details |
| products | Product information |
| sellers | Seller information |
| product_category_translation | Product category translations |

---

## Processing Performed

The Bronze layer performs minimal processing:

- Read CSV files using PySpark
- Infer and validate schema
- Load data into Delta tables
- Verify record counts

No business transformations, data cleansing, or derived columns are created in this layer.

---

## Output

The Bronze layer provides raw Delta tables that serve as the source for all transformations performed in the Silver layer.

---

## Bronze Layer Summary

- Raw data successfully ingested into Microsoft Fabric
- Original data preserved without modifications
- Bronze Delta tables created
- Foundation established for Silver layer transformations
