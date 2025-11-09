# Crisis Impact Analysis Dashboard

A Streamlit dashboard to analyze **pre-crisis vs crisis** performance for a food-delivery startup. It turns raw CSVs into stakeholder-ready KPIs, trends, and ranked impact lists, with exports and built-in explainers.

![hero](docs/hero.png)

---

## What problem does this solve?

QuickBite Express faced a June 2025 crisis: a viral food-safety incident and a delivery outage led to sharp drops in orders, satisfaction, and partner retention. Leadership needs clear, actionable insight across customers, orders, delivery performance, ratings, and revenue to guide recovery actions. :contentReference[oaicite:0]{index=0}

This dashboard operationalizes the **Primary Analysis** questions (pre-crisis vs crisis) so teams can:
- Quantify demand decline month-over-month.
- Identify most affected cities and high-volume restaurants.
- Track cancellations and SLA compliance shifts.
- Monitor ratings and extract negative-review themes.
- Estimate revenue impact and loss per month. 

---

## Thought process (approach)

**1) Periodization and consistency**
- Label each order as `Pre-Crisis` or `Crisis` using a fixed cutoff (2025-06-01) to ensure consistent comparisons across all views. :contentReference[oaicite:2]{index=2}

**2) Filter-first design**
- Build a single filtered “orders view” (period, city, restaurant, date range). Feed every KPI and chart from this view for trustable drill-downs.

**3) KPI definitions that map to the brief**
- Monthly Orders Decline compares average monthly orders (crisis vs pre).  
- Cancellation Rates and SLA Compliance computed by period.  
- Ratings monthly average and negative-keyword extraction on crisis reviews.  
- Revenue Impact estimates average monthly revenue gap. 
**4) High-signal visualizations**
- Overview trend with crisis cutoff.
- Ranked bar charts for cities and restaurants, focusing on high-volume operators. 

**5) Explainability and exports**
- “About this chart” blocks under each viz.
- One-click CSV exports for the filtered data and ranked declines.

---

## Final output (deliverables)

- **Interactive dashboard** (`app.py`):  
  - KPIs: Monthly Orders Decline, Cancel Rates (pre vs crisis), SLA Decline  
  - Tabs: Overview, Cities, Restaurants, Ratings, Revenue  
  - Filters: Period, City, Restaurant, Date Range  
  - Guided help and chart explainers  
  - CSV exports (filtered orders, city/restaurant declines)

- **Reproducible analysis code** (`utils/`):  
  - `data_loader.py`: loads CSVs, creates date fields, applies crisis labeling.  
  - `analysis.py`: computes KPIs and aggregates aligned to the challenge prompts.  
  - `visualizations.py`: Plotly charts with consistent styling.



---

## Features

- Filters that apply everywhere
- Plotly visuals with consistent template and helpful hovers
- “About this chart” explainers and optional guided tour
- One-click CSV exports for what you’re seeing

---

## Repository structure
streamlit_app_raw/
├─ app.py
├─ utils/
│ ├─ init.py
│ ├─ data_loader.py
│ ├─ analysis.py
│ └─ visualizations.py
├─ data/
│ ├─ fact_orders.csv
│ ├─ fact_order_items.csv
│ ├─ fact_delivery_performance.csv
│ ├─ fact_ratings.csv
│ ├─ dim_delivery_partner_.csv 
│ ├─ dim_customer.csv
│ ├─ dim_menu_item.csv
│ └─ dim_restaurant.csv
└─ .streamlit/

