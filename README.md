# 🚀 Retail Customer Segmentation Project (Databricks + Power BI)

This is a complete, end-to-end data analysis project that starts from ingesting raw data from various sources and ends with a fully interactive dashboard to drive smart marketing decisions.

---

## 🏗️ 1. Project Architecture

The project follows a modern **Medallion Architecture** to ensure data quality and separation of concerns at different stages:

![Project Architecture](images/architecture.jpg)

1.  **Data Source:** Data from OLTP SQL Server databases and various APIs.
2.  **Data Ingestion:** Using **Azure Data Factory** to pull raw data.
3.  **Data Lake:** Storing the raw data in an **Azure Storage Account**.
4.  **Processing:**
    * Using **Azure Databricks** (PySpark) to process the data through 3 layers:
    * **Bronze:** A raw, duplicated copy of the source data (Parquet format).
    * **Silver:** Cleaned, standardized data (e.g., mismatched IDs were resolved).
    * **Gold:** Aggregated, analysis-ready data (tables joined, RFM model applied).
5.  **Dashboard:** Using **Power BI** to connect to the Gold layer and visualize the insights.

---

## 📊 2. The Final Dashboard (Power BI)

A 3-page interactive dashboard was built to tell the complete data story.

### Page 1: Executive Summary

A high-level overview of the most important Key Performance Indicators (KPIs).

![Executive Summary](images/dashboard_summary.png)

* **Total Sales:** 178K.
* **Total Customers:** 27 unique customers.
* **Avg. Sale per Customer:** 6.58K.
* **Customer Tiers:** The majority of customers are "Bronze" (48%), followed by "Gold" (30%) and "Silver" (22%).

### Page 2: Products & Customer Deep Dive

An interactive page to understand *what* each customer segment is buying.

![Product Deep Dive](images/dashboard_products.png)

* **Categories:** "Electronics" is the most dominant category by sales.
* **Products:** The "Smartwatch" is the single best-selling product.
* **(The Story):** By using the `Customer_Tier` slicer, we can filter to see exactly what "Gold" tier customers prefer, allowing for highly targeted marketing campaigns.

### Page 3: Store Performance Analysis

Analyzing the performance of each store and, more importantly, the *quality* of customers each store attracts.

![Store Performance](images/dashboard_stores.png)

**⭐ The Project's Key Storytelling Insight:**

* **"High Street Store":** This is the **top-performing store** in sales (approx. 90K). The reason is clear: its customer base is almost entirely **Gold Tier**.
* **"Cairo Festival City" Store:** This is the **second-best store** (approx. 60K), but its composition is completely different. Its customer base is almost 100% **Bronze Tier**.

**The Business Decision (Insight):**
* We must stock "High Street Store" with our most premium, high-margin products.
* We must run discounts, bundles, and volume-based offers at "Cairo Festival City" to increase sales from our Bronze customers.

---

## 🚀 3. Technical Details & How to Run

* **Code:** The full PySpark analysis is in the `analysis.ipynb` notebook.
* **Power BI File:** The complete interactive dashboard is in `visulization.pbix`.
* **Security:** All credentials (like the Azure Storage Key) have been hidden in a `.env` file, which is included in `.gitignore` and is not uploaded to GitHub, ensuring the project is secure.