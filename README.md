# Maven Fuzzy Factory — E-Commerce Product Analytics

**SQL + Power BI | Marketing Performance | Product Analytics | Customer Retention | Funnel Analysis**

## 📌 Project Overview

This project analyzes approximately three years of e-commerce activity from **Maven Fuzzy Factory**, covering website sessions, pageviews, orders, products, and refunds.

The objective was to understand:

- How marketing channels perform
- Which products drive revenue and profitability
- How effectively visitors convert into customers
- Where customers drop out of the purchase funnel
- Why mobile users underperform desktop users
- How well the business retains existing customers
- Where refunds are creating financial risk
- Which business problems should be prioritized for experimentation

The analysis was performed using **SQL** and translated into an interactive **Power BI dashboard**.

---

## 🗂️ Dataset

The database contains six core tables:

| Table | Records |
|---|---:|
| `website_sessions` | 472,871 |
| `website_pageviews` | 1,188,124 |
| `orders` | 323,313 |
| `order_items` | 400,025 |
| `order_item_refunds` | 1,731 |
| `products` | 4 |

The tables allow the analysis to connect:

**Marketing Source → Website Session → Pageview → Order → Product → Refund**

The website-session data covers **19 March 2012 to 19 March 2015**.

---

# 🔎 Analysis Areas

The project was structured around five analytical areas:

### 1. Marketing Performance

- Traffic by marketing source
- Conversion rate by source
- Revenue and gross profit by source
- Revenue per session
- Marketing source × device performance

### 2. Product Performance

- Units sold
- Revenue
- Gross profit
- Gross profit margin
- Refund rate
- Refunded revenue and gross profit

### 3. Customer & Retention

- One-time vs repeat customers
- Repeat customer rate
- Customer value
- 30/60/90-day retention
- Time to second purchase

### 4. Funnel & Root Cause Analysis

- Product → Cart → Shipping → Billing → Purchase
- Desktop vs mobile conversion
- Shipping → Billing drop-off
- Marketing channel × device
- Socialbook mobile performance

### 5. Recommendations & Experimentation

- Prioritized business problems
- Proposed A/B tests
- Hypotheses
- Primary and secondary metrics
- Success criteria

---

# 📊 Key Findings

## 1. qsearch drives scale, but not the highest efficiency

`qsearch` generated **316,035 sessions**, representing approximately **66.8% of total traffic**.

However, its **6.75% conversion rate** was below `bsearch` at **7.19%**.

`socialbook` performed weakest, with only a **3.21% conversion rate**.

**Business implication:**  
The largest traffic source is not necessarily the most efficient at converting visitors.

---

## 2. qsearch is the largest contributor to revenue and profit

qsearch generated approximately:

- **$1.28M revenue**
- **$800K gross profit**
- **21,333 orders**

It is therefore the strongest channel in terms of overall business scale.

However, direct/NULL traffic had the highest revenue per session at **$4.46**, while socialbook had the lowest at **$2.08**.

**Important limitation:** advertising-spend data is not available, so ROI/ROAS cannot be calculated from this dataset.

---

## 3. The Original Mr. Fuzzy is the primary product driver

**The Original Mr. Fuzzy** generated:

- **24,226 units sold**
- **$1.21M revenue**
- **$738.9K gross profit**

It is the clear leader in sales volume, revenue and total gross profit.

However, it has the **lowest gross profit margin** among the four products at **61.01%**.

By comparison:

- Birthday Sugar Panda — **68.49%**
- Hudson River Mini Bear — **68.36%**
- Forever Love Bear — **62.51%**
- Original Mr. Fuzzy — **61.01%**

This creates an important distinction:

> **Mr. Fuzzy is strongest in scale, while Birthday Sugar Panda and Hudson River Mini Bear are stronger in profitability per dollar of revenue.**

---

# 👥 Customer Retention

Customer retention emerged as one of the biggest opportunities.

Out of **31,696 customers**:

- **31,105** were one-time customers
- **591** were repeat customers
- Repeat customer rate = **1.86%**

There were no customers with four or more purchases in the analyzed data.

More importantly, repeat customers were significantly more valuable:

| Metric | One-time | Repeat |
|---|---:|---:|
| Revenue / Customer | $59.93 | $125.81 |
| Profit / Customer | $37.59 | $79.22 |

Repeat customers generated **more than twice the revenue and profit per customer**.

The average time to a second purchase was **35.16 days**, suggesting that the **30–35 day period** could be an important window for re-engagement.

---

# 📱 Mobile Conversion Gap

Desktop users converted at:

**8.50%**

Mobile users converted at:

**3.09%**

That means desktop conversion was approximately **2.75× mobile conversion**.

The gap appeared across every marketing source.

The most severe example was Socialbook:

- Desktop: **4.99%**
- Mobile: **0.83%**

---

# 🚨 Funnel Bottleneck

The biggest funnel problem occurs at:

**Shipping → Billing**

Overall:

