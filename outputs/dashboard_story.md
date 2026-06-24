# Dashboard Story – Retail Executive Sales Dashboard
## For Leadership Audience | FY 2024–2025 | 4,200 Orders | ₹21.7 Crore Revenue

---

## 1. Executive Summary

The retail business delivered ₹21.7 crore in total sales across 4,200 orders in the 2024–2025 period, achieving an overall profit margin of 15.3% and a net profit of ₹3.33 crore. Sales grew by 4.3% from 2024 to 2025, with both order volume and revenue increasing steadily.

The business story is a tale of two halves: **Technology is the engine of profitability** (18.2% margin, 84% of total profit), while **Furniture is the hidden drag** (6.9% margin, high returns). The South region leads on volume; the East quietly earns the best margin. And the data tells a sharp, actionable lesson on discounting: **every percentage point of discount above 20% costs significantly more than it returns**.

This dashboard is designed to give leadership an at-a-glance view of where performance is strong, where risk is accumulating, and what actions have the highest potential impact.

---

## 2. What Is Performing Well

**Technology Category — The Clear Revenue Engine**
Technology accounts for ₹15.39 crore in sales (70.9% of the total) at an 18.2% profit margin — the highest of all three categories. All four sub-categories (Copiers, Accessories, Phones, Machines) are profitable, with margins ranging from 18.0% to 18.5%. The business is well-positioned in Technology and should protect and grow this segment.

**South Region — Highest Sales Volume**
The South region leads all regions with ₹6.47 crore in sales and ₹99.9 lakh in profit. With 1,210 orders — 28.8% of all orders — South is the most active market. Customer demand here is robust.

**Home Office Segment — Best Margin Profile**
Despite having the most orders (1,446), the Home Office segment earns the best margin (15.5%) and the highest absolute profit (₹1.16 crore). This segment is both large and profitable — a rare combination.

**Organic Channel — Volume Leader**
Organic channel generates 40.9% of all sales with 1,694 orders, making it the backbone of customer acquisition. No paid media cost suggests strong brand recognition or SEO performance.

**Year-Over-Year Growth**
Sales grew from ₹10.62 crore (2024) to ₹11.08 crore (2025), a 4.3% increase. Both order count and revenue per order improved slightly, indicating healthy business momentum.

---

## 3. What Is Underperforming

**Furniture Category — Low Margin, High Returns**
Furniture generates ₹5.16 crore in sales but earns only a 6.9% profit margin — less than half the company average of 15.3%. Tables and Bookcases sub-categories sit at just 5.7% margin. Worse, Furniture has a 7.7% return rate — 2.6× higher than Technology (3.0%). The combination of thin margins and high returns makes Furniture the highest business risk in the portfolio.

**High-Discount Orders (>20%) — Value Destruction Zone**
Orders with discounts above 20% (1,150 orders, 27.4% of all orders) collectively earn only an 8.0% average margin. Orders with >30% discounts actually lose money (−5.0% margin, ₹1.02 lakh in losses across 64 orders). Despite being a small volume, this bucket represents a policy failure — prices are being cut below cost for some orders.

**Standard Class Shipping — Slow Delivery at Scale**
With 2,435 orders using Standard Class and an average delivery time of 4.7 days, a large portion of customers experience slower-than-expected delivery. This is likely contributing to dissatisfaction and indirectly to Furniture's high return rate.

**West Region — Lowest Margin**
The West region earns the lowest profit margin (15.1%) despite generating ₹4.89 crore in sales, similar to the East. The gap versus East (15.6%) may seem small, but applied across ₹4.89 crore in sales, it represents approximately ₹24 lakh in foregone profit.

---

## 4. What Risks Are Visible

**Discount Policy Risk:** 64 orders exceeded 30% discount and collectively lost ₹1.02 lakh. If this trend continues without a cap, cumulative losses will grow. The current discount approval process appears to lack guardrails.

**Furniture Return Rate Risk:** An 88-return volume in Furniture at 7.7% return rate creates reverse logistics costs, product write-offs, and reputational risk. Returns in Furniture likely eliminate the original order's margin entirely.

