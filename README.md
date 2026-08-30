# Maven Fuzzy Factory --- E-Commerce Product Analytics

**SQL Analysis • Power BI Dashboard • Business Recommendations**

An end-to-end e-commerce analytics project using **MySQL, SQL, Power BI
and DAX** to analyze marketing performance, product profitability,
customer retention, refunds, and the purchase funnel --- and translate
the findings into actionable business recommendations and proposed
experiments.

------------------------------------------------------------------------

## 📌 Project Overview

This project analyzes approximately three years of Maven Fuzzy Factory
e-commerce activity, from **19 March 2012 to 19 March 2015**.

The analysis connects:

**Marketing Source → Website Session → Pageview → Order → Product →
Refund**

The goal was to identify where the business is performing well, where
customers are being lost, and which areas should be prioritized for
improvement or experimentation.

### Key questions addressed

-   Which marketing sources generate the most traffic, orders, revenue
    and profit?
-   Which channels convert traffic most effectively?
-   Which products drive sales and gross profit?
-   Which products have the strongest margins and highest refund rates?
-   How valuable are repeat customers compared with one-time customers?
-   Where do users drop out of the purchase funnel?
-   How different are desktop and mobile conversion rates?
-   Why is the mobile experience underperforming?
-   Which problems should be prioritized for further testing?

------------------------------------------------------------------------

# 📊 Executive Summary

The analysis reveals a business that **scaled strongly over the
three-year period**, but also has substantial opportunities in **mobile
conversion, checkout optimization and customer retention**.

### 🔑 Key Findings

  -----------------------------------------------------------------------
  Area                                Finding
  ----------------------------------- -----------------------------------
  **Traffic leader**                  `gsearch` generated **316,035
                                      sessions**, approximately **66.8%**
                                      of total traffic

  **Marketing scale**                 `gsearch` generated **21,333
                                      orders**, **\$1.28M revenue** and
                                      **\$800K gross profit**

  **Marketing efficiency**            `bsearch` converted at **7.19%**,
                                      slightly above `gsearch` at
                                      **6.75%**

  **Weakest channel**                 `socialbook` had the lowest
                                      conversion rate at **3.21%** and
                                      revenue/session of **\$2.08**

  **Product leader**                  **The Original Mr. Fuzzy** led in
                                      units, revenue and total gross
                                      profit

  **Highest-margin product**          **Birthday Sugar Panda** had the
                                      highest gross-profit margin at
                                      **68.49%**

  **Refund risk**                     **Birthday Sugar Panda** had the
                                      highest refund rate at **6.04%**

  **Customer retention**              Only **1.86%** of customers were
                                      repeat customers

  **Customer value**                  Repeat customers generated
                                      substantially more revenue and
                                      gross profit per customer

  **Device gap**                      Desktop conversion was **8.50%** vs
                                      **3.09%** on mobile

  **Largest funnel problem**          Shipping → Billing had a **94.39%
                                      drop-off**

  **Priority opportunity**            Investigate and improve the
                                      **mobile checkout experience**,
                                      especially the Shipping → Billing
                                      transition
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 🗃️ Dataset

The project uses the Maven Fuzzy Factory database containing six core
tables:

  Table                       Records
  ---------------------- ------------
  `website_sessions`          472,871
  `website_pageviews`       1,188,124
  `orders`                 **32,313**
  `order_items`               400,025
  `order_item_refunds`          1,731
  `products`                        4

### Data relationships

``` text
Marketing Source
       ↓
Website Session
       ↓
Website Pageview
       ↓
Order
       ↓
Order Item / Product
       ↓
Refund
```

------------------------------------------------------------------------

# 🔎 Analysis Areas

## 1. Marketing Performance

`gsearch` was the dominant acquisition source:

  Source            Sessions   Share
  --------------- ---------- -------
  `gsearch`          316,035   66.8%
  Direct / NULL       83,328   17.6%
  `bsearch`           62,823   13.3%
  `socialbook`        10,685    2.3%

### Conversion

  Source            Orders   Conversion
  --------------- -------- ------------
  Direct / NULL      6,118        7.34%
  `bsearch`          4,519        7.19%
  `gsearch`         21,333        6.75%
  `socialbook`         343        3.21%

The important distinction is between **scale and efficiency**. `gsearch`
drives the largest amount of business activity, while `bsearch` converts
slightly more efficiently.

