<a id="top"></a>

# **DE'STORE RETAIL SALES PERFORMANCE ANALYSIS (2024–2025)**

*An insight-driven Excel dashboard project for a multi-city Nigerian retail superstore.*

**Prepared by:** Daniel Diala 

**Tools:** Microsoft Excel (data cleaning, pivot tables, pivot charts, slicers, dashboards)

---

## Table of Contents

1. [Project Background](#1-project-background)
   - [1.1 About De'Store](#11-about-destore)
   - [1.2 Business Problem](#12-business-problem)
   - [1.3 Project Objectives](#13-project-objectives)
   - [1.4 Headline Metrics](#14-headline-metrics)
2. [Data Structure & Initial Checks](#2-data-structure--initial-checks)
3. [Executive Summary](#3-executive-summary)
4. [Insights Deep Dive](#4-insights-deep-dive)
   - [4.1 Overview](#41-overview)
   - [4.2 Customer & Transaction Analysis](#42-customer--transaction-analysis)
   - [4.3 Product Performance](#43-product-performance)
5. [Takeaway](#5-takeaway)
6. [Recommendations](#6-recommendations)
7. [Limitations & Assumptions](#7-limitations--assumptions)
8. [Skills Demonstrated](#8-skills-demonstrated)

---

## 1. Project Background

### 1.1 About De'Store

De'Store is a retail superstore with outlets across six Nigerian cities: **Lagos, Abuja, Kano, Ibadan, Benin City and Port-Harcourt**. The store sells fast-moving consumer goods in four categories (**Personal Care, Beverages, Household and Snacks**) across 20 products such as Toothpaste, Pepsi, Juice, Deodorant, Soap and Detergent. Customers pay by Bank Transfer, Cash, POS or Online, and every sale is recorded as an invoice line item with the customer, product, quantity, unit price, payment method, date and branch location.

This project analyses **24 months of transactions (1 January 2024 to 31 December 2025)** to show how the business is performing, where its money comes from, and where it is slipping. The dataset is a simulated retail transaction log built to reflect a multi-branch Nigerian retailer, and it deliberately contains the kind of errors found in real exports.

### 1.2 Business Problem

Management has transaction records but no single view of how the business performed across 2024 and 2025. The headline numbers hide a puzzle:

> **Both years recorded exactly 1,500 invoices, yet revenue fell from ₦6.95M to ₦6.30M (−9.4%) and units sold fell from 9,146 to 8,547 (−6.5%).**

Customers did not stop coming; each visit simply became worth less. At the same time, the strongest branches, categories and payment channels changed from one year to the next, so it was unclear where to protect revenue, where to invest, and which products and customers matter most.

### 1.3 Project Objectives

- **Measure overall performance:** total revenue, number of transactions, average sale value and units sold, with a year-on-year (2024 vs 2025) comparison.
- **Find the revenue drivers:** which product categories and individual products generate the most, and the least, revenue.
- **Compare locations:** which of the six cities lead, which lag, and how that changed between years, to guide expansion and stock allocation.
- **Understand customers:** how male and female customers differ in spending and category preference.
- **Understand payment behaviour:** which payment methods bring in the most revenue and the most transactions.
- **Turn findings into action:** give leadership clear, measurable recommendations on stocking, marketing, regional focus and data capture.

### 1.4 Headline Metrics

| Metric | Value | Definition |
| --- | --- | --- |
| Total Revenue | ₦13,246,572 | Sum of Total_Amount across all transactions |
| Total Transactions | 3,000 | Distinct count of Invoice_ID |
| Total Quantity Sold | 17,693 units | Sum of Quantity |
| Average Revenue | ₦4,400.85 | Total Revenue divided by the 3,010 line items in the cleaned data (about ₦4,415 per distinct invoice) |
| Revenue 2024 vs 2025 | ₦6.95M vs ₦6.30M | A fall of 9.4% on an identical 1,500 invoices per year |


---

## 2. Data Structure & Initial Checks

The data is one flat table in which each row is one invoice line item (a single product sold within a transaction). The raw export was kept untouched on its own sheet as an audit trail, and every KPI, pivot table and dashboard is built from the cleaned copy.

### Field Dictionary (Clean Data)

| Field | Type | Description | Values / Range |
| --- | --- | --- | --- |
| Invoice_ID | Text | Unique identifier of each sales transaction | INV00001 – INV03000 |
| Customer_Name | Text | Full name of the customer | Free text |
| Gender | Category | Recorded gender of the customer | Male, Female, Unknown |
| Product_Category | Category | High-level product grouping | Beverages, Household, Personal Care, Snacks |
| Product_Name | Category | Specific product purchased | 20 products; N/P = not provided |
| Quantity | Integer | Units bought on the line item | 1 – 10 typical; 90 – 150 for bulk orders |
| Unit_Price | Integer (₦) | Price per unit in Naira | ₦55 – ₦27,300 |
| Total_Amount | Integer (₦) | Line value, calculated as Quantity × Unit_Price | ₦56 – ₦273,000 |
| Payment_Method | Category | How the customer paid | Bank Transfer, Cash, Online, Pos; N/P |
| Date | Date | Transaction date (DD/MM/YYYY) | 01/01/2024 – 31/12/2025 |
| Location | Category | City of the store branch | Abuja, Benin City, Ibadan, Kano, Lagos, Port-Harcourt; N/P |

### Initial Checks

- Row counts were reconciled from 3,036 raw rows to 3,010 cleaned rows after duplicate invoices were reviewed; 3,000 distinct invoices remain.
- Category labels, date formats, misaligned values, missing values, duplicates and outliers were all checked. What was found and how it was handled is summarised in [Section 7](#7-limitations--assumptions).
- Total_Amount was verified or rebuilt as Quantity × Unit_Price so that every revenue figure comes from one consistent rule.

[📊 View Worksheet](./DeStore_Sales_Performance_Worksheet.xlsx)



---

## 3. Executive Summary

De'Store earned **₦13.25M from 3,000 transactions** across 2024 and 2025, but revenue slipped **9.4% in 2025** even though the number of invoices stayed at 1,500 in both years. The shortfall is a basket-value problem, not a customer-traffic problem.

The slowdown is concentrated in the second half of 2025, when every month from June to December earned less than the same month of 2024.

- **Beverages overtook Personal Care** as the top category.
- **Kano and Ibadan overtook Lagos and Port-Harcourt** in the branch ranking.
- **Female customers outspent male customers.**
- **Bank Transfer** is the most used and highest-earning payment method, and **Toothpaste** is the best-selling product.


---

## 4. Insights Deep Dive

The dashboard has three analysis pages, each with the same KPI strip (Total Revenue, Average Revenue, Total Quantity Sold, Total Transactions) and interactive slicers. A fourth page holds the written summary and recommendations and is covered in [Section 5](#5-takeaway) and [Section 6](#6-recommendations). Year-on-year figures below come from switching the Date (Year) slicer between 2024 and 2025.

[📊 View Interactive Dashboard](./DeStore_Sales_Performance_Dashboard.mp4)

### 4.1 Overview

**Objective:** give leadership a quick read of total performance and answer three questions. Is revenue growing or shrinking? Which categories and locations earn the most? Which gender spends more? Slicers for Date (Year) and Location let the viewer filter every chart on the page.

<img width="1213" height="482" alt="DeStore Dashboard 1" src="https://github.com/user-attachments/assets/72a4d351-818c-4754-97de-ed31859a06a3" />



*Figure 1: Overview dashboard page.*

#### Revenue Trend 

A two-line chart was used because the question is how two years compare month by month, and a line makes seasonality and gaps easy to see.

<img width="789" height="171" alt="DeStore Dashboard 2" src="https://github.com/user-attachments/assets/6dbe15c4-5c10-41fc-9b56-104b0917e975" />


*Figure 2: Revenue Trend by month, 2024 (white) vs 2025 (green).*

- **Revenue fell 9.4% year on year, from ₦6.95M to ₦6.30M**, while invoices stayed flat at 1,500 and units dropped 6.5% (9,146 to 8,547). Revenue per invoice slipped from about ₦4,634 to ₦4,197.
- **The decline sits in the second half.** 2025 beat 2024 from February to May (for example March ₦623K against ₦387K), taking H1 up about 7%. From June onward every month was lower, and H2 2025 earned about 22% less than H2 2024 (₦3.07M against ₦3.93M).
- **2024 was strongest in September (₦774K), November (₦737K) and December (₦722K)**, a pre-festive peak that 2025 did not repeat. The 2025 low points were January (₦372K), August (₦390K), April (₦393K) and October (₦394K).
- Monthly revenue is volatile in both years, ranging from ₦364K to ₦774K, so stock and staffing plans should follow the monthly pattern rather than a flat average.

#### Revenue By Category 

A column chart ranks the four categories side by side. The two lighter bars mark the top two earners.

<img width="615" height="429" alt="figure-4-revenue-by-category" src="https://github.com/user-attachments/assets/20fb0e4d-7819-47bb-a607-8d3787e44b51" />


*Figure 3: Revenue by product category.*

- **Personal Care leads overall with ₦3.83M (28.9% of revenue)**, followed by Beverages ₦3.51M (26.5%), Household ₦3.05M (23.0%) and Snacks ₦2.86M (21.6%). The gap between first and last is ₦0.96M, so no category is negligible.
- **The leader changed between years.** Personal Care topped 2024 (₦2.16M) but fell 22.6% in 2025 (₦1.67M), while Beverages rose 27% from ₦1.55M to ₦1.96M and took first place. Household (−19.6%) and Snacks (−16.2%) also declined.
- Beverages was the only category to grow, which means the overall decline came from three of the four categories.

#### Revenue By Location 

A horizontal bar chart suits long city names and makes the ranking of branches easy to read.

<img width="567" height="429" alt="figure-5-revenue-by-location" src="https://github.com/user-attachments/assets/f43e63c9-6b85-4f8d-9962-4d4baa90cc3e" />


*Figure 4: Revenue by branch location.*

- **Lagos is the largest branch with ₦2.49M (18.8%)**, but Kano (₦2.33M), Ibadan (₦2.32M) and Benin City (₦2.26M) are all within 10% of it. Revenue is spread across the network rather than dependent on one city.
- **Abuja is the weakest branch at ₦1.63M (12.3%)**, about 35% below Lagos, and it was the lowest city in both years.
- **The 2025 ranking shifted sharply.** Kano grew 33% (₦1.00M to ₦1.33M) to take first place, Ibadan was almost flat (−3%), Lagos fell 26% (₦1.43M to ₦1.06M) and Port-Harcourt fell 29% (₦1.21M to ₦0.86M).
- ₦147K (1.1%) of revenue has no location recorded (N/P). It is shown as its own bar so the total still reconciles to ₦13.25M.

#### Revenue By Gender

A doughnut chart shows each gender's share of the whole.

<img width="247" height="167" alt="DeStore Dashboard 5" src="https://github.com/user-attachments/assets/fff73d69-6f85-4adf-881b-08cc523a42e1" />


*Figure 5: Revenue by customer gender.*

- **Female customers contributed ₦6.69M (50.5%) and male customers ₦6.24M (47.1%)**, a gap of about ₦454K. Customers with no recorded gender add ₦315K (2.4%).
- **Spending was balanced in 2024** (₦3.42M female, ₦3.41M male) **but diverged in 2025.** Female revenue slipped 4.4% to ₦3.27M while male revenue fell 16.9% to ₦2.83M, so women outspent men by about 15% in 2025.


---

### 4.2 Customer & Transaction Analysis

**Objective:** explain how customers pay and what they buy. Which payment methods earn the most and are used most often? Do men and women buy different categories? Which category sells best in each city? Slicers for Date (Year) and Location filter the page.

<img width="1213" height="487" alt="DeStore Dashboard 3" src="https://github.com/user-attachments/assets/9c43adb6-96f5-4648-8c16-9a51ed0a9d12" />


*Figure 6: Customer & Transaction Analysis dashboard page.*

#### Payment Method Analysis 

A combination chart puts revenue (columns) and number of transactions (red line) on one view, so the value and the frequency of each payment method can be compared together.

<img width="1258" height="434" alt="figure-8-payment-method" src="https://github.com/user-attachments/assets/6e3282fa-788b-49f8-979e-26dd11938e78" />


*Figure 7: Payment method revenue and transaction count.*

- **Bank Transfer leads on both measures:** ₦3.77M (28.4% of revenue) from 929 transactions (31% of all transactions). Cash follows with ₦3.49M from 714 transactions, then POS (₦3.18M, 742) and Online (₦2.69M, 579).
- **Cash carries the biggest ticket.** Average revenue per transaction is about ₦4,890 for Cash, ₦4,650 for Online, ₦4,290 for POS and ₦4,050 for Bank Transfer. Bank Transfer wins on volume, Cash on value per sale.
- **Channel momentum differs.** Bank Transfer revenue grew 8.9% in 2025 and Cash 1.5%, while POS fell 31% (₦1.89M to ₦1.30M) and Online fell 16%. The drop in POS (about ₦590K) and Online (about ₦231K) is larger than the whole net decline of ₦655K, partly offset by growth in Bank Transfer and Cash.
- Only 36 transactions (₦114K, under 1% of revenue) have no payment method recorded.

#### Transaction By Gender 

<img width="638" height="440" alt="figure-9-transactions-by-gender" src="https://github.com/user-attachments/assets/481a1f4f-58bd-42d5-b64b-f63051603b18" />


*Figure 8: Number of transactions by gender.*

- Female customers made **1,474 transactions (49.1%)**, male customers **1,426 (47.5%)**, and 100 (3.3%) have no gender recorded.
- Transaction counts are almost equal, yet female revenue is about 7% higher, so women spend slightly more per transaction (about ₦4,540 against ₦4,375 for men).

#### Category By Gender 

<img width="633" height="443" alt="figure-10-category-by-gender" src="https://github.com/user-attachments/assets/d6a1497a-3557-4415-ae08-1e2a7b1d21ef" />


*Figure 9: Revenue by product category and gender.*

- **Women favour Personal Care (₦1.96M, 29% of their spend) and Snacks (₦1.81M, 27%).** Men favour Beverages (₦1.81M, 29%) and spread the rest almost evenly between Personal Care and Household.
- **Snacks is the sharpest difference.** Women spent ₦1.81M on Snacks against ₦0.99M for men, which is 83% more.
- **Household leans male:** ₦1.69M from men against ₦1.31M from women, about 29% more.
- This supports category promotions that target each group instead of one general campaign.

#### Category By Location

<img width="1257" height="440" alt="figure-11-category-by-location" src="https://github.com/user-attachments/assets/40e1f794-952d-43e0-bd3f-4f03c8462b7e" />


*Figure 10: Revenue by product category across branch locations.*

- **The best-selling category differs by city.** Beverages leads in Lagos (₦800K, 32% of the city's revenue) and Ibadan (₦733K), Household leads in Kano (₦813K), Personal Care leads in Port-Harcourt, and Snacks narrowly leads in Benin City (₦646K) and Abuja (₦464K).
- **Port-Harcourt depends on Personal Care.** Its ₦961K is the largest single bar on the chart and 46% of the city's revenue, while Snacks there is only ₦296K.
- **Abuja is lowest on Household (₦293K, the smallest bar on the chart) and Personal Care (₦411K)** and only mid-table on Snacks and Beverages.
- One stock plan for all six cities would over-supply some categories and under-supply others, so assortment should be set city by city.


---

### 4.3 Product Performance

**Objective:** identify the best-selling and weakest products so that restocking and marketing spend can follow the product mix. The page shows the ten highest-earning products and the ten lowest, with slicers for Gender and Location.

<img width="1208" height="491" alt="DeStore Dashboard 4" src="https://github.com/user-attachments/assets/8c1f9a31-4b14-40f1-8741-c69394048bd6" />


*Figure 11: Product Performance dashboard page.*

#### Top Selling Products 

<img width="1890" height="413" alt="figure-13-top-10-products" src="https://github.com/user-attachments/assets/17d03596-4fcd-45cf-8a38-d8149812e137" />

*Figure 12: Top 10 products by revenue.*

- **Toothpaste is the clear number one with ₦1.23M (9.3% of all revenue)**, about 39% ahead of second-placed Pepsi (₦884K). Juice (₦835K), Deodorant (₦823K) and Air Freshener (₦776K) follow.
- **The top 10 products earn ₦7.74M, or 58% of revenue.** Sales are concentrated in a short list, so stock-outs on these items would hurt far more than on the rest of the range.
- The list mixes categories (Personal Care, Beverages, Household and Snacks), which shows strength comes from individual products as well as from category.

#### Bottom Selling Products 

<img width="1895" height="444" alt="figure-14-bottom-10-products" src="https://github.com/user-attachments/assets/c39c70ec-0478-4822-a94f-1eafa033f51e" />

*Figure 13: Bottom 10 products by revenue.*

- **Bleach is the lowest-earning named product at ₦432K**, followed by Water (₦490K) and Cookies (₦494K).
- **The weak end of the range is tightly bunched.** Apart from the unresolved N/P label, the bottom nine products sit between ₦432K and ₦585K, so the gap to the leaders is a matter of degree, not of products that do not sell.
- Sales with no product recorded (N/P) total ₦98K, which shows the cost of incomplete data capture.


---

## 5. Takeaway

**Problem revisited.** De'Store could not see why revenue fell in 2025 even though it served the same number of transactions as in 2024.

**Objectives revisited.** Measure performance, find the revenue drivers, compare locations, understand customers and payments, and turn the findings into action. The analysis answers each of these:

| Objective | What the Analysis Found |
| --- | --- |
| Overall performance | ₦13.25M from 3,000 invoices and 17,693 units. Revenue fell 9.4% in 2025 with the same invoice count, because revenue per invoice dropped. The fall is concentrated in June to December. |
| Revenue drivers | Personal Care is the largest category overall, but Beverages was the only category to grow in 2025 and now leads. Ten products earn 58% of revenue, led by Toothpaste (₦1.23M). |
| Locations | Lagos is the biggest branch but fell 26% in 2025, as did Port-Harcourt (−29%). Kano grew 33% to lead in 2025. Abuja is the weakest branch in both years. Each city has a different best-selling category. |
| Customers | Women and men spent evenly in 2024, but women outspent men by about 15% in 2025. Women lean to Personal Care and Snacks, men to Beverages and Household. |
| Payment behaviour | Bank Transfer earns the most and is used most often. Cash has the highest average ticket. POS and Online revenue fell sharply in 2025. |
| Action | Eight recommendations in [Section 6](#6-recommendations) target the basket-value decline, the two weakening cities, the growing cities, city-level assortment, gender-targeted promotions, payment channels, product focus and data capture. |

>  De'Store's revenue problem is not fewer customers but lower value per visit, concentrated in the second half of 2025, in Lagos and Port-Harcourt, in Personal Care and in POS and Online payments, while Kano, Beverages and Bank Transfer are growing. Recovery depends on restoring basket value in the weakening cities and categories and on putting stock and promotions where demand is actually moving.

**A caution from the sensitivity check.** 41 unusually large records (29 bulk orders of 90 to 150 units and 12 sales at unit prices above ₦15,000) account for about 27% of revenue. Without them, the 2024 and 2025 totals are almost level (₦4.83M against ₦4.78M). Much of the year-on-year gap therefore comes from fewer very large orders, which is why large orders should be tracked as their own segment (see [Section 6](#6-recommendations) and [Section 7](#7-limitations--assumptions)).


---

## 6. Recommendations

| # | Observation | Recommendation | Owner and Measure |
| --- | --- | --- | --- |
| 1 | Revenue fell 9.4% with the same 1,500 invoices; revenue per invoice dropped to about ₦4,197, mostly from June to December. | Split monthly revenue into invoice count × average ticket and track very large orders separately. Test basket-building offers such as bundles and multi-buy deals in H2. | Sales and Finance. Track revenue per invoice against the 2024 level of about ₦4,634. |
| 2 | Lagos (−26%) and Port-Harcourt (−29%) lost the most revenue in 2025. | Run a root-cause review on stock availability, pricing, local competition and demand shifts. Port-Harcourt depends on Personal Care (46% of its revenue), so check that category first. | Regional operations. Aim to restore the 2024 run-rate (Lagos ₦1.43M, Port-Harcourt ₦1.21M per year). |
| 3 | Kano grew 33% and Ibadan held steady while the rest fell. | Deepen stock and run targeted marketing in Kano (Household) and Ibadan (Beverages), and study what is working there for use in other branches. | Supply chain and Marketing. Track branch revenue growth and stock-out rate. |
| 4 | The best-selling category differs in each city. | Set category assortment per city: Beverages in Lagos and Ibadan, Household in Kano, Personal Care in Port-Harcourt, Snacks in Benin City and Abuja. | Merchandising. Track category share by city. |
| 5 | Women favour Personal Care and Snacks, men favour Beverages and Household, and male spend fell 16.9% in 2025. | Run gender-targeted promotions, with Personal Care and Snacks offers aimed at women and Beverages and Household bundles to win back male spend. | Marketing. Track male and female revenue by category. |
| 6 | Bank Transfer leads revenue and volume, Cash has the highest ticket, while POS (−31%) and Online (−16%) fell. | Keep Bank Transfer and Cash frictionless, and investigate the POS and Online decline, for example terminal downtime, checkout problems or payment failures. | Finance and IT. Track revenue and success rate by payment method. |
| 7 | Ten products earn 58% of revenue, led by Toothpaste (9.3%). | Protect stock and shelf space for the top 10, and review price and placement for the lowest-earning named products (Bleach, Water, Cookies). | Category managers. Track top-10 availability and weak-product sales. |
| 8 | Missing, misaligned and extreme values appeared in the raw export. | Add mandatory fields, drop-down lists and range checks (price and quantity) at the point of sale, and add an order-type flag for bulk orders. | Data and IT. Track the share of N/P records and records failing validation. |

---

## 7. Limitations & Assumptions

The dataset was not free of errors. The table below shows what was found in the raw export, what was done about it, and what would prevent it in future.

| Issue Found | Mitigation | Recommendation |
| --- | --- | --- |
| Inconsistent category labels in Gender ('M', 'male', 'Femle'), Payment_Method ('Transfer', 'transfr') and Location ('Port Harcourt' vs 'Port-Harcourt'). | Standardised each field to one controlled list: Male, Female, Unknown; Bank Transfer, Cash, Online, Pos, N/P; and one spelling per city. | Use drop-down lists or data validation at the point of entry so labels cannot drift. |
| Misaligned or shifted values, such as an Invoice_ID or product name sitting in the Payment_Method or Location column. | Rows were traced and re-aligned using data type and context. Values that could not be recovered were set to N/P. | Export from the sales system in a fixed schema and add a column-type check on every load. |
| Mixed date formats ('2025-08-07 00:00:00', '2024/07/31' and plain text). | All dates were parsed and standardised to a single DD/MM/YYYY format. | Store dates as true date fields at source. |
| Missing values: 47 Customer_Name, 37 Product_Name, 36 each in Unit_Price, Payment_Method and Location, and 33 Total_Amount. | Total_Amount was rebuilt as Quantity × Unit_Price. Unrecoverable categories were labelled N/P, not deleted, so row and transaction counts stay intact. | Make these fields mandatory in the sales system and report the N/P rate as a data-quality KPI. |
| 36 duplicate Invoice_ID entries in the raw data. | Each was reviewed and merged as a legitimate multi-item invoice or removed as a true duplicate, reducing 3,036 rows to 3,010. Ten Invoice_IDs still appear on two rows, so transaction KPIs use a distinct count of Invoice_ID (3,000) to avoid double counting. | Add a line-item number so that each invoice line has a unique key. |
| Quantity outliers: 29 records of 90–150 units against a normal 1–10. | Retained and flagged as plausible bulk or wholesale orders, not silently dropped. | Add an order-type field (retail or bulk) so bulk orders can be reported separately. |
| Extreme unit prices: 12 records at ₦15,000–₦27,300 against ₦55–₦1,500 for every other record. Together with the bulk orders they make up about ₦3.64M (27%) of revenue. | Retained as recorded, since they could not be verified. A sensitivity check shows that without these 41 records 2024 and 2025 revenue are nearly level (₦4.83M against ₦4.78M), so results that rely on them, including the Toothpaste ranking, should be read with care. | Validate prices against a product price list, add upper and lower price limits, and report headline KPIs with and without very large records. |
| Unresolved N/P values: 36 records each for product, payment method and location. | Kept as their own N/P category so every chart still reconciles to ₦13.25M (₦98K, ₦114K and ₦147K of revenue respectively). | Treat the N/P rate as a quality measure and trace the source of missing records. |

### Assumptions

- The dataset is simulated, so the findings illustrate the analytical approach and should not be read as real company results.
- Total_Amount equals Quantity × Unit_Price, and all values are in nominal Naira with no inflation adjustment.
- Average Revenue is Total Revenue divided by the 3,010 line items (₦4,400.85). Transaction counts use the distinct count of Invoice_ID (3,000).
- Year-on-year figures compare calendar 2024 with calendar 2025 using the Date (Year) slicer. Gender is taken as recorded and was not verified.
- N/P records stay in the totals, so category, location and payment figures add up to the overall ₦13.25M.


---

## 8. Skills Demonstrated

| Skill | How It Was Applied in This Project |
| --- | --- |
| Data cleaning and standardisation | Fixed inconsistent labels, typos, mixed date formats and misaligned columns, and used the N/P placeholder to keep record counts intact. |
| Data quality assessment | Profiled the raw export for missing values, duplicates and outliers, and logged each issue with its resolution. |
| Data validation and outlier handling | Reviewed duplicate invoices, flagged bulk quantities and tested how sensitive the results are to extreme values. |
| Calculated fields and KPI design | Built Total_Amount = Quantity × Unit_Price and defined Total Revenue, Average Revenue, distinct transactions and units sold. |
| Pivot tables and pivot charts | Summarised revenue by month, category, location, gender, payment method and product, and cross-tabulated location × category and gender × category. |
| Dashboard design and interactivity | Designed a three-page dashboard with KPI cards, page navigation, and Date (Year), Location and Gender slicers, using a consistent green colour scheme. |
| Chart selection | Matched each question to a chart: line for trends, column and bar for rankings, doughnut for share, and a combination chart for revenue against volume. |
| Year-on-year and segment analysis | Compared 2024 with 2025 and segmented by location, gender, category, payment method and product. |
| Business problem solving and storytelling | Framed a business problem, answered it with evidence, and converted the findings into measurable recommendations for named teams. |
| Technical documentation | Produced a field dictionary, data-quality log, KPI definitions and this README so that the analysis can be reproduced and audited. |

[Back to top](#top)

---

*De'Store Retail Sales Performance Analysis | Prepared by Daniel Diala*

