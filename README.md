# Customer Shopping Behavior Analysis 🛍️📈

An end-to-end data analytics project analyzing customer shopping behavior across 3,900 transactions. This project demonstrates data engineering and business intelligence workflows by cleaning raw data in **Python (Pandas)**, performing deep-dive relational analysis in **PostgreSQL**, and building an executive-level **Power BI** dashboard to drive strategic business decisions.

---

## 🚀 Project Overview
The goal of this project is to uncover actionable insights into customer spending patterns, cohort segmentation, item preferences, and subscription behaviors. By tracking these key performance indicators (KPIs), businesses can optimize targeted marketing, streamline shipping logistics, and refine customer retention programs.

## 📊 Dataset Summary
The data spans **3,900 transactions** across **18 behavioral and demographic features**, including:
* **Demographics:** Age, Gender, Location, Subscription Status.
* **Purchase Details:** Item Purchased, Category, Purchase Amount (USD), Season, Size, Color.
* **Behavioral Ratios:** Discount Applied, Promo Code Used, Previous Purchases, Frequency of Purchases, Review Rating, Shipping Type.
* **Data Quality Note:** 37 records missing in the `Review Rating` column were programmatically handled during the EDA phase.

---

## 🛠️ Tech Stack & Workflow

### 1. Exploratory Data Analysis & ETL (Python)
Raw transactional data was prepared and staged using Python and the `pandas` library:
* **Missing Value Imputation:** Addressed the 37 missing values in the `Review Rating` column by imputing the **median rating** specific to each product category to maintain statistical integrity.
* **Schema Standardization:** Standardized column naming conventions to `snake_case` for easier SQL querying and schema documentation.
* **Feature Engineering:**
  * Created an `age_group` column to bin consumers into distinct demographic cohorts (Young Adult, Adult, Middle-aged, Senior).
  * Derived a `purchase_frequency_days` field to normalize recurring purchase cycles.
* **Redundancy Filtering:** Verified perfect correlation between `discount_applied` and `promo_code_used`; dropped the redundant column to ensure a clean database schema.
* **Database Pipeline:** Established a connection to a local PostgreSQL instance and automatically loaded the structured DataFrame into transactional staging tables.

### 2. Relational Database Queries (SQL)
With the data structured in PostgreSQL, we executed deep-dive analysis to answer operational business questions. Below are key findings:

* **Revenue Split by Gender:** Men generated significantly higher overall volume than women.
  * **Female:** $75,191
  * **Male:** $157,890
* **Customer Value Cohorts:** Classified the customer lifecycle based on historical purchase frequencies:
  * **Loyal Buyers:** 3,116 customers
  * **Returning Buyers:** 701 customers
  * **New Customers:** 83 customers
* **Subscription Engagement:** Evaluated repeat buyers (>5 checkouts) against active subscription tiers:
  * **Non-Subscribed Repeat Buyers:** 2,518
  * **Subscribed Repeat Buyers:** 958
* **Top Revenue Drivers by Age Demographic:**
  1. **Young Adult:** $62,143
  2. **Middle-aged:** $59,197
  3. **Adult:** $55,978
  4. **Senior:** $55,763

### 3. Business Intelligence Dashboard (Power BI)
The cleaned datasets were pulled into Power BI to create an interactive, cross-filtered executive dashboard mapping core retail metrics:

* **High-Level KPIs:** Houses macro metrics like total user counts (3.9K), average basket spend ($59.76), and baseline review satisfaction scores (3.75).
* **Category Penetration:** Visualizes revenue split by department—identifying **Clothing** ($104K / 1.7K orders) and **Accessories** ($74K / 1.2K orders) as primary business engines over Footwear and Outerwear.
* **Subscription Ratios:** Clearly charts the 27% (Yes) to 73% (No) subscription split to identify conversion opportunities.

![Customer Behavior Dashboard](customers_behavior_dashboard.pdf) 
*(Note: Replace this path with your uploaded image filename, e.g., `images/dashboard.png`, once added to your repo)*

---

## 📌 Strategic Business Recommendations

1. **Monetize the Non-Subscriber Base:** With 73% of customers currently sitting outside the subscription program—yet generating $170,436 in revenue—implementing targeted checkout incentives or premium delivery benefits can unlock massive recurring value.
2. **Nurture High-Value Life Cycles:** Design direct loyalty paths targeting the 701 "Returning" and 83 "New" buyers to actively move them into the predictable "Loyal" tier (which currently holds a stellar 3,116 users).
3. **Optimize Markdown Strategies:** Monitor items with extreme discount dependencies (e.g., Hats at a 50.00% discount rate and Sneakers at 49.66%) to prevent margin erosion while maintaining high inventory turnover.
4. **Demographic Advertising Baskets:** Direct high-tier marketing budgets toward standard "Young Adult" and "Middle-aged" segments, while leveraging premium shipping upgrades (Express) to incentivize bigger shopping carts.

---

## 📂 Repository Structure
```directory
├── data/
│   └── Customer Shopping Behavior Analysis.pdf   # Original data analysis brief
├── scripts/
│   └── data_cleaning.py                          # Python pandas ETL script
├── sql/
│   └── business_queries.sql                      # PostgreSQL analytical queries
├── dashboard/
│   └── customers_behavior_dashboard.pdf          # Final Power BI Report Export
└── README.md                                     # Project documentation