Advertising-spend data is not available, so **ROI/ROAS cannot be
calculated** from this dataset.

------------------------------------------------------------------------

# 🧸 2. Product Performance

**The Original Mr. Fuzzy** is the clear scale leader:

-   **24,226 units sold**
-   **\$1,211,057.74 revenue**
-   **\$738,893 gross profit**
-   **61.01% gross-profit margin**

### Gross-profit margins

  Product                    Gross Profit Margin
  ------------------------ ---------------------
  Birthday Sugar Panda                **68.49%**
  Hudson River Mini Bear              **68.36%**
  Forever Love Bear                       62.51%
  The Original Mr. Fuzzy                  61.01%

This creates two different product strengths:

-   **The Original Mr. Fuzzy** → strongest in scale and total profit
-   **Birthday Sugar Panda / Hudson River Mini Bear** → strongest in
    profitability per dollar of revenue

------------------------------------------------------------------------

# 🔁 3. Customer Retention

The customer base is overwhelmingly made up of one-time buyers.

-   **31,105** one-time customers
-   **591** repeat customers
-   **0** customers with 4+ orders
-   Repeat-customer rate: **1.86%**

Repeat customers were substantially more valuable individually:

  Customer Type     Avg. Revenue / Customer   Avg. Profit / Customer
  --------------- ------------------------- ------------------------
  One-time                          \$59.93                  \$37.59
  Repeat                           \$125.81                  \$79.22

**Business implication:** Improving repeat purchases could increase
customer value without relying entirely on acquiring additional
customers.

------------------------------------------------------------------------

# 🛒 4. Purchase Funnel & Root Cause Analysis

The purchase funnel was analyzed as:

``` text
Product → Cart → Shipping → Billing → Purchase
```

The largest bottleneck occurs between **Shipping and Billing**:

-   Shipping sessions: **64,484**
-   Billing sessions: **3,617**
-   Drop-off: **94.39%**

This is the most significant funnel problem identified in the analysis.

The data does not prove the exact cause, but the size of the drop
strongly supports investigating the transition from shipping information
to billing.

------------------------------------------------------------------------

# 📱 5. Desktop vs Mobile

A major conversion gap exists between devices:

  Device      Sessions   Purchases   Conversion
  --------- ---------- ----------- ------------
  Desktop      327,027      27,805    **8.50%**
  Mobile       145,844       4,508    **3.09%**

Desktop converts at almost **2.75×** the mobile rate.

### Shipping → Billing by device

-   **Mobile:** 3.49%
-   **Desktop:** 6.08%

The transition performs poorly on both devices, but is substantially
weaker on mobile.

------------------------------------------------------------------------

# 📉 6. Socialbook Performance

`socialbook` is the weakest marketing source across several measures:

-   Conversion: **3.21%**
-   Revenue/session: **\$2.08**
-   Orders: **343**

The problem is especially pronounced on mobile:

  Device      Sessions   Purchases   Conversion
  --------- ---------- ----------- ------------
  Mobile         4,573          38    **0.83%**
  Desktop        6,112         305    **4.99%**

This suggests two issues may be interacting:

1.  Lower-quality traffic from `socialbook`
2.  A weaker mobile conversion experience

The dataset supports this pattern, but does not establish causality.

------------------------------------------------------------------------

# 💰 7. Refund Analysis

  Product                    Units Sold   Refunded Items   Refund Rate
  ------------------------ ------------ ---------------- -------------
  Birthday Sugar Panda            4,985              301     **6.04%**
  The Original Mr. Fuzzy         24,226            1,237     **5.11%**
  Forever Love Bear               5,796              129     **2.23%**
  Hudson River Mini Bear          5,018               64     **1.28%**

**Birthday Sugar Panda** combines the highest gross-profit margin with
the highest refund rate, making it a product worth investigating.

**Hudson River Mini Bear** combines a high margin with the lowest refund
rate.

------------------------------------------------------------------------

# 💡 Business Recommendations

### 1. Improve the mobile checkout experience

Investigate the Shipping → Billing transition, with particular attention
to mobile usability, form friction, validation and payment-flow issues.

### 2. Improve customer retention

Test post-purchase engagement, personalized offers,
replenishment/reminder campaigns and other strategies designed to
encourage a second purchase.

### 3. Investigate weaker landing-page performance

