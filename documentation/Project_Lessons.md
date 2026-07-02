# Project Lessons

## Lesson 1

Never assume the datatype of a column.

Always inspect:

- Schema
- Sample Data
- NULL values

before performing transformations.

---

## Lesson 2

Business understanding is more important than writing Spark code.

Before transforming any table ask:

- What does this table represent?
- What business process generated this data?
- What questions should this table answer?

---

## Lesson 3

Always validate every transformation.

Workflow:

Read
↓

Transform
↓

Validate
↓

Document
↓

Commit

---

## Lesson 4

NULL values do not always indicate bad data.

Sometimes NULL represents business reality.

Example:

Undelivered orders

still have

NULL delivery dates.

---

## Lesson 5

Understand the data model before writing code.

The Order Items table taught us:

- Composite Keys
- Fact Tables
- One row per purchased item
- Quantity represented using multiple rows

---

## Lesson 6

Always investigate unusual data instead of making assumptions.

Example:

Repeated product_id values

Instead of assuming duplicates, investigate the business meaning.

This led us to understand how quantities are stored in this dataset.


## Mistakes I Made

### Customers

- Used df instead of customers_df.

Lesson:
Always use descriptive DataFrame names.

---

### Orders

- Forgot notebook variables disappear after restarting Spark.

Lesson:
Always rebuild DataFrames from Delta tables.

---

### Orders

- Used incorrect timestamp format.

Lesson:
Always inspect sample data before parsing timestamps.

---

### Orders

- Compared timestamps instead of dates.

Lesson:
Business rules are often different from technical implementations.
