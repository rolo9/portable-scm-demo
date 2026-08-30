# Portable SCM MVP Report

This report is a deterministic projection of the Build #010 and Build #011 structured CSV outputs. The CSV files remain the machine-readable sources of truth.

## Run Contract and Status

| Field | Value |
| --- | --- |
| Portable SCM contract version | 0.1 |
| Actual report period | 2025-08 |
| Projected endpoint | 2025-10 |
| Previous planning as-of | 2025-07 |
| Current planning as-of | 2025-08 |
| Forecast horizon months | 1 |
| Projected valuation basis ID | STANDARD-2025 |
| Top N | 10 |
| Canonical validation | PASS |
| Build #010 execution | PASS |
| Build #011 execution | PASS |
| Portable MVP technical readiness | PASS |

## Actual Inventory Value — Increase Top-N


## Actual Inventory Value — Decrease Top-N

| rank | item_code | prior_inventory_quantity | current_inventory_quantity | prior_inventory_value | current_inventory_value | actual_value_change | quantity_effect | unit_cost_effect | value_reconciliation_residual | target_directional_state | forecast_comparison_status | receipt_quantity | shipment_quantity | disposal_expiry_quantity | reconciliation_residual_quantity | movement_reconciliation_status |
|------|-----------|--------------------------|----------------------------|-----------------------|-------------------------|---------------------|-----------------|------------------|-------------------------------|--------------------------|----------------------------|------------------|-------------------|--------------------------|----------------------------------|--------------------------------|
| 1    | SYN-002   | 200.0                    | 160.0                      | 2400.0                | 1920.0                  | -480.0              | -480.0          | 0.0              | 0.0                           | NO_POLICY_BASIS          | NO_COMPARISON_BASIS        | 0.0              | 50.0              | 10.0                     | 20.0                             | UNRECONCILED                   |
| 2    | SYN-001   | 400.0                    | 390.0                      | 4000.0                | 3900.0                  | -100.0              | -100.0          | 0.0              | 0.0                           | NO_POLICY_BASIS          | COMPARABLE                 | 40.0             | 50.0              | 0.0                      | 0.0                              | RECONCILED                     |

## Projected Inventory Value — Increase Top-N


## Projected Inventory Value — Decrease Top-N


## Projected Items Without Comparison Basis

| item_code |  comparison_status  | projected_endpoint | previous_planning_as_of_month | current_planning_as_of_month | valuation_basis_id |
|-----------|---------------------|--------------------|-------------------------------|------------------------------|--------------------|
| SYN-001   | NO_COMPARISON_BASIS | 2025-10            | 2025-07                       | 2025-08                      | STANDARD-2025      |
| SYN-002   | NO_COMPARISON_BASIS | 2025-10            | 2025-07                       | 2025-08                      | STANDARD-2025      |

## Technical Readiness

Portable MVP Ready for Company Pilot = **PASS**

This is technical readiness evidence only. It is not Company Pilot authorization.
