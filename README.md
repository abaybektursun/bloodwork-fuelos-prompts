# Bloodwork + fuelOS MCP Prompt Pack

Your blood panel shows where your markers landed twice a year. It does not show what you ate, which supplements you actually took, or how you felt on Tuesday afternoon between draws.

This open-source prompt pack pairs **your bloodwork** (via the Function Health connector or any exported lab PDF from Quest, LabCorp, InsideTracker, or Superpower) with **your daily intake log in [fuelOS](https://fuelos.site/connect?ref=bloodwork-pack)** inside a single Claude or ChatGPT thread.

> **Informational use only.** Every prompt in this pack organizes your own records for personal review and clinician visits. None of these prompts diagnose conditions, prescribe treatments, or replace a licensed physician.

---

## Setup (2 minutes)

### Option A: Live Dual-Connector Mode (Function Health + fuelOS)

Works in **Claude** (web/desktop) and **ChatGPT**:

1. **Connect Function Health**
   - In Claude: `Settings → Connectors → Browse Connectors → Function Health` (or custom connector URL `https://services.functionhealth.com/ai-chat/mcp`).
   - In ChatGPT: link Function Health in `Settings → Apps & Connectors` (or Health).
2. **Connect fuelOS** (read-only over OAuth 2.1 + PKCE)
   - Search **fuelOS** in the directory, or add custom connector URL:
     ```text
     https://api.fuelos.site/mcp
     ```
   - Sign in with the Apple account you use in the fuelOS iOS app. Full setup guide: [fuelos.site/connect](https://fuelos.site/connect?ref=bloodwork-pack).
3. **Open one chat** with both connectors enabled and paste any prompt below.

### Option B: Lab PDF + fuelOS Mode (Quest, LabCorp, InsideTracker, Superpower, or Function PDF)

1. Connect **fuelOS** (`https://api.fuelos.site/mcp`) in Claude or ChatGPT.
2. Download your lab report PDF (for Function Health: `my.functionhealth.com/documents` → *Lab result of record*).
3. Drag the PDF into your chat and paste any prompt below.

---

## The 6 Prompts

| # | Prompt | What it compares | File |
|---|---|---|---|
| **1** | **Biomarker-to-Plate Gap Audit** | Flagged labs vs. 21–30 day food intake (39 nutrients) and supplement stack | [01-biomarker-to-plate-gap-audit.md](prompts/01-biomarker-to-plate-gap-audit.md) |
| **2** | **Supplement Stack Reality Check** | Before/after blood panels + active/paused stack doses + daily check-ins | [02-supplement-stack-reality-check.md](prompts/02-supplement-stack-reality-check.md) |
| **3** | **Symptom → Plate → Lab Trace** | Low check-in days (energy, clarity, bloating, inflammation, cravings, skin) vs. meals and biomarkers | [03-symptom-plate-lab-trace.md](prompts/03-symptom-plate-lab-trace.md) |
| **4** | **90-Day Pre-Retest Experiment Brief** | 1–2 out-of-range markers → clean daily intake targets to test before your next draw | [04-90-day-pre-retest-brief.md](prompts/04-90-day-pre-retest-brief.md) |
| **5** | **1-Page Clinician Visit Prep** | Neutral summary of lab flags, 30-day averages, active doses, check-in trends, and 5 questions for your doctor | [05-clinician-one-page-prep.md](prompts/05-clinician-one-page-prep.md) |
| **6** | **Data Quality & Bias Audit** | Checks logging gaps, hand-corrected vs. estimated meals, and sample size before you trust a pattern | [06-data-quality-and-bias-audit.md](prompts/06-data-quality-and-bias-audit.md) |

---

## See a Real Worked Example

Before connecting your own data, inspect what the output looks like:

- Synthetic lab panel: [examples/synthetic-function-panel.md](examples/synthetic-function-panel.md)
- Worked output (Prompts #1 and #3 run against a 21-day fuelOS log): [examples/sample-output.md](examples/sample-output.md)

---

## Guardrails Built Into Every Prompt

1. **Zero invented numbers:** Every prompt requires the assistant to state exact date ranges, days logged, and raw averages returned by fuelOS tools before drawing comparisons.
2. **Check-in polarity safety:** fuelOS stores all 8 check-in dimensions on a `0.0–1.0` scale where `1.0` is always better (`bloating: 1.0` = comfortable, `0.0` = severe). Each prompt reminds the model not to invert symptom scores.
3. **Unit discipline:** Prompts read dietary intake from `get_daily_intake` and `get_nutrient_trends` (where sodium is `sodium_mg`) rather than mixing Apple Health units (`get_health_metrics`, where sodium is in grams).
4. **Clinician-first framing:** Outputs end with specific questions to review with a licensed healthcare provider.

---

## Get fuelOS

- Setup & MCP directory links: [fuelos.site/connect](https://fuelos.site/connect?ref=bloodwork-pack)
- iOS App Store: [Download fuelOS](https://apps.apple.com/us/app/fuelos/id6756439581?pt=126258939&ct=mcp_bloodwork_pack&mt=8)

## License

MIT. Fork it, adapt the prompts for your own lab provider, or open a PR to add new non-diagnostic workflows.
