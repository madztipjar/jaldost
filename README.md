# JalDost — Clean Water Safety Agent 💧

An **agentic AI assistant** that turns raw village water-test readings into a
safety verdict, an action plan, and a bilingual field report — in under a
minute, on a low-end phone, **fully offline**.

Built for the **Code for a Billion — Bharat Agentic-AI Hackathon 2026**
(Code for India) · Track: **Health** · Built with **AgentFoundry (AF)**,
the official IDE.

## The problem

- **600 million** people in India face high-to-extreme water stress, and
  **~200,000 deaths every year** are attributed to inadequate access to safe
  water (NITI Aayog, Composite Water Management Index).
- Groundwater in parts of **387 districts** exceeds nitrate limits and parts
  of **276 districts** exceed fluoride limits (Central Ground Water Board).
- Under the Jal Jeevan Mission, village women and frontline workers already
  test water sources with Field Test Kits (FTKs) — but a raw number means
  nothing without the official standard, the health meaning, and the next
  action. Contaminated sources keep being used because nobody at the point
  of testing can interpret the result.

## What JalDost does

A frontline health worker (ASHA/ANM) or Village Water & Sanitation Committee
member enters 7 FTK readings — pH, TDS, turbidity, nitrate, fluoride, iron,
coliform. The **agent** then works autonomously through a visible
perceive → reason → act loop, calling discrete tools:

1. **`perceive`** — validates the readings and *reflects on missing data*:
   untested parameters are flagged and the verdict is marked provisional.
2. **`lookup_standards`** — loads the BIS **IS 10500:2012** drinking-water
   limits (acceptable & permissible) from its knowledge base.
3. **`assess_parameter`** — classifies every reading OK / CAUTION / UNSAFE
   with a plain-language explanation of the health harm.
4. **`compute_risk`** — aggregates a weighted risk score and overall verdict.
5. **`plan_remediation`** — plans immediate household actions and
   source-level fixes, worst risk first, plus a retest schedule.
6. **`draft_report`** — writes a bilingual (English + Hindi) field report
   ready to forward to the PHC medical officer and Gram Panchayat.

Every tool call is shown in an on-screen **agent reasoning trace**, so the
worker — and any auditor — can see exactly how the verdict was reached.

## Run it

No build step, no server, no API key. It is a static web app:

```bash
# Option 1: just open the file
open index.html            # or double-click it

# Option 2: serve locally
python3 -m http.server 8000
# then visit http://localhost:8000
```

Try the three built-in sample villages (safe source, fluoride-belt source,
contaminated well), or enter your own FTK readings. Leave a field blank to
watch the agent flag the data gap itself.

## Files

| File | Purpose |
|---|---|
| `index.html` | The web app (UI + wiring) |
| `agent.js` | The agent engine: knowledge base, tools, reasoning loop (pure JS, also testable in Node) |
| `README.md` | This file |
| `LICENSE` | MIT |

Smoke-test the engine headlessly:

```bash
node -e "const {runWaterSafetyAgent}=require('./agent.js'); \
const r=runWaterSafetyAgent({source:{name:'Handpump 3',village:'Rampur',district:'Nagaur',type:'Handpump',tester:'ASHA'}, \
readings:{ph:6.9,tds:780,turbidity:7,nitrate:68,fluoride:0.8,iron:0.45,coliform:'present'}}); \
console.log(r.risk, r.report)"
```

## Design choices

- **Zero-dependency & offline-first:** rural connectivity is patchy and the
  users' phones are low-end, so the agent is deterministic, explainable and
  runs entirely client-side. No citizen data ever leaves the device.
- **Grounded in official standards:** every verdict cites BIS IS 10500:2012
  acceptable/permissible limits — the same standard Indian labs test against.
- **Fits existing public infrastructure:** designed around the Jal Jeevan
  Mission's FTK programme and the ASHA/PHC escalation chain, not a parallel
  system.

## Roadmap

- Photo-based FTK strip reading (camera → readings).
- District-level dashboard aggregating anonymised source verdicts for
  public-health surveillance.
- More languages (the report generator is structured for i18n) and more
  parameters (chloride, hardness, arsenic).

## License

MIT — released open-source so any NGO or government body can adopt it.
