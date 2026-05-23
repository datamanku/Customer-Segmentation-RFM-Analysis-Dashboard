
---

# Customer Segmentation (RFM Analysis) Dashboard

<img width="1156" height="637" alt="image" src="https://github.com/user-attachments/assets/1fa0c0f5-975c-454e-b9a0-f8110ffc5996" />


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

---

## Business Problem

The business had transaction data but lacked a structured framework to answer critical customer strategy questions such as which customers contribute the highest long-term value, which customers are loyal repeat buyers worth protecting, which customers are at risk of dropping off, and which new customers should be nurtured into higher-value segments. 

Without customer segmentation, marketing and retention teams cannot prioritize campaigns effectively, and leadership cannot align customer strategy with value creation. RFM analysis is a standard marketing framework for ranking customers by how recently, how frequently, and how much they purchase, specifically to support targeted actions. 

---

## Executive Questions Solved

This dashboard was built to answer the following business questions:

- Which customers are the most valuable based on recency, repeat buying behavior, and spending? 
- How is the customer base distributed across strategic segments such as Champions, Loyal Customers, At Risk, and Lost or low-engagement customers? 
- Which customers require retention, loyalty, or win-back intervention? 
- Which recently acquired customers show potential for long-term value development? 
- How can the business operationalize segment-based targeting using customer-level detail? 

---

## Dataset

This uses retail transaction data containing customer, invoice, product, quantity, price, and date information, which is then aggregated to the customer level for RFM scoring and segmentation. This specifically works from invoice-level retail data and derives customer-level Recency, Frequency, and Monetary metrics for each customer ID. 

The analytical grain of the final model is the customer, because segmentation decisions are made at the customer level rather than at the transaction line level. This design is consistent with other RFM Power BI implementations that summarize sales orders into customer-level metrics before assigning segment labels. 

---

## Data Preparation

Data preparation focused on creating a customer-level analytical table for RFM logic. The raw transaction data is grouped by customer so that each customer receives a single set of metrics for last purchase date, purchase count, and total spend. 

The standard preparation flow for this style of RFM dashboard includes calculating Recency as days since the last purchase, Frequency as total or distinct purchase count, and Monetary as total spend over the evaluation period. This transformed model supports targeted filtering, segment-level views, and customer-level action lists. 

- ### **Blank Customer ID**:
During the initial data review, I found that the Customer ID column contained blank values in several rows. Since these records could not be linked to a specific customer, they were excluded from the final dataset.

<img width="1291" height="824" alt="image" src="https://github.com/user-attachments/assets/8d86ec7e-2655-4e5b-b046-b1d0adb7ea85" />

- ### **Negative and Zero Revenue**:
While checking the transaction data, I noticed multiple rows with negative values in the Quantity column. These represented returned transactions, so they were removed because they did not contribute to revenue analysis. I also identified rows where Unit Price was recorded as zero. Since a zero price is not meaningful for sales analysis, these records were filtered out to maintain data quality and accuracy. And also no product can have unit price of zero and it was contributing to zero value in revenue , hence it was also eliminated.

After applying these cleaning steps, the dataset was refined and prepared for modeling and further analysis.

<img width="1827" height="819" alt="image" src="https://github.com/user-attachments/assets/f7067149-000f-4cef-b600-5e232d4a2b37" />


---

## Data Model

A new calculated CustomerRFM summary table is created to support segmentation analysis, with customer ID as the key entity and derived last purchased date, Recency, Frequency, and Monetary values attached to each customer record. In comparable Power BI RFM implementations, this table is built from the transactional table using summary logic and then connected to a segment mapping or score table for classification. 

<img width="652" height="379" alt="image" src="https://github.com/user-attachments/assets/b83cda89-5ba3-4c6b-81bc-a08937531309" />


For practical analytical structure for this project many new calculated columns were created including : customer identifier, recency value, frequency value, monetary value, individual Recency score, Frequency score and Monetary score, a combined score, and a segment label including but not limited to as Champion customer, Loyal Customer or At Risk customer. This model shifts the report from descriptive sales reporting into customer strategy analysis. 


- ### **Model**:
<img width="688" height="443" alt="image" src="https://github.com/user-attachments/assets/ec885362-249f-4856-ad2a-2b14c57b2462" />




---

## DAX Measures

Key analytical logic used in the project includes:

- ### **Last Purchase Date**:   
The most recent date on which a customer made a purchase. It is used to calculate recency in RFM analysis.

- ### **Frequency**:  
The total number of purchases or transactions made by a customer. It shows how often the customer buys.

- ### **Monetary**:
The total amount of money a customer has spent. It reflects the customer’s overall spending contribution.

<img width="652" height="379" alt="image" src="https://github.com/user-attachments/assets/58c19552-4c66-4001-b892-d74b57e6df88" />

- ### **Recency**:
The number of days since the customer’s last purchase. A lower value usually means a more active customer. Date difference between the customer’s last purchase date and the evaluation date.

<img width="658" height="337" alt="image" src="https://github.com/user-attachments/assets/bbe4e3de-e0ed-43a5-981d-3bfbf5aa7504" />


- ### **Frequency Score**:
A ranked score given to customers based on how often they purchase. Higher scores indicate more frequent buyers.
 
<img width="959" height="397" alt="image" src="https://github.com/user-attachments/assets/2216fd47-d24d-4f36-83ed-09545b7415f7" />

- ### **Monetary Score**:
A ranked score assigned based on total spending. Higher scores represent customers with greater monetary value.

<img width="952" height="382" alt="image" src="https://github.com/user-attachments/assets/298df292-a582-4119-a930-3034d67098a6" />

