---
name: csv-portfolio-cleaner
description: Processes CSV exports of stock/crypto positions (including complex Interactive Brokers multi-section Activity Statements AND modern Flex Queries) when user says #LimpiaCSV. Anonymizes by removing all personal identifiers (name, account number, etc.). Extracts positions, trade dates, commissions, ISINs, names and key financial metrics. Standardizes tickers/columns, calculates metrics, and outputs a clean, model-friendly CSV with rich portfolio summary optimized for Grok Build CLI / EcoPort.
---

# CSV Portfolio Cleaner

## Purpose
Transform raw broker CSV exports into a clean, anonymized, and highly structured CSV that Grok Build CLI and EcoPort can understand immediately.

Supports **two** Interactive Brokers formats:

1. **Classic Activity Statement** (Spanish multi-section: "Posiciones abiertas", "Operaciones", "Cambio en NAV"...)
2. **Modern Flex Query** (English headers: ClientAccountID, Symbol, MarkPrice, TradeDate, CostBasisPrice...)

Remove every trace of personal data while preserving and enriching with economically relevant information: current positions + purchase history dates + commissions paid + global P&L, deposits, dividends, cash position, closed positions with realized P/L, ISINs and net performance.

## When to Use
- User provides a .csv file containing portfolio positions or a full broker activity statement / Flex Query.
- The file may contain personal fields (names, account numbers, emails, addresses, full descriptions, broker details).
- Especially powerful with Interactive Brokers exports (both classic Activity Statement and Flex Query).
- Goal: prepare data for further processing by Grok Build CLI (analysis, strategy suggestions, risk assessment, performance review, EcoPort import, etc.).

## Instructions

### Step 1: Receive and Parse the CSV
- Accept the file path or raw CSV content.
- **Auto-detect format**:
  - Flex Query → looks for `ClientAccountID` + headers like `MarkPrice`, `TradeDate`, `CostBasisPrice`.
  - Classic Activity Statement → looks for sections like "Posiciones abiertas", "Operaciones", "Header"/"Data" pattern.
- Use the corresponding specialized parser (see `scripts/process_portfolio_csv.py`).

### Step 2: Identify and Remove Personal Information
Strictly delete or ignore columns containing personal data (name, account number, email, address, etc.).

### Step 3: Extract & Enrich
- Positions with units, prices, cost basis, unrealized P/L
- First/Last buy dates + total commissions paid
- Cash, deposits, dividends, realized P/L
- ISINs and instrument names
- Calculated metrics (P/L %, weight, etc.)

### Step 4: Output
Produce a clean CSV + a short human-readable summary optimized for EcoPort / Grok analysis.

## Script
The heavy lifting is done by `scripts/process_portfolio_csv.py`.

```bash
python scripts/process_portfolio_csv.py input.csv output.csv
```

## Notes
- Always anonymize.
- Prefer the Flex Query format when possible (cleaner structure).
- The output is designed to feed directly into EcoPort or further Grok analysis.
