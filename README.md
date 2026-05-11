# StewardLand Pro Forma — Client User Guide

## Overview

This is an interactive financial model for real estate development projects. It calculates:
- Monthly cash flow projections
- Debt draw schedules and repayment
- Equity investment requirements and returns
- IRR and equity multiples for investors
- Waterfall distribution based on performance hurdles

**Key principle:** All inputs are editable, and the model recalculates in real-time as you change assumptions.

---

## Getting Started (First Time)

### 1. Load the app
Navigate to the StewardLand Pro Forma dashboard. You'll see generic default values.

### 2. Reset or customize
- **Option A (Recommended):** Click "Reset to Defaults" in the sidebar to start fresh
- **Option B:** Keep the defaults and edit one section at a time

### 3. Start with Timeline & Scenario
Go to **Timeline & Scenario** tab:
- **Total Duration:** How long is the project? (e.g., 60 months for a 5-year build)
- **Closing Lag:** Months between signing a contract and receiving payment (typically 12 for residential)
- **Construction Start Lag:** Months after contract before construction begins (typically 1)
- **Scenario:** Toggle between "Land Only" (no construction) and "Full Build" (includes vertical costs)

⚠️ **Important Rule:** Closing Lag must be ≥ Construction Start Lag + Build Duration.  
Example: If build takes 11 months, start lag is 1, then closing lag must be ≥ 12 months.

### 4. Define Unit Types
Go to **Unit Types** tab. For each unit type, define:
- **Name:** e.g., "Townhouse Entry", "Single Family Estate"
- **Lot Price:** Land value per unit (CAD)
- **Home Price:** Selling price per unit (Full Build only)
- **Vertical Cost/Unit:** Your construction cost per unit (Full Build only)

The model will show:
- Total lot revenue (Land Only)
- Total home revenue (Full Build)
- Gross margin per unit = Home Price − Vertical Cost − Lot Price

### 5. Set Phasing & Absorption
Go to **Phasing & Absorption** tab:
- **Sales per Month:** How many units do you expect to sell each month? (e.g., 2.5)
- **Pre-Sales:** How many units are contracted before month 0? (e.g., 3)
- **Phases:** Define when each group of units becomes available
  - Phase 1 might be "Townhouses" (months 0–28)
  - Phase 2 might be "Single Family" (months 6–42, overlapping with Phase 1)

**Phases can overlap.** During the overlap window, buyers can choose from units in both phases.

### 6. Enter Costs
Go to **Costs** tab:

- **Land Acquisition:** Total cost of the land, paid in month 0 (or specify a different month)
- **Horizontal / Civil:** Roads, utilities, servicing. Enter total, start month, end month, and profile:
  - `Linear` = evenly distributed
  - `Front Loaded` = heavy in early months
  - `Back Loaded` = heavy in later months
- **Soft Costs:** Architecture, permits, marketing, contingency. Linear distribution only.
- **Vertical Construction:** (Full Build only)
  - Build Duration: How many months to construct one unit (e.g., 11)
  - Cost Curve: S-Curve distribution (`standard`, `front-heavy`, `back-heavy`)

### 7. Configure Financing
Go to **Financing & Waterfall** tab:

**Senior Debt:**
- **LTC (Loan-to-Cost):** What % of eligible costs does the lender finance? (typical: 65%)
- **Annual Interest Rate:** Lender's rate (e.g., 7.5% current market)
- **Origination Fee:** Upfront fee on first draw (typical: 1%)

**LP Equity Waterfall:**
- **Preferred Return:** Guaranteed annual % return to LP (e.g., 8%)
- **GP Promote:** GP's share of profits above preferred return (e.g., 20%)

**Waterfall Tiers (Advanced):**
The model distributes profits in this order:
1. Return LP's capital
2. Pay LP preferred return (accrued interest)
3. Split remaining profits based on LP's IRR:
   - **Tier 1 (up to 15% IRR):** LP 80% / GP 20%
   - **Tier 2 (15%–20% IRR):** LP 80% / GP 20%
   - **Tier 3+ (above 20% IRR):** LP 70% / GP 30%

If your project performs better, GP gets a larger cut of the upside.

---

## Reading the Results

