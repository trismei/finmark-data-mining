# FinMark Customer Segmentation (Data Mining Project)

This repository contains the end-to-end data mining workflow for FinMark Corporation’s customer segmentation project using clustering techniques.

## Business Problem
FinMark currently offers standard financial products (e.g., savings, credit, loans) with limited personalization. This project builds a clustering-based customer segmentation model to support personalised product recommendations that improve customer satisfaction and service relevance.

## Project Outputs
- **Milestone 1:** Data Preparation & Exploratory Data Analysis (EDA)
- **Milestone 2:** Clustering & Customer Segmentation Report (K-Means, DBSCAN, Hierarchical)
- **Terminal Assessment:** Final Report + Presentation + Product Recommendations


<h2>Repository Structure</h2>
<pre>
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
└── README.md
</pre>




### Folder Descriptions

- **Milestone_1_Project_Data_Preparation_and_EDA/**  
  Contains all files for **Milestone 1**, including:
  - raw datasets (original provided files)
  - processed datasets (cleaned + engineered outputs)
  - Jupyter notebook for EDA
  - milestone documentation and notes

Future milestones will be added as separate folders following the same structure.

---

## Data Sources

### Raw Datasets
- `Transaction_Data.csv` – transaction-level customer activity  
- `Product_Offering_Data.csv` – product metadata and target groups  
- `Customer_Feedback_Data.csv` – satisfaction and feedback indicators  

### Processed / Derived Datasets
- `finmark_cleaned_transactions.csv` – cleaned transaction records  
- `finmark_engineered_customer_features.csv` – customer-level engineered features used for EDA and clustering  

---

## Tools & Methods

**Tech Stack**
- Python
- Pandas, NumPy
- Matplotlib, Seaborn
- Jupyter Notebook

**Key Techniques**
- Data verification and consistency checks  
- Missing value handling (business-rule based)  
- Feature engineering (customer-level aggregation, proportions, recency, frequency)  
- Exploratory Data Analysis (descriptive statistics, distributions, correlations)  

---

## Milestone Progress

### Milestone 1 – Project Data Preparation and Exploratory Data Analysis (EDA)
- Data preparation and verification  
- Data cleaning and preprocessing  
- Feature engineering  
- EDA visualizations and statistical summaries  
- Key patterns and feature importance for clustering  

---

## Notes for Reviewers / Mentors
- Raw and processed datasets are separated for transparency and reproducibility.
- Notebook file paths use relative directory structure.
- Outputs are organized by milestone for clarity and grading.

---
