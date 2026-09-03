# Superstore-Marketing-Campaign-analysis-for-gold-membership-acceptance
End-to-end data analytics capstone project analyzing Superstore's Gold Membership  campaign using Excel, SQL, Python, Machine Learning and Power BI.

# 🛒 Superstore Marketing Campaign Analysis

> **End-to-end data analytics capstone project** analyzing a retail superstore's Gold Membership marketing campaign using Excel, SQL, Python, Machine Learning and Power BI.

---

## 👤 Author
**Sujal More**

Data Analytics Capstone Project

---

## 📌 Overview
Every year-end, Superstore runs a promotional campaign inviting existing customers to purchase a **Gold Membership offering a 20% discount** on all purchases. Despite the campaign effort, only **15.05% of customers accepted** the offer — leaving 85% unreached.

This project uses data analytics and machine learning to answer:
- **Who** is most likely to accept the membership?
- **What** demographic and behavioral factors drive acceptance?
- **How** can the business improve campaign ROI next time?

---

## 📊 Dataset
- **2,213 customers | 22 features**
- **Source:** Superstore Sales Campaign Dataset

| Feature Type | Columns |
|---|---|
| Demographics | Age, Income, Education, Marital Status, Family Size |
| Spending | Wine, Meat, Fish, Fruits, Sweets, Gold Products |
| Channels | Web, Store, Catalogue, Deals, Web Visits |
| Target Variable | Response (1 = Accepted, 0 = Declined) |

---

## 🗂️ Project Phases

| Phase | Description |
|---|---|
| 1 | Business Understanding & KPI Framework |
| 2 | Data Validation — Excel |
| 3 | SQL Database Design & DDL |
| 4 | Data Ingestion into SQL |
| 5 | Python + SQL Connection |
| 6 | Data Cleaning, Feature Engineering & EDA |
| 7 | Statistical Analysis & Predictive Modelling |
| 8 | Power BI Dashboard Development |
| 9 | Strategic Insights & Recommendations |

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| Excel | Data validation & integrity checks |
| MySQL | Database design, storage & querying |
| Python | EDA, feature engineering, statistics, modelling |
| Power BI | Interactive dashboards & KPI reporting |

---

## 🐍 Python Libraries

```python
pandas, numpy          # Data manipulation
matplotlib, seaborn    # Visualization
scipy                  # Statistical testing
scikit-learn           # Machine learning
imbalanced-learn       # SMOTE oversampling
mysql-connector-python # SQL connection
```

---

## ⚙️ Feature Engineering

New features created from existing columns:

| Feature | How Created |
|---|---|
| Age | 2026 - Year_Birth |
| Tenure_Days | Today - Dt_Customer |
| Total_Spend | Sum of all Mnt* columns |
| Category_Breadth | Count of categories with non-zero spend |
| Total_Purchases | Sum of all channel purchases |
| Web_Store_Ratio | NumWebPurchases / NumStorePurchases |
| Family_Size | Kidhome + Teenhome |

---

## 📈 Statistical Analysis

| Test | Variables | Result |
|---|---|---|
| T-Test | Income vs Response | ✅ Significant (p=0.0000) |
| T-Test | Total Spend vs Response | ✅ Significant (p=0.0000) |
| T-Test | Recency vs Response | ✅ Significant (p=0.0000) |
| T-Test | Age vs Response | ❌ Not Significant (p=0.328) |
| Chi-Square | Education vs Response | ✅ Significant (p=0.0001) |
| Chi-Square | Marital Status vs Response | ✅ Significant (p=0.0000) |
| ANOVA | Total Spend by Education | ✅ Significant (F=16.92) |

---

## 🤖 Machine Learning Models

### The Challenge — Class Imbalance
```
Non-Responders: 1,880 (85%)
Responders:       333 (15%)
```
A model predicting "No" for everyone achieves 85% accuracy but catches zero actual responders — completely useless for marketing.

### The Solution — SMOTE
SMOTE (Synthetic Minority Oversampling Technique) balances the training data by creating synthetic responder examples — resulting in 1,504 vs 1,504 balanced classes.

### Model Comparison

| Model | Accuracy | Recall | F1 Score | ROC-AUC | Responders Caught |
|---|---|---|---|---|---|
| Logistic Regression | 86% | 18% | 0.28 | 0.80 | 12 |
| Random Forest | 86% | 22% | 0.33 | 0.84 | 15 |
| **RF + SMOTE ✅** | **84%** | **48%** | **0.47** | **0.83** | **32** |

**Recommended Model: Random Forest + SMOTE**
- Catches 32 real responders vs 15 in baseline — more than double
- Recall jumped from 22% → 48%
- In marketing, missing a genuine prospect costs far more than a false alarm

