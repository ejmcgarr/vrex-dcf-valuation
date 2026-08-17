# Varex Imaging (VREX) DCF and trading comps note

This project builds a simple but defensible valuation of Varex Imaging to assess whether Teledyne Technologies' $18.90 per share all-cash offer announced on 10 Aug 2026 looks fair.

## Project structure

- `scripts/valuation_dcf.py` – data pull, DCF build, WACC, sensitivity analysis and trading comps cross-check.
- `output/` – generated charts and summary data.
- `requirements.txt` – project dependencies.

## Core assumptions

- 5-year explicit forecast period, annual bins.
- Unlevered free cash flow (UFCF) is built from operating profit less cash taxes, plus depreciation, less capex and reinvestment in working capital.
- WACC is calculated using CAPM for cost of equity and a realistic after-tax cost of debt based on current debt and interest expense.
- Terminal value is estimated using a Gordon growth model and checked against an exit multiple approach.
- Comparable companies include GE HealthCare (GEHC) and Teledyne (TDY), with the explicit caveat that Varex does not have a clean pure-play public comp.

## How to run

```bash
python3 -m pip install -r requirements.txt
python3 scripts/valuation_dcf.py
```

The script saves:

- `output/vrex_dcf_summary.csv`
- `output/wacc_growth_sensitivity.png`
- `output/implied_value_vs_offer.png`

## Base-case conclusion

The script was run against actual Varex financial data and market inputs. In the base case:

- WACC: 6.87%
- Actual beta: 0.877
- DCF implied share value: ~$24.33/share
- Exit-multiple implied value: ~$23.06/share
- Teledyne offer price: $18.90/share

This implies the $18.90 offer is below the model-implied intrinsic value by roughly 23% to 29%, depending on the valuation method. The offer therefore looks modestly attractive from a buyer’s standpoint, but not obviously opportunistic in a simple base-case DCF framework, especially when considering the uncertainty around terminal value and the lack of a clean pure-play public comp.

The qualitative conclusion is that the offer is within a plausible valuation range, but not necessarily a clear “cheap” deal relative to intrinsic value under a standard DCF framework.

This is a deal-note style framework, not a legal fairness opinion. It is meant for interview preparation and for demonstrating a structured valuation process.
