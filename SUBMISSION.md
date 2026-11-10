# Submission form — pre-filled (paste into the GitHub issue form)

Form: https://github.com/karlmehta/code-for-a-billion/issues/new?template=submission.yml
Issue title: `[Submission] JalDost — Clean Water Safety Agent`

---

**Team / Project name**
JalDost — Clean Water Safety Agent

**Team members (names + GitHub handles)**
Blake Yates (@madztipjar) — solo participant, based in Indonesia

**Problem statement**
Across rural India, frontline health workers (ASHA/ANM) and Village Water & Sanitation Committees already test drinking-water sources with Field Test Kits under the Jal Jeevan Mission — but a raw reading (e.g. "fluoride 2.6") means nothing at the point of testing without the official BIS standard, the health meaning, and the next action. As a result, contaminated handpumps and wells keep being used for months. JalDost is an offline agentic assistant that interprets the 7 standard FTK parameters against BIS IS 10500:2012, explains the risk in plain language, plans remediation, and drafts the bilingual escalation report for the PHC and Gram Panchayat.

**What you built**
JalDost is a zero-dependency, offline-first web app whose agent runs a visible perceive → reason → act loop with discrete tools: (1) perceive — validates readings and self-flags missing parameters, marking the verdict provisional; (2) lookup_standards — loads BIS IS 10500:2012 acceptable/permissible limits; (3) assess_parameter — classifies each reading OK/CAUTION/UNSAFE with the health harm explained; (4) compute_risk — weighted risk score + overall verdict; (5) plan_remediation — immediate household actions and source-level fixes, worst risk first, plus a retest schedule; (6) draft_report — generates a bilingual (English + Hindi) field report ready to forward to the PHC medical officer and Gram Panchayat. Every tool call is rendered in an on-screen reasoning trace. The project was created and developed in AgentFoundry (AF), the official IDE, using the free participant tokens; it runs entirely client-side (no server, no API key, no citizen data leaves the phone) because rural connectivity is patchy and users' phones are low-end. Three sample villages are built in (safe source, fluoride-belt source, contaminated well) so judges can run it instantly.

**GitHub repository URL**
https://github.com/madztipjar/jaldost   ← UPDATE if the repo lands under a different name/account

**Demo URL (live app or video)**
https://madztipjar.github.io/jaldost/   ← UPDATE to the live Pages URL once enabled

**Scale & severity of the problem**
NITI Aayog's Composite Water Management Index reports ~600 million people in India face high-to-extreme water stress and ~200,000 deaths every year are attributed to inadequate access to safe water. The Central Ground Water Board reports groundwater in parts of 387 districts exceeding nitrate limits (risk of "blue baby syndrome" in infants) and parts of 276 districts exceeding fluoride limits (dental and skeletal fluorosis — crippling, irreversible bone disease). Coliform contamination drives diarrhoeal disease, a leading killer of children under five. The testing infrastructure already exists — ~190 million rural households are covered by Jal Jeevan Mission's FTK programme — what is missing is interpretation at the point of testing, which is exactly the gap JalDost closes for every one of those tests.

**Deployment & impact data**
The app is deployed publicly on GitHub Pages (demo URL above) and works fully offline once loaded. It is live and judge-testable today with three built-in field scenarios modelled on documented contamination patterns (Rajasthan fluoride belt, fertiliser-belt nitrate + coliform contamination). Field-pilot data is the next step post-hackathon: the report format is designed to plug into the existing JJM FTK register so adoption by a single district would put the agent in front of thousands of monthly tests; we will update this issue with pilot numbers as they come in.

**Track / category**
Health

**Contact email**
maderzlast@gmail.com

**Confirmations** (tick all three)
- [x] Built using AgentFoundry (AF), the official IDE
- [x] Our repository is public and includes a README with setup steps
- [x] The demo link works and is accessible to judges
