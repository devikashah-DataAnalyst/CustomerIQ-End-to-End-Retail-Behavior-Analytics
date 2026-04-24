
## 🛍️ CustomerIQ — Customer Shopping Behavior Analysis

An end-to-end retail data analytics project built to uncover what drives customer purchasing decisions, loyalty, and revenue across 3,900 transactions. This project moves from raw data all the way to an interactive executive dashboard — covering Python-based data preparation, SQL business intelligence in PostgreSQL, and a 4-page Power BI dashboard with custom DAX measures.

---

## 📌 Project at a Glance

🗃️ 3,900 transactional records analysed

📋 18 dataset columns spanning demographics, behavior, and purchase data

🔍 10 structured SQL business intelligence queries

📊 4 interactive Power BI dashboard pages with drill-through navigation

💡 $108,000+ in untapped subscription revenue identified

🛠️ Python · PostgreSQL · Power BI · DAX · SQLAlchemy · Pandas

---

## 📁 Project Structure

📂 data/raw — Original unmodified dataset in CSV format

📂 data/cleaned — Production-ready dataset after cleaning and feature engineering

📂 python — Scripts for EDA, feature engineering, and database upload

📂 sql — 10 structured business intelligence queries in PostgreSQL

📂 powerbi — CustomerIQ interactive dashboard file (.pbix)

📂 report — Final analysis report in PDF format

---

## 🧩 The Business Problem

A retail company noticed shifting purchasing patterns across customer demographics, product categories, and payment preferences. Leadership needed answers, not just data. The central question driving this entire project was:

> "How can the company use consumer shopping data to identify trends, improve customer engagement, and optimise marketing and product strategy?"

To answer this, the project was structured across five analytical layers — data cleaning, feature engineering, SQL business intelligence, customer segmentation, and interactive dashboarding.

---

## 🗂️ Dataset Overview

The dataset contains 3,900 rows and 18 columns covering every major dimension of retail customer behavior.

👤 Customer Demographics — Age, Gender, Location

🛒 Purchase Details — Item Purchased, Category, Amount in USD, Season, Size, Color

📦 Subscription and Loyalty — Subscription Status, Previous Purchases

⭐ Behavior and Engagement — Discount Applied, Review Rating, Shipping Type, Purchase Frequency

🔧 Engineered Features — age_group, purchase_frequency_days, Purchase_Date created synthetically for time-series analysis

One data quality issue was resolved upfront. 37 missing values in the Review Rating column were imputed using category-level medians, preserving distributional integrity without introducing bias into the dataset.

---

## ⚙️ Methodology

The project follows a structured five-step analytics pipeline consistent with professional data environments.

🔹 Step 1 — Exploratory Data Analysis using Python

The dataset was loaded using pandas and profiled for structure and summary statistics. 37 null values were identified in the Review Rating column and resolved via category-median imputation. All column names were standardised to snake_case. The promo_code_used column was confirmed redundant against discount_applied and subsequently dropped.

🔹 Step 2 — Feature Engineering using Python

Three new analytical columns were created. The age_group column bins continuous age values into meaningful customer segments. The purchase_frequency_days column was derived from behavioral purchase data. A synthetic Purchase_Date column was constructed to enable time-series analysis and unlock Power BI time intelligence DAX functions such as TOTALYTD and PREVIOUSMONTH.

🔹 Step 3 — Database Integration using SQLAlchemy and PostgreSQL

The Python environment was connected to PostgreSQL via SQLAlchemy. The cleaned DataFrame was loaded into a structured relational schema, making the data ready for business-level querying.

🔹 Step 4 — SQL Business Intelligence using PostgreSQL

10 structured queries were executed covering revenue attribution by gender, customer loyalty classification using CASE WHEN logic, product rankings using RANK window functions, discount risk identification, and shipping behavior analysis across customer segments.

🔹 Step 5 — Power BI Dashboard using DAX and Power BI Desktop

The CustomerIQ dashboard was built across 4 thematic pages with 5 custom DAX measures, cross-filtering slicers for Gender, Category, Subscription Status, and Shipping Type, and drill-through navigation connecting all pages.

---

## 🔎 SQL Business Intelligence Results

### 💰 Revenue by Gender

Male customers generated $157,890 in total revenue at 67.7% of the base, while female customers contributed $75,191 at 32.3%. The average transaction values are remarkably close — $60.31 for male and $58.98 for female — confirming the gap is driven entirely by volume, not spending power. This is a campaign opportunity, not a product problem.

---

### ⭐ Top 5 Products by Average Review Rating

🥇 Gloves — 3.86 out of 5.0 — Accessories

🥈 Sandals — 3.84 out of 5.0 — Footwear