**Single-Category Revenue Concentration:** Technology represents 70.9% of revenue. A supply disruption, competitive price pressure, or regulatory change in Technology could significantly impact the total business. Over-reliance on one category creates fragility.

**Campaign Channel Attribution Gap:** 24 orders (0.6%) have missing `campaign_channel` data. If this scales, marketing attribution will become unreliable and budget allocation decisions will be flawed.

---

## 5. What Opportunities Are Visible

**Improve Furniture Profitability:** Pricing adjustments of even 3–4 percentage points in Furniture margins would add ₹15–20 lakh to annual profit without requiring revenue growth.

**Grow East Region:** East region has the best profit margin (15.6%) but the fewest orders (897). It is the most efficient region for value creation. Investing in marketing, sales capacity, and delivery infrastructure in East could yield high-quality growth.

**Referral and Social Channel Expansion:** Referral (15.7% margin) and Social (15.8% margin) channels deliver above-average profitability. These likely come with lower customer acquisition costs than Paid. Scaling referral programmes and social commerce investment could grow high-margin revenue.

**Email Marketing Scale-Up:** Email generates ₹3.45 crore in sales at a 15.5% margin across 657 orders — one of the more consistent channels. Email is generally low-cost at scale; increasing send frequency and personalisation could compound returns.

**Home Office Upsell Opportunity:** Home Office segment is already the largest and most profitable. Targeted cross-sell campaigns (e.g., Technology + Office Supplies bundles for home office setups) could increase average order value.

---

## 6. Recommended Business Actions

| Priority | Action | Expected Outcome |
|---|---|---|
| **1 – Immediate** | Cap all discounts at 25%; require director approval above 20% | Eliminate loss-making >30% discount orders; improve margins by ~0.5pp |
| **2 – Short Term** | Investigate and address Furniture return root causes | Reduce 7.7% Furniture return rate; protect thin margins |
| **3 – Short Term** | Reprice Furniture Tables and Bookcases sub-categories | Bring sub-category margins from 5.7% toward 8–10% |
| **4 – Medium Term** | Invest in East region marketing and supply chain | Grow highest-margin region's order volume by 15–20% |
| **5 – Medium Term** | Scale Social and Referral acquisition channels | Grow above-average margin order base |
| **6 – Ongoing** | Audit Standard Class delivery performance | Reduce delivery delays; improve customer satisfaction and return rates |
| **7 – Strategic** | Diversify revenue beyond Technology | Reduce 70.9% Technology dependency through Furniture and Office Supplies improvement |

---

## 7. Limitations of the Dashboard

- **No customer-level analysis:** The dataset contains `customer_id` but the dashboard does not show customer lifetime value (CLV) or repeat purchase rates. High-value customers may be receiving unnecessary discounts.
- **No cost of acquisition for channels:** The campaign channel analysis shows revenue and margin, but without media spend data, the true ROI of Paid, Email, or Social channels cannot be confirmed.
- **Return reason not captured:** `return_flag` is binary. Without knowing why orders were returned, targeted interventions for Furniture are difficult to design precisely.
- **2 years of data only:** Seasonality analysis is limited to 2024–2025. Multi-year trend analysis would improve forecasting accuracy.
- **Customer rating has 32 missing values:** The customer_rating field has gaps that prevent a fully complete satisfaction analysis by segment, region, or delivery mode.
- **City/state-level analysis limited:** The dashboard shows regional performance, but the dataset contains city-level data that could surface micro-market opportunities not visible at the regional level.

---

## 8. Suggested Next Analysis

- **Customer Lifetime Value (CLV) by segment:** Build cohort analysis to determine which segments retain and grow over time.
- **Discount elasticity modelling:** Use regression (as in Part 3) to quantify the precise profit impact of each discount percentage point — move from observation to quantified policy.
- **Delivery delay vs. return rate correlation:** Test whether stores/orders with delivery_days > 5 have statistically higher return_flag rates.
- **Sub-category deep dive for Furniture:** Identify whether specific product lines within Tables and Bookcases drive the majority of losses and returns.
- **Campaign channel CAC analysis:** Integrate ad spend data to compute true channel ROI, not just revenue and margin from sales data.
- **State-level mapping:** Create a geographic heat map of profitability by state to identify micro-markets for investment or cost reduction.
