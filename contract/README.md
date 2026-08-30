# Portable SCM Contract 0.1

The public boundary is seven separate canonical CSV facts plus
`run-config.json`. Every CSV uses UTF-8 text, a header row, canonical `YYYY-MM`
month values, and one row per declared key. Identifiers must be non-empty;
numeric measures must be valid and non-negative; enumerated values must be in
their documented set; and declared keys must be unique. Structurally valid but
unmatched facts remain missing. They are never silently zero-filled or matched
to a nearest or latest version.

## Canonical inputs

| File | Declared row meaning / key | Fields |
| --- | --- | --- |
| `inventory_actual.csv` | observed inventory at `item_code x period` | `item_code`, `period`, `inventory_quantity`, `valuation_unit_cost`, `inventory_value`, `valuation_basis` |
| `demand_forecast.csv` | forecast version at `item_code x target_month x forecast_created_month` | `item_code`, `target_month`, `forecast_created_month`, `demand_forecast_quantity` |
| `shipment_actual.csv` | realized shipment at `item_code x period` | `item_code`, `period`, `shipment_quantity` |
| `supply_plan.csv` | plan version at `item_code x target_month x supply_plan_created_month` | `item_code`, `target_month`, `supply_plan_created_month`, `planned_supply_quantity` |
| `inventory_movement_actual.csv` | realized non-shipment movement at `item_code x period x movement_type` | `item_code`, `period`, `movement_type`, `movement_quantity` |
| `inventory_policy.csv` | policy fact at `item_code x effective_month` | `item_code`, `effective_month`, `target_inventory_months` |
| `projected_valuation_basis.csv` | fixed valuation fact at `item_code x valuation_basis_id` | `item_code`, `valuation_basis_id`, `fixed_valuation_unit_cost` |

`inventory_actual.valuation_basis` is `REPORTED` when quantity, unit cost, and
value are an accepted source fact, and `CALCULATED` when the adapter has
explicitly constructed the accepted actual-value bridge. The Portable Core
does not retrieve proprietary costs or infer that bridge.

`inventory_movement_actual.movement_type` is one of `RECEIPT`,
`DISPOSAL_EXPIRY`, `TRANSFER_IN`, `TRANSFER_OUT`, `ADJUSTMENT_IN`, or
`ADJUSTMENT_OUT`. Shipment is its own canonical fact and must not be duplicated
as a non-shipment movement.

One physical source may emit zero, one, or multiple canonical logical
datasets. Each emitted dataset must independently preserve its canonical
schema, grain, validation, and missing-data semantics. This physical-source
cardinality does not create a new canonical dataset or permit a wide combined
Portable table.

## Run configuration

`run-config.json` contains:

- `portable_scm_contract_version`, exactly `"0.1"`;
- `actual_report_period`;
- `projected_endpoint`;
- `previous_planning_as_of_month`;
- `current_planning_as_of_month`;
- `projected_valuation_basis_id`;
- optional `forecast_horizon_months`, default `1`;
- optional `top_n`, default `10`.

Configuration contains no source locations, workbook names, credentials, or
connector settings.

## Portable outputs

`actual_inventory_change.csv` preserves the accepted Actual Inventory Value
bridge. Quantity effect plus unit-cost effect plus explicit residual reconcile
the value change. Forecast, policy, and movement comparison statuses remain
explicit when a compatible basis is unavailable.

`projected_inventory_value_portfolio.csv` uses the selected fixed valuation
basis to value the protected projected quantity revision. Missing required
versions or valuation facts produce `NO_COMPARISON_BASIS`; no substitute
version, zero-fill, or invented cause is used. Actualization, supply revision,
demand revision, and explicit residual remain the protected top-level bridge.

`projected_inventory_actualization_detail.csv` is additive beneath the
top-level `Actualization Effect`. For comparable facts it reconciles represented
realized Supply, realized Demand/Shipment, accepted non-shipment movement, and
an explicit detail residual. It does not change the protected top-level
revision or value formulas, add a floor/clamp, or claim business causality.

`report.md` is a deterministic projection of structured CSV results.
`run_manifest.json` records validation, execution/readiness status, parameters,
and `run_identity`. The Actualization Detail sidecar records the same bounded
identity categories for its standalone output. Current `run_identity` contains:

- the exact private implementation commit;
- stable implementation scope `capabilities/scm-inventory-analysis`;
- SHA-256 identities of all seven exact canonical input files;
- the SHA-256 identity of exact `run-config.json` bytes.

It records no remote URL, branch, credential, token, local path, user path, or
company source path. Historical manifests are not rewritten.

## Adapter and authority boundary

The Portable / Generic side owns canonical filenames, schemas, grains,
normalization and validation, `run-config`, deterministic analytical semantics,
structured-output meanings, and generic report semantics.

The Company Adapter remains outside this distribution. It owns source file,
workbook, sheet, and column identities; discovery, naming, version, and storage
rules; source quirks; source-to-canonical mappings and joins; proprietary cost
retrieval; selection or construction of `REPORTED` versus `CALCULATED` actual
valuation facts; confidential values and paths; source history/availability;
and company-runtime wiring.

No company-specific mapping, new policy rule, floor/clamp, optimization, or
causal explanation is part of this contract.
