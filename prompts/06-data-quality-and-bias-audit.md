# Prompt 06 — Data Quality & Bias Audit

**Best for:** Sanity-checking your fuelOS data before you draw any conclusions about your bloodwork or symptoms.

**Requires:** fuelOS MCP connector.

---

```text
Before I draw any conclusions linking my intake to my bloodwork or check-ins, run a strict data-quality audit on my last 30 days in fuelOS.

Call:
- `list_meals` for the last 30 days (`limit: 200`)
- `get_meal` on a sample of 10 recent meals to inspect `userCorrected`, `foodItems`, `entries`, and `portionFraction`
- `get_check_ins` (`limit: 30`)
- `list_stack`
- `get_health_inventory`

Audit and report:
1. **Logging completeness:** How many of the last 30 days have 0 meals, 1–2 meals (likely partial days), vs. 3+ meals? Warn me how partial days skew 30-day averages.
2. **Estimate vs. verified provenance:** From the sampled meals, how many have `entries[].product` (barcode-scanned labels) or `userCorrected` fields vs. pure AI estimates?
3. **Check-in coverage:** How many days have check-ins, which dimensions are tracked consistently, and how many days include notes?
4. **Stack & wearable gaps:** Note any stack items missing dose/unit/schedule, or whether Apple Health sync is empty.
5. **What is safe to analyze right now:** Tell me plainly which questions my current dataset is strong enough to answer, and which ones need 14+ cleaner days of logging first.
```
