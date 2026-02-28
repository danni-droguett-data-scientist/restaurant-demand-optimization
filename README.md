# Restaurant Demand Optimization (Forecasting + KPIs)

End-to-end Data Science project to **forecast demand** and **optimize restaurant profitability**, combining:
- Exploratory Data Analysis (EDA)
- Operational & financial KPIs
- Menu engineering
- Predictive models (baselines + ML + time series)
- Evaluation and business recommendations

> Built as a portfolio project (GitHub/LinkedIn): modular, reproducible, and adaptable to different restaurant contexts.

**Language / Idioma:** English | [Español](README.es.md)

---

## Business Goal

Optimize:
- **Profitability** (margin and estimated profit)
- **Waste reduction** (better purchasing and inventory planning)
- **Operations** (staffing by shift, production planning)
- **Demand forecasting**: **daily**, **weekly**, and **30-day** horizons

---

## Config & Assumptions (adaptable)

These parameters are configurable to reuse the project across different restaurants:

- **Base currency**: CLP (configurable)
- **Tax**: VAT 19% (configurable)
- **Tip**: optional 10% (excluded from revenue by default)
- **Channels**: `dine_in`, `takeaway`, `delivery`
- **Menu size (SKUs)**: typically 40–80 (configurable)
- **Typical opening hours**: 11:00–00:00, 6 days/week (configurable)

---

## Data (POS & Operations)

Expected data (real or synthetic):
- Date/time, tickets/receipts, products, quantities, prices
- Ingredient/recipe costs (for food cost)
- Inventory and turnover
- Staffing per shift and labor costs (for productivity)
- Monthly fixed costs (for profit estimates)

> Best practice: `data/raw/` and `data/processed/` are not committed to Git.

---

## Project Structure

```text
restaurant-demand-optimization/
├── data/
│   ├── raw/              # gitignored
│   └── processed/        # gitignored
├── notebooks/
├── src/
│   ├── forecasting/
│   ├── kpis/
│   └── main.py
├── reports/
├── README.md
├── README.es.md
├── requirements.txt
├── .gitignore
└── .gitattributes