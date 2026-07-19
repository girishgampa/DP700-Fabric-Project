# 🚀 End-to-End Microsoft Fabric Data Engineering Project
![Microsoft Fabric](https://img.shields.io/badge/Microsoft%20Fabric-Data%20Engineering-0078D4?logo=microsoftazure&logoColor=white)
![PySpark](https://img.shields.io/badge/PySpark-Data%20Processing-E25A1C?logo=apachespark&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboards-F2C811?logo=powerbi&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-green)

> An end-to-end Data Engineering solution built using **Microsoft Fabric**, **PySpark**, **Delta Lake**, **Medallion Architecture**, **Semantic Models**, and **Power BI** to transform raw e-commerce data into business-ready analytics.

---

## 📌 Project Overview

This project demonstrates the implementation of a modern data engineering pipeline using **Microsoft Fabric** and the **Medallion Architecture (Bronze → Silver → Gold)**.

Starting from raw CSV files, the project ingests, transforms, and models data into a Star Schema before building a Semantic Model and interactive Power BI dashboards for business reporting.

The solution follows industry best practices for data ingestion, transformation, dimensional modeling, and analytics.

---

## 🏗️ Architecture

![Architecture](screenshots/Architecture.png)

### Data Flow

```text
Raw CSV Files
      │
      ▼
Bronze Layer
(Raw Delta Tables)
      │
      ▼
Silver Layer
(Data Cleaning & Transformation)
      │
      ▼
Gold Layer
(Fact & Dimension Tables)
      │
      ▼
Semantic Model
      │
      ▼
Power BI Dashboards
```

---

# 🛠️ Technology Stack

| Category | Technologies |
|-----------|-------------|
| Cloud Platform | Microsoft Fabric |
| Data Processing | PySpark |
| Storage | OneLake, Lakehouse |
| Data Format | Delta Tables |
| Data Modeling | Star Schema |
| Analytics | Power BI |
| Language | Python, SQL |
| Documentation | Markdown |
| Version Control | Git & GitHub |

---

# 📂 Repository Structure

```text
fabric-medallion-architecture-project/
│
├── architecture/
│   ├── README.md
│   ├── Data_Model.md
│   ├── ER_Diagram.png
│   ├── Medallion_Architecture.md
│   └── Project_Flow.md
│
├── datasets/
│
├── documentation/
│   ├── Bronze.md
│   ├── Silver.md
│   ├── Gold.md
│   ├── Dimension_Tables.md
│   ├── Fact_Tables.md
│   ├── Semantic_Model.md
│   ├── Sales_Dashboard.md
│   ├── Operations_Dashboard.md
│   ├── Business_Insights.md
│   ├── Data_Dictionary.md
│   ├── Interview_Questions.md
│   ├── Project_Lessons.md
│   └── Daily_Log.md
│
├── notebooks/
│
├── powerbi/
│
├── sql/
│
├── screenshots/
│
├── CONTRIBUTING.md
├── LICENSE
└── README.md
```

---

# 🥉 Bronze Layer

The Bronze layer is responsible for ingesting raw source data into Microsoft Fabric Lakehouse.

### Responsibilities

- Load raw CSV datasets
- Preserve source data
- Create Bronze Delta tables
- Perform schema validation
- Maintain data lineage

---

# 🥈 Silver Layer

The Silver layer performs data cleaning, transformation, and standardization.

### Key Transformations

- Data type conversions
- Null handling
- Duplicate removal
- Column standardization
- Derived columns
- Data quality validation

---

# 🥇 Gold Layer

The Gold layer provides a business-ready dimensional model optimized for reporting.

### Dimension Tables

- dim_customer
- dim_product
- dim_category
- dim_seller
- dim_date

### Fact Tables

- fact_sales
- fact_payments

### Features

- Star Schema
- Business KPIs
- Delivery Metrics
- Review Metrics
- Sales Analytics

---

# 📊 Semantic Model

The Semantic Model was created using the Gold layer to provide an optimized analytical layer for Power BI.

Features include:

- One-to-Many relationships
- Star Schema
- Hidden helper tables
- Business measures
- Optimized reporting model

---

# 📈 Dashboards

## Sales Dashboard

Provides insights into:

- Revenue
- Orders
- Customers
- Products
- Sales Trends
- Product Categories

![Sales Dashboard](screenshots/Sales_Dashboard.png)

---

## Operations Dashboard

Provides operational insights including:

- Delivery Performance
- Shipping Analysis
- Customer Reviews
- Seller Performance
- Delivery Status

![Operations Dashboard](screenshots/Operations_Dashboard.png)

---

# 💡 Business Insights

The dashboards provide actionable business insights including:

- Revenue trends over time
- Top-performing product categories
- Customer purchasing patterns
- Seller performance analysis
- Delivery efficiency
- Payment method distribution
- Customer satisfaction metrics

---

# 📁 Dataset

**Brazilian E-Commerce Public Dataset by Olist**

The dataset contains:

- Customers
- Orders
- Products
- Sellers
- Payments
- Reviews
- Geolocation
- Product Categories

---

# ▶️ Project Workflow

1. Upload raw CSV files to Microsoft Fabric Lakehouse.
2. Execute Bronze notebooks to ingest raw data.
3. Execute Silver notebooks for data transformation.
4. Execute Gold notebooks to create fact and dimension tables.
5. Build the Semantic Model.
6. Open the Power BI report.
7. Analyze business insights using interactive dashboards.

---

# 📚 Documentation

Detailed documentation is available for every stage of the project.

- Architecture
- Bronze Layer
- Silver Layer
- Gold Layer
- Semantic Model
- Fact Tables
- Dimension Tables
- Dashboards
- Business Insights
- Lessons Learned

---

# 🎯 Skills Demonstrated

- Microsoft Fabric
- Lakehouse
- OneLake
- PySpark
- SQL
- Delta Tables
- Medallion Architecture
- ETL / ELT
- Data Modeling
- Star Schema
- Semantic Models
- Power BI
- Data Visualization
- Business Intelligence
- Documentation
- Git & GitHub

---

# 🚀 Future Enhancements

- Implement Incremental Loading
- Add Microsoft Fabric Pipelines
- Implement Slowly Changing Dimensions (SCD Type 2)
- Add Data Quality Framework
- Integrate Real-Time Analytics
- CI/CD Deployment Pipeline
- Performance Optimization

---

# 🤝 Contributing

Contributions are welcome!

If you'd like to improve this project:

1. Fork the repository.
2. Create a feature branch.
3. Commit your changes.
4. Submit a Pull Request.

Please ensure:

- Documentation is updated.
- Notebook execution is verified.
- Existing project structure is maintained.

For more information, see [CONTRIBUTING.md](CONTRIBUTING.md).

---

# 📜 License

This project is licensed under the MIT License.

See the [LICENSE](LICENSE) file for details.

---

# 👨‍💻 Author

**Girish Gampa**

If you found this project helpful, consider ⭐ starring the repository.
