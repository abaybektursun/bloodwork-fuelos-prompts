# Prompt 02 — Supplement Stack Reality Check

**Best for:** Auditing whether the bottles on your counter actually align with your bloodwork changes and daily check-ins, or whether you are doubling up on nutrients you already get from food.

**Requires:** Function Health connector (ideally 2 sequential panels) or uploaded lab PDFs + fuelOS MCP connector.

---

```text
Audit my current supplement stack against my bloodwork and my daily intake log in fuelOS.

Step 1 — Pull my records:
- Call `list_stack` to get every item (dose, unit, form, schedule, paused status).
- Call `get_nutrient_trends` over the last 30 days for the nutrients my stack targets (e.g., vitaminD, magnesium, zinc, iron, vitaminB12, folate, calcium, potassium, caffeine).
- Call `get_check_ins` for the last 30 days. Remember: all fuelOS check-in scores are on a 0.0 to 1.0 scale where 1.0 is ALWAYS better (1.0 = high energy/sharp clarity/comfortable digestion/no inflammation/no cravings; 0.0 = severe).
- Read my bloodwork from Function Health or the attached lab PDFs (comparing my latest panel to the prior panel if two dates are present).

Step 2 — Produce a Stack Audit with four sections:
1. **Stack vs. Food + Labs Table:** One row per active item in `list_stack`:
   - Item, dose, form, and schedule
   - What my food already supplies on average per day
   - Corresponding lab marker (current value and change since prior draw, if available)
   - Relevant check-in notes or trends
2. **Overlap & Redundancy Check:** Flag any nutrient where food + stack combined approaches high daily totals, or where multiple items cover the same pathway. Note any paused items separately.
3. **Zero-Signal Check:** Identify stack items where neither lab markers nor 30-day check-ins show a clear signal yet, noting when sample size or missing pre-baseline labs prevent a conclusion.
4. **Clinician Review List:** 3 concrete questions to ask my doctor about simplifying, timing, or re-testing specific items in this stack.

Boundary: Informational summary only. Do not instruct me to stop prescribed medications or diagnose deficiencies.
```
