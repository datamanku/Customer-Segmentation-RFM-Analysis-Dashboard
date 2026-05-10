
---

# Customer Segmentation (RFM Analysis) Dashboard

<img width="1270" height="718" alt="image" src="https://github.com/user-attachments/assets/ba302e89-f0c1-4c00-8f90-3f2e114ce8fe" />

---

An executive-level customer segmentation solution built in Power BI using RFM analysis to classify customers by purchasing behavior and support retention, loyalty, and reactivation strategy. This dashboard transforms transaction-level retail data into actionable customer intelligence by scoring customers on Recency, Frequency, and Monetary value, then organizing them into strategic business segments such as Champions, Loyal Customers, New Customers, and At Risk customers. 

---

## Navigation

- [Executive Summary](#executive-summary) 
- [Business Problem](#business-problem) 
- [Executive Questions Solved](#executive-questions-solved)
- [Dataset](#dataset)
- [Data Preparation](#data-preparation) 
- [Data Model](#data-model)
- [DAX Measures](#dax-measures)
- [Dashboard KPIs](#dashboard-kpis) 
- [Dashboard Design (Business Problem -> Analysis -> Insights & Recommendations -> Action)](#dashboard-design-business-problem---analysis---insights--recommendations---action)
- [Executive Business Insights](#executive-business-insights) 
- [Actionable Business Recommendations](#actionable-business-recommendations) 
- [Business Value Delivered](#business-value-delivered)
- [Tools & Skills Used](#tools--skills-used)

---

## Executive Summary

Customer growth does not create business value unless the business can identify which customers are most valuable, which customers are truly loyal, and which customers are beginning to disengage. This dashboard was designed to solve that challenge by converting raw invoice-level transaction data into a customer-level segmentation model. 

Using RFM analysis, the solution helps decision-makers evaluate customer quality, prioritize outreach, and build more targeted retention and loyalty programs. Rather than treating the customer base as one undifferentiated group, the dashboard enables a segment-led view of customer behavior and business opportunity. 

## Business Problem

The business had transaction data but lacked a structured framework to answer critical customer strategy questions such as which customers contribute the highest long-term value, which customers are loyal repeat buyers worth protecting, which customers are at risk of dropping off, and which new customers should be nurtured into higher-value segments. 

Without customer segmentation, marketing and retention teams cannot prioritize campaigns effectively, and leadership cannot align customer strategy with value creation. RFM analysis is a standard marketing framework for ranking customers by how recently, how frequently, and how much they purchase, specifically to support targeted actions. 

## Executive Questions Solved

This dashboard was built to answer the following business questions:

- Which customers are the most valuable based on recency, repeat buying behavior, and spending? 
- How is the customer base distributed across strategic segments such as Champions, Loyal Customers, At Risk, and Lost or low-engagement customers? 
- Which customers require retention, loyalty, or win-back intervention? 
- Which recently acquired customers show potential for long-term value development? 
- How can the business operationalize segment-based targeting using customer-level detail? 

## Dataset

The project uses retail transaction data containing customer, invoice, product, quantity, price, and date information, which is then aggregated to the customer level for RFM scoring and segmentation. The tutorial-based project specifically works from invoice-level retail data and derives customer-level Recency, Frequency, and Monetary metrics for each customer ID. 

The analytical grain of the final model is the customer, because segmentation decisions are made at the customer level rather than at the transaction line level. This design is consistent with other RFM Power BI implementations that summarize sales orders into customer-level metrics before assigning segment labels. 

## Data Preparation

Data preparation focused on creating a customer-level analytical table for RFM logic. The raw transaction data is grouped by customer so that each customer receives a single set of metrics for last purchase date, purchase count, and total spend. 

The standard preparation flow for this style of RFM dashboard includes calculating Recency as days since the last purchase, Frequency as total or distinct purchase count, and Monetary as total spend over the evaluation period. This transformed model supports targeted filtering, segment-level views, and customer-level action lists. 

## Data Model

A calculated customer summary table is created to support segmentation analysis, with customer ID as the key entity and derived R, F, and M values attached to each customer record. In comparable Power BI RFM implementations, this table is built from the transactional table using summary logic and then connected to a segment mapping or score table for classification. 

A practical analytical structure for this project includes customer identifier, recency value, frequency value, monetary value, individual R, F, and M scores, a combined score, and a segment label such as Champion or At Risk. This model shifts the report from descriptive sales reporting into customer strategy analysis. 

## DAX Measures

Key analytical logic used in the project includes:

- Last Purchase Date = maximum purchase date by customer. 
- Frequency = distinct count or total count of transactions by customer, depending on the dataset grain. 
- Monetary Value = total sales or spend by customer. 
- Recency = date difference between the customer’s last purchase date and the evaluation date. 
- R, F, and M Scores = percentile-based or threshold-based scores used to classify customers from low to high value. 
- Total / Combined Score = concatenation or combination of the three component scores to support segment mapping. 
- Segment = business classification such as Champions, Loyal Customers, At Risk, Need Attention, or Lost Customers. 

## Dashboard KPIs

The dashboard highlights customer strategy through KPIs and summary views such as total customers, segment distribution, high-value customer groups, and customer-level drill-down. These are common and appropriate outputs of RFM dashboards because the goal is to show both the size and quality of the customer base. 

From an executive perspective, the most important KPI categories are customer volume, segment composition, loyalty strength, churn risk, and customer spend quality. Together, these create a practical operating view for retention and growth teams. 

## Dashboard Design (Business Problem -> Analysis -> Insights & Recommendations -> Action)

The dashboard design follows a business flow of problem to analysis to insight to action. First, it establishes the size and composition of the customer base, then it breaks that base into RFM segments, and finally it enables filtered analysis of specific customer groups for targeted action. 

This is the correct executive structure for customer segmentation reporting because segmentation is only useful when it supports differentiated decisions. Segment-level dashboards are most valuable when they help teams move directly from customer classification to campaign, retention, and reactivation planning. 

## Visual Analysis

### 1. Segment Distribution
**Business Question:** How is the customer base distributed across strategic value segments? 

**Insight:** The visual reveals the mix of high-value, stable, emerging, and at-risk customers across the portfolio, allowing decision-makers to assess whether revenue concentration is healthy or overly dependent on a narrow group. 

**Executive Decision:** Use segment mix to allocate loyalty, retention, and reactivation budgets more effectively across the customer base. 

### 2. Total Customers
**Business Question:** What is the scale of the addressable customer base being managed through segmentation? 

**Insight:** This KPI establishes the size of the customer universe and acts as the baseline for segment penetration, campaign reach, and retention planning. 

**Executive Decision:** Use this KPI as the denominator for customer strategy targets and segment-specific performance reviews. 

### 3. Champion Customers
**Business Question:** How many top-value customers currently drive the strongest business performance? 

**Insight:** Champion customers combine strong recency, high purchase frequency, and high spend, making them the most strategically valuable group in the portfolio. 

**Executive Decision:** Protect this segment through premium engagement, early access programs, and personalized upsell strategies. 

### 4. Loyal Customers
**Business Question:** How strong is the stable repeat-purchase customer base? 

**Insight:** Loyal customers represent dependable recurring value and are strong candidates for cross-sell, upsell, and relationship-expansion initiatives. 

**Executive Decision:** Design campaigns that deepen wallet share and increase lifetime value for this segment. 

### 5. At Risk / Need Attention Customers
**Business Question:** Which customers show early signals of disengagement or churn risk? 

**Insight:** Customers with weak recency but historically meaningful frequency or spend indicate recoverable value that may be lost without intervention. 

**Executive Decision:** Launch win-back and reminder journeys before these customers become fully lost. 

### 6. Customer Detail Table
**Business Question:** Which specific customers belong to each segment, and what are their behavioral patterns? 

**Insight:** The detail view operationalizes the segmentation by exposing customer-level metrics and segment labels, which makes the dashboard useful beyond strategy review and into campaign execution. 

**Executive Decision:** Share these customer-level lists with CRM, sales, or lifecycle marketing teams for direct action. 

## Executive Business Insights

Several high-impact business insights emerge from the analysis. Customer value is not defined by spend alone, but by a combination of recent engagement, repeat purchase behavior, and monetary contribution. RFM is valuable specifically because it surfaces these three dimensions together rather than relying on revenue alone. 

The analysis also makes it clear that high-value customers should not be managed in the same way as new, low-engagement, or at-risk customers. Segment-led decision-making is more effective than broad, undifferentiated campaign planning because each segment represents a different value and risk profile. 

## Actionable Business Recommendations

Based on the dashboard, the business should consider the following actions:

- Protect Champion Customers with loyalty benefits, premium service, and early access programs. 
- Grow Loyal Customers through personalized cross-sell and upsell campaigns. 
- Nurture New Customers with onboarding and repeat-purchase incentives so they mature into higher-value segments. 
- Reactivate At Risk Customers using targeted win-back offers and reminder journeys. 
- Use customer-level segmentation outputs to power CRM workflows and retention campaigns. 

## Business Value Delivered

This dashboard delivers business value by converting raw transaction data into a strategic customer segmentation framework, helping leadership prioritize customer actions based on behavioral value instead of broad assumptions. It also creates an operational bridge between analytics and execution by enabling segment-specific targeting. 

The solution is especially strong as a portfolio project because it demonstrates both analytical modeling and business storytelling. It shows the ability to translate raw business data into decision-support outputs that are useful for marketing, retention, and customer growth strategy. 

## Tools & Skills Used

- Power BI Desktop. 
- DAX and calculated tables. 
- Customer segmentation and RFM analysis. 
- KPI design and interactive dashboarding. 
- Retention, loyalty, and customer value analytics. 
- Executive-style business storytelling for analytics portfolios. 