🥉 Boots — 3.82 out of 5.0 — Footwear

4️⃣ Hat — 3.80 out of 5.0 — Accessories

5️⃣ Skirt — 3.78 out of 5.0 — Clothing

---

### 🚚 Shipping Type vs. Average Purchase Amount

Express shipping customers spend an average of $60.48 per transaction versus $58.46 for Standard — a $2.02 delta. Higher-spend customers are self-selecting premium shipping. This is a clear behavioural upsell signal that can be packaged into a loyalty perk bundle.

---

### 📋 Subscriber vs. Non-Subscriber Analysis

Subscribed — 1,053 customers · $59.49 average spend · $62,645 total revenue · 27% of base

Non-Subscribed — 2,847 customers · $59.87 average spend · $170,436 total revenue · 73% of base

The near-identical average spend between both groups is the critical finding. The entire revenue gap is explained by volume, not behaviour. Converting even a fraction of the 2,847 non-subscribers at no change to their natural spend pattern unlocks over $108,000 in subscription revenue.

---

### 🏷️ Discount-Dependent Products — Risk Register

🔴 Hat — 50.00% discount rate — 1 in 2 sales requires a discount — HIGH RISK

🔴 Sneakers — 49.66% discount rate — approaching full discount dependency — HIGH RISK

🔴 Coat — 49.07% discount rate — seasonal markdown risk — HIGH RISK

🟠 Sweater — 48.17% discount rate — winter clearance pattern — MEDIUM HIGH

🟠 Pants — 47.37% discount rate — monitor closely — MEDIUM HIGH

---

### 💎 High-Spending Discount Users

839 customers, representing 21.5% of the total base, applied a discount and still spent above the dataset average of $59.76. Purchase amounts in this group range from $62 to $100. This cohort represents premium deal-seekers — high-value customers who respond to promotions without needing deep discounts to convert. They are best protected with personalised threshold-based offers rather than blanket price reductions.

---

### 🏆 Top 3 Products per Category by Total Orders

Accessories — Jewelry 171 orders · Sunglasses 161 · Belt 161

Clothing — Blouse 171 orders · Pants 171 · Shirt 169

Footwear — Sandals 160 orders · Shoes 150 · Sneakers 145

Outerwear — Jacket 163 orders · Coat 161 · Hoodie 159

Order volumes are tightly clustered between 145 and 171 across all categories, indicating a balanced product portfolio with no single dominant SKU. Category anchors including Jewelry, Blouse, Sandals, and Jacket are prime candidates for featured placement in marketing campaigns.

---

## 👥 Customer Segmentation

Customers were classified into three behavioural segments using CASE WHEN logic applied to the previous_purchases column.

🟢 Loyal — 3,116 customers — 79.9% of base — 10 or more previous purchases — Reward and Upsell

🟡 Returning — 701 customers — 18.0% of base — 2 to 9 previous purchases — Nurture and Upgrade

🔴 New — 83 customers — 2.1% of base — 0 to 1 previous purchases — Onboard and Convert

The 80% Loyal base is a significant competitive strength. However, only 83 new customers represent a serious top-of-funnel problem that the strong retention figures are currently masking from leadership.

---

### 📊 Revenue by Age Group

Young Adult 18 to 35 — $62,143 — 26.6% of total revenue

Middle-Aged 36 to 55 — $59,197 — 25.4% of total revenue

Adult — $55,978 — 24.0% of total revenue

Senior 56 and above — $55,763 — 23.9% of total revenue

Revenue is remarkably balanced across all four age groups, ranging from $55,763 to $62,143. This resilience reduces concentration risk but signals a one-size-fits-all approach across segments. Differentiated age-based messaging would likely unlock meaningful incremental revenue from each group.

---

## 📊 Power BI Dashboard — CustomerIQ

The CustomerIQ Power BI dashboard translates all analytical findings into a stakeholder-ready, interactive reporting tool structured across four thematic pages, each designed for a specific audience.

📌 Page 1 — Executive Overview

KPI cards, subscription status donut chart, revenue by category, and sales by category. Built for C-Suite and Senior Management who need a one-screen performance summary without navigating into detail.

📈 Page 2 — Sales Deep Dive

Monthly revenue trend, quarterly year-on-year comparison, weekday versus weekend revenue split, and seasonal revenue breakdown. Built for Sales Directors and Category Managers tracking performance over time.

👤 Page 3 — Customer Segmentation

Segment distribution, age group revenue heatmap, gender revenue split, and a spend versus rating scatter plot. Built for CRM and Marketing teams planning targeted engagement strategies.

📦 Page 4 — Product and Shipping

Top products matrix with data bars, discount dependency risk table, shipping type versus revenue combo chart, and a season by shipping heatmap. Built for Product Managers and Operations teams reviewing supply and pricing decisions.

