# Chart Selection Justification – Executive Dashboard
## Design Rationale for Each Visualisation

---

## Design Principles Applied Across the Dashboard

| Principle | How Applied |
|---|---|
| **Correct chart selection** | Each chart matches the analytical question — lines for trends, bars for comparisons, scatter for relationships |
| **Clear hierarchy** | KPI cards at top → trends next → category/region breakdowns → shipping/returns at bottom |
| **Minimal clutter** | No 3D charts, no gridline overload, no decorative elements; chart ink maximised for data |
| **Consistent color usage** | Blue = sales/positive; Orange/Red = losses or risk; Green = above-average margins |
| **Proper labels** | All axes labelled with units (₹); KPI cards show values and % change |
| **Readable titles** | All chart titles phrase the business question, not the data source (e.g., "How Are Monthly Sales Trending?") |
| **Appropriate sorting** | Bar charts sorted descending by measure; no alphabetical sorting of categories |
| **Useful filters** | Region, Category, Customer Segment, Ship Mode — the four most actionable dimensions |
| **No misleading scales** | All axes start at zero; no dual-axis manipulation |
| **Business interpretation** | Annotations and tooltips provide meaning, not just numbers |

---

## Chart 1 – Sales Trend View (Line Chart)

**Business Question:** How are total sales and profit changing over time?

**Chart Type Selected:** Line chart (dual-line for Sales and Profit)

**Why This Chart Type is Appropriate:**
A line chart is the standard for showing change over time. It allows the eye to immediately detect direction (up/down), rate of change, and any seasonality or anomalies. A bar chart for trend data would obscure the continuity of movement; a pie chart would be meaningless for time series data.

**Fields Used:**
- X-axis: Order Date (continuous, monthly)
- Y-axis (left): SUM([sales])
- Y-axis (right): SUM([profit])
- Color: Measure names (distinguishes Sales vs Profit lines)

**Design Principle Applied:** Dual-line with different colours (blue for sales, green for profit) makes the margin gap immediately visible. Year markers added as reference lines.

**Mistake Avoided:** Not using a bar chart for trend — bars imply discrete categories, not continuous time. Not truncating the Y-axis to exaggerate growth.

---

## Chart 2 – Regional Performance View (Horizontal Bar Chart)

**Business Question:** Which regions generate the most sales and profit? How do margins compare?

**Chart Type Selected:** Horizontal bar chart with colour encoding for profit margin

**Why This Chart Type is Appropriate:**
A horizontal bar chart is ideal for comparing a ranked set of named categories (the 4 regions). Bars make magnitude comparisons intuitive. The horizontal orientation allows full region names to display without rotation. A map could also work but requires geographic data; a bar chart communicates performance ranking more directly.

**Fields Used:**
- Y-axis: Region (dimension)
- X-axis: SUM([sales]) — bar length
- Color: [Profit Margin] calculated field — encodes margin on a diverging scale
- Labels: SUM([profit]) displayed on bars

**Design Principle Applied:** Sorted descending by sales so the highest-performing region appears first. Colour gradient on margin helps identify East's margin advantage at a glance without a separate chart.

**Mistake Avoided:** Not using a pie chart for regional share — pies make precise comparisons difficult. Not using alphabetical sort which would hide the performance ranking.

---

## Chart 3 – Category Profitability View (Bar Chart with Sub-Category Drill-Down)

**Business Question:** Which categories and sub-categories are profitable, and which are dragging performance?

**Chart Type Selected:** Grouped / stacked bar chart with Category > Sub-Category hierarchy; colour by profit (positive = blue, negative = red)

**Why This Chart Type is Appropriate:**
A bar chart directly encodes magnitude, making it easy to compare sub-category profit values. The colour encoding (blue for profit, red for loss) immediately surfaces which sub-categories should concern leadership. A treemap was considered but is harder to read precise values; a highlight table was also considered but is less scannable for a leadership audience.

**Fields Used:**
- X-axis (or Y-axis): SUM([profit])
- Dimension: Category / Sub-Category
- Color: SUM([profit]) on diverging scale (red for negative, blue for positive)
- Size: SUM([sales]) as label

**Design Principle Applied:** Sorted descending by profit. Technology sub-categories dominate the top; Furniture sub-categories are clearly visible at lower profit levels. Negative values highlighted in red.

**Mistake Avoided:** Not using a pie chart which cannot show negative values. Not showing revenue alone without profit context — revenue without margin is misleading for category comparison.

---

## Chart 4 – Customer Segment View (Side-by-Side Bar Chart)

**Business Question:** How do the three customer segments compare on sales, profit, and order volume?

**Chart Type Selected:** Side-by-side bar chart comparing three segments across three metrics

**Why This Chart Type is Appropriate:**
A side-by-side bar enables direct comparison of multiple measures (sales, profit, orders) across a small number of categories (3 segments). It is preferable to a stacked bar when the interest is in comparing individual values rather than parts of a whole.

