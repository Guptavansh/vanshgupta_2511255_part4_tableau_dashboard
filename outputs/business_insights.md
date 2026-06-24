# Business Insights – Executive Dashboard
## Dataset: dashboard_sales_data.xlsx | 4,200 Orders | 2024–2025

---

## Calculated Fields Created in Tableau

| Calculated Field | Formula | Business Purpose |
|---|---|---|
| **Profit Margin** | `SUM([profit]) / SUM([sales])` | Measures profitability as % of revenue |
| **Cost** | `SUM([sales]) - SUM([profit])` | Derives cost of goods from sales and profit |
| **Average Order Value** | `SUM([sales]) / COUNT([order_id])` | Revenue efficiency per transaction |
| **Return Rate** | `SUM([return_flag]) / COUNT([order_id])` | Proportion of orders returned |
| **Shipping Delay Bucket** | `IF [delivery_days]=0 THEN "Same Day" ELSEIF [delivery_days]<=2 THEN "Fast (1-2 days)" ELSEIF [delivery_days]<=4 THEN "Standard (3-4 days)" ELSEIF [delivery_days]<=6 THEN "Slow (5-6 days)" ELSE "Very Slow (7+ days)" END` | Groups delivery speed into actionable segments |
| **Discount Tier** | `IF [discount]=0 THEN "No Discount" ELSEIF [discount]<=0.10 THEN "Low (1-10%)" ELSEIF [discount]<=0.20 THEN "Medium (11-20%)" ELSEIF [discount]<=0.30 THEN "High (21-30%)" ELSE "Very High (>30%)" END` | Categorises discount levels for profit impact analysis |
| **Year** | `YEAR([order_date])` | Enables year-over-year comparison |

---

## Overall KPI Summary

| Metric | Value |
|---|---|
| Total Sales | ₹21.7 Crore (₹217,017,652) |
| Total Profit | ₹3.33 Crore (₹33,306,313) |
| Overall Profit Margin | **15.3%** |
| Total Orders | 4,200 |
| Return Rate | **4.5%** |
| Average Discount | 13.7% |
| Average Delivery Days | 3.6 days |
| Sales Growth 2024→2025 | **+4.3%** (₹106.2M → ₹110.8M) |

---

## Insight 1 – Sales Trend: Steady Growth with Seasonal Peaks

**Observation:** Total sales grew from ₹10.62 crore (2024) to ₹11.08 crore (2025) — a 4.3% YoY increase. Profit followed the same trajectory, rising from ₹1.65 crore to ₹1.68 crore.

**Data Evidence:** 2024 orders: 2,057 | 2025 orders: 2,143. Sales per order in 2025 is marginally higher.

**Business Interpretation:** The business is growing steadily. Order volume increased by 86 orders (4.2%) while revenue grew proportionally, indicating consistent average order sizes.

**Recommended Action:** Investigate whether growth is driven by new customers or existing customers ordering more. Segment the trend by customer_segment to identify which group is driving growth. Consider seasonal promotion planning based on monthly peaks.

---

## Insight 2 – Regional Performance: South Leads, East Has Highest Margin

**Observation:** South region generates the highest sales (₹6.47 crore, 29.8% of total), but East region achieves the best profit margin (15.6% vs 15.1–15.4% for other regions).

**Data Evidence:**

| Region | Sales | Profit | Margin | Orders |
|---|---|---|---|---|
| South | ₹6.47 Cr | ₹99.9 Lakh | 15.4% | 1,210 |
| North | ₹5.46 Cr | ₹83.1 Lakh | 15.2% | 1,056 |
| West | ₹4.89 Cr | ₹74.0 Lakh | 15.1% | 1,037 |
| East | ₹4.89 Cr | ₹76.0 Lakh | **15.6%** | 897 |

**Business Interpretation:** South region dominates on volume but earns similar margins to others. East's higher margin with fewer orders suggests better pricing discipline or product mix. West has the lowest margin despite significant sales.

**Recommended Action:** Analyse West region's discount and product mix patterns to close the margin gap. Replicate East's margin management practices. Explore what is driving South's volume advantage.

---

## Insight 3 – Category Profitability: Technology Dominates, Furniture Is a Risk

**Observation:** Technology accounts for 70.9% of total sales (₹15.39 crore) and 84.2% of total profit (₹2.80 crore) at an 18.2% margin. Furniture generates ₹5.16 crore in sales but only a 6.9% margin — less than half the overall average.

**Data Evidence:**

| Category | Sales | Profit | Margin |
|---|---|---|---|
| Technology | ₹15.39 Cr | ₹2.80 Cr | **18.2%** |
| Office Supplies | ₹1.15 Cr | ₹17.1 Lakh | 14.9% |
| Furniture | ₹5.16 Cr | ₹35.6 Lakh | **6.9%** |

**Business Interpretation:** Furniture is disproportionately resource-intensive relative to profit contribution. Tables and Bookcases sub-categories have the lowest margins (5.7%), and Furniture also has the highest return rate (7.7% vs 3.0–3.7% for others).

**Recommended Action:** Review pricing strategy for Furniture, especially Tables and Bookcases. Consider whether high-discount Furniture orders should be deprioritised. Explore why Furniture return rates are 2.6× those of Technology.

---

## Insight 4 – Customer Segment Behaviour: Home Office Shows Best Margin

**Observation:** Home Office segment generates the highest sales (₹7.45 crore) and the best profit margin (15.5%), despite having the most orders (1,446). Consumer and Corporate segments show near-identical performance.

**Data Evidence:**

