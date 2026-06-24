# Part 4 – Tableau Executive Dashboard & Data Storytelling
**BITSoM Business Analytics Certification**  
**Repository:** `studentname_studentid_part4_tableau_dashboard`

---

## Business Problem Summary

As a business analyst for a retail leadership team, the objective is to build an executive Tableau dashboard that monitors sales performance, profitability, customer segments, category performance, shipping performance, discount impact, and return patterns. The dashboard must tell a clear business story — not just display charts — and support leadership decision-making on marketing, pricing, inventory, and operations.

**Key Business Questions:**
- Which regions, categories, and customer segments are driving performance?
- Where is the business losing money (discounts, returns, low-margin categories)?
- What are the trends over time?
- Which shipping modes and channels are most efficient?

---

## Dataset Description

**File:** `data/dashboard_sales_data.xlsx`  
**Sheet:** `dashboard_sales_data`  
**Rows:** 4,200 orders  
**Period:** 2024–2025

| Field | Type | Description |
|---|---|---|
| order_id | String | Unique order identifier |
| order_date | Date | Order placement date |
| ship_date | Date | Shipping date |
| customer_id | String | Unique customer identifier |
| customer_segment | Categorical | Consumer, Corporate, Home Office |
| region | Categorical | North, South, East, West |
| state | Categorical | Indian state |
| city | Categorical | City name |
| category | Categorical | Furniture, Office Supplies, Technology |
| sub_category | Categorical | 13 sub-categories |
| product_name | String | Product name |
| ship_mode | Categorical | Standard Class, Second Class, First Class, Same Day |
| sales | Numerical | Order revenue (₹) |
| quantity | Numerical | Units ordered |
| discount | Numerical | Discount applied (0–1 scale) |
| profit | Numerical | Order profit (₹) — can be negative |
| return_flag | Binary | 1 = returned, 0 = not returned |
| delivery_days | Numerical | Days between order and ship |
| customer_rating | Numerical | Rating 1–5 (32 missing values) |
| campaign_channel | Categorical | Organic, Paid, Email, Social, Referral (24 missing) |

**Data Quality Notes:**
- 32 missing values in `customer_rating` — excluded from rating-specific views; noted in tooltips
- 24 missing values in `campaign_channel` — excluded from channel analysis
- No missing values in core measures (sales, profit, quantity, discount)
- Dates stored as Excel serial numbers — converted correctly to date format in Tableau

---

## Tableau Workbook Description

**File:** `tableau/executive_dashboard.twbx`

The workbook contains:
- 8 individual worksheet views (supporting sheets)
- 1 executive dashboard combining all views
- 5 calculated fields
- 4 interactive filters (Region, Category, Customer Segment, Ship Mode)
- Action filters enabling cross-chart highlighting

**Sheets in Workbook:**
1. Sales Trend View — Line chart of monthly sales and profit
2. Regional Performance View — Horizontal bar chart by region (sales + margin)
3. Category Profitability View — Bar chart by category and sub-category
4. Customer Segment View — Comparison bars for 3 segments
5. Shipping Performance View — Order count and avg delivery by ship mode
6. Discount vs Profit View — Scatter plot + Discount Tier summary bar
7. Return Analysis View — Return rate by category and segment
8. Campaign Channel View — Sales and margin by acquisition channel

---

## Calculated Fields Created

| Field Name | Formula | Purpose |
|---|---|---|
| **Profit Margin** | `SUM([profit]) / SUM([sales])` | Profitability % for all views |
| **Cost** | `SUM([sales]) - SUM([profit])` | Cost of goods derived from sales and profit |
| **Average Order Value** | `SUM([sales]) / COUNT([order_id])` | Revenue efficiency per transaction |
| **Return Rate** | `SUM([return_flag]) / COUNT([order_id])` | Proportion of orders returned |
| **Shipping Delay Bucket** | IF/ELSEIF on delivery_days | Groups 0, 1–2, 3–4, 5–6, 7+ days into labelled buckets |
| **Discount Tier** | IF/ELSEIF on discount | Groups 0%, 1–10%, 11–20%, 21–30%, >30% |
| **Year** | `YEAR([order_date])` | Year-over-year comparison |

---

## Dashboard Components

