# Dollar Bank — Customer Churn Analysis (SQL • Python • Tableau)

**End-to-end project:** exploratory analysis with SQL, a deep-dive EDA with Python, and an interactive Tableau dashboard to present actionable business insights.

---

## Table of contents
- [Introduction](#introduction)  
- [Repository structure](#repository-structure)  
- [Data](#data)  
- [Methodology](#methodology)  
- [Dashboard & Visuals (what to look at)](#dashboard--visuals-what-to-look-at)  
- [Key findings & insights](#key-findings--insights)  
- [Recommendations](#recommendations)  
- [How to run the analysis (quick)](#how-to-run-the-analysis-quick)  
- [Screenshots](#screenshots)  
- [License & notes](#license--notes)

---

## Introduction
Dollar Bank asked for an analysis to understand why customers were leaving its credit card product and how losses can be reduced. This project joins three datasets, performs EDA and feature engineering in Python, and implements a polished, interactive Tableau dashboard that surfaces the key churn drivers and highest-impact customer segments.

---




## Data
- `bankchurners.csv` — account & churn flags, months-on-book, card category, credit limit, contact counts.  
- `basic_client_info.csv` — demographics: `gender`, `education_level`, `income_category`, `marital_status`, `customer_age`.  
- `enriched_churn_data.csv` — aggregated transaction metrics per client (total transaction amount, count, change metrics).

**Churn definition:** `Attrited Customer` flag in `bankchurners.csv`. When computing rates in the dashboard we use distinct clients (`COUNTD(clientnum)`) to avoid double counting.

---

## Methodology
1. **SQL**: use SELECT/joins to understand row counts and to produce a clean combined table for analysis.  
2. **Python**: deep-dive EDA (Pandas), data cleaning, distribution checks, correlation checks, and feature creation (age bins, months-on-book buckets, churn flag, LOD-like client aggregates where needed).  
3. **Tableau**: build interactive visuals — KPI cards, heatmaps, grouped bar charts with gender, scatterplots with trend lines, and Pareto analyses — and assemble into a dashboard for stakeholder consumption.

---

## Dashboard & Visuals (what to look at)

### KPI overview
![KPI cards](screenshots/screenshot_kpi.png)

**What it shows**: total customers (~10K), average age (46 yrs), average transaction amount (all customers ≈ $4,404), average for churned customers ≈ $3,095, and overall churn ≈ 16%.

---

### Customer Churn Summary & Relationship period
![Summary & Relationship](screenshots/screenshot_summary_relationship.png)

**What it shows**: a detailed churn summary table split by age group and gender, and a grouped bar chart of churn by relationship period (Mid-Term, Established, Long-Term, Very-Long-Term) split by gender. This helps identify whether churn concentrates at a particular customer tenure.

---

### Churn by card type & spending behavior
![Card type & Spending vs Churn](screenshots/screenshot_spend_cardtype.png)

**What it shows**: counts of churned customers by card type and demographics, and a scatterplot of `Total Transaction Amount ($)` vs `Total Transaction Count` (blue = churned, orange = existing). The scatter shows churners cluster at lower transaction counts and amounts.

---

### Churn by education & age
![Education × Income & Age groups](screenshots/screenshot_edu_age.png)

**What it shows**: (left) heatmap of churn rate (%) by `Education Level` (rows) × `Income Category` (columns); (right) churn rate by age bins (20s, 30s, 40s, ...). Useful for demographic targeting.

---

### Pareto analysis — segments & churn concentration
![Pareto: clients vs churned](screenshots/screenshot_pareto_clients_churned.png)

**What it shows**: Pareto charts with segments created from combinations of `Gender`, `Education Level`, and `Marital Status`. They reveal which small set of segments generate the majority of churn (the "vital few").

---

## Key findings & insights
- **Overall churn ~16%** — substantial and worth addressing.  
- **Lower spenders churn more** — churned customers have average transaction amounts ~\$3.1k vs \$4.4k for overall customers; churners often have <100 transactions.  
- **Demographic hotspots** — female customers 41–50 and certain education×income intersections show elevated churn.  
- **Relationship-period risk** — established (25–36 months) and long-term (37–48 months) buckets show notable churn in several cohorts.  
- **Pareto insight** — a small set of segments (female graduates; male graduates single) account for a disproportionate share of churn.

---

## Recommendations
1. Target high-churn segments with tailored retention offers.  
2. Offer activity incentives for low-activity customers (increase transaction frequency).  
3. Implement milestone outreach for customers around 24–36 months tenure.  
4. A/B test retention offers for top 3 churn-driving segments.

---

## How to run the analysis (quick)
1. Open `notebooks/customer_churn.ipynb` in Jupyter Lab / VS Code.  
2. Ensure the CSVs are in `data/` (same path the notebook expects).  
3. Install required packages:
```bash
pip install pandas numpy matplotlib seaborn jupyterlab


## Repository structure

