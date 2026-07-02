# Interview Questions

---

## Why should ZIP codes be stored as String?

Leading zeros are preserved only when ZIP codes are stored as String.

---

## Why are IDs stored as String?

IDs are identifiers, not numeric values.

Arithmetic operations are never performed on IDs.

---

## Why convert timestamps in the Silver Layer instead of Bronze?

Bronze stores raw data exactly as received.

Silver is responsible for cleansing and standardization.

---

## Why compare Dates instead of Timestamps when determining On Time deliveries?

Businesses usually define "On Time" based on the delivery date, not the exact delivery time.

A package delivered at 3 PM on the promised day should still be considered On Time.

---

## Why isn't order_item_id the Primary Key?

order_item_id restarts from 1 for every order.

The combination

(order_id, order_item_id)

uniquely identifies each record.

---

## What is a Composite Primary Key?

A Composite Primary Key is formed using multiple columns when no single column uniquely identifies a row.

Example:

(order_id, order_item_id)

---

## Why should price be stored as Decimal?

Money should never be stored as Integer because decimal values would be lost.

Decimal also provides better precision than floating point types.

---

## Why does the dataset not contain a quantity column?

Each purchased item is represented by a separate row.

If a customer purchases three units of the same product, three rows are created instead of storing quantity = 3.