**KPI Cards (Top Row):**
- Total Sales: ₹21.7 Crore
- Total Profit: ₹3.33 Crore
- Overall Profit Margin: 15.3%
- Return Rate: 4.5%

**Charts (5 minimum, 8 included):**
1. Monthly Sales & Profit Trend (Line Chart)
2. Sales by Region with Margin (Bar Chart)
3. Category & Sub-Category Profitability (Bar Chart)
4. Customer Segment Performance (Side-by-Side Bars)
5. Discount Tier vs Profit Margin (Bar + Scatter)
6. Return Rate by Category (Horizontal Bar)
7. Shipping Mode Volume & Speed (Bar Chart)
8. Campaign Channel Performance (Bar with Color)

---

## Filters and Interactions Used

| Filter | Type | Applied To |
|---|---|---|
| Region | Quick filter | All views |
| Category | Quick filter | All views |
| Customer Segment | Quick filter | All views |
| Ship Mode | Quick filter | Shipping, Discount, and Return views |
| Order Date | Range filter | Trend and regional views |

**Action Filters:** Clicking a region in the Regional Performance View cross-filters Category and Segment views to show performance only for that region.

---

## Key Business Insights

1. **Technology drives 70.9% of sales and 84.2% of profit** at an 18.2% margin — the company's core strength.
2. **Furniture is a risk** — 6.9% margin + 7.7% return rate create compounding profitability pressure.
3. **Discounts above 20% destroy value** — orders with >30% discount generate net losses (−5.0% margin).
4. **South region leads on volume** (₹6.47 Cr); East region leads on margin (15.6%).
5. **Home Office segment** is simultaneously the largest and most profitable customer group.
6. **Standard Class** carries 58% of orders with the slowest delivery (4.7 days avg).
7. **Organic channel dominates** in volume (40.9% of orders); Social and Referral have the best margins.
8. **Sales grew 4.3% YoY** from ₹10.62 Crore (2024) to ₹11.08 Crore (2025).

---

## Dashboard Story Summary

The dashboard tells a story of a profitable but uneven business. Technology is the engine; Furniture is the drag. The South market is thriving; the East is quietly efficient. Discounting is being applied too generously in some pockets, with 64 orders actually losing money. Shipping is predominantly via Standard Class, which delivers the slowest experience. The Organic acquisition channel is strong, but Referral and Social deserve more investment given their above-average margins.

**The three most urgent leadership actions:** (1) Cap discounts at 25%, (2) Address Furniture returns, and (3) Invest in East region capacity.

---

## Assumptions and Limitations

- Profit margin is calculated as SUM(profit)/SUM(sales) — this is gross margin and excludes operating costs, marketing spend, and logistics overhead.
- Return flag is binary; the reason for return is not captured, limiting root cause analysis.
- Campaign channel has 24 missing values; campaign attribution is therefore slightly incomplete.
- Delivery days = ship_date − order_date; actual delivery to customer may differ if the ship date is not the same as arrival.
- Customer ratings have 32 missing values; satisfaction analysis by segment or region should be interpreted with this caveat.
- The dataset covers 2 years; multi-year trend analysis would require additional historical data.

---

## Screenshots Included

| File | Contents |
|---|---|
| `screenshots/full_dashboard.png` | Complete executive dashboard with KPI cards, all charts, and filters |
| `screenshots/sales_trend_view.png` | Sales and profit trend over time (line chart) |
| `screenshots/regional_performance_view.png` | Regional performance bar chart with margin colour |
| `screenshots/category_profitability_view.png` | Category and sub-category profitability |
| `screenshots/filter_interaction_view.png` | Dashboard with filter applied (e.g., Technology category selected) |

---

## Repository Structure

```
part4_tableau_dashboard/
├── data/
│   └── dashboard_sales_data.xlsx
├── tableau/
│   └── executive_dashboard.twbx
├── outputs/
│   ├── dashboard_story.md
│   ├── business_insights.md
│   └── chart_selection_justification.md
├── screenshots/
│   ├── full_dashboard.png
│   ├── sales_trend_view.png
│   ├── regional_performance_view.png
│   ├── category_profitability_view.png
│   └── filter_interaction_view.png
└── README.md
```