---

### 📐 DAX Measures Implemented

Total Revenue — sums all purchase amounts across the filtered dataset

Avg Purchase Amount — calculates average transaction value responding to all active slicers

Avg Review Rating — average rating using category-level median imputation for 37 missing values

Subscription Rate % — live percentage of subscribed customers relative to total customer count

High-Spend Discount Customers — count of customers who applied a discount and still exceeded the average purchase amount

---

## 💡 Key Findings

🔑 Male customers generate 2.1 times more revenue than female customers, driven entirely by volume rather than per-transaction spend difference.

🔑 80% of the customer base is already Loyal, but only 83 new buyers entered the funnel — a critical acquisition warning that retention figures are currently hiding.

🔑 Hat, Sneakers, and Coat each carry approximately 50% discount rates, representing a direct margin risk that requires an immediate pricing strategy review.

🔑 73% of customers are non-subscribers despite spending virtually the same per transaction as subscribers, leaving over $108,000 in subscription revenue unconverted.

🔑 Express shipping customers average $2.02 more per transaction, a proven behavioural signal that can be monetised through a structured loyalty tier.

🔑 839 customers representing 21.5% of the base are high-spend discount users — a premium deal-seeker cohort that should never be treated with blanket price cuts.

---

## 🎯 Strategic Recommendations

1️⃣ Scale Subscription Acquisition — Highest Priority

With 73% of customers unsubscribed despite identical spending behaviour, this is the single largest revenue lever available without acquiring a single new customer. Target the 2,518 frequent buyers who are not yet subscribers with value-led incentives including early collection access, free express shipping, and birthday discounts. No change to their natural spending is required. Conversion alone unlocks over $108,000 in subscription revenue.

---

2️⃣ Protect Margins on Discount-Heavy Products

Hat, Sneakers, and Coat each require a discount on roughly 1 in 2 sales. Replace blanket discounts with personalised threshold-based promotions — for example, spend $80 and receive 15% off Hats. This maintains conversion rates for price-sensitive buyers while meaningfully protecting gross margin across the category.

---

3️⃣ Invest in Female-Segment Campaigns

Female customers contribute 32% of revenue despite nearly identical per-transaction values compared to male customers. The gap is purely a volume problem, not a product or pricing issue. Invest in category-specific campaigns across Clothing and Accessories through social commerce and influencer partnerships to close the acquisition volume gap.

---

4️⃣ Build a Returning-to-Loyal Conversion Programme

The 701 Returning customers represent the clearest near-term loyalty opportunity in the dataset. A structured nurture sequence combining personalised product recommendations with a milestone reward at purchase number 10 could convert a meaningful portion of this segment to Loyal status within 6 to 12 months.

---

5️⃣ Monetise the Express Shipping Signal

Express shipping customers already spend $2.02 more per transaction naturally. Bundling priority shipping with a repeat-purchase discount converts this existing behavioural signal into a $5 to $8 incremental revenue opportunity per engaged customer through a dedicated Express Perks loyalty tier.

---

6️⃣ Fix the New Customer Acquisition Funnel — Critical

Only 83 customers classified as New is a serious warning sign. The business is sustaining itself on a loyal existing base without replenishing it at the top. Allocate budget toward paid search for category-specific terms, referral incentives for existing Loyal customers, and abandoned-cart remarketing flows. Set a firm KPI target to grow the New customer segment to 5% or above within 12 months.

---

## 🗺️ Next Steps

⏱️ 0 to 3 months — Deploy the subscription conversion campaign targeting 2,518 non-subscriber frequent buyers. Implement personalised discount thresholds for Hat, Sneakers, and Coat to begin margin recovery immediately.

📅 3 to 6 months — Build a time-series revenue forecasting model using the engineered Purchase_Date column. Integrate real-time data refresh into the Power BI dashboard via PostgreSQL Direct Query or an API connector.

🚀 6 to 12 months — Develop a predictive churn model using logistic regression or random forest on the Returning customer segment. Apply RFM scoring — Recency, Frequency, Monetary — for dynamic segmentation inside the CRM platform.

---

## 👨‍💻 About This Project

This project was built as a senior data analyst portfolio piece demonstrating end-to-end analytical thinking — from raw data ingestion and rigorous cleaning, through SQL-driven business intelligence, to a commercially grounded executive dashboard. Every finding is paired with a business interpretation. Every recommendation is tied to a quantified opportunity. The goal was not simply to describe the data, but to prescribe what the business should do next.

🛠️ Python · MYSQL · Power BI · DAX · SQLAlchemy · Pandas

📁 3,900 records · 18 features · 4 engineered columns · 10 SQL queries · 4-page dashboard

