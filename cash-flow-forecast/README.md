# 13-Week Rolling Cash Flow Forecast

> **Treasury Portfolio Project** | Built by [Kofoworola Adetona](https://www.linkedin.com/in/kofoworola-adetona) | April 2026


## Business Problem

Every company, from a Lagos fintech to a multinational energy firm needs to know one thing at all times: **will we have enough cash next week?**

When businesses fail to forecast their cash position, they get caught short. They miss supplier payments, breach loan covenants, or draw expensive emergency credit. A treasury analyst's most important daily task is building and maintaining a rolling cash flow forecast that shows exactly when money comes in, when it goes out, and what the closing balance will be each week.

This model solves that problem for a simulated Nigerian fintech company operating across 13 weeks.

---

## What This Model Does

This is a **fully Excel workbook** with 6 sheets. the raw transaction data. Nothing is hardcoded. Change one transaction in the raw data and every KPI, balance and chart updates automatically.

| Sheet | What It Does |
|---|---|
| `Raw_Transaction_Data` | 1,000 real AR/AP transactions — the single source of truth |
| `1_Weekly_Pivot` | Aggregates transactions by week using SUMIFS — replicates a Pivot Table |
| `2_Aging_Schedule` | Groups AR and AP by how overdue they are (0–30, 31–60, 61–90, 91–120, 120+ days) |
| `3_CashFlow_Forecast` | 13-week forecast: Opening + Inflows − Outflows = Closing Balance |
| `4_Scenario_Analysis` | Models the impact of Dangote Industries paying one week late |
| `5_Dashboard` | Links KPIs from all sheets into one real-time executive summary |


## Key Excel Skills Demonstrated

### SUMIFS — the backbone of the model
```excel
= SUMIFS(Raw!H:H, Raw!E:E, "Inflow", Raw!D:D, 3)
```
*Translation: "Sum the Amount column, but only where Type = Inflow AND Week = 3"*

Used in: Weekly Pivot (by week), Cash Flow Forecast (by category per week)

---

### SUMPRODUCT — aging schedule buckets
```excel
= SUMPRODUCT(
    (Raw!F4:F1003 = "Dangote Industries") *
    (Raw!E4:E1003 = "Inflow") *
    (TODAY() - Raw!C4:C1003 >= 31) *
    (TODAY() - Raw!C4:C1003 <= 60) *
    Raw!H4:H1003
  )
```
*Translation: "Sum amounts where counterparty = Dangote, type = Inflow, and invoice is 31–60 days overdue"*

Used in: Aging Schedule (AR and AP buckets by counterparty)

---

### Rolling balance logic — closing becomes next opening
```excel
Week 1 Opening  = $B$5  (assumption input)
Week 1 Closing  = Opening + Net Cash Flow
Week 2 Opening  = Week 1 Closing   ← this is the rolling mechanism
Week 2 Closing  = Week 2 Opening + Week 2 Net
...and so on for 13 weeks
```

---

### Scenario analysis — late payment impact
```excel
= IF(week = $B$8,
    Base_Closing - $B$9,          ← reduce Week 3 by delayed amount
    IF(week = $B$8 + 1,
       Base_Closing + $B$9,       ← recover in Week 4
       Base_Closing))             ← no change in all other weeks
```
*Change the customer name, week, or amount in the assumptions box and the entire scenario updates.*

---

### Conditional formatting — automatic risk signals
- 🟢 Green closing balance = above minimum buffer
- 🔴 Red closing balance = below ₦5M minimum — action required
- Aging buckets colour-coded by risk level (Current → Critical)

---

## 📊 Key Insights From the Model

| Metric | Value |
|---|---|
| Opening cash balance | ₦5,000,000 |
| Total 13-week inflows | Pulled from 1,000 raw transactions |
| Total 13-week outflows | Pulled from 1,000 raw transactions |
| Minimum closing balance (base case) | Calculated automatically |
| Weeks below ₦5M buffer | Flagged automatically with ⚠️ |
| Late payment scenario — Week 3 impact | −₦3,000,000 on closing balance |
| Scenario recovery | Week 4 (payment received one week late) |

---

## 🏦 Treasury Concepts Covered

| Concept | Where Applied |
|---|---|
| **Cash flow forecasting** | 3_CashFlow_Forecast — 13-week rolling model |
| **Working capital management** | Opening/closing balance rollforward |
| **Accounts receivable aging** | 2_Aging_Schedule — AR buckets by counterparty |
| **Accounts payable aging** | 2_Aging_Schedule — AP buckets by supplier |
| **Liquidity buffer** | Minimum cash threshold with automatic breach alerts |
| **Scenario analysis** | 4_Scenario_Analysis — late payment modelling |
| **Payment risk** | Risk ratings and treasury action recommendations per counterparty |

---

## 📁 File

| File | Description |
|---|---|
| `Cash_Flow_Forecast_Kofoworola_Adetona_FINAL.xlsx` | Full Excel workbook — 6 sheets, 1,000 transactions, 903 live formulas |

---

## 🔗 About This Portfolio

This project is part of my treasury and payments analyst portfolio, built while completing the **GearUp Africa Analyst Programme** (Corporate Treasury & Transaction Banking track) and the **Financial Edge Commercial Banking Pathway**.

Other projects in this portfolio:

| # | Project | Skills |
|---|---|---|
| 1 | Accounts Receivable Reconciliation Tracker | VLOOKUP, IFERROR, conditional formatting |
| 2 | **13-Week Cash Flow Forecast** ← you are here | SUMIFS, SUMPRODUCT, scenario analysis, aging schedule |
| 3 | Payments Analysis Dashboard *(coming soon)* | SQL, Python, data visualisation |

---

## 👤 Author

**Kofoworola Adetona**
Final-year Finance student · University of Lagos (First Class, GPA 4.58/5.0)
Cohort President · GearUp Africa Analyst Programme 2027

📧 adetonakofoworola@gmail.com
💼 [LinkedIn](https://www.linkedin.com/in/kofoworola-adetona)
🐙 [GitHub Portfolio](https://github.com/Kofoonly/treasury-portfolio)
