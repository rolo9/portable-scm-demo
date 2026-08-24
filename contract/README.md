# Portable SCM Contract 0.1

The public boundary consists of seven separate canonical CSV facts plus `run-config.json`. Internal storage and executable implementation are not part of this distribution.

## Canonical datasets

| Dataset | Exact header | Declared row meaning / unique grain |
| --- | --- | --- |
| `inventory_actual.csv` | `item_code,period,inventory_quantity,valuation_unit_cost,inventory_value,valuation_basis` | observed inventory at `item_code × period` |
| `demand_forecast.csv` | `item_code,target_month,forecast_created_month,demand_forecast_quantity` | forecast version at `item_code × target_month × forecast_created_month` |
| `shipment_actual.csv` | `item_code,period,shipment_quantity` | realized shipment at `item_code × period` |
| `supply_plan.csv` | `item_code,target_month,supply_plan_created_month,planned_supply_quantity` | plan version at `item_code × target_month × supply_plan_created_month` |
| `inventory_movement_actual.csv` | `item_code,period,movement_type,movement_quantity` | realized non-shipment movement at `item_code × period × movement_type` |
| `inventory_policy.csv` | `item_code,effective_month,target_inventory_months` | policy fact at `item_code × effective_month` |
| `projected_valuation_basis.csv` | `item_code,valuation_basis_id,fixed_valuation_unit_cost` | fixed valuation fact at `item_code × valuation_basis_id` |

All period fields use canonical `YYYY-MM`. Identifiers must be non-empty. Numeric measures are finite and non-negative. `valuation_basis` is `REPORTED` or `CALCULATED`; `movement_type` is one of `RECEIPT`, `DISPOSAL_EXPIRY`, `TRANSFER_IN`, `TRANSFER_OUT`, `ADJUSTMENT_IN`, or `ADJUSTMENT_OUT`. Shipment facts belong exclusively in `shipment_actual.csv`; `inventory_movement_actual.csv` contains non-shipment movements only. Rows must be unique at each declared grain. A structurally valid unmatched fact remains missing: the Core never silently zero-fills, fabricates a comparison basis, or substitutes a nearest/latest version.

## Run configuration

The accepted v0.1 surface is:

- `portable_scm_contract_version`, exactly `"0.1"`;
- `actual_report_period`;
- `projected_endpoint`;
- `previous_planning_as_of_month`;
- `current_planning_as_of_month`;
- `projected_valuation_basis_id`;
- optional `forecast_horizon_months`, default `1`;
- optional `top_n`, default `10`.

Month values use `YYYY-MM`. The required planning versions are exact; the Core does not substitute a nearest or latest version. Source locations, workbook settings, credentials, connector settings, and other company-specific configuration are outside this contract.

## Deterministic analytical semantics

Actual inventory change preserves the accepted valuation bridge. `REPORTED` means inventory value is a canonical reported fact; `CALCULATED` means the canonical value is quantity multiplied by unit cost. The bridge decomposes actual value change into quantity effect, unit-cost effect, and reconciliation residual without inventing causality. Forecast, target, movement, or valuation evidence that is absent stays absent; no missing fact becomes zero.

Projected inventory value uses the single `projected_valuation_basis_id` selected in run configuration as a fixed unit-cost basis for both planning versions. It does not fall back to another basis. Items lacking the exact required forecasts, plans, actualization basis, or selected valuation basis retain incomplete comparison evidence and are classified `NO_COMPARISON_BASIS`; they do not enter Increase/Decrease ranking.

The structured CSV outputs are the analytical sources of truth. `report.md` is only a deterministic human-readable projection of existing structured results: it adds no calculation, classification, cause, or policy judgment. `run_manifest.json` records deterministic validation, execution, output, and technical-readiness evidence. Technical readiness does not authorize a Company Pilot or publication.

No new business policy is implied by validation, ranking, classifications, or the report.

## Generic Adapter / Company Adapter boundary

The Portable / Generic side owns the canonical filenames, schemas, declared grains, validation and normalization, `run-config.json`, deterministic analytical semantics, structured-output meaning, and generic report semantics.

A Company Adapter remains external and owns company workbook/sheet/column names, discovery and naming/version-storage rules, source quirks, source-to-canonical mapping, proprietary cost retrieval, selection/construction of `REPORTED` versus `CALCULATED` facts, confidential paths and values, and runtime-specific wiring. This distribution neither implements nor describes a Company Adapter.
