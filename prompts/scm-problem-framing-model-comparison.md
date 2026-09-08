# SCM Problem Framing Model Comparison

Use the same prompt across models. Run two conditions:

- Condition A: prompt only.
- Condition B: require the model to read `reasoning-reference/README.md` first and treat its semantic boundaries as authoritative for the task.

Compare reasoning quality, unsupported assumptions, problem decomposition, trade-off awareness, and the amount of Human correction required.

---

You are a Senior SCM Decision Partner.

The purpose of this task is not to rush to a solution. First convert the situation into a decision-ready problem structure across management, supply chain, manufacturing, inventory, and capital-efficiency perspectives.

## Situation

An organization already identifies excess-inventory SKUs using an existing rule such as inventory coverage above a defined threshold.

Potential background causes include:
- planned discontinuation;
- lot scale;
- demand forecast error;
- validation;
- manufacturing-site transfer;
- grouped production for efficiency or cost;
- other temporary supply conditions.

Planned-discontinuation items may intentionally carry inventory to support an exit schedule.

For low-demand / large-lot items, reducing inventory months mechanically may require much more frequent production and can worsen factory efficiency, cost, or supply stability.

The internal term "campaign manufacturing" may not have a stable definition.

For example:
- one lot = 100 units, monthly demand = 100, four lots are grouped;
- one lot = 100 units, monthly demand = 500, five lots are required every month.

Both involve multiple lots, but their inventory meaning is different.

The available Supply Plan is a logistics receipt / sales-available delivery plan, not a strict manufacturing plan.

For example, a factory may manufacture two lots together in June while logistics receives one lot in July and one lot in August.

The immediate objective is not to judge factory efficiency itself. It is to identify corporate-inventory-forming supply-design patterns with meaningful review potential from an enterprise perspective.

However, optimizing only the formal excess-inventory count can create problems:
- items below the threshold may still have very large inventory-value impact;
- forcing low-demand items below the threshold may increase production frequency and cost;
- KPI improvement may worsen overall economics or resilience.

The current inventory target / baseline itself may also lack a strong economic rationale and should not automatically be assumed optimal.

## Task

Before proposing solutions, perform Problem Framing.

Clarify:
1. What is the real problem to solve?
2. What should actually be optimized?
3. Where can KPI optimization conflict with enterprise optimization?
4. What is the minimum data that should first be assembled across the portfolio?
5. What useful derived signals can be calculated mechanically from those data?
6. Which items should be escalated to Human investigation?
7. What information should come from factories, and what should be derived from existing data instead?
8. Which parts of the current inventory policy may be used as current facts, and which parts should remain validation targets?
9. How can the problem be defined without depending on the label "campaign manufacturing"?
10. What trade-offs must ultimately be compared before management can make a decision?

## Constraints

- Do not use excess-inventory case count as the sole success metric.
- Do not assume inventory reduction is always good.
- Do not assume production efficiency is always good.
- Do not guess unknown business rules.
- Explicitly label missing information.
- Do not begin by proposing a large optimization model.
- Prefer analysis possible from existing structured data first.
- Distinguish Fact, Interpretation, and Recommendation.

Finally, provide three questions that the SCM owner should think about next.
