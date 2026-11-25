# Prompt 03 — Symptom → Plate → Lab Trace

**Best for:** Connecting recurring low-energy, brain fog, bloating, inflammation, craving, or skin days in fuelOS check-ins back to specific meals, caffeine timing, and lab flags.

**Requires:** Function Health connector (or lab PDF) + fuelOS MCP connector.

---

```text
Help me investigate patterns behind my lowest-scoring check-in days by cross-referencing fuelOS check-ins, meals, stack, and bloodwork.

Step 1 — Pull the real data:
- Call `get_check_ins` with `limit: 30`.
  IMPORTANT SCALE RULE: fuelOS check-ins run 0.0 to 1.0 where 1.0 is ALWAYS better. For bloating, inflammation, and cravings, 1.0 means comfortable/normal/none and 0.0 means severe. Never invert this.
- Identify the 4 to 6 days with the lowest scores (especially any days with written notes) and 4 high-scoring baseline days for contrast.
- For those specific low days AND the day immediately before each low day (to catch late caffeine, heavy dinners, or low-fiber days), call `get_daily_intake` and then `get_meal` on the standout meals to inspect `foodItems`, `bioactives`, timestamps, and `entries`.
- Call `list_stack` and review relevant biomarkers from Function Health or the attached lab PDF (e.g., ferritin, vitamin D, B12, thyroid panel, fasting insulin/HbA1c, hs-CRP).
- If `get_health_inventory` shows synced Apple Health sleep or HRV data, optionally pull those days with `get_health_metrics` for context.

Step 2 — Report:
1. **Low-Day Timeline:** A compact table comparing my lowest check-in days (score + note) against the same day's and prior day's meals, late-day caffeine, saturated fat, fiber, and sodium.
2. **Contrast vs. Good Days:** What differed consistently between my low-scoring days and my high-scoring days? State exact counts (e.g., "3 of 4 low-bloating-score days followed X").
3. **Bloodwork Context:** Note which lab markers sit in the same neighborhood as these symptoms, clearly marking what is observed correlation vs. hypothesis.
4. **14-Day Self-Observation Test:** Propose 1–2 simple food/timing variables to observe in fuelOS over the next 14 days (using daily check-ins) and 3 questions to bring to my clinician.

Boundary: Do not diagnose food intolerances or medical conditions. State clearly when there are too few low days to draw a pattern.
```
