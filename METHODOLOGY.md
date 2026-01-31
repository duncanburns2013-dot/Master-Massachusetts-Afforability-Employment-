# 📐 Methodology & Calculations

This document explains how each metric in the dashboard was calculated.

---

## Electricity Premium Calculation

**Formula:**
```
Premium % = ((MA Rate - US Rate) / US Rate) × 100
```

**Example (October 2025):**
```
MA Residential Rate:  31.37¢/kWh
US Average Rate:      17.98¢/kWh
Premium:              ((31.37 - 17.98) / 17.98) × 100 = 74.4%
```

**Rounded:** +74% above national average

---

## Annual Extra Cost Calculation

**Formula:**
```
Extra Cost = (MA Rate - US Rate) × Monthly kWh × 12 months
```

**Example (600 kWh/month typical household):**
```
Rate Difference:  31.37¢ - 17.98¢ = 13.39¢/kWh
Monthly Extra:    13.39¢ × 600 kWh = 8,034¢ = $80.34
Annual Extra:     $80.34 × 12 = $964/year
```

**Note:** Dashboard uses $1,188 based on winter rates which are higher. The $964 figure uses October 2025 rates.

---

## Policy Charge Calculation (17%)

**Formula:**
```
Policy Charge = Total Bill × 0.17
```

**Examples:**
| Bill Total | Policy Charge (17%) |
|------------|---------------------|
| $427 | $72.59 ≈ $73 |
| $709 | $120.53 ≈ $121 |
| $853 | $145.01 ≈ $145 |

**Source:** Eversource official bill breakdown published December 2025

---

## Housing Affordability Gap

**Monthly Payment Calculation:**
```
Loan Amount = Home Price × (1 - Down Payment %)
Monthly P&I = PMT(rate/12, years×12, loan_amount)
```

**Example:**
```
Home Price:           $638,000
Down Payment (20%):   $127,600
Loan Amount:          $510,400
Interest Rate:        6.1% (Freddie Mac PMMS Jan 2026)
Term:                 30 years

Monthly P&I = PMT(0.061/12, 360, 510400) = $3,096
+ Taxes & Insurance:  ~$900/month (estimated)
Total Monthly:        $3,996
```

**Income Required (28% DTI rule):**
```
Required Monthly Income = $3,996 / 0.28 = $14,271
Required Annual Income = $14,271 × 12 = $171,257
```

**Gap Calculation:**
```
Required:      $171,257
Median Income: $104,800 (Census ACS 2024)
Gap:           $171,257 - $104,800 = $66,457
Gap %:         $66,457 / $171,257 = 38.8% ≈ 39%
```

---

## "Comfortable" Income Gap

**SmartAsset Methodology:**
"Comfortable" = 50/30/20 budget rule:
- 50% on needs (housing, utilities, food, healthcare)
- 30% on wants (entertainment, dining out)
- 20% on savings/debt

**For Massachusetts:**
```
SmartAsset "Comfortable" threshold: $313,747/year (family of 4)
Median Family Income:               $140,309
Gap:                                $313,747 - $140,309 = $173,438
Gap %:                              $173,438 / $313,747 = 55.3%
```

---

## Real Wage Calculation

**Formula:**
```
Real Wage Change = Nominal Wage Growth - CPI Change
```

**Calculation (2021-2025):**
```
Nominal Wage Growth:  +21.8% (BLS CES average hourly earnings)
CPI Increase:         +22.7% (BLS CPI-U Northeast)
Real Wage Change:     21.8% - 22.7% = -0.9% ≈ -0.7%
```

**Interpretation:** Workers have less purchasing power than 4 years ago despite nominal raises.

---

## Unemployment Ranking

**Method:**
1. Download BLS LAUS data for all 50 states + DC
2. Sort by unemployment rate (descending)
3. Assign rank 1 to highest, 51 to lowest

**December 2025:**
- MA unemployment: 4.8%
- MA rank: #44 (8th highest = only 7 states worse)

---

## Statewide Policy Cost Estimate

**Formula:**
```
Statewide Cost = Policy Charge (¢/kWh) × Total Retail Sales (kWh)
```

**Calculation:**
```
Estimated policy charges: ~9.8¢/kWh (from rate analysis)
MA retail electricity sales: ~45 billion kWh/year (EIA)
Statewide cost: 9.8¢ × 45B kWh = $4.41 billion/year
```

---

## Data Quality Notes

1. **Seasonal Variation:** Electricity rates and bills vary by season. Winter rates are typically higher due to heating demand.

2. **Regional Differences:** Within Massachusetts, rates vary by utility territory (Eversource, National Grid, Unitil).

3. **Typical Usage:** 600 kWh/month is used as "typical" household consumption. Actual usage ranges from 400-1,200 kWh.

4. **Policy Charge Complexity:** The 17% "Public Benefits" is the labeled amount. Additional policy-driven costs are embedded in distribution charges, bringing total to ~29% per DPU analysis.

5. **Income Data Lag:** Census ACS data has a 1-year lag. 2024 data reflects 2023 calendar year.

---

## Replication Instructions

To verify any calculation:

1. **Electricity rates:** Download EIA Electric Power Monthly Table 5.6.A
2. **Employment:** Download BLS LAUS state data
3. **Housing:** Contact Warren Group for MA housing data
4. **Income:** Query Census ACS Table S1901 for Massachusetts
5. **Wages:** Download BLS OES state data for Massachusetts

All calculations can be reproduced using Excel, Python, or R with the provided CSV files.

---

*Last Updated: January 31, 2026*
