# olist-ecommerce-analytics (EDA)
# 📦 Exploratory Data Analysis — Olist Brazilian E-Commerce

This project presents a complete Exploratory Data Analysis (EDA) of the **Olist
Brazilian E-Commerce Public Dataset**. The goal of this analysis is to transform
raw transactional data into meaningful business insights that support
data-driven decision-making.

Using Python and data visualization techniques, this project evaluates customer
satisfaction, logistics efficiency, product performance, geographic
distribution, and payment behavior.

---

## 📌 Project Objective

The primary objective of this project is to:

- Analyze overall order volume and trends over time
- Identify top-performing and lowest-rated product categories
- Evaluate delivery efficiency and its impact on customer satisfaction
- Study payment distribution patterns
- Analyze freight cost structure by price and geography
- Generate business-level insights and recommendations

---

## 📂 Dataset Overview

The Olist dataset contains multiple interconnected tables (~120 MB, 2016–2018):

| Table | Contents |
|---|---|
| Customers | Customer IDs & locations (27 states) |
| Orders | Status & 5 timestamps per order |
| Order Items | Products, prices, freight per order |
| Payments | Payment type, installments, value |
| Reviews | Scores (1–5) & optional comments |
| Products | Attributes & Portuguese categories |
| Sellers | Seller IDs & locations |
| Geolocation | Zip-code coordinates (1M+ rows) |
| Category Translation | Portuguese → English category names |

These were merged using common keys (`order_id`, `customer_id`, `product_id`,
`seller_id`) into one unified master dataset of ~96,000 delivered orders.

📥 **Source:** [Brazilian E-Commerce Public Dataset by Olist — Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
(Dataset not included in this repo — download from Kaggle.)

---

## ⚙️ Project Workflow

The analysis was conducted in the following sequence:

1. **Data loading and inspection** — shapes, dtypes, missing values, duplicates, join-key validation
2. **Data cleaning** — datetime parsing, geolocation dedup (26%), missing-value strategy, category translation
3. **Multi-table merging** — orders + customers + items + payments + reviews + products + sellers
4. **Feature engineering** — delivery days, estimated delay, `was_late` flag, freight %, purchase month
5. **Exploratory analysis** — trends, delivery vs. reviews, categories, geography, payments, freight
6. **Business interpretation** — insights, recommendations, limitations

| Notebook | Focus |
|---|---|
| `01_data_understanding.ipynb` | Schema, data quality, table relationships |
| `02_data_cleaning.ipynb` | Cleaning, translation, master dataset build |
| `03_exploratory_analysis.ipynb` | Full exploratory analysis & visualizations |
| `04_insights_conclusion.ipynb` | Findings, recommendations, limitations |

---

## 📊 KPI Snapshot

- **Total Orders (delivered):** ~96,000
- **Total Revenue:** R$ [run KPI cell in Notebook 03]
- **Average Order Value:** R$ [run KPI cell]
- **Average Delivery Time:** 12.1 days
- **On-Time Rate:** 93.4% (6.6% late)
- **Repeat Customer Rate:** [run KPI cell]

---

## 📈 Key Insights

1. **⏱️ Delivery speed is the #1 satisfaction driver.** Late orders average
   **2.28** vs **4.29** on-time. **52.3% of late deliveries receive a 1-star
   review**, vs only 6.6% of on-time orders.
2. **⭐ Reviews are polarized** — 1★ and 5★ dominate; customers rarely feel neutral.
3. **🏷️ Lowest-rated categories:** computer accessories, furniture/decor,
   telephony (≥200 orders each) — likely shipping-sensitive goods.
4. **🛏️ Volume leaders:** bed/bath/table & health/beauty dominate order volume.
5. **🗺️ Geographic concentration:** São Paulo (SP) alone accounts for **42% of
   all orders**.
6. **💳 Credit card dominates payments**, with ~2.9 installments per order on average.
7. **📦 Freight is flat (R$20–80)** regardless of item price — cheap items and
   remote northern states (RR, AP, AM) carry the heaviest relative burden.
8. **📉 Freight cost barely hurts satisfaction (4.21 → 4.04 across buckets) —
   lateness hurts ~10× more.** Fix delays, not freight prices.

---

## 💡 Business Recommendations

- **Prioritize logistics SLAs over freight subsidies** — lateness (−2 pts) hurts
  far more than shipping cost (−0.2 pts)
- **Tighten delivery estimates** — orders arrive a median 12 days early, so
  estimates have slack that better routing could absorb
- **Introduce packaging/QA standards** for fragile, low-rated categories
- **Expand beyond São Paulo** into under-penetrated North/Northeast regions
- **Push credit-card installment options** at checkout — the preferred behavior
- **Protect low-value orders** from uneconomical freight (freight &gt; item price
  for ~3% of orders)

---

## 🛠 Tools & Technologies

Python · Pandas · NumPy · Matplotlib · Seaborn · Google Colab

---

## 🔮 Future Scope

- Customer segmentation using **RFM analysis**
- **Sales forecasting** models
- **Churn prediction**
- **Recommendation system**
- Interactive dashboards (**Power BI / Tableau**)

---

## ⚠️ Limitations

- Data covers **2016–2018 only** — marketplace conditions have since changed
- **No cost/margin data** — we see revenue and satisfaction, not profitability
- **Review non-response bias** — only ~40% of orders have reviews
- A few Portuguese categories mapped to `'unknown'` after translation
- The &gt;100% freight bucket holds only ~3k orders (3%) — small-sample effect

---

## ▶️ How to Run

1. Download the dataset from [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
2. Open the notebooks in order in Colab or Jupyter
3. Set `DATA_PATH` in Notebooks 01 & 02 to your CSV location
4. Run top-to-bottom — Notebook 02 saves `olist_master.csv`, which 03 & 04 load

---

## 👤 Author

[Your Name] · [LinkedIn / GitHub]
