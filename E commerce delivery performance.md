# Business Requirements Document (BRD)

## E-Commerce Delivery Performance Analysis

---

### 1. Document Overview

| Field | Detail |
|---|---|
| **Project Name** | E-Commerce Delivery Performance Analysis |
| **Prepared By** | Shruti Vishwakarma |
| **Role** | Business Analyst (Self-Initiated Project) |
| **Date** | August 2026 |
| **Data Source** | Olist Brazilian E-Commerce Public Dataset (Kaggle) |
| **Tools Used** | Microsoft Excel, Power BI |

---

### 2. Business Problem Statement

Operations and customer support teams need visibility into delivery performance in order to reduce customer dissatisfaction, minimize refund/complaint volume, and improve regional logistics planning. Without a clear breakdown of *where* and *how often* deliveries run late, it is difficult to prioritize operational improvements effectively.

An analysis of 99,441 real customer orders found that approximately **7.9% of all orders were delivered later than their promised estimated delivery date**. This project investigates whether these delays are evenly spread or concentrated in specific regions, in order to help operations and logistics stakeholders prioritize where to focus improvement efforts.

---

### 3. Stakeholders

| Stakeholder | Interest in this Analysis |
|---|---|
| **Operations Manager** | Owns overall delivery performance and refund/cost impact of late orders |
| **Customer Support Lead** | Handles complaint volume directly tied to late deliveries |
| **Regional Logistics Coordinator** | Responsible for carrier/route performance within specific states |

---

### 4. Business Questions / Objectives

1. What percentage of all orders are delivered later than the estimated delivery date?
2. Are late deliveries concentrated in specific states/regions, or spread evenly across the country?
3. Does high order volume correlate with a high late-delivery rate, or are they independent?
4. Which regions should be prioritized for operational or logistics review?

---

### 5. Data Source & Scope

- **Dataset:** Olist Brazilian E-Commerce Public Dataset (Kaggle) — publicly available, real transactional data
- **Records analyzed:** 99,441 delivered orders
- **Tables used:** `orders`, `customers`
- **Time period:** Orders spanning 2017–2018
- **Scope limitation:** Analysis covers delivery timing and regional distribution only; it does not include shipping cost, carrier-level performance, or product-category breakdown in this version.

---

### 6. Methodology

1. Calculated a per-order **Late/On-Time flag** by comparing `order_delivered_customer_date` against `order_estimated_delivery_date`.
2. Connected the `orders` and `customers` tables via `customer_id` to bring in regional (state-level) data.
3. Built a DAX measure (`Late %`) to calculate the true late-delivery rate **within each state**, rather than raw order counts — avoiding the misleading effect of high-volume states appearing "worse" simply due to order volume.
4. Visualized results in Power BI using a state-level bar chart, sorted by actual late-delivery percentage.

---

### 7. Key Findings

- **Overall late-delivery rate:** ~7.9% of all 99,441 orders arrived after their promised delivery date.
- **Volume ≠ delay rate:** São Paulo (SP) accounts for the highest raw order volume, but does **not** have the highest late-delivery rate — indicating that scale alone does not explain delivery delays.
- **Regions with the highest late-delivery rates:** States including **Alagoas (AL), Maranhão (MA), Piauí (PI), Ceará (CE), and Sergipe (SE)** showed meaningfully higher late-delivery percentages than the national average. Specifically: **Alagoas (AL): 23%, Maranhão (MA): 18.88%, Piauí (PI): 15.35%, Ceará (CE): 14.67%, and Sergipe (SE): 14.57%** — each well above the national average of 7.9%.
- This pattern suggests that **regional/logistics factors** (e.g. distance from distribution hubs, carrier coverage) — rather than order volume — are likely the primary driver of delivery delays.

---

### 8. Recommendations

1. **Prioritize logistics review** in the identified high-late-rate states (AL, MA, PI, CE, SE) rather than allocating equal review effort across all regions.
2. **Investigate carrier/route performance** specifically in these states to determine whether delays stem from carrier capacity, distance, or estimated-delivery-date miscalibration.
3. **Reassess estimated delivery date accuracy** for underperforming regions — if promised dates are unrealistic for certain areas, adjusting expectations could reduce the late-delivery percentage without operational changes.
4. **Monitor high-volume regions (e.g. SP) separately** to ensure performance remains stable as scale increases, even though they are not currently the worst performers.

---

### 9. Success Metrics

- Reduction in national late-delivery rate from ~7.9% to a defined target (e.g. under 5%) within a set review period.
- Reduction in late-delivery rate specifically within the top 5 flagged states.
- Decrease in delivery-related customer support complaint volume, tracked as a secondary indicator.

---

### 10. Appendix

- Dashboard: Power BI report — *E-commerce Delivery Performance Analysis* (regional breakdown page)
- Dataset citation: Olist, *Brazilian E-Commerce Public Dataset by Olist*, Kaggle.