### Dashboard
Shows key metrics at a glance:
- **Project IRR:** Unlevered return (before debt)
- **LP IRR:** Levered return to the limited partner
- **LP Equity Multiple:** How much the LP's money multiplies (e.g., 2.0× means 2x return)
- **Net Profit:** Total cash generated after all costs and debt repayment
- **Peak Debt:** Highest debt balance during the project
- **LTC at Peak:** Actual loan-to-cost ratio at peak debt (should be ≤ your target)

**Tip:** Use the charts to spot trends:
- **Cash Position:** Negative early (construction phase) → positive when sales begin → crossover when debt is paid
- **Revenue vs Costs:** Watch when revenue finally exceeds costs (breakeven month)

### Monthly Cash Flow
Detailed month-by-month breakdown:
- Costs: land, horizontal, soft, vertical
- Revenue: deposits (in trust) and actual closings
- Debt: draws and repayment
- Equity: required capital from LP
- Interest: compounding cost of debt

**Tip:** Look for "Revenue Closings" — that's when money actually arrives. Months with zero revenue but high costs = maximum equity draw.

### Sources & Uses
Summary of capital sources (debt + equity) and where it went (land, construction, interest).

**Cost-to-Complete Chart:**
- Red line: How much cost is still owed
- Green line: How much revenue has been collected
- Blue dashed line: How much debt capacity is still available

Watch for the crossover point — that's when you've sold enough to cover all remaining costs.

### Distribution Waterfall
Final numbers:
- **LP Return of Capital:** Gets their invested amount back
- **LP Preferred Return:** Gets the guaranteed interest
- **LP Above-Pref:** Gets a share of excess profit
- **GP Promote:** Gets their carry on the upside

---

## Validation Checklist

Before presenting to lenders or investors, verify:

- [ ] **Revenue math:** Total units × average selling price ≈ Total Revenue shown
- [ ] **Cost math:** Land + Horizontal + Soft + Vertical ≈ Total Costs shown
- [ ] **Closing timing:** First revenue appears at month (pre-sales + closing lag)
- [ ] **Debt repayment:** Final debt should be ≈ $0 if all units sell
- [ ] **Margin:** Net Profit ÷ Total Revenue = healthy margin (10–20% typical)
- [ ] **LP returns:** IRR > preferred return if project succeeds (otherwise deal is broken)
- [ ] **Tiers:** If LP IRR < 15%, GP promote should be at Tier 1 (20%)

---

## Common Customizations

### Scenario: Market Downturn (50% absorption)
- Go to **Phasing & Absorption** → reduce `salesPerMonth` to 1.25
- Go to **Dashboard** → watch LP IRR drop
- Adjust prices in **Unit Types** to see if higher prices recover the IRR

### Scenario: Faster Sales (luxury segment)
- Increase `salesPerMonth` to 4
- Reduce `closingLagMonths` if your market allows (e.g., 9 instead of 12)
- Watch debt repay faster and interest drop

### Scenario: Construction Cost Inflation
- Go to **Unit Types** → increase `verticalCostPerUnit` by 10–20%
- Go to **Dashboard** → see the impact on margin and LP IRR
- Consider increasing `homePrice` to recover margin

---

## Support & Questions

If a value doesn't make sense:
1. **Hover over the field** for inline guidance
2. **Check the Calculation Reference** in Timeline & Scenario for definitions
3. **Review Monthly Cash Flow** to see exactly when/where money moves

For complex scenarios (multi-currency, mezzanine debt, JV structures), contact your development advisor.

---

## Technical Notes

This model uses:
- **Monthly cash flow simulation** (not annual — more accurate for construction)
- **Actual/360 day count** for interest (standard North American real estate)
- **Capitalized interest** (unpaid interest is added to debt balance)
- **LTC accrual** (loan grows as eligible costs are incurred; max = LTC% × total eligible costs)
- **Newton-Raphson IRR** (accurate to ±0.01% per annum)

All calculations are deterministic — same inputs always produce same outputs. No Monte Carlo or stochastic modeling.

---

**Version:** 1.0  
**Last Updated:** [DATE]  
**Client:** [CLIENT NAME]  
**Project:** [PROJECT NAME if applicable]
