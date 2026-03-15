**Project Title**
"Early Churn Risk Identification in E-Commerce Using Behavioral Segmentation"

---

**The Problem Statement**
In e-commerce, businesses typically only recognize lost customers after they have already left, making retention efforts too late to be effective. This project investigates whether early behavioral signals, specifically inactivity patterns and engagement levels, can identify at-risk users before they fully churn, enabling timely intervention while the customer is still recoverable.

---

**The Central Question**
Can user inactivity and behavioral patterns predict churn risk early enough to enable meaningful intervention and does behavioral segmentation reveal which users are most valuable to protect?

---

**Supporting Questions the Analysis Answered**
1. How many users are currently active, at risk, or already churned based on inactivity thresholds?
2. Are at-risk users financially distinguishable from active users through spend and purchase behavior?
3. Which behavioral segments represent the highest revenue risk if lost?
4. Do low-activity users who purchase consistently represent a hidden high-value customer group?
5. What is the intervention window - how many days exist between early warning and confirmed churn?
6. How does purchase frequency distribute across churn categories?

---

**Dataset**

| Table | Dataset Level | Source |
|-------|--------------|--------|
| Table 1 | Synthetic e-commerce clickstream | Generated dataset |

| Column | Description |
|--------|-------------|
| UserID | Unique customer identifier |
| SessionID | Session the event occurred in |
| Timestamp | Exact date and time of event |
| EventType | Action taken (page_view, purchase, etc.) |
| ProductID | Product involved (where applicable) |
| Amount | Purchase value (purchase events only) |
| Outcome | Redundant with EventType - dropped during cleaning |

- **Size:** 74,817 rows, 1,000 users
- **Time Period:** January 1, 2024 – July 24, 2024

---

**Python & Analytical Skills Showcased**

- Datetime conversion and date arithmetic
- GroupBy aggregation and multi-column agg()
- Lambda functions and custom apply() logic
- Boolean indexing and filtering
- Median-based thresholding
- Multi-condition segmentation with .loc
- Matplotlib and seaborn visualization
- Side-by-side chart layouts for scale imbalance
- Box plots, histograms, bar charts, horizontal bar charts

---

**Analytical Decisions Made**

| Decision | Original Plan | Final Decision | Reason |
|----------|--------------|----------------|--------|
| Churn threshold | 30 days | 15 days | Max inactivity in dataset was only 19 days |
| Potential churn threshold | 25 days | 7 days | Same reason — adjusted to fit actual data |
| Activity level split | Not defined | Median total events (75) | Splits users evenly, resistant to outliers |
| Quiet Loyal definition | 1-2 purchases | Purchase frequency >= median | More defensible - normalizes for duration |
| Dataset end date | Hardcoded July 24 | Max last_activity timestamp | Eliminated negative inactivity values |

---

**Tools Used**

| Tool | Purpose |
|------|---------|
| VS Code | Development environment |
| Python (pandas, numpy) | Data cleaning, feature engineering, segmentation |
| Matplotlib + Seaborn | All visualizations |
| Jupyter Notebooks | Analysis pipeline |
| GitHub | Portfolio publishing |

---

**Key Findings**

| Finding | Evidence |
|---------|---------|
| At-risk users are financially invisible | Potential Churn spend $2,629 vs Active $2,640 — $11 difference |
| Quiet Loyal users are hidden high-value customers | 2 of top 10 spenders are Quiet Loyal, each spending ~$5,000 |
| Intervention window is narrow | Only 7 days between early warning and confirmed churn |
| High Activity Potential Churn is most urgent | 34 users, spend up to $4,600, behavior mirrors best users |

---

**Final Outputs**

| Label | Count | Percentage |
|-------|-------|-----------|
| Active | 928 | 92.8% |
| Potential Churn | 66 | 6.6% |
| Churned | 6 | 0.6% |

| Segment | Count |
|---------|-------|
| High Activity — Active | 499 |
| Low Activity — Active | 243 |
| Low Activity — Retained (Quiet Loyal) | 186 |
| High Activity — Potential Churn | 34 |
| Low Activity — Potential Churn | 32 |
| High Activity — Churned | 3 |
| Low Activity — Churned | 3 |

---

**Project Structure**
```
Ecommerce_Churn_Analysis/
├── data/
│   ├── raw/
│   └── cleaned/
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_user_features.ipynb
│   ├── 03_churn_labeling.ipynb
│   ├── 04_behavioral_segmentation.ipynb
│   └── 05_EDA_visuals_and_insights.ipynb
├── reports/
│   └── screenshots/
├── README.md
└── requirements.txt
```