- ### **Recency Score**:
A ranked score based on how recently a customer purchased. Higher scores usually mean the customer bought more recently.

<img width="1088" height="410" alt="image" src="https://github.com/user-attachments/assets/94c47d38-6a0e-48fa-996d-e9b81db9ffb5" />

- ### **Segment**: 
A customer group formed by combining RFM scores. It helps classify customers into meaningful business categories such as Champions, Loyal Customers, At Risk, Need Attention, or Lost Customers.

<img width="1281" height="422" alt="image" src="https://github.com/user-attachments/assets/8d6e22b6-04ad-40dc-b85a-3b65cb4657f5" /> 

---

## Dashboard KPIs

The dashboard highlights customer strategy through KPIs and summary views such as total customers, segment distribution, high-value customer groups, and customer-level drill-down. These are common and appropriate outputs of RFM dashboards because the goal is to show both the size and quality of the customer base. 

The dashboard is professionally framed around the following KPI layer:

- ### **Total Customers**
<img width="182" height="105" alt="image" src="https://github.com/user-attachments/assets/f9964fd9-7400-483f-af82-fa01d4557399" />


- ### **Champion Customers**
<img width="185" height="105" alt="image" src="https://github.com/user-attachments/assets/143caac2-3fdc-480b-8aa5-168a8fb2322d" />


- ### **Loyal Customers**
<img width="186" height="111" alt="image" src="https://github.com/user-attachments/assets/47821c71-4fc3-43c4-a937-02fa0198b6e2" />


- ### **New Customers**
<img width="182" height="105" alt="image" src="https://github.com/user-attachments/assets/da9f0e8a-fc56-4fc6-950a-3edfed62944c" />


- ### **At Risk Customers**
<img width="184" height="112" alt="image" src="https://github.com/user-attachments/assets/27ebd6be-fcec-4392-8bae-f7c888fbfaa7" />


- ### **Average Frequency Score**
<img width="362" height="92" alt="image" src="https://github.com/user-attachments/assets/7b47fce2-6f0d-4817-b35f-44e883dbe4f7" />


- ### **Average Monetary Score**
<img width="364" height="92" alt="image" src="https://github.com/user-attachments/assets/9f8a3ff2-33ca-4a23-b10a-5871b279ed30" />


- ### **Average Recency Score**
<img width="360" height="97" alt="image" src="https://github.com/user-attachments/assets/e83b18b3-ce8a-40d6-90a9-3ee5ad3104a2" />


From an executive perspective, the most important KPI categories are customer volume, segment composition, loyalty strength, and customer spend quality. Together, these create a practical operating view for retention and growth teams. 

---

## Dashboard Design (Business Problem -> Analysis -> Insights & Recommendations -> Action)

The dashboard design follows a business flow of problem to analysis to insight to action. First, it establishes the size and composition of the customer base, then it breaks that base into RFM segments, and finally it enables filtered analysis of specific customer groups for targeted action. 

This is the correct executive structure for customer segmentation reporting because segmentation is only useful when it supports differentiated decisions. Segment-level dashboards are most valuable when they help teams move directly from customer classification to campaign, retention, and reactivation planning. 

## Visual Analysis

### 1. Segment Distribution
**Business Question:** How is the customer base distributed across strategic value segments? 

**Insight:** The visual reveals the mix of high-value, stable, emerging, and at-risk customers across the portfolio, allowing decision-makers to assess whether revenue concentration is healthy or overly dependent on a narrow group. 

**Executive Decision:** Use segment mix to allocate loyalty, retention, and reactivation budgets more effectively across the customer base. 

<img width="554" height="376" alt="image" src="https://github.com/user-attachments/assets/818d5eb9-63d6-4308-aacc-da96bee9f466" />


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

<img width="588" height="377" alt="image" src="https://github.com/user-attachments/assets/398c6050-ba8e-4413-8ee1-948cc518d97f" />


---

## Executive Business Insights

Several high-impact business insights emerge from the analysis. Customer value is not defined by spend alone, but by a combination of recent engagement, repeat purchase behavior, and monetary contribution. RFM is valuable specifically because it surfaces these three dimensions together rather than relying on revenue alone. 

The analysis also makes it clear that high-value customers should not be managed in the same way as new, low-engagement, or at-risk customers. Segment-led decision-making is more effective than broad, undifferentiated campaign planning because each segment represents a different value and risk profile. 

---

## Actionable Business Recommendations

Based on the dashboard, the business should consider the following actions:

- Protect Champion Customers with loyalty benefits, premium service, and early access programs. 
- Grow Loyal Customers through personalized cross-sell and upsell campaigns. 
- Nurture New Customers with onboarding and repeat-purchase incentives so they mature into higher-value segments. 
- Reactivate At Risk Customers using targeted win-back offers and reminder journeys. 
- Use customer-level segmentation outputs to power CRM workflows and retention campaigns. 

---

## Business Value Delivered

This dashboard delivers business value by converting raw transaction data into a strategic customer segmentation framework, helping leadership prioritize customer actions based on behavioral value instead of broad assumptions. It also creates an operational bridge between analytics and execution by enabling segment-specific targeting. 

The solution is especially strong as a portfolio project because it demonstrates both analytical modeling and business storytelling. It shows the ability to translate raw business data into decision-support outputs that are useful for marketing, retention, and customer growth strategy. 

---

## Tools & Skills Used

- Power BI Desktop. 
- DAX and calculated tables. 
- Customer segmentation and RFM analysis. 
- KPI design and interactive dashboarding. 
- Retention, loyalty, and customer value analytics. 
- Executive-style business storytelling for analytics portfolios.

---

