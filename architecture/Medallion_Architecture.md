[⬅ Back to Architecture](README.md) | [🏠 Main Project](../README.md)


# Medallion Architecture

## Overview

This project implements the **Medallion Architecture** in Microsoft Fabric to organize data into progressive layers of quality and refinement.

The Medallion Architecture separates raw, cleansed, and business-ready data into three logical layers:

- **Bronze** – Raw data ingestion
- **Silver** – Cleaned and standardized data
- **Gold** – Business-ready analytical model

This layered approach improves data quality, simplifies maintenance, and provides a scalable foundation for analytics and reporting.

---

## Architecture Flow

```
                    Raw CSV Files
                          │
                          ▼
                 Bronze Lakehouse Layer
              (Raw Delta Tables - No Changes)
                          │
                          ▼
                Silver Lakehouse Layer
         (Cleaned & Standardized Delta Tables)
                          │
                          ▼
                 Gold Lakehouse Layer
         (Fact & Dimension Tables - Star Schema)
                          │
                          ▼
                  Semantic Model
                          │
                          ▼
                Power BI Dashboards
```

---

## Bronze Layer

The Bronze layer stores the raw source data exactly as received.

### Purpose

- Preserve original source data
- Enable data traceability
- Support reprocessing if required
- Maintain historical records

### Characteristics

- Raw CSV ingestion
- Delta Tables
- Source of truth

---

## Silver Layer

The Silver layer prepares the data for analytical processing.

### Purpose

- Improve data quality
- Standardize datasets
- Remove inconsistencies
- Prepare reusable datasets

### Transformations

- Data type conversions
- Column standardization
- Duplicate handling
- Null value handling
- Derived columns

---

## Gold Layer

The Gold layer contains business-ready data optimized for reporting.

### Purpose

- Support business analytics
- Build dimensional models
- Improve query performance
- Simplify Power BI reporting

### Components

- Fact Tables
- Dimension Tables
- Business Metrics
- Star Schema

---

## Benefits of Using Medallion Architecture

### Improved Data Quality

Each layer progressively improves the quality and reliability of the data.

### Scalability

The architecture supports adding new datasets and business requirements without redesigning the pipeline.

### Reusability

Clean Silver tables and Gold models can be reused across multiple reports and analytical workloads.

### Better Performance

Business users access optimized Gold tables instead of querying raw transactional data.

### Simplified Maintenance

Separating ingestion, transformation, and business modeling makes debugging and enhancements easier.

---

## Technologies Used

| Layer | Technology |
|--------|------------|
| Bronze | Microsoft Fabric Lakehouse |
| Silver | PySpark |
| Gold | PySpark + Delta Tables |
| Semantic Model | Power BI |
| Reporting | Power BI Dashboards |

---

## Related Documentation

- `documentation/Bronze.md`
- `documentation/Silver.md`
- `documentation/Gold.md`
- `architecture/Data_Model.md`
