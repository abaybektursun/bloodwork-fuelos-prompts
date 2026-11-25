# Worked Example Output (Synthetic Panel + 21-Day fuelOS Log)

Below is an example of what Claude or ChatGPT produces when pairing [synthetic-function-panel.md](synthetic-function-panel.md) with the 21-day seeded fuelOS demo account (`Alex`, 34M).

---

## Output A — Prompt 01 (Biomarker-to-Plate Gap Audit)

### 1. Data coverage check
- **Lab draw date:** 2026-11-01 (synthetic Function panel)
- **fuelOS window queried:** Last 21 consecutive days (`get_nutrient_trends`, `list_stack`, `get_goals`)
- **Logging completeness:** 21 of 21 days logged (5 entries/day, average ~2,150 kcal/day vs. 2,450 kcal goal)

### 2. Biomarker-to-Intake Table

| Biomarker & Status | 21-Day Food Avg (`get_nutrient_trends`) | Active Stack (`list_stack`) | Observed Gap or Mismatch |
|---|---|---|---|
| **Vitamin D: 28 ng/mL** *(Low)* | **~9.3 mcg/day** (~372 IU/day; spikes to 14–17 mcg only on salmon days, 0–3 mcg on non-fish days) | **Vitamin D3 + K2:** 2,000 IU liquid, `08:30` daily | Dietary Vitamin D is modest on non-fish days; despite an active 2,000 IU stack entry, serum 25-OH Vitamin D sits below 30 ng/mL—worth checking adherence, absorption with fat, or re-test timing with a clinician. |
| **ApoB: 104 mg/dL** *(Borderline High)* | **Saturated fat: ~26 g/day** (spikes to 34–39 g on ribeye steak and cream pasta nights); **Fiber: ~26 g/day** vs. **35 g goal** | None targeting lipids | Fiber runs ~9 g/day below the 35 g target, while saturated fat concentrates heavily in two recurring dinners (ribeye 21 g sat fat; restaurant cream pasta 26 g sat fat). |
| **RBC Magnesium: 4.4 mg/dL** *(Low-Normal)* | **~335 mg/day** from food (oats, quinoa, spinach, walnuts) | **Magnesium Glycinate:** 400 mg capsule, `21:30` nightly | Food + stack totals ~735 mg/day when taken consistently; low-normal RBC magnesium suggests checking consistency, timing, or whether baseline predates starting the stack. |
| **Omega-3 Index: 5.1%** *(Suboptimal)* | Salmon logged ~10 of 21 days (~1.8–2.1 g EPA+DHA per salmon meal) | **Omega-3 EPA/DHA:** 2,000 mg softgel, `13:00` daily | Current logged food + stack EPA/DHA is substantial; because red-blood-cell Omega-3 reflects a ~90–120 day window, recent habits may not be reflected in the Nov 1 draw yet. |
| **Ferritin: 44 ng/mL** *(Low-Normal)* | **Iron: ~11 mg/day** (higher on beef/lentil days, lower on yogurt/chicken/salmon days) | None | Moderate dietary iron, adequate for adult male RDA (8 mg) with B12 (640 pg/mL) and Folate (16.4 ng/mL) both solid. |

### 3. Top 3 patterns worth investigating
1. **ApoB vs. fiber and two high-saturated-fat dinners:** Observed fact: fiber averages ~26 g/day (target 35 g), and 3 cream-pasta nights + 7 ribeye nights account for a large share of weekly saturated fat. Hypothesis: shifting fiber up toward 35 g and swapping heavy cream sauces is a clean, testable dietary variable before the next draw.
2. **Vitamin D + Omega-3 timing vs. draw date:** Observed fact: both Vitamin D3 (2,000 IU) and Omega-3 (2,000 mg) appear active in `list_stack`, yet both blood markers remain low/suboptimal. Hypothesis: either those items were added shortly before the draw or skipped frequently—neither can be confirmed from a 21-day window alone.
3. **Sodium spikes on restaurant nights:** Observed fact: average daily sodium stays near ~2,100 mg on home-cooked days, but jumps above ~2,900 mg on cream pasta nights (1,580 mg in dinner alone).

### 4. Questions for my clinician
1. With 25-OH Vitamin D at 28 ng/mL while taking 2,000 IU/day of D3+K2 with breakfast, should we adjust the dose or retest in 90 days?
2. Given ApoB at 104 mg/dL and LDL-C at 118 mg/dL, would a 90-day trial raising daily fiber from 26 g to 35 g and lowering saturated fat make sense before discussing further options?
3. Does my ferritin of 44 ng/mL warrant any follow-up given normal B12 and folate, or is it fine for my baseline?
4. When should I retest Omega-3 Index and RBC Magnesium so the blood draw reflects a full 90–120 days of my current routine?

---

## Output B — Prompt 03 (Symptom → Plate → Lab Trace)

*Scale check from `get_check_ins`: all fuelOS scores run `0.0–1.0` where `1.0` = best/comfortable/none.*

### 1. Lowest check-in days found (last 21 days)
- **Energy & Mental Clarity dips (`energy: 0.45`, `cognitiveClarity: 0.50`, `cravings: 0.55` on 3 of 21 days):**
  - Every single dip occurred the morning **after** a `Double espresso (4pm)` entry (+150 mg caffeine at 16:00, pushing total daily caffeine from 190 mg to **340 mg**, above the 300 mg goal).
  - Matching check-in note: *"Wired at midnight after 4pm espresso, slept ~5.5h"*.
  - On all 18 days without a 4pm espresso, next-day `energy` averaged `0.80` and `cognitiveClarity` averaged `0.82`.
- **Digestive comfort dips (`bloating: 0.32`, `inflammation: 0.68` on 3 of 21 days):**
  - All 3 dips occurred on the exact evening `Creamy parmesan chicken pasta` was logged (980 kcal, 26 g saturated fat, 4 g fiber, 1,580 mg sodium).
  - Matching check-in note: *"Noticeable heaviness and bloating after cream pasta dinner"*.
  - On all 18 other days, `bloating` averaged `0.88` (comfortable).

### 2. 14-Day Self-Observation Test
1. **Caffeine cutoff before 13:00:** Keep morning cold brew (190 mg) and drop afternoon espresso for 14 days; watch whether `energy` and `cognitiveClarity` stay near `0.80+` with fewer next-day cravings.
2. **Swap heavy cream dinners:** Track whether `bloating` remains above `0.85` when replacing heavy-cream restaurant pasta, and share the log with your clinician if digestive discomfort persists on non-dairy meals.
