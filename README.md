# 🛒 E-Commerce Sales & Customer Behavior Analysis

**Turning raw transactional data into revenue, profit, and customer insights — using Python, SQL, and Power BI.**
---
## 📌 About This Project

I built this project to answer a question every e-commerce business eventually has to ask: **why is revenue inconsistent, and where is money actually being lost?**

Rather than treating this as a single-tool exercise, I ran it as a full analytics workflow — the kind you'd actually see on the job. I started in **Python** to clean and explore five raw datasets, moved into **MySQL** to answer structured business questions with SQL, and finished in **Power BI** to package everything into an interactive dashboard that a non-technical stakeholder could actually use to make decisions.

The goal wasn't just to make charts — it was to trace a real business problem (inconsistent growth + order cancellations eating into profit) all the way through to a set of concrete, defensible recommendations.

---

## 🎯 Business Problem

An e-commerce company was seeing:
- 📉 Inconsistent revenue growth across months, with some periods showing **negative growth**
- 🔁 A meaningful volume of **cancelled orders**, quietly eating into profit
- ⚖️ Orders and quantity sold **not lining up with profit** — a signal that revenue alone was the wrong metric to optimize for
- 🏆 Heavy reliance on the **Electronics** category, with no clarity on whether other categories were being under-leveraged

**Objectives:**
1. Improve the consistency of revenue growth
2. Identify high- and low-performing months
3. Optimize product category performance
4. Reduce order cancellations
5. Increase overall profitability — not just revenue

---

## 🧰 Tech Stack

| Layer | Tools |
|---|---|
| **Data Wrangling & EDA** | Python, Pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn |
| **Database** | MySQL, SQLAlchemy |
| **Querying** | SQL (joins, subqueries, window functions, aggregations) |
| **Business Intelligence** | Power BI (DAX, interactive filtering) |
| **Environment** | Jupyter Notebook |

---

## 🗂️ Dataset

The analysis is built on five related source files that together mirror a real e-commerce backend:

| File | What it holds |
|---|---|
| `customers.csv` | Customer master data |
| `products.csv` | Product catalog — category, brand, price, rating, stock, discount % |
| `transactions.csv` | Order-level fact table — quantity, price, status, payment method, shipping cost |
| `sessions.csv` | Browsing session data |
| `reviews.csv` | Customer product reviews |

`transactions.csv` is the core fact table. It was merged with `products.csv` on `product_id` and `customers.csv` on `customer_id` to build a single analysis-ready dataset, with an engineered `revenue` field (`quantity × price`) added on top.

---

## 🔄 Project Workflow

```
Raw CSVs (customers, products, transactions, sessions, reviews)
        │
        ▼
Python (Pandas) → clean, merge, engineer features (revenue, age_group, purchase_frequency_days)
        │
        ▼
MySQL (SQLAlchemy) → load cleaned data into `shopping_data` table
        │
        ▼
SQL → answer 14 structured business questions
        │
        ▼
Power BI → interactive dashboard (revenue, profit, orders, growth, status)
        │
        ▼
Business Insights & Recommendations
```

---

## 📊 Exploratory Data Analysis (Python)

A sample of the visual analysis performed in the notebook:

**Revenue is heavily concentrated in Electronics — nearly 3x the next-closest category.**

**Demand, on the other hand, is spread across categories** — the top 10 best-selling products by unit volume span Sports, Home & Garden, Electronics, Clothing, and more.

**Two brands — EcoLiving and NovaTech — punch well above their weight**, together accounting for roughly half the revenue of the top 5 brands combined.

**Discounting doesn't behave the way you'd expect.** Average revenue actually *dips* at a 25% discount and peaks around 10% and 40% — a clear signal that blanket discounting isn't the right strategy.

**Product rating is one of the strongest visible demand drivers** — quantity sold climbs sharply as rating approaches 5.0.

---

## 🧮 SQL Analysis

After loading the cleaned dataset into MySQL (`E_COMMERCE_BEHAVIOR.shopping_data`), I wrote 14 queries to answer real business questions — not just "SELECT *" practice, but the kind of questions a stakeholder actually asks:

- 💰 What's our total revenue, order count, and unique customer base?
- 📦 Which products are most in demand, and which generate the most revenue — are they the same products?
- 🏷️ Which categories have the best ratings, and which generate revenue *above average*?
- 🥇 Who are the top 3 products in every category? *(solved with a `RANK() OVER (PARTITION BY ...)` window function)*
- 🔁 Who are our repeat customers, and which day had the single highest revenue?
- 💎 Who bought our most expensive product?

Full queries live in [`E_commerce.sql`](./E_commerce.sql) — including joins, correlated subqueries, `HAVING` clauses, and window functions.

---

## 📈 Power BI Dashboard

The final deliverable: an interactive dashboard letting stakeholders filter by **Category**, **Year**, and **Order Status** (Cancelled / Completed / Pending / Refunded) — built specifically so the business could isolate the cost of cancellations instead of only seeing blended totals.

**Headline KPIs:**

| Total Revenue | Profit | Total Orders | Quantity | Revenue Growth |
|:---:|:---:|:---:|:---:|:---:|
| **$4.65M** | **$1.08M** | **52K** | **78K** | **▲ 1199.9%** |

The single most useful insight the dashboard surfaces: **Electronics leads on revenue but not on profit.** Health, Food & Grocery, and Sports convert more efficiently into profit — meaning a revenue-first marketing strategy would actually be mis-allocating budget.

---

## 💡 Key Insights

- 📅 Revenue is **strongly seasonal** — trough in February (~$298K), peak in December (~$607K)
- 🔌 **Electronics** drives ~27–28% of revenue but isn't the top profit category
- ⚠️ **Cancelled/refunded orders** are a direct, now-measurable drag on profit
- 🎯 Demand is broad-based; **revenue and brand value are concentrated**
- 🏷️ Discount strategy needs to be **tier-tested**, not applied broadly
- ⭐ **Ratings correlate strongly with demand** — reputation management is a growth lever, not just a CX metric
- 💳 **Credit card** is the dominant payment method by a wide margin<img width="585" height="341" alt="Dashboard_snapshot" src="https://github.com/user-attachments/assets/685d1202-8aee-4f26-b937-7c248c855be7" />


---

## ✅ Recommendations

1. Build a recurring cancellation/refund report by category & payment method to root-cause losses
2. Shift promotional investment toward **profit leaders** (Health, Food & Grocery, Sports), not just revenue leaders
3. A/B test discount tiers instead of applying uniform discounts
4. Actively manage low-rated listings — rating is a demand lever
5. Scale inventory & staffing ahead of the Q4 seasonal peak
6. Deepen vendor relationships with top-performing brands (EcoLiving, NovaTech)
7. Operationalize the Power BI dashboard as a recurring reporting tool, not a one-off deliverable

---

## 🧠 Skills Demonstrated

`Data Cleaning` `Data Merging & Feature Engineering` `Exploratory Data Analysis` `SQL (Joins, Subqueries, Window Functions)` `Database Integration (SQLAlchemy)` `Power BI Dashboarding` `Business Storytelling` `Root-Cause Analysis`

---

## 👤 About Me

I'm a data analyst who enjoys taking a messy, multi-table dataset and turning it into something a business can actually act on. This project reflects how I like to work: start with the business problem, not the tool — and let the tool choice follow from what the problem actually needs.

📫 Feel free to connect or reach out if you'd like to talk through the approach, the SQL, or the dashboard design decisions.

⭐ If this project was useful or interesting to you, a star on the repo is always appreciated!