`/lander-5` had the highest conversion rate at **10.17%**, while
`/lander-3` and `/lander-1` performed substantially worse.

### 4. Investigate `socialbook`

The channel has both low conversion and low revenue/session, with
especially weak mobile performance.

### 5. Investigate refund drivers

Review customer feedback, product expectations, quality and delivery
experience for products with higher refund rates, particularly Birthday
Sugar Panda and The Original Mr. Fuzzy.

------------------------------------------------------------------------

# 🧪 Proposed A/B Tests

The project includes **proposed experiments**, not completed
experiments.

  -----------------------------------------------------------------------
  Priority                Experiment              Primary Metric
  ----------------------- ----------------------- -----------------------
  🔴 High                 Mobile Shipping →       Shipping → Billing
                          Billing redesign        conversion

  🔴 High                 Mobile checkout         Mobile purchase
                          simplification          conversion

  🟠 Medium               Post-purchase retention Repeat-purchase rate
                          campaign                

  🟠 Medium               Landing-page            Landing-page conversion
                          optimization            

  🟡 Medium               Socialbook traffic /    Channel conversion
                          landing-page            
                          optimization            
  -----------------------------------------------------------------------

These experiments are recommendations derived from observed patterns.
The dataset does **not** contain treatment/control groups, so no claim
of experimental causality is made.

------------------------------------------------------------------------

# ⚠️ Analytical Limitations

### A/B Testing

The dataset does not contain experimental treatment/control groups. The
proposed experiments are **business recommendations**, not completed
experiments.

### Marketing ROI / ROAS

Advertising-spend data is not available. Therefore, channel **ROI and
ROAS cannot be calculated**.

### Causal Inference

The analysis identifies strong patterns and areas requiring
investigation, but observational data alone cannot prove the exact
underlying cause of problems.

------------------------------------------------------------------------

# 📊 Power BI Dashboard

The project contains a six-page Power BI dashboard:

1.  **Executive Overview**
2.  **Marketing Performance**
3.  **Product Performance**
4.  **Customer & Retention**
5.  **Funnel & Root Cause**
6.  **Recommendations & A/B Tests**

Dashboard screenshots are available in the [`Dashboard`](Dashboard/)
folder.

The Power BI source file is available in [`Power BI`](Power%20BI/).

------------------------------------------------------------------------

# 🗂️ Project Structure

``` text
Maven-Fuzzy-Factory-Analytics/
│
├── README.md
│
├── Dashboard/
│   ├── 01_Executive_Overview.png
│   ├── 02_Marketing_Performance.png
│   ├── 03_Product_Performance.png
│   ├── 04_Customer_Retention.png
│   ├── 05_Funnel_Root_Cause.png
│   └── 06_Recommendations_AB_Tests.png
│
├── Documentation/
│   └── Maven_Fuzzy_Factory_Project_Documentation.docx
│
├── Power BI/
│   └── Maven_Fuzzy_Factory_Analytics.pbix
│
└── SQL/
    ├── 01_database_setup/
    │   ├── create_mavenfuzzyfactory_vApril2022.sql
    │   └── preparing_workbench_vApril2022.sql
    │
    └── 02_business_analysis/
        └── maven_fuzzy_factory_analysis.sql
```

------------------------------------------------------------------------

# 🛠️ Tools & Technologies

-   **MySQL** --- Database exploration, joins and aggregation
-   **SQL** --- Marketing, product, customer, funnel and refund analysis
-   **Power BI** --- Interactive dashboard and data visualization
-   **DAX** --- Measures and calculated metrics
-   **Git & GitHub** --- Version control and project documentation
-   **Git LFS** --- Storage of large SQL and Power BI files

------------------------------------------------------------------------

# 🎯 Final Takeaway

Maven Fuzzy Factory shows strong business growth, but the analysis
highlights a clear opportunity to improve the **quality of that
growth**.

The most important priorities are:

> **Fix the mobile checkout bottleneck → improve customer retention →
> optimize weaker landing experiences → investigate Socialbook and
> refund performance.**

At the same time, the product analysis shows that **scale and
profitability are not always the same thing**. The Original Mr. Fuzzy
dominates total contribution, while Birthday Sugar Panda and Hudson
River Mini Bear demonstrate stronger gross-profit margins.

Overall, the project combines **SQL-based analysis, Power BI
visualization and business reasoning** to move from raw e-commerce data
to practical decisions and testable recommendations.