- Shipping sessions: **64,484**
- Billing sessions: **3,617**
- Drop-off: **94.39%**

The problem becomes even clearer when split by device:

| Device | Shipping → Billing |
|---|---:|
| Desktop | 6.08% |
| Mobile | 3.49% |

Mobile users are therefore substantially less effective at progressing through this stage.

**Business implication:**  
The mobile checkout experience, particularly the transition from Shipping to Billing, should be investigated first.

---

# 💰 Refund Risk

Refund analysis revealed two products requiring attention.

### Birthday Sugar Panda

Highest refund rate:

**6.04%**

### Original Mr. Fuzzy

Largest financial impact:

- Refunded revenue: **$61.8K**
- Refunded gross profit: **$37.7K**
- Refund rate: **5.11%**

Therefore:

- **Birthday Sugar Panda** is the highest-rate refund concern.
- **Original Mr. Fuzzy** is the largest absolute financial concern.

Meanwhile, Hudson River Mini Bear combines a **68.36% margin** with the lowest refund rate of **1.28%**, making it particularly attractive from a profitability/risk perspective.

---

# 💡 Recommended Business Priorities

Based on the analysis, four experiments were prioritized:

| Priority | Experiment | Problem |
|---:|---|---|
| 🥇 1 | **Mobile Checkout** | Shipping → Billing drop-off |
| 🥈 2 | **Retention Campaign** | 1.86% repeat customers |
| 🥉 3 | **Landing Page** | Large landing-page performance variation |
| 4 | **Socialbook Mobile** | 0.83% mobile conversion |

### 1. Mobile Checkout

Test a simplified mobile checkout with fewer fields, clearer progress indicators, larger buttons and a simplified billing experience.

**Primary metric:** Shipping → Billing conversion rate.

### 2. Retention Campaign

Test targeted post-purchase re-engagement around the observed **30–35 day repurchase window**.

**Primary metric:** Second-purchase rate within 60 days.

### 3. Landing Page

Test a redesigned landing page inspired by the characteristics of the stronger-performing `/lander-5`.

**Primary metric:** Landing-page → Order conversion rate.

### 4. Socialbook Mobile

Test a dedicated mobile-optimized landing and checkout experience for Socialbook mobile traffic.

**Primary metric:** Purchase conversion rate.

---

# 📈 Power BI Dashboard

The analysis was converted into a six-page interactive Power BI dashboard:

1. **Executive Overview**
2. **Marketing Performance**
3. **Product Performance**
4. **Customer & Retention**
5. **Funnel & Root Cause**
6. **Recommendations & A/B Tests**

The dashboard is designed to move from:

**Overall Business Performance → Diagnostic Analysis → Root Causes → Recommended Actions**

---

# ⚠️ Important Limitations

### A/B Testing

The dataset does **not** contain randomized treatment/control groups or experiment identifiers.

Therefore, this project **does not calculate actual A/B-test winners**.

The experiments presented are **business-driven proposals based on observed problems**, not completed experiments.

### Marketing ROI

Advertising-spend data is not available.

Therefore, channel **ROI/ROAS cannot be calculated**. The analysis is limited to traffic, conversions, revenue and profit.

### Root Cause

The analysis identifies strong patterns and areas requiring investigation, but observational data alone cannot prove the exact underlying cause of a problem—for example, why users abandon the mobile checkout.

---

# 🛠️ Tools & Technologies

- **MySQL** — Data exploration, joins, aggregation and business analysis
- **SQL** — Marketing, product, customer, funnel and refund analysis
- **Power BI** — Interactive dashboard and data visualization
- **DAX** — Measures and calculated metrics
- **Data storytelling** — Translating analytical findings into business recommendations

---

# 📁 Project Structure

```text
maven-fuzzy-factory-ecommerce-analytics/
│
├── README.md
│
├── SQL/
│   ├── 01_dataset_exploration.sql
│   ├── 02_marketing_analysis.sql
│   ├── 03_product_analysis.sql
│   ├── 04_customer_retention.sql
│   ├── 05_funnel_analysis.sql
│   └── 06_root_cause_analysis.sql
│
├── Power BI/
│   └── Maven_Fuzzy_Factory_Analytics.pbix
│
├── Documentation/
│   └── E-Commerce_Product_Analytics.pdf
│
└── Dashboard/
    ├── Executive_Overview.png
    ├── Marketing_Performance.png
    ├── Product_Performance.png
    ├── Customer_Retention.png
    ├── Funnel_Root_Cause.png
    └── Recommendations_AB_Tests.png
```

---

# 🎯 Final Project Takeaway

The analysis shows a business that has **scaled strongly but has significant opportunities in conversion optimization and customer retention**.

The most actionable findings are:

> **Fix the mobile checkout bottleneck → improve customer retention → optimize weaker landing experiences → investigate Socialbook mobile performance.**

At the same time, product analysis shows that **scale and profitability are not always the same thing**, while the retention analysis demonstrates that repeat customers are substantially more valuable than one-time buyers.
