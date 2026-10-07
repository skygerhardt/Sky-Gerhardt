---
type: spec
capability: marginal-analysis
engagement: perfect-competition
date: 2026-10-05
status: built
build_with: "ChatGPT, from this file"
--- 

# Marginal Analysis — Model Specification 

## Purpose
The goal of this model is to assist the farm in determining how many beds of mesclun, tomatoes, and carrots to plant in order to optimize profit. It must choose the optimal crop mix while taking into consideration the 64 available beds, the bed cap for each crop, labor needs, fertilizer prices, decreasing returns, and the four temporary worker cap.

## Inputs — the named contract
| Name | Value | Unit | Source |
|---|---:|---|---|
| TOM_CAP | 20 | beds | Case scenario, crop table |
| TOM_PRICE | 8800 | USD per bed | Case scenario, crop table |
| TOM_HRS | 2.5 | hours per week per bed | Case scenario, crop table |
| TOM_FERT | 880 | USD per bed | Case scenario, crop table |
| TOM_DIM | 10% | percent | Case scenario, crop table |
| CAR_CAP | 20 | beds | Case scenario, crop table |
| CAR_PRICE | 2094 | USD per bed | Case scenario, crop table |
| CAR_HRS | 0.833 | hours per week per bed | Case scenario, crop table |
| CAR_FERT | 440 | USD per bed | Case scenario, crop table |
| CAR_DIM | 2.5% | percent | Case scenario, crop table |
| MES_CAP | 30 | beds | Case scenario, crop table |
| MES_PRICE | 2700 | USD per bed | Case scenario, crop table |
| MES_HRS | 1.25 | hours per week per bed | Case scenario, crop table |
| MES_FERT | 880 | USD per bed | Case scenario, crop table |
| MES_DIM | 1.25% | percent | Case scenario, crop table |
| WEEKS | 36 | weeks | Case scenario, farm table |
| FIXED_COST | 20000 | USD per season | Case scenario, farm table |
| TOTAL_BEDS | 64 | beds | Case scenario, farm table |
| OWNER_HRS | 720 | hours | Case scenario, farm table |
| OWNER_RATE | 34.72 | USD per hour | Case scenario, farm table |
| TEMP_MAX | 4 | workers | Case scenario, farm table |
| TEMP_RATE | 17.36 | USD per hour | Case scenario, farm table |
| TEMP_HRS_PER_WORKER | 1440 | hours per worker | Case scenario, farm table |

## Structure
The worksheet should be set up so that the model computations are distinct from the assumptions and inputs. The case inputs, crop-level revenue and cost calculations, labor calculations, marginal-cost schedules, optimization model, validation checks, and a final output section that concisely describes the suggested planting mix and financial outcomes should all be included. To make the calculations easy to comprehend and audit, the workbook should use named ranges instead of unexplained cell references. 

## Calculation logic
The model should calculate labor hours for each crop using the formula LABOR_HRS(q) = q × HRS_PER_BED × WEEKS × (1 + DIM_PCT)^q. Revenue should be calculated using the number of beds planted multiplied by revenue per bed, while fertilizer cost should be calculated using beds planted multiplied by fertilizer cost per bed. To calculate overall agricultural labor, the model should incorporate labor needs for all three crops. Temporary labor should cover any extra hours needed after the owner's available labor has been utilized. After that, the total labor cost should be computed and transformed into a blended labor rate that may be distributed across the crops once more. Fertilizer, labor, and fixed costs should all be included in total costs. Profit should be calculated as total revenue less total costs. By adjusting the amount of tomato, carrot, and mesclun beds while adhering to all necessary restrictions, the optimization should maximize overall farm profit. After the owner's 720 available hours are used, the model should calculate any remaining temporary labor hours and determine the number of temporary workers required based on 1,440 available hours per worker, while keeping the total number of temporary workers at or below four. The model should also calculate the marginal cost of each additional bed for tomatoes, carrots, and mesclun so that marginal cost can be compared with the revenue per bed for each crop. 

## Conventions
Before hiring any temporary workers, the owner's 720 available hours should be utilized. The ratio of permanent to temporary labor should be decided at the farm level rather than individually for each crop, and temporary labor should only be utilized during hours that exceed the owner's available capacity. The farm's blended labor rate should be used to return labor expenses to specific crops. Since the farm cannot plant a portion of a bed, all planting selections should be made using entire numbers. Tomatoes cannot exceed 20 beds, carrots cannot exceed 20 beds, mesclun cannot exceed 30 beds, and the farm cannot use more than 64 beds total. Temporary labor also cannot exceed the capacity of four workers. If the profit-maximizing solution uses fewer than 64 beds, the model should allow beds to remain unused rather than forcing all available land to be planted. Marginal cost should be calculated from the model instead of assuming ahead of time that it always increases.

## Validation rules

The completed workbook must satisfy the published acceptance criteria for this case. The optimal planting mix should be 10 tomato beds, 20 carrot beds, and 30 mesclun beds, for a total of 60 beds. The resulting season profit should be approximately $42,762. The standalone points where price is approximately equal to marginal cost should occur around 10 beds for tomatoes, 10 beds for carrots, and 6 beds for mesclun.

The labor formula must also pass a q = 1 hand calculation. For one tomato bed, required labor should equal 1 × 2.5 × 36 × 1.10, which is 99 hours. At least one intermediate marginal-cost result should be cross-checked against the Farm Profit Lab to confirm that the calculations inside the model agree with a separate implementation of the same case.

Solver should be run from two different starting points, specifically 0/0/0 and 20/0/0, to check whether GRG Nonlinear reaches the same solution from both starting mixes. If the results disagree, that should be treated as an audit finding rather than ignored.

Every calculated cell in the workbook must contain a formula rather than a pasted or hard-coded result, and calculated cells should reference the named inputs defined in this specification. The workbook must contain no formula errors, and all named ranges should exist and be used consistently. The final planting solution must use integer bed counts, remain within each crop's individual bed cap, use no more than 64 total beds, and require no more than four temporary workers.
## Outputs
The recommended number of tomato, carrot, and mesclun beds, the total number of beds used, total revenue, fertilizer costs, total labor hours, owner labor used, temporary labor needed, the number of temporary workers needed, total labor cost, blended labor rate, total costs, and total profit should all be clearly reported in the final model. Additionally, it should display the pertinent marginal-cost figures and indicate if the significant labor, crop-cap, and land restrictions are binding or have residual capacity. 

## Audit findings
- I checked the tomato labor formula at q = 1. The workbook returned 99 hours, which matches the hand calculation 1 × 2.5 × 36 × 1.10. This check would catch a missing exponent or incorrect labor formula.

- I checked that calculated cells use formulas rather than pasted values and searched the workbook for #REF!, #DIV/0!, and #NAME? errors. The calculated outputs were formula-driven and I did not find those formula errors. This check would catch broken references or hard-coded model results.

- I checked the constraint cells at the 10 tomato, 20 carrot, and 30 mesclun mix. The mix stays within the crop caps, uses only 60 of the 64 available beds, and remains within the labor constraints. This check would catch an infeasible recommended planting plan.

- I located the tomato marginal-cost dip between beds 5 and 6 and noted it for Stage 3 analysis. I am not explaining the cause here because that belongs in Stage 3.
