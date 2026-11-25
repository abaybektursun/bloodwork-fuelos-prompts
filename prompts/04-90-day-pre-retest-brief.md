# Prompt 04 — 90-Day Pre-Retest Experiment Brief

**Best for:** Turning 1–2 out-of-range biomarkers into a measurable, single-variable intake plan before your next quarterly or semi-annual blood draw.

**Requires:** Function Health connector (or lab PDF) + fuelOS MCP connector.

---

```text
I want to prepare a clean, measurable 90-day tracking brief before my next blood draw, focused on these 1–2 biomarkers: [INSERT 1–2 BIOMARKERS, e.g., ApoB and Vitamin D, OR leave blank to pick my top 2 flagged markers].

Step 1 — Measure my real baseline from fuelOS:
- Call `get_profile`, `get_goals`, and `list_stack`.
- Call `get_nutrient_trends` over the last 30 days for the dietary levers tied to those markers (for example: fiber, saturatedFat, protein, sugar, sodium, vitaminD, iron, magnesium, potassium).
- Call `get_check_ins` (`limit: 30`) to record my current baseline averages (remember: 0.0 to 1.0 where 1.0 is always better).

Step 2 — Build my 90-Day Tracking Brief:
1. **Baseline Snapshot:** Current lab value(s) with draw date, current 30-day fuelOS daily average(s), current goal targets, and active stack items touching those markers.
2. **Testable Daily Targets (for clinician sign-off):** Propose 2–3 concrete, measurable daily intake benchmarks I can track in fuelOS (using foods I already log in `list_meals`, not an invented meal plan).
3. **Confounder Watchlist:** List variables that could muddy the next blood draw (inconsistent logging days, paused supplements, training spikes, recent illness) and how to note them in fuelOS check-ins.
4. **Clinician Check-In:** Draft a short 3-sentence message I can send my doctor to confirm whether these dietary targets and my planned retest timing make sense for me.

Boundary: Informational planning only—explicitly note that supplement dose changes or medical interventions should be confirmed with a clinician.
```
