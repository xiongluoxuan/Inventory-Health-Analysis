# Inventory Health Analysis

## Project Overview

This project analyzes SKU-level inventory health using sales, inventory, forecast, supplier lead time, cost, and price data. The goal is to identify healthy SKUs, watch-list SKUs, and potential inventory risks to support procurement and supply chain decisions.

The analysis was completed with Excel, Power Query, and Python. The project focuses on a clear and reproducible workflow rather than only creating charts.

## Business Questions

- Which SKUs are currently healthy?
- Which SKUs require closer monitoring?
- Are there SKUs with high business value that should receive priority attention?
- How can sales, inventory gap, forecast gap, supplier lead time, and margin be combined into a simple SKU health framework?

## Tools Used

- Excel
- Power Query
- Pivot Table
- Python
- Pandas
- Jupyter Notebook

## Dataset

The dataset contains daily SKU-level supply chain records, including:

- Date
- SKU ID
- Warehouse ID
- Supplier ID
- Region
- Units Sold
- Inventory Level
- Supplier Lead Time
- Reorder Point
- Order Quantity
- Unit Cost
- Unit Price
- Promotion Flag
- Stockout Flag
- Demand Forecast

## Analysis Workflow

1. Imported the raw supply chain dataset.
2. Checked data structure, column types, missing values, duplicate records, and date range.
3. Created business metrics:
   - Revenue
   - Inventory Gap
   - Forecast Gap
   - Gross Margin per Unit
4. Built SKU-level summary metrics using Excel Pivot Table and Python Pandas.
5. Classified SKUs into health status groups:
   - Healthy
   - Watch
   - Risk
6. Created an attention list for SKUs that require monitoring.
7. Built a simple dashboard to summarize SKU health distribution.

## Key Metrics

| Metric | Definition |
|---|---|
| Revenue | Units Sold x Unit Price |
| Inventory Gap | Inventory Level - Reorder Point |
| Forecast Gap | Inventory Level - Demand Forecast |
| Gross Margin per Unit | Unit Price - Unit Cost |
| Promotion Records | Count of records where Promotion Flag = 1 |
| Stockout Records | Count of records where Stockout Flag = 1 |

## SKU Health Logic

The project uses a simple rule-based classification framework:

```text
If Avg Forecast Gap < 0: Risk
Else if Avg Inventory Gap < 50: Watch
Else if Avg Supplier Lead Time > 10: Watch
Else: Healthy
```

This rule is designed for learning and portfolio demonstration. In a real business setting, thresholds should be adjusted based on service level targets, product category, supplier reliability, and demand volatility.

## Key Findings

- Total SKUs analyzed: 50
- Healthy SKUs: 40
- Watch SKUs: 10
- Risk SKUs: 0
- 80% of SKUs are currently healthy.
- 20% of SKUs require monitoring.
- SKU_38 has the highest revenue among Watch SKUs and should be prioritized for further review.

## Business Recommendation

For Watch SKUs, the next step is to review supplier lead time stability, reorder point settings, and safety stock assumptions. High-revenue Watch SKUs should be prioritized because they have greater business impact if supply issues occur.

## Project Structure

```text
Inventory-Health-Analysis/
├── 01_Raw_Data/
│   └── supply_chain_dataset1.csv
├── 02_Excel/
│   └── SKU Health Analysis.xlsx
├── 03_Python/
│   ├── requirements.txt
│   └── 基础 SKU Health Analysis.ipynb
└── README.md
```

## Notes

This is a beginner-friendly supply chain analytics portfolio project. The purpose is to demonstrate a complete analysis workflow, including data cleaning, metric creation, SKU classification, dashboard building, and business interpretation.
