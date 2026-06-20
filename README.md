# Euro Area Banks — Financial Analysis (2006–2024)

Empirical analysis of the financial structure and resilience of Euro Area Significant Institutions, covering balance sheet composition, capital adequacy, asset quality (NPLs), profitability (ROAE), cost efficiency, and market concentration.

The analysis replicates and extends to 2024 a set of key charts published by the ECB in its *Financial Integration Report* and *Financial Stability Review*, using bank-level data from BankFocus (Bureau van Dijk).

## Data

The dataset includes approximately 100 Euro Area Significant Institutions with annual financial statements from 2006 to 2024, sourced from **BankFocus** (Bureau van Dijk). Variables cover total assets, loans, deposits, equity, risk-weighted assets, capital ratios, NPLs, profitability metrics, and cost-to-income ratios.

> The raw dataset is not included in this repository due to licensing restrictions. To replicate the analysis, export a comparable sample from BankFocus using the variable names referenced in the notebook.

## Analysis

| Section | Description |
|---|---|
| **Balance Sheet Composition** | Asset and liability structure (% of total assets) across 2016, 2018, and 2024 |
| **Capital Ratios & RWA** | Total risk exposure (bars) and median CET1 / Tier 1 / Total Capital ratios (lines), 2017–2024 |
| **Non-Performing Loans** | Performing and non-performing loans (stacked bars) with NPL ratio (line), 2015–2024. Missing values recovered via a 2-of-3 algebraic imputation rule |
| **Profitability (ROAE)** | Quartile-based trends and distribution summary (median, asset-weighted average, IQR) |
| **Cost-to-Income Ratio** | Time-series evolution (2006–2024) and cross-sectional comparison by bank size (2018 vs 2024) |
| **Market Concentration** | Share of total sample assets held by the top 5 banks over time |

## Methodological notes

- **Capital ratios** use two distinct samples: RWA bars are computed on a quasi-balanced panel (≤1 missing year, interpolated), while ratio medians use a strict annual filter requiring all four metrics (RWA, CET1, Tier 1, TCR) to be non-null.
- **NPL imputation**: given the triple (NPL, Gross Loans, NPL Ratio), if exactly one value is missing the other two recover it algebraically. Observations with fewer than two available values are dropped.
- **Cost-to-income**: banks with fewer than 5 valid years are excluded; CTI values above 150% are winsorized. Bank size categories follow ECB conventions (SI: TA > €30bn; remaining banks split into quartiles).

## Requirements

```
pandas
numpy
matplotlib
openpyxl
```

## Authors

- **Marco Giovannini** — (https://github.com/MarcoGiova99)
- **Vittoria Calonghi** — (https://github.com/Vittoria-C)
- **Matteo Montali** — (https://github.com/matteomontali)

Project developed for the course *Applied Data Science for Banking and Finance*, Università Cattolica del Sacro Cuore (A.Y. 2025–2026).
