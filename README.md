# NYC 311 Service Requests — Data Cleaning Pipeline

**Riley Allen** · [rileyallen2412@gmail.com](mailto:rileyallen2412@gmail.com) · [LinkedIn](https://linkedin.com/in/rileyallen2412)  
Project 3 of 4 · Data Analytics Portfolio

---

## Overview

A production-style data cleaning pipeline applied to NYC's 311 Service Request dataset — one of the largest open civic datasets in the world, with millions of rows spanning noise complaints, heat outages, pothole reports, and more.

This project demonstrates the full wrangling lifecycle: from raw, messy government data to a clean, analysis-ready dataset with engineered features and a documented audit trail of every cleaning decision.

## Skills demonstrated

`Python` · `Pandas` · `NumPy` · `Matplotlib` · `Seaborn` · `data wrangling` · `documentation` · `Git`

## Pipeline stages

| Stage | Description |
|-------|-------------|
| 1 | Load & inspect — shape, types, null rates, baseline snapshot |
| 2 | Missing value analysis — heatmap, imputation decisions |
| 3 | Data type corrections — date parsing, numeric casting, validation |
| 4 | Text normalization — borough names, status, complaint types |
| 5 | Duplicate detection — exact, key-level, and business-logic dedupes |
| 6 | Feature engineering — response time, temporal features |
| 7 | Cleaning summary report — before/after comparison |

## Dataset

**Source:** [NYC Open Data — 311 Service Requests (2010–Present)](https://data.cityofnewyork.us/Social-Services/311-Service-Requests-from-2010-to-Present/erm2-nwe9/about_data)  
**API endpoint:** NYC Open Data Socrata API (`erm2-nwe9`)  
**Sample:** 200,000 rows · Jan 2022–present · ordered by most recent

**To download the exact dataset used in this project**, paste this URL into your browser:

```
https://data.cityofnewyork.us/resource/erm2-nwe9.csv?$limit=200000&$where=created_date>='2022-01-01'&$order=created_date DESC
```

Save the downloaded file as `data/311_service_requests.csv`.

> The raw and cleaned CSVs are excluded from this repository via `.gitignore` due to file size. The API URL above is fully reproducible — running it will return the same dataset structure used here.

## Repository structure

```
nyc-311-cleaning/
├── data/                        # Local only — gitignored
│   ├── 311_service_requests.csv # Raw download from NYC Open Data
│   ├── 311_cleaned.csv          # Output of the pipeline
│   ├── fig_null_heatmap.png
│   ├── fig_null_rates.png
│   ├── fig_complaints_by_hour.png
│   └── fig_response_by_borough.png
├── notebooks/
│   └── nyc_311_cleaning_pipeline.ipynb
├── .gitignore
└── README.md
```

## Results summary

| Metric | Before | After |
|--------|--------|-------|
| Rows | — | — |
| Columns | — | — |
| Total null cells | — | — |
| Duplicate rows | — | — |
| Engineered features | 0 | 6 |

> Fill in the before/after numbers after running the notebook.

## Key cleaning decisions

| Decision | Rationale |
|----------|-----------|
| Dropped columns with ≥80% null values | Too sparse to impute reliably |
| Dropped rows with null `Unique Key` or `Created Date` | Non-negotiable identifiers |
| Filled optional location fields with `'UNKNOWN'` | Null = not provided, not an error |
| Used `errors='coerce'` for date parsing | Handles inconsistent formats safely |
| Nullified coordinates outside NYC bounding box | Likely data entry errors |
| Capped `response_hours` at 8,760 (1 year) | Implausibly long values are errors |

## How to run

```bash
# Clone the repo
git clone https://github.com/ryry2412/nyc-311-cleaning.git
cd nyc-311-cleaning

# Install dependencies
pip install pandas numpy matplotlib seaborn jupyter

# Download data (see Dataset section above), then:
jupyter notebook notebooks/nyc_311_cleaning_pipeline.ipynb
```

## Portfolio

- ✅ **Project 1:** [SQL Data Exploration](https://github.com/ryry2412/retail-ecommerce-sql)
- ✅ **Project 2:** [Python EDA + A/B Test](https://github.com/ryry2412/bank-marketing-eda-ab-test)
- ✅ **Project 3:** Data Cleaning Pipeline ← this project
- 🔲 **Project 4:** Dashboard Storytelling (Tableau Public)
