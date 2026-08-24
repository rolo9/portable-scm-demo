# Portable SCM MVP Report

This report is a deterministic projection of the Build #010 and Build #011 structured CSV outputs. The CSV files remain the machine-readable sources of truth.

## Run Contract and Status

| Field | Value |
| --- | --- |
| Portable SCM contract version | 0.1 |
| Actual report period | 2025-03 |
| Projected endpoint | 2025-05 |
| Previous planning as-of | 2025-01 |
| Current planning as-of | 2025-03 |
| Forecast horizon months | 1 |
| Projected valuation basis ID | STANDARD-2025 |
| Top N | 5 |
| Canonical validation | PASS |
| Build #010 execution | PASS |
| Build #011 execution | PASS |
| Portable MVP technical readiness | PASS |

## Actual Inventory Value — Increase Top-N

| rank |  item_code  | prior_inventory_quantity | current_inventory_quantity | prior_inventory_value | current_inventory_value | actual_value_change | quantity_effect | unit_cost_effect | value_reconciliation_residual | target_directional_state | forecast_comparison_status | receipt_quantity | shipment_quantity | disposal_expiry_quantity | reconciliation_residual_quantity | movement_reconciliation_status |
|------|-------------|--------------------------|----------------------------|-----------------------|-------------------------|---------------------|-----------------|------------------|-------------------------------|--------------------------|----------------------------|------------------|-------------------|--------------------------|----------------------------------|--------------------------------|
| 1    | SYN-B12-ACT | 100.0                    | 120.0                      | 1000.0                | 1200.0                  | 200.0               | 200.0           | 0.0              | 0.0                           | NO_POLICY_BASIS          | COMPARABLE                 | 70.0             | 50.0              | 0.0                      | 0.0                              | RECONCILED                     |

## Actual Inventory Value — Decrease Top-N


## Projected Inventory Value — Increase Top-N

| rank |   item_code    | previous_projected_ending_inventory_quantity | current_projected_ending_inventory_quantity | projected_quantity_revision | fixed_valuation_unit_cost | previous_projected_inventory_value | current_projected_inventory_value | projected_inventory_value_revision | actualization_effect_value | supply_revision_effect_value | demand_revision_effect_value | represented_revision_value | value_residual |
|------|----------------|----------------------------------------------|---------------------------------------------|-----------------------------|---------------------------|------------------------------------|-----------------------------------|------------------------------------|----------------------------|------------------------------|------------------------------|----------------------------|----------------|
| 1    | SYN-BRIDGE     | 100.0                                        | 129.0                                       | 29.0                        | 100.0                     | 10000.0                            | 12900.0                           | 2900.0                             | 1500.0                     | 1000.0                       | 400.0                        | 2900.0                     | 0.0            |
| 2    | SYN-HIGH-VALUE | 100.0                                        | 105.0                                       | 5.0                         | 100.0                     | 10000.0                            | 10500.0                           | 500.0                              | 500.0                      | 0.0                          | 0.0                          | 500.0                      | 0.0            |
| 3    | SYN-QTY-LARGE  | 100.0                                        | 120.0                                       | 20.0                        | 10.0                      | 1000.0                             | 1200.0                            | 200.0                              | 200.0                      | 0.0                          | 0.0                          | 200.0                      | 0.0            |
| 4    | SYN-TIE-A      | 100.0                                        | 105.0                                       | 5.0                         | 40.0                      | 4000.0                             | 4200.0                            | 200.0                              | 200.0                      | 0.0                          | 0.0                          | 200.0                      | 0.0            |
| 5    | SYN-TIE-B      | 100.0                                        | 105.0                                       | 5.0                         | 40.0                      | 4000.0                             | 4200.0                            | 200.0                              | 200.0                      | 0.0                          | 0.0                          | 200.0                      | 0.0            |

## Projected Inventory Value — Decrease Top-N

| rank |   item_code   | previous_projected_ending_inventory_quantity | current_projected_ending_inventory_quantity | projected_quantity_revision | fixed_valuation_unit_cost | previous_projected_inventory_value | current_projected_inventory_value | projected_inventory_value_revision | actualization_effect_value | supply_revision_effect_value | demand_revision_effect_value | represented_revision_value | value_residual |
|------|---------------|----------------------------------------------|---------------------------------------------|-----------------------------|---------------------------|------------------------------------|-----------------------------------|------------------------------------|----------------------------|------------------------------|------------------------------|----------------------------|----------------|
| 1    | SYN-DEC-HIGH  | 100.0                                        | 95.0                                        | -5.0                        | 100.0                     | 10000.0                            | 9500.0                            | -500.0                             | -500.0                     | 0.0                          | 0.0                          | -500.0                     | 0.0            |
| 2    | SYN-DEC-LARGE | 100.0                                        | 80.0                                        | -20.0                       | 10.0                      | 1000.0                             | 800.0                             | -200.0                             | -200.0                     | 0.0                          | 0.0                          | -200.0                     | 0.0            |

## Projected Items Without Comparison Basis

|       item_code        |  comparison_status  | projected_endpoint | previous_planning_as_of_month | current_planning_as_of_month | valuation_basis_id |
|------------------------|---------------------|--------------------|-------------------------------|------------------------------|--------------------|
| SYN-B12-ACT            | NO_COMPARISON_BASIS | 2025-05            | 2025-01                       | 2025-03                      | STANDARD-2025      |
| SYN-MISS-BASIS         | NO_COMPARISON_BASIS | 2025-05            | 2025-01                       | 2025-03                      | STANDARD-2025      |
| SYN-MISS-CURR-FORECAST | NO_COMPARISON_BASIS | 2025-05            | 2025-01                       | 2025-03                      | STANDARD-2025      |
| SYN-MISS-CURR-SUPPLY   | NO_COMPARISON_BASIS | 2025-05            | 2025-01                       | 2025-03                      | STANDARD-2025      |
| SYN-MISS-PREV-FORECAST | NO_COMPARISON_BASIS | 2025-05            | 2025-01                       | 2025-03                      | STANDARD-2025      |
| SYN-MISS-PREV-SUPPLY   | NO_COMPARISON_BASIS | 2025-05            | 2025-01                       | 2025-03                      | STANDARD-2025      |

## Technical Readiness

Portable MVP Ready for Company Pilot = **PASS**

This is technical readiness evidence only. It is not Company Pilot authorization.
