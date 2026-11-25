# Prompt 05 — 1-Page Clinician Visit Prep

**Best for:** Walking into a primary care, longevity, or specialist appointment with a crisp, neutral 1-page brief instead of trying to remember what you ate and took over the last month.

**Requires:** Function Health connector (or lab PDF) + fuelOS MCP connector.

---

```text
Prepare a neutral, 1-page clinician visit summary combining my recent bloodwork with my last 30 days in fuelOS.

Step 1 — Gather facts from fuelOS:
- Call `get_profile`, `get_goals`, and `list_stack`.
- Call `get_nutrient_trends` (30 days) for: energy, protein, carbs, fat, saturatedFat, fiber, sugar, sodium, potassium, caffeine, plus any micronutrients linked to my flagged labs.
- Call `get_check_ins` (`limit: 30`). Remember: 0.0 to 1.0 scale where 1.0 is always better (1.0 = comfortable/normal/none for bloating, inflammation, cravings).
- Call `get_health_inventory`; if resting heart rate, HRV, or sleep duration are synced, pull the last 30 days via `get_health_metrics` and state the unit returned.

Step 2 — Format as a crisp, printable 1-page brief (under 500 words):
- **Patient Context (self-logged):** Age, sex, height, weight, activity level, logging coverage (X of 30 days logged).
- **Flagged Labs (from panel dated YYYY-MM-DD):** Bullet list of out-of-range or borderline values only.
- **30-Day Daily Intake Averages:** Compact table (energy, protein, fiber, saturated fat, sodium_mg, caffeine_mg, plus relevant micronutrients).
- **Current Supplements & Medications (`list_stack`):** Name, dose, form, schedule (mark any paused items).
- **Daily Check-In Summary (30 days):** Average score per tracked dimension + recurring written notes.
- **Optional Wearable Summary:** Only if present in `get_health_metrics`.
- **5 Questions for Today's Visit:** Direct, non-leading questions my doctor can answer quickly.

Tone: Objective, clinical-friendly, zero hype, zero self-diagnosis. Clearly state that intake values are self-logged estimates.
```
