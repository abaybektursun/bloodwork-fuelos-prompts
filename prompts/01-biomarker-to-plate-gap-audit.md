# Prompt 01 — Biomarker-to-Plate Gap Audit

**Best for:** Right after a new blood panel lands, to see how your actual daily food and supplement intake lines up with every out-of-range or borderline marker.

**Requires:** Function Health connector (or uploaded lab PDF) + fuelOS MCP connector.

---

```text
You have access to two sources of my personal records:
1. My bloodwork (via the Function Health connector or the lab PDF attached in this chat).
2. My daily intake log via the fuelOS MCP tools.

Before writing any interpretation, call the fuelOS tools first:
- `get_profile` and `get_goals`
- `list_stack` (to see my active and paused supplements/medications)
- `get_nutrient_trends` over the last 30 days (ask me for my UTC offset if you do not know it; otherwise state the offset you used), passing all nutrients relevant to my flagged/borderline markers in one `nutrients: [...]` call—such as vitaminD, iron, vitaminB12, folate, magnesium, zinc, fiber, saturatedFat, sugar, sodium, potassium, and protein.
- Never pull dietary nutrients from `get_health_metrics` (avoid double-counting and unit mismatches; `get_nutrient_trends` reports canonical units like `sodium_mg`).

Output structure:
1. **Data coverage check:** State the exact lab draw date, the fuelOS date range queried, and how many days had logged intake. Flag if fewer than 14 days were logged.
2. **Biomarker-to-Intake Table:** For every out-of-range or borderline biomarker with a dietary or supplement link, build a table with columns:
   - Biomarker, value, and lab status
   - 30-day average from food (from `get_nutrient_trends`, excluding 0-logged days separately from logged days)
   - Active dose in my fuelOS Stack (from `list_stack`, noting dose, form, and schedule)
   - Observed gap or mismatch
3. **Top 3 patterns worth investigating:** Separate observed facts in the numbers from hypotheses. Do not invent numbers or assume I took supplements that are paused.
4. **Questions for my clinician:** Write 4 specific, concise questions grounded in these exact numbers to discuss at my next visit.

Boundary: Keep this strictly informational and educational—no clinical diagnosis and no prescription or dosage commands.
```
