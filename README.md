# FinMark Customer Segmentation — Data Mining Project

End-to-end data mining workflow for FinMark Corporation's customer segmentation project using clustering techniques on transactional, product, and feedback data.

---

## Business Problem

FinMark currently offers standard financial products (savings, credit, loans) with limited personalization. This project builds a clustering-based customer segmentation model to identify distinct customer groups and support targeted product recommendations — improving customer satisfaction and service relevance.

---

## Project Outputs

| Milestone | Description | Status |
|-----------|-------------|--------|
| Milestone 1 | Data Preparation & Exploratory Data Analysis (EDA) | ✅ Complete |
| Milestone 2 | Clustering & Customer Segmentation (K-Means) | ✅ Complete |
| Terminal Assessment | Final Report + Presentation + Product Recommendations | ✅ Complete |

---

## Repository Structure

```
finmark-customer-segmentation/
│
├── Milestone_1_Project_Data_Preparation_and_EDA/
│   │
│   ├── data/
│   │   ├── raw/
│   │   │   ├── Transaction_Data.csv
│   │   │   ├── Product_Offering_Data.csv
│   │   │   └── Customer_Feedback_Data.csv
│   │   │
│   │   └── processed/
│   │       ├── finmark_cleaned_transactions.csv
│   │       └── finmark_engineered_customer_features.csv
│   │
│   ├── notebooks/
│   │   └── Milestone_1_Project_Data_Preparation_and_EDA.ipynb
│   │
│   └── Milestone_1_README.md
│
├── Milestone_2_Clustering_and_Customer_Segmentation/
│   │
│   ├── data/
│   │   └── processed/
│   │       └── finmark_customers_with_clusters.csv
│   │
│   ├── notebooks/
│   │   └── Milestone_1_and_2.ipynb
│   │
│   └── Milestone_2_README.md
│
└── README.md
```

### Folder Descriptions

- **Milestone_1_Project_Data_Preparation_and_EDA/**
  Contains all files for Milestone 1, including raw datasets, processed/engineered outputs, EDA notebook, and milestone documentation.

- **Milestone_2_Clustering_and_Customer_Segmentation/**
  Contains the clustering notebook, the labeled customer output CSV, and milestone documentation. Builds directly on the engineered features produced in Milestone 1.

---

## Data Sources

### Raw Datasets
| File | Description |
|------|-------------|
| `Transaction_Data.csv` | Transaction-level customer activity (5,050 records, 5 columns) |
| `Product_Offering_Data.csv` | Product metadata, risk level, and target segments (15 products) |
| `Customer_Feedback_Data.csv` | Satisfaction scores and likelihood-to-recommend per customer (5,050 records) |

### Processed / Derived Datasets
| File | Description |
|------|-------------|
| `finmark_cleaned_transactions.csv` | Cleaned transaction records after preprocessing |
| `finmark_engineered_customer_features.csv` | Customer-level aggregated features used for EDA and clustering (993 customers, 17 features) |
| `finmark_customers_with_clusters.csv` | Final output with cluster labels and cluster_label column appended (993 customers) |

---

## Tools & Methods

**Tech Stack**
- Python 3
- Pandas, NumPy
- Matplotlib, Seaborn
- Scikit-learn
- Jupyter Notebook

**Key Techniques**

*Milestone 1 — Data Preparation & EDA*
- Data verification and consistency checks
- Missing value handling (business-rule based)
- Outlier detection via boxplots and IQR analysis
- Feature engineering: customer-level aggregation, transaction type proportions, recency, frequency, active months
- Exploratory Data Analysis: descriptive statistics, distribution plots, correlation heatmap, income-level segmentation

*Milestone 2 — Clustering*
- Feature selection (11 behavioral features) guided by EDA variance analysis
- Feature scaling via StandardScaler (required for distance-based algorithms)
- K selection using Elbow Method (inertia) and Silhouette Score (K=2 through K=9)
- K-Means clustering (final model: K=3, random_state=42, n_init=10)
- Cluster validation via PCA projection (2D scatter plot) and cluster profile heatmap
- Cluster interpretation and business labeling

---

## Milestone Progress

### Milestone 1 — Data Preparation and EDA ✅

- Data loading and shape verification across 4 datasets
- Preprocessing: dropped redundant text columns, winsorized satisfaction scores, normalized column names
- Feature engineering: total/avg/min/max transaction amounts, active months, recency days, transaction frequency per month, transaction type proportions (bill payment, investment, loan payment, purchase), average satisfaction and recommendation scores
- Derived `income_level` feature via quartile-based binning (Low / Medium / High) for EDA use
- EDA visualizations: histogram grid, boxplots, correlation heatmap, income-level breakdowns
- Key findings: right-skewed transaction amounts, high recency variance as churn signal, compositional transaction type proportions, stable but non-differentiating satisfaction scores

### Milestone 2 — Clustering and Customer Segmentation ✅

- Selected 11 features for clustering based on EDA variance analysis and behavioral relevance
- Applied StandardScaler preprocessing to equalize feature contributions
- Evaluated K=2 through K=9; selected K=3 based on elbow inflection and business interpretability
- Fitted final K-Means model; produced cluster distribution: 251 / 458 / 274 customers
- Validated clusters via PCA scatter plot and cluster profile heatmap
- Identified and labeled three customer segments:

| Cluster | Label | Size | Key Trait |
|---------|-------|------|-----------|
| 0 | Low-Value / At-Risk | 251 (25.3%) | Highest recency (68.6 days), lowest activity — churn risk |
| 1 | High-Value / Core Active | 458 (46.1%) | Highest spend (₱17,259 avg), most active months, lowest recency |
| 2 | Purchase-Oriented Moderate | 274 (27.6%) | Strongest purchase share (48%), highest likelihood-to-recommend |

- Exported labeled dataset to `finmark_customers_with_clusters.csv`

---

## Key Results

- **993 customers** analyzed across 3 raw datasets
- **11 behavioral features** selected for clustering
- **K = 3** selected as final cluster count (silhouette score: 0.116)
- **3 actionable segments** identified with distinct behavioral profiles and recommended business strategies:
  - Cluster 0 → Re-engagement campaigns, personalized investment offers
  - Cluster 1 → Retention programs, upselling of premium products, VIP service
  - Cluster 2 → Product promotions, purchase bundling, referral programs

---

## Notes for Reviewers / Mentors

- Raw and processed datasets are separated for transparency and reproducibility.
- Notebook file paths use relative directory structure (`../data/raw/`, `../data/processed/`).
- Column names containing spaces (e.g., `txn_type_prop_bill payment`) were normalized to underscores before clustering to ensure pipeline compatibility.
- `total_transaction_count` was excluded from the final clustering feature set despite high variance ranking — it is redundant with `active_months` and `total_transaction_amount`.
- K=2 produced a higher silhouette score (0.131) than K=3 (0.116), but K=3 was selected for greater business interpretability — specifically to distinguish the purchase-oriented segment (Cluster 2) which is not separable under a two-cluster solution.
- Outputs are organized by milestone for clarity and grading.
