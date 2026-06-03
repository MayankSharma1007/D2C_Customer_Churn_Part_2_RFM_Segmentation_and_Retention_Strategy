# D2C Customer Churn Intelligence & Retention Analytics
## Part 2 – RFM Segmentation & Retention Strategy

---

## Project Overview

Customer retention is significantly more cost-effective than customer acquisition. Before deploying a machine learning churn prediction model, businesses can identify valuable customer groups using behavioral segmentation techniques.

This project performs customer segmentation using:

- RFM Analysis (Recency, Frequency, Monetary Value)
- Customer Support Behaviour
- Return and Refund Behaviour
- Campaign Engagement
- Category Diversity
- Loyalty Membership
- Discount Usage Patterns

The objective is to identify customer groups with different retention requirements and recommend targeted business actions.

---

## Business Objective

The company wants to understand:

- Which customers are most valuable.
- Which customers are likely to become inactive.
- Which customers require immediate retention intervention.
- Which customer segments should receive marketing budget priority.
- How retention strategies can be customized for different customer groups.

---

## Dataset Information

The analysis uses the D2C Customer Churn dataset package consisting of multiple customer, transaction and engagement datasets.

Datasets used:

| Dataset | Description |
|----------|-------------|
| customers.csv | Customer master information |
| orders.csv | Customer purchase history |
| support_tickets.csv | Customer support interactions |
| web_events.csv | Website and campaign engagement |
| intervention_history.csv | Historical retention interventions |
| churn_labels.csv | Churn status labels |
| rfm_snapshot.csv | Existing customer behavioural attributes |

---

# Methodology

## Step 1 – RFM Feature Engineering

Three key customer behaviour metrics were created using order history.

### Recency

Measures the number of days since the customer's most recent purchase.

Customers who purchased recently are generally more engaged and less likely to churn.

### Frequency

Measures the total number of orders placed by a customer.

Frequent purchasers usually demonstrate stronger platform loyalty.

### Monetary Value

Measures total spending by a customer across all purchases.

Higher monetary value generally indicates greater business importance.

---

## Step 2 – RFM Scoring

Each customer was assigned scores ranging from 1 to 5.

### Recency Score

Customers with recent purchases receive higher scores.

### Frequency Score

Customers with more purchases receive higher scores.

### Monetary Score

Customers with higher spending receive higher scores.

### Combined RFM Score

Overall customer quality was represented using:

RFM Score = R Score + F Score + M Score

---

## Step 3 – Additional Behavioural Signals

To improve segmentation quality, multiple non-RFM signals were incorporated.

### Support Behaviour Signals

Generated features:

- Ticket Count
- Average Resolution Time
- Average Sentiment Score
- Reopened Ticket Count

These variables help identify dissatisfaction and support-related friction.

---

### Return Behaviour Signals

Generated features:

- Total Returned Orders
- Return Rate

High return rates may indicate product dissatisfaction, poor customer experience or potential churn risk.

---

### Campaign Engagement Signals

Generated features:

- Email Opens (Last 30 Days)
- Campaign Clicks (Last 30 Days)
- Engagement Score

These variables identify customers who actively respond to marketing communication.

---

### Category Diversity

Measures the number of unique product categories purchased by a customer.

Customers purchasing across multiple categories generally demonstrate stronger attachment to the platform.

---

### Loyalty Features

Customer membership information was incorporated through loyalty tiers.

Higher loyalty tiers generally indicate stronger long-term retention potential.

---

### Discount Behaviour

Average discount usage percentage was calculated for every customer.

This feature helps identify customers whose purchasing decisions are heavily influenced by promotions.

---

# Customer Segments Created

A total of eight customer segments were created using a combination of RFM metrics and behavioural signals.

---

## 1. Champions

### Characteristics

- High Recency Score
- High Frequency Score
- High Monetary Score

### Business Importance

These customers represent the most valuable customer group and generate significant revenue.

---

## 2. Loyal Customers

### Characteristics

- Frequent purchases
- Consistent engagement
- Strong purchase history

### Business Importance

Reliable source of recurring revenue.

---

## 3. New Customers

### Characteristics

- Recently acquired
- Limited purchase history

### Business Importance

Future growth potential if nurtured correctly.

---

## 4. At Risk Customers

### Characteristics

- Previously active
- Declining recent engagement

### Business Importance

High recovery potential before churn occurs.

---

## 5. Dormant Customers

### Characteristics

- Long inactivity periods
- Low recent engagement

### Business Importance

Potential reactivation opportunities.

---

## 6. Discount Sensitive Customers

### Characteristics

- Heavy dependence on promotions
- Strong discount usage behaviour

### Business Importance