**Fields Used:**
- X-axis: Customer Segment
- Y-axis: Measure values (Sales, Profit, Margin % — toggle via Measure Names filter)
- Color: Customer Segment (consistent palette across all views)

**Design Principle Applied:** Profit margin shown as a secondary annotation on bars. Segments shown in order of sales performance (Home Office → Consumer → Corporate).

**Mistake Avoided:** Not using a line chart (segments are not time-based categories). Not using a single stacked bar which would hide individual segment comparisons.

---

## Chart 5 – Shipping Performance View (Bar Chart + Reference Line)

**Business Question:** Which shipping modes are used most, and how do delivery times compare?

**Chart Type Selected:** Dual bar chart — one for order count by ship mode, one for average delivery days

**Why This Chart Type is Appropriate:**
Two separate bar charts (or a combined view with dual axes) clearly answers both questions: volume and speed. A scatter plot was considered but with only 4 ship modes, a bar chart is more readable. A table would work but is less visually impactful for leadership.

**Fields Used:**
- X-axis: Ship Mode
- Y-axis (chart 1): COUNT([order_id])
- Y-axis (chart 2): AVG([delivery_days])
- Color: Ship Mode (consistent across charts)
- Reference line: Average delivery days (3.6 days overall)

**Design Principle Applied:** Reference line at 3.6 days average immediately shows which modes exceed the average. Standard Class is clearly the outlier on delivery time despite being the most-used mode.

**Mistake Avoided:** Not combining volume and delivery on a single dual-axis chart with different scales — dual-axis can mislead when scales differ dramatically.

---

## Chart 6 – Discount vs Profit View (Scatter Plot + Bar Comparison)

**Business Question:** Is there a relationship between discount level and profitability? At what threshold does discounting become harmful?

**Chart Type Selected:** Scatter plot (individual orders: discount on X, profit on Y) + summary bar chart by Discount Tier (calculated field)

**Why This Chart Type is Appropriate:**
A scatter plot is the correct choice for showing relationships between two continuous numerical variables (discount % vs profit ₹). It reveals both the direction and distribution of the relationship. The bar chart by Discount Tier provides a clean aggregated summary for leadership.

**Fields Used:**
- Scatter: X = [discount], Y = [profit], Color = Category
- Bar: X = [Discount Tier] (calculated field), Y = AVG([Profit Margin])
- Reference line: Profit = 0 (breakeven)

**Design Principle Applied:** Breakeven reference line at profit = 0 clearly shows the "loss zone". Color by category reveals that Furniture orders are disproportionately in the high-discount, low-profit quadrant.

**Mistake Avoided:** Not using a line chart for this — a line would imply sequential order. Not showing only aggregated data, which would hide the individual order distribution.

---

## Chart 7 – Return Analysis View (Bar Chart by Category and Segment)

**Business Question:** Which categories and customer segments have the highest return rates, and is there a pattern?

**Chart Type Selected:** Horizontal bar chart showing return rate % by Category and Customer Segment

**Why This Chart Type is Appropriate:**
Return rate is a proportion (0–100%) across named categories. A bar chart directly encodes proportions for easy comparison. A heat table was considered as an alternative for showing Category × Segment combinations, but a bar chart is clearer for a leadership audience focusing on the top-line finding.

**Fields Used:**
- Y-axis: Category / Customer Segment
- X-axis: [Return Rate] calculated field (SUM(return_flag)/COUNT(order_id))
- Color: Return rate on a gradient (low = blue, high = red)
- Labels: Exact return rate %

**Design Principle Applied:** Colour gradient immediately draws attention to Furniture's 7.7% return rate. Sorted by return rate descending. Reference line at overall average (4.5%).

**Mistake Avoided:** Not showing raw return counts — count alone would be unfair to Furniture which has fewer orders. Rate normalises for order volume. Not using a pie chart which cannot show multiple categories clearly.

---

## Chart 8 – Campaign Channel View (Bar Chart)

**Business Question:** Which campaign channels drive the most sales and which produce the best margins?

**Chart Type Selected:** Bar chart with dual measure encoding (bar height = sales, colour = profit margin)

**Why This Chart Type is Appropriate:**
With 5 channels, a bar chart is ideal — it ranks channels by volume while the colour simultaneously conveys margin quality. This avoids requiring two separate charts to answer one connected question.

**Fields Used:**
- X-axis: Campaign Channel
- Y-axis: SUM([sales])
- Color: [Profit Margin] calculated field (diverging colour scale)
- Tooltip: Profit, Orders, Average Order Value

**Design Principle Applied:** Organic's dominance in volume is immediately clear from bar height. The colour reveals that Social and Referral, while smaller, earn better margins — a nuanced finding that a simple bar by revenue alone would miss.

**Mistake Avoided:** Not using a pie for channel share — pie charts cannot encode two measures simultaneously. Not sorting alphabetically — sorted by sales volume to show performance ranking.