| Segment | Sales | Profit | Margin | Orders |
|---|---|---|---|---|
| Home Office | ₹7.45 Cr | ₹1.16 Cr | **15.5%** | 1,446 |
| Consumer | ₹7.19 Cr | ₹1.10 Cr | 15.3% | 1,355 |
| Corporate | ₹7.06 Cr | ₹1.07 Cr | 15.2% | 1,399 |

**Business Interpretation:** Home Office buyers — likely small business owners or freelancers — have the best margin profile, possibly because they buy premium Technology products with fewer discount demands.

**Recommended Action:** Prioritise Home Office segment in marketing and CRM targeting. Develop tailored product bundles for Home Office buyers. Investigate whether Corporate segment's slightly lower margin is due to negotiated pricing or volume discounts.

---

## Insight 5 – Discount Impact: Discounts Above 20% Destroy Profitability

**Observation:** There is a clear and dramatic decline in profitability as discount levels increase. Orders with no discount earn a 20.6% margin; orders with discounts above 30% actually generate net losses (−5.0% margin).

**Data Evidence:**

| Discount Band | Orders | Sales | Profit | Margin |
|---|---|---|---|---|
| 0% (No Discount) | 1,024 | ₹6.58 Cr | ₹1.35 Cr | **20.6%** |
| 1–10% | 979 | ₹5.76 Cr | ₹98.0 Lakh | 17.0% |
| 11–20% | 1,047 | ₹4.87 Cr | ₹66.3 Lakh | 13.6% |
| 21–30% | 1,086 | ₹4.29 Cr | ₹34.5 Lakh | 8.0% |
| >30% | 64 | ₹20.7 Lakh | **−₹1.02 Lakh** | **−5.0%** |

**Business Interpretation:** The discount threshold for value destruction appears to be above 20%. The >30% discount bucket (64 orders) is generating net losses — these orders consume resources and reduce overall profitability.

**Recommended Action:** Implement a discount cap policy: no approvals above 25% without regional director sign-off. Consider removing the >30% discount tier entirely unless used for strategic accounts. Replace high-discount promotions with value-add offers (free shipping, bundled products).

---

## Insight 6 – Shipping Performance: Standard Class Carries 58% of Orders but Delivers Slowly

**Observation:** Standard Class shipping handles 2,435 of 4,200 orders (58%) with an average delivery time of 4.7 days. Same Day shipping, while fastest (0.4 days), covers only 241 orders (5.7%).

**Data Evidence:**

| Ship Mode | Orders | Sales | Avg Delivery Days |
|---|---|---|---|
| Standard Class | 2,435 | ₹12.28 Cr | 4.7 days |
| Second Class | 894 | ₹4.77 Cr | 2.7 days |
| First Class | 630 | ₹3.19 Cr | 1.8 days |
| Same Day | 241 | ₹1.46 Cr | 0.4 days |

**Business Interpretation:** A large proportion of customers choose Standard Class, which has the slowest delivery. High delivery times may contribute to the overall 4.5% return rate. Customer ratings may also be negatively impacted.

**Recommended Action:** Analyse correlation between delivery_days and customer_rating and return_flag. If a relationship exists, consider upgrading default shipping to Second Class or offering free Standard Class to Second Class upgrades as a loyalty benefit.

---

## Insight 7 – Return Patterns: Furniture Returns Are a Business Risk

**Observation:** Furniture has a return rate of 7.7% — more than double the Technology return rate (3.0%). Office Supplies sits at 3.7%. Overall return rate is 4.5% (189 of 4,200 orders).

**Data Evidence:**

| Category | Returns | Total Orders | Return Rate |
|---|---|---|---|
| Furniture | 88 | 1,147 | **7.7%** |
| Office Supplies | 61 | 1,669 | 3.7% |
| Technology | 42 | 1,384 | **3.0%** |

**Business Interpretation:** Furniture's high return rate, combined with its already-low profit margin (6.9%), creates a compounding profitability risk. Each return in Furniture likely erases any margin earned on the original sale plus incurs logistics costs.

**Recommended Action:** Investigate Furniture return reasons (wrong size, damage, quality mismatch). Implement mandatory product photography and detailed dimension information on listings. Consider a "no return" policy for large Furniture items with partial refund options instead.

---

## Insight 8 – Campaign Channel: Organic Is the Best Performer

**Observation:** Organic traffic generates the most sales (₹8.88 crore, 40.9% of total) and the most orders (1,694). Referral has the highest margin efficiency relative to orders. Paid channel has a good volume but needs ROI analysis.

**Data Evidence:**

| Channel | Orders | Sales | Profit | Margin |
|---|---|---|---|---|
| Organic | 1,694 | ₹8.88 Cr | ₹1.34 Cr | 15.1% |
| Paid | 849 | ₹4.01 Cr | ₹60.5 Lakh | 15.1% |
| Email | 657 | ₹3.45 Cr | ₹53.6 Lakh | 15.5% |
| Social | 584 | ₹3.11 Cr | ₹49.1 Lakh | 15.8% |
| Referral | 392 | ₹2.12 Cr | ₹33.4 Lakh | 15.7% |

**Business Interpretation:** Social and Referral channels deliver the best margins (15.7–15.8%), while Organic has the highest volume. Email performs consistently. Paid channel drives volume but needs cost-of-acquisition analysis to confirm true ROI.

**Recommended Action:** Invest more in Social and Referral channel development as they produce above-average margins. Ensure Paid channel CAC (cost of acquisition) is tracked against actual margins. Scale Email campaigns as they deliver consistent results with likely low marginal cost.
