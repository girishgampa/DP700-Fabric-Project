[⬅ Back to main project](../README.md)


# Architecture

This folder contains the architectural design and supporting documentation for the **DP700 Microsoft Fabric Analytics Project**.

It explains how data flows through the platform, how the Medallion Architecture is implemented, and how the analytical data model is designed for reporting in Power BI.

## Contents

| File | Description |
|------|-------------|
| **Project_Flow.md** | End-to-end workflow of the project from raw data ingestion to business dashboards. |
| **Medallion_Architecture.md** | Implementation of the Bronze, Silver, and Gold layers using Microsoft Fabric Lakehouse. |
| **Data_Model.md** | Star schema design, fact tables, dimension tables, and table relationships. |
| **ER_Diagram.png** | Entity Relationship Diagram illustrating the analytical data model. |

## Architecture Overview

The project follows a modern analytics architecture using Microsoft Fabric:

```
Raw Data
    │
    ▼
Bronze Layer
    │
    ▼
Silver Layer
    │
    ▼
Gold Layer
    │
    ▼
Semantic Model
    │
    ▼
Power BI Dashboards
```

Each document in this folder focuses on one part of the overall architecture and explains the design decisions behind the implementation.