---

## 🔑 Feature Importance (RF + SMOTE)

| Rank | Feature | Importance |
|---|---|---|
| 1 | Recency | 13.9% |
| 2 | Web/Store Ratio | 11.9% |
| 3 | Total Spend | 11.6% |
| 4 | Income | 10.0% |
| 5 | Tenure Days | 9.7% |
| 6 | Family Size | 7.3% |
| 7 | Store Purchases | 6.4% |

---

## 💡 Key Findings

- Responders earn **$9,386 more** annually ($60,210 vs $50,824)
- Responders spend **nearly 2x more** ($985 vs $539)
- **Recency is #1 predictor** — responders last shopped 35 days ago vs 51
- **Catalogue users are 75% more likely** to respond
- **Age has no statistical impact** on acceptance
- **PhD holders** show highest acceptance rate (21%)
- **Very High income customers** (>$90k) show ~50% acceptance rate
- **Wine and Meat** are the strongest category indicators of acceptance

---

## 📋 Spending by Category

| Category | Responders | Non-Responders |
|---|---|---|
| Wine | $502.62 | $270.18 |
| Meat | $293.77 | $144.50 |
| Gold Products | $61.25 | $40.84 |
| Fish | $51.71 | $35.14 |
| Sweets | $38.37 | $25.03 |
| Fruits | $37.94 | $24.27 |

---

## 📢 Channel Performance

| Channel | Share | Responders Avg | Non-Responders Avg |
|---|---|---|---|
| In-Store | 39% | 6.08 | 5.76 |
| Web | 27.5% | 5.07 | 3.91 |
| Catalogue | 17.9% | 4.20 | 2.40 |
| Deals | 15.6% | 2.34 | 2.32 |

---

## ✅ Recommendations to Business

1. **Target Income > $55,000 and Total Spend > $400 customers first** — highest conversion probability
2. **Lead with Catalogue and Web channels** — catalogue users are 75% more likely to respond
3. **Time campaign within 30 days of last purchase** — Recency is the #1 predictor
4. **Re-engage dormant customers (60+ days) separately** — don't pitch membership until they're active again
5. **Redesign offer for family households** — current benefits don't align with family spending priorities
6. **Use predictive model to score customers before campaign** — focus on top 20-30% predicted responders

---

## 🔭 Future Scope

- Collect richer data — browsing history, past campaign responses, transaction timestamps
- Try advanced models — XGBoost, Neural Networks
- A/B test Catalogue vs Web channel effectiveness
- Retrain model after each campaign with new response data
- Redesign membership benefits specifically for family households

---

## 📁 Repository Structure

```
superstore-marketing-campaign-analysis/
│
├── data/
│   ├── superstore_cleaned.csv      # Original cleaned dataset
│   └── superstore_final.csv        # Feature engineered dataset
│
├── notebooks/
│   └── superstore_analysis.ipynb   # Complete Python analysis
│
├── dashboard/
│   └── Superstore_Dashboard.pbix   # Power BI dashboard file
│
├── presentation/
│   └── Superstore_Campaign_Analysis.pptx
│
├── report/
│   └── Superstore_Campaign_Report.docx
│
└── README.md
```

---

## 📊 Dashboard Preview

### Executive Dashboard
- KPI Cards: Acceptance Rate (15.05%), Avg Income ($52k), Avg Spend ($607)
- Membership Response Distribution — Donut Chart
- Acceptance Rate by Education & Marital Status
- Average Spend by Product Category
- Filters: Education | Marital Status

<img width="1345" height="771" alt="EXECUTIVE  DASHBOARD" src="https://github.com/user-attachments/assets/75fe934c-8c1b-48e0-ba74-44c885f0f456" />


### Marketing Dashboard
- Total Spend vs Recency Scatter Plot — by Response Group
- Average Total Spend by Income Band
- Acceptance Rate by Income Band
- Avg Spend by Category — Responders vs Non-Responders
- Filters: Response Label | Family Size

<img width="1327" height="775" alt="MARKETING DASHBOARD" src="https://github.com/user-attachments/assets/bd843798-4a9f-40a9-9608-746f185dc45c" />


---

## 📌 Results Summary

| Metric | Value |
|---|---|
| Total Customers | 2,213 |
| Acceptance Rate | 15.05% |
| Average Income | $52,247 |
| Average Total Spend | $607.02 |
| Top Spending Category | Wine ($305.15) |
| Top Channel | In-Store (39%) |
| Best Model | Random Forest + SMOTE |
| Model Recall | 48% |
| ROC-AUC | 0.83 |
| Responders Correctly Caught | 32 out of 67 |

---

*Capstone Project — Data Analytics with GenAI | Career247*
