# 📦 Olist E-Commerce Strategy & Logistics EDA

> **Transforming 96k+ Transactions into SLA Optimization, Customer Retention, and Geographic Growth Strategies**

![Python](https://img.shields.io/badge/Python-3.9+-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=flat&logo=pandas)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebooks-F37626?style=flat&logo=jupyter)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

## Executive Summary

An analysis of **96,182 delivered orders** across Brazil (2016–2018) reveals a core operational insight: **Delivery reliability, not freight price, drives customer retention and satisfaction.**

While freight cost variations show minimal impact on review scores (4.21 vs 4.04 across freight buckets), **delivery delays trigger an immediate ~2.0 point collapse in review scores** (4.29 on-time vs. 2.28 late), with **52.3% of delayed orders receiving a 1-star review**. With marketplace retention standing at a critical low of **3.0%** (2,793 repeat buyers out of ~93,000), service failures permanently erode customer Lifetime Value (LTV).

---

## 📊 Business Problem & Core Objectives

* **Identify Retention Drivers:** Pinpoint why 97% of customers purchase only once.
* **Quantify Delivery SLA Impact:** Measure the exact elasticity between shipping delays and review score decay.
* **Optimize Pricing & Freight Strategy:** Determine if freight costs stifle conversion or customer satisfaction.
* **Geographic Arbitrage:** Evaluate logistics bottlenecks across state clusters (e.g., São Paulo vs. North/Northeast).

---

## 📈 Strategic Insights & Impact Matrix

| Strategic Area | Key Metric / Observation | Business Impact | Actionable Recommendation |
| :--- | :--- | :--- | :--- |
| **Logistics SLAs** | 52.3% of late orders receive 1★ reviews; on-time avg is 4.29 vs 2.28 late. | Unreliable delivery drives customer churn and brand erosion. | Reallocate freight subsidy budgets toward carrier SLA enforcement and penalty clauses. |
| **Customer Retention** | 3.0% repeat customer rate (2,793 repeat buyers). | High Customer Acquisition Cost (CAC) with non-existent LTV recovery. | Build post-purchase email flows, loyalty tiers, and automated recovery offers for 1-star review customers. |
| **Geographic Density** | São Paulo (SP) holds 42% of order volume. | Growth capped in core region; high shipping friction in North/Northeast. | Establish fulfillment nodes in Northeast hubs (e.g., Bahia/Pernambuco) to reduce regional transit times. |
| **Pricing & Freight** | Freight > Item Price for 3% of orders; freight cost variation causes only -0.17 score drop. | Customers tolerate reasonable freight if items arrive on time. | Set minimum basket thresholds (R$50+) for freight discounts rather than flat shipping subsidies. |

---

## 🛠 Project Workflow & Technical Architecture

```text
[Raw Olist Tables (9 CSVs)] 
        │
        ├──> 01_schema_validation.ipynb  (Key checks, join validation, cardinality)
        ├──> 02_cleaning_feature_eng.ipynb (Dedup, EN translation, date parsing, delta metrics)
        ├──> 03_exploratory_analysis.ipynb (Statistical distributions, state mapping, correlation)
        └──> 04_executive_summary.ipynb    (Strategic recommendations, LTV analysis, limitations)
```
### Feature Engineering Highlights

* `delivery_days`: Elapsed days from `order_purchase_timestamp` to customer delivery.
* `delivery_delay_days`: Delta between actual delivery date and estimated delivery date (`actual - estimated`).
* `was_late`: Boolean indicator (`delivery_delay_days > 0`).
* `freight_ratio`: `total_freight / total_price` evaluating relative shipping burden.

---

## 🎯 Key Visualizations (Highlights)

> *(Insert 2-3 key charts or visual outputs here from Notebook 03: e.g., On-Time vs. Late Review Distribution, Revenue Concentration Map, or Delay Days vs. Review Score)*

---

## 📁 Data Source & Setup

The dataset used in this project is the **Brazilian E-Commerce Public Dataset by Olist** hosted on Kaggle, consisting of **9 CSV files**:

* `olist_customers_dataset.csv`
* `olist_geolocation_dataset.csv`
* `olist_order_items_dataset.csv`
* `olist_order_payments_dataset.csv`
* `olist_order_reviews_dataset.csv`
* `olist_orders_dataset.csv`
* `olist_products_dataset.csv`
* `olist_sellers_dataset.csv`
* `product_category_name_translation.csv`

### How to Access the Data:
1. Download the raw CSV files from the [Kaggle Dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce).
2. **Local Environment:** Place all 9 `.csv` files inside the `data/raw/` directory.
3. **Google Colab Environment:** Upload all 9 `.csv` files into your active session storage or mount your Google Drive folder path.

---

## ⚠️ Data Limitations & Risk Factors

* **Historical Window:** Data reflects 2016–2018 market dynamics; current inflation and logistics infrastructure differ.
* **Margin Blindspot:** Lacks COGS (Cost of Goods Sold) and marketing spend; recommendations focus on top-line growth and satisfaction rather than net margin.
* **Selection Bias:** Review responses skew toward extreme experiences (1★ and 5★ polarization).

---

## ⚙️ How to Reproduce

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/your-username/olist-eda-strategy.git](https://github.com/your-username/olist-eda-strategy.git)
   cd olist-eda-strategy
