# Payment Reconciliation Automation (Python)

## Problem
Manually matching internal payment records against bank statements is slow and error‑prone. Treasury teams need to quickly identify:
- Payments missing from the bank statement
- Extra bank entries with no internal record
- Amount mismatches (partial payments, data entry errors)
- Timing differences (bank delays)

## Solution
This Python script automates the reconciliation process. It loads both datasets, matches them using multiple strategies, and produces a clear report.

## Features
- **Exact matching** on transaction ID
- **Fuzzy matching** on amount + recipient name + date tolerance (±1 day) – handles bank processing delays
- **Status flags** for each transaction: Matched, Amount mismatch, Internal only (missing from bank), Bank only (no internal record)
- **Summary report** with counts and actionable recommendations
- **CSV export** for audit or further analysis

## Files in this folder
| File | Description |
|------|-------------|
| `reconcile_improved.ipynb` | The full Python script (run in Google Colab / Jupyter) |
| `sample_report.csv` | Example output using the included sample data |
| `README.md` | This file |

## How to run
1. Open the notebook in [Google Colab](https://colab.research.google.com/).
2. Run all cells (Runtime → Run all).
3. View the printed reconciliation report and summary.
4. Download the generated `reconciliation_report.csv` from the Colab environment.

## Sample output (from the script)
| transaction_id | amount_internal | amount_bank | status                                |
|----------------|----------------|-------------|---------------------------------------|
| TXN001         | 5000.00        | 5000.00     | Matched (exact)                       |
| TXN002         | 12000.00       | 11800.00    | Amount mismatch                       |
| TXN003         | 7500.00        | NaN         | Internal only (missing from bank)     |
| TXN006         | NaN            | 4500.00     | Bank only (no internal record)        |

## Skills demonstrated
- Python (pandas, datetime)
- Data merging (left/outer joins)
- Conditional logic and fuzzy matching
- Report generation for stakeholders
- Version control (GitHub)

## Next improvements planned
- Add support for uploading CSV files directly (instead of hardcoded data)
- Send email alerts for critical discrepancies
- Build a simple dashboard using Streamlit
