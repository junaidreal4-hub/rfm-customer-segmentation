# RFM Customer Segmentation (Online Retail)

## Motivation
Segment customers using Recency, Frequency, and Monetary value (RFM) to identify high-value customers and propose targeted marketing actions.

## Data
Source: UCI Machine Learning Repository — Online Retail dataset (01/12/2010 to 09/12/2011).  
Link: https://archive.ics.uci.edu/dataset/352/online+retail

## Method
- Clean transactions (remove missing CustomerID, cancellations, invalid Quantity/UnitPrice).
- Build RFM table per customer:
  - **Recency** = days since last purchase
  - **Frequency** = number of unique invoices
  - **Monetary** = total spend
- Score R/F/M into 1–5 bins (quintiles) and assign segment labels: Champions, Loyal Customers, Potential Loyalists, At Risk, Hibernating, Others.

## Results
### Segment counts
![Customer count by segment](Reports/Figures/segment_counts.png)

### Revenue by segment
![Total revenue by segment](Reports/Figures/segment_revenue.png)

### Average scores by segment
![Average RFM scores heatmap](Reports/Figures/segment_avg_scores_heatmap.png)

**Key findings:**
- Champions (962 customers) contribute ~5.81M revenue with avg recency ~12.9 days
- Hibernating (824 customers) show avg recency ~228.5 days and contribute only ~189.8k

Output files:
- `Data/Processed/rfm_table.csv`
- `Data/Processed/rfm_scored_segments.csv`
- `Data/Processed/segment_summary.csv`

## Business actions
- **Champions**: loyalty perks, referrals, early access.
- **Loyal Customers**: upsell bundles and cross-sell recommendations.
- **At Risk**: win-back campaign (personalized offer).
- **Hibernating**: reactivation flow (reminder + incentive).

## How to run
1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
2. Download the dataset from UCI and place it here:
   ```
   Data/raw/Online Retail.xlsx
   ```
3. Run notebooks in order:
   - `Notebooks/01_load_and_clean.ipynb`
   - `Notebooks/02_rfm_table.ipynb`

## Repository structure
```
rfm-customer-segmentation/
├── Data/
│   ├── raw/                  # Raw dataset (not committed)
│   └── Processed/            # Cleaned + RFM outputs
├── Notebooks/                # Analysis notebooks
├── Reports/Figures/          # Exported plots
├── .gitignore
└── README.md
```
