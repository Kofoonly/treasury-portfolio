# 13-Week Rolling Cash Flow Forecast (Excel)

## Problem

Treasury teams need to know whether the business will have enough cash to meet its obligations. Without a structured forecast, companies risk:

- Missing supplier payments or salary runs
- Breaching minimum cash covenants with lenders
- Failing to spot the impact of a late customer payment before it causes a cash crunch
- Making investment or borrowing decisions based on guesswork rather than data

Manual cash tracking in basic spreadsheets is disconnected inflows and outflows are entered separately, nothing links back to the actual transaction data, and scenario testing requires rebuilding the whole model from scratch.

## Solution

This Excel model automates the 13-week cash flow forecast for a simulated Nigerian fintech company. It pulls directly from 1,000 raw AR/AP transactions using SUMIFS formulas, builds an aging schedule and models a late payment scenario.


## Files in This Folder

| File | Description |
|---|---|
| `Cash_Flow_Forecast_Project.xlsx` | 
| `README.md` | This file |

## How to Use

1. Download `Cash_Flow_Forecast_Project.xlsx`
2. Open in Microsoft Excel (2016 or later recommended)
3. Start on the **Dashboard** sheet for the full summary view
4. Navigate to **Transaction_Data** to see the 1,000 source transactions
5. To test the scenario: go to **CashFlow_Forecast**


## Skills Demonstrated

- **Excel**: SUMIFS, SUMPRODUCT, IFERROR, conditional formatting, data validation
- **Treasury**: Cash flow forecasting, working capital management, liquidity planning
- **Aging analysis**: AR/AP aging buckets, counterparty risk rating, payment priority flags
- **Scenario modelling**: Late payment impact analysis, buffer breach identification
- **Financial reporting**: Executive dashboard, KPI linking across sheets
- **Version control**: GitHub
