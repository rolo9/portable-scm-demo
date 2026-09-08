# SCM Reasoning Reference — Public Distribution

Status: public, non-authoritative reasoning reference.

This document is a deliberately small, company-independent semantic skeleton for comparing AI model reasoning with and without durable external structure. It contains no proprietary source mappings, company data, credentials, paths, or private repository content.

## Purpose

Use this reference when asking an AI model to reason about inventory and supply-design problems without letting it freely redefine the business meaning of the inputs.

The reference is intentionally narrower than a full SCM framework. It defines only the semantic boundaries that should remain stable while the model performs problem framing and interpretation.

## Fact types

Treat the following as distinct facts rather than interchangeable columns:

- Inventory Actual: observed inventory at an item and period.
- Demand Forecast: a forecast for a target period, tied to the version / creation period that produced that view.
- Shipment Actual: realized outbound demand / shipment at an item and period.
- Supply Plan: a planned logistics receipt / sales-available supply quantity for a target period, tied to the plan version that produced that view.
- Inventory Movement Actual: realized non-shipment movement such as receipt, disposal, transfer, or adjustment where separately represented.
- Inventory Policy: an observed policy / target fact. It is not automatically assumed to be economically optimal.
- Valuation Basis: a fixed valuation fact used to translate quantity exposure into value exposure when authorized.

## Important semantic boundaries

### Plan is not actual

A Supply Plan is an expectation. It must not be silently treated as a realized receipt.

### Logistics plan is not manufacturing plan

A logistics receipt plan describes when supply becomes available to the downstream inventory system. It does not prove when, how many lots at once, or under what manufacturing campaign logic the factory produced the material.

Example:
- a factory may manufacture two lots together in June;
- downstream logistics may receive one lot in July and one lot in August.

Use logistics receipt patterns to analyze corporate inventory formation first. Request manufacturing-event evidence only when it is load-bearing to the decision.

### Multi-lot is not automatically campaign inventory

Lot count alone is not enough.

If one lot equals one month of demand, four lots grouped together may create roughly four months of coverage. If monthly demand already requires five lots, producing five lots is not necessarily inventory-building concentration.

Normalize lot / receipt quantities by demand before interpreting concentration.

### Current policy is evidence, not truth

An existing inventory threshold or target may be the current policy and should be represented accurately. Do not silently replace it with a new threshold. However, do not assume that the current policy is globally optimal when evaluating supply design.

### Inventory reduction is not automatically good

Reducing inventory may increase production frequency, setup burden, cost, and supply risk. High inventory may also be economically inefficient. The decision is a trade-off, not a one-direction objective.

### Missing is missing

Do not fabricate missing business facts, substitute an unavailable plan version with a nearby version, or infer manufacturing causes from logistics facts alone.

## Reasoning boundary

Use the sequence:

`Fact -> Derived Feature -> Interpretation -> Human Decision`

The model may calculate transparent features and propose interpretations. It must distinguish those interpretations from observed facts and from final Human decisions.

## First-order supply-design screen

When data exists, useful first-order signals can include:

- one-lot demand coverage;
- planned logistics receipt expressed as demand coverage;
- number of active receipt months;
- interval between planned receipts;
- maximum / typical receipt concentration;
- annual planned receipt versus annual demand;
- inventory trajectory / inventory-month trajectory;
- inventory value exposure;
- relationship between current inventory policy and the observable supply cycle.

These are candidate analytical features, not universal thresholds.

## Human investigation boundary

Use machine-readable existing facts before asking people to reproduce them.

Human or factory investigation is most valuable for causal/contextual facts such as:

- setup or campaign efficiency;
- capacity constraints;
- validation / transfer / discontinuation;
- material or quality constraints;
- production coordination;
- supply-risk rationale;
- other load-bearing operational constraints absent from the structured data.

## What this reference intentionally does not define

- a universal excess-inventory threshold;
- a universal campaign-manufacturing definition;
- an optimal inventory target;
- a production scheduling algorithm;
- a shortage-risk policy;
- company-specific business rules;
- autonomous final decision authority.

Its purpose is to constrain semantic drift while leaving room for models to demonstrate problem-framing and reasoning quality.