Revenue generating but margin-sensitive customer group.

---

## 7. High Value Unhappy Customers

### Characteristics

- High spending behaviour
- Elevated complaints, returns or dissatisfaction signals

### Business Importance

Highest churn-risk revenue segment.

---

## 8. Regular Customers

### Characteristics

- Moderate behaviour across most metrics
- No strong positive or negative indicators

### Business Importance

Large customer base with potential for future growth.

---

# Retention Strategy

Different customer segments require different retention approaches.

| Segment | Recommended Action |
|----------|------------------|
| Champions | VIP programs and exclusive benefits |
| Loyal Customers | Loyalty rewards and cross-selling |
| New Customers | Onboarding campaigns and education |
| At Risk Customers | Personalized win-back campaigns |
| Dormant Customers | Reactivation offers |
| Discount Sensitive Customers | Targeted promotional campaigns |
| High Value Unhappy Customers | Priority customer support intervention |
| Regular Customers | Product discovery and engagement campaigns |

---

# Campaign Budget Prioritization

Assuming a limited retention budget of ₹100,000, marketing resources should be allocated according to expected business impact.

| Priority | Segment | Budget Allocation |
|----------|----------|------------------|
| 1 | High Value Unhappy | 30% |
| 2 | At Risk | 25% |
| 3 | Champions | 15% |
| 4 | Loyal Customers | 10% |
| 5 | New Customers | 8% |
| 6 | Discount Sensitive Customers | 5% |
| 7 | Regular Customers | 4% |
| 8 | Dormant Customers | 3% |

This allocation prioritizes customers who can generate the highest return on retention investment.

---

# Manual Review Cases

Automated segmentation cannot always capture every customer scenario.

To improve decision quality, fifteen customers with conflicting behavioural indicators were manually reviewed.

These cases included combinations of:

- High spending but low engagement
- High return behaviour
- Elevated support activity
- Mixed retention indicators

Detailed analysis is documented in:

**manual_review_cases.md**

---

# Repository Structure

```text
Part_2_RFM_Segmentation/
│
├── README.md
├── requirements.txt
│
├── rfm_segmentation.ipynb
│
├── retention_strategy.md
├── manual_review_cases.md
│
├── customers.csv
├── orders.csv
├── support_tickets.csv
├── web_events.csv
├── intervention_history.csv
├── churn_labels.csv
├── rfm_snapshot.csv
│
├── outputs/
│   ├── segments.csv
│   ├── segment_distribution.png
│   ├── rfm_distribution.png
│   ├── recency_distribution.png
│   ├── frequency_distribution.png
│   └── monetary_distribution.png
```

---

# How To Run

## Clone Repository

```bash
git clone <repository-url>
```

## Navigate To Project Folder

```bash
cd Part_2_RFM_Segmentation
```

## Install Dependencies

```bash
pip install -r requirements.txt
```

## Launch Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
rfm_segmentation.ipynb
```

Run all notebook cells sequentially.

---

# Outputs Generated

## 1. rfm_segmentation.ipynb

Contains:

- Data loading
- Feature engineering
- RFM creation
- Behavioural signal generation
- Customer segmentation
- Visual analysis
- Business interpretation

---

## 2. segments.csv

Contains:

- Customer ID
- Segment Name
- Recency
- Frequency
- Monetary Value
- Support Signals
- Return Behaviour
- Campaign Engagement
- Loyalty Information
- Discount Behaviour

---

## 3. retention_strategy.md

Contains:

- Segment definitions
- Customer behaviour explanation
- Retention recommendations
- Expected business value
- Budget prioritization strategy

---

## 4. manual_review_cases.md

Contains:

- Fifteen manually reviewed customers
- Dataset-backed reasoning
- Recommended actions
- Business justifications

---

# Key Business Insights

1. Customer retention decisions improve significantly when behavioural signals are combined with traditional RFM analysis.

2. High Value Unhappy Customers represent the most important retention opportunity because they combine strong revenue contribution with visible dissatisfaction.

3. At Risk Customers provide substantial recovery potential at a lower cost than acquiring new customers.

4. Campaign engagement, support activity and return behaviour provide valuable context beyond purchase history.

5. Segment-based retention planning enables more efficient allocation of marketing resources and retention budgets.

---

# Conclusion

This project demonstrates how RFM segmentation combined with behavioural analytics can provide actionable customer retention insights before deploying predictive machine learning models. The resulting segments allow businesses to prioritize retention resources, design personalized campaigns and improve customer lifetime value through data-driven decision making.

---

## Author

**Mayank Sharma**

Capstone Project – D2C Customer Churn Intelligence & Retention Analytics

**Part 2: RFM Segmentation & Retention Strategy**
