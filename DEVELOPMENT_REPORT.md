# 🏗️ Development Case Study: Building *Citation Needed: The Academic Career Simulator*

* **Live Deployment:** [https://bluebrazelton.com/citation-needed/](https://bluebrazelton.com/citation-needed/)
* **Repository:** [github.com/bluebrazelton-dotcom/citation-needed](https://github.com/bluebrazelton-dotcom/citation-needed)
* **Architecture:** Single-file HTML5 (`<canvas>`), Vanilla JavaScript, Tailwind CSS (CDN), Browser `localStorage`
* **Development Model:** Iterative AI-Collaborative Engineering (Scoping $\rightarrow$ Single-Shot Prototype $\rightarrow$ Multi-Discipline Expansion $\rightarrow$ Automated Telemetry & QA $\rightarrow$ Production Deployment)

---

## 1. Project Genesis & Pre-Build Scoping

The objective of this project was to evaluate how an AI coding collaborator (Gemini Argon) handles building a complete, playable browser-based incremental and active-management game from scratch—and to compare the workflow and output against parallel single-shot builds in Claude and ChatGPT.

Rather than jumping blindly into code generation, the build began with a three-question scoping phase to lock in the game design, mechanics, and aesthetic constraints:

1. **Tone & Satirical Philosophy:** Rather than cynical or punishing satire, the game was designed as an affectionate, humorous insider simulation of academic life—capturing the realities of graduate school, peer review, grant writing, and the tenure track for players both inside and outside higher education. Failure states (such as harsh peer reviews or rejected grant applications) were intentionally built as surmountable rites of passage rather than game-ending roadblocks.
2. **Active Gameplay Over Idle Waiting:** To avoid "second-tab syndrome" (where players abandon an idle clicker while waiting for energy bars to refill), the core loop was engineered around continuous active engagement: a precision sweet-spot timing bar, clickable room anomalies, and interactive *Revise & Resubmit* gatekeeper battles, paced for a complete playthrough from Undergrad to Endowed Chair in roughly **30–35 minutes**.
3. **Visual & Technical Direction:** A vibrant, modern pixel-art aesthetic rendered entirely through procedural HTML5 `<canvas>` drawing routines—requiring zero external image spritesheets—featuring an autonomous scholar sprite that physically runs between workstations and upgrades academic regalia with each promotion.

---

## 2. Iterative Engineering Timeline

### Phase 1: The Single-Shot STEM Prototype (*Bench to Chair*)
* Generated a complete, self-contained HTML5 application focused on a **Bench Scientist** in a wet lab environment.
* Implemented the 4-station floor layout (**Wet Bench**, **Manuscript Desk**, **NSF/NIH Grant Portal**, **Espresso Bar**), the 6-tier career rank progression, 5 visible lab equipment props (**Vortex Mixer** through **Cryo-EM Suite**), and 4 autonomous staff NPCs with rotating speech bubbles.
* Built the active sweet-spot timing bar (scaling up to an **8x Combo**), interactive **Reviewer #2** decision letters, and clickable room anomalies (unbalanced centrifuges, `-80°C` freezer alarms, and seminar pizza).

### Phase 2: Multi-Discipline Expansion (4 Complete Paths)
* Expanded the architecture from a single STEM path to four full academic disciplines:
  1. **🧬 Bench Scientist (STEM)**
  2. **📋 Social Scientist**
  3. **📜 Historian**
  4. **⚖️ Legal Scholar**
* Engineered isolated `localStorage` state snapshots per discipline so players can switch paths at any time via the **Switch Path** modal without losing progress.
* Designed custom procedural pixel-art rooms, 20 unique equipment props, 16 staff archetypes, custom currency labels, and discipline-specific gatekeepers (such as the *Epistemological Gatekeeper* in Social Science, the *1743 Lyon Parish Register Rival* in History, and the *2L Executive Footnote Editor* in Law Review).

### Phase 3: Embedded QA Bot & Mathematical Pacing Audit
* Because an LLM cannot visually playtest a live browser canvas in real time, we engineered an **in-game Automated QA, Monte Carlo Simulator, and Visual AI Bot Suite** alongside a static mathematical balance audit.
* **Bottleneck Discovery & Resolution:** Telemetry revealed a mid-to-late-game pacing slowdown between Rank 4 (*Assistant Professor*) and Rank 6 (*Endowed Chair*) caused by steeper equipment cost curves relative to linear grant payouts.
* **Applied Economy Fixes:**
  * Introduced an exponential career stage prestige multiplier ($1.35^{\text{stage}}$) compounding with rank base multipliers.
  * Added a **Publication $\rightarrow$ Grant Synergy** where each published work increases grant approval odds by **+4%** (from a 25% baseline up to a **90% cap**) and boosts grant payout size by **+12%**.
  * Standardized equipment cost scaling to `1.55x` and staff scaling to `1.45x`, while adding a **-5% manuscript data cost discount** (up to 50% off) and passive citation generation (`+18/s` and `+75/s`) to Tier 4 and Tier 5 equipment upgrades.

### Phase 4: True Disciplinary Asymmetry & High-Speed Physics Polish
* **Disciplinary Asymmetry:** Replaced uniform cross-path math with unique passive mechanics and strategic pacing profiles for each discipline (see Section 3 below).
* **Sub-Stepped Delta-Time Physics (`1x` to `50x`):** Clamped frame delta-time and implemented physics sub-stepping ($\Delta t \le 0.02\text{s}$) so player walking, NPC wandering, and timing bar sweeps never overshoot or jitter when running the Visual AI Bot at `50x` speed.
* **Canvas Viewport Expansion & Clamping:** Expanded the `<canvas>` resolution to `860x440` and added `clampBoxToCanvas()` across all speech bubbles, floating text particles, and anomaly labels to prevent edge clipping near outer workstations.
* **Promotion Alert UX:** Added a pulsing top-bar promotion alert button, celebratory canvas banner, and particle confetti burst when rank requirements are met.

### Phase 5: Rebranding & Production Deployment
* Rebranded the simulator to **Citation Needed: The Academic Career Simulator**.
* Hid the developer QA & Bot button behind a secret keyboard shortcut (**`Shift + Q`**) to keep the public UI clean while retaining full telemetry access for live demos.
* Configured account-level GitHub Pages custom domain routing (`bluebrazelton-dotcom.github.io` $\rightarrow$ `bluebrazelton.com/citation-needed/`) and Open Graph metadata.

---

## 3. Disciplinary Asymmetry & Mechanics Matrix

While all four disciplines are balanced to complete within a **~31–34 minute** active play window, each path features a distinct mechanical identity:

| Discipline Path | Custom Pixel Environment | Primary Currency | Signature Passive Mechanic | Strategic Gameplay Profile |
| :--- | :--- | :--- | :--- | :--- |
| **🧬 Bench Scientist** | Sterile wet lab with yellow/black safety hazard stripes | Raw Data | **Lab Automation Synergy** | Every hired staff member boosts equipment click and passive output by **+5%**; features a `1.14x` equipment power curve and a `1.22x` R01 grant ceiling. |
| **📋 Social Scientist** | Warm hardwood qualitative & mixed-methods studio | Field Notes | **Mixed-Methods Triangulation** | Hitting sweet-spot timing combos generates immediate bonus Foundation Grant funding (**35%** of click power) and awards **+15%** bonus peer-review citations. |
| **📜 Historian** | Mahogany archive with a crimson Persian runner rug | Archival Finds | **Archival Monograph Gravitas** | Drafting a monograph requires deeper archival work (`20%` per step instead of `25%`), but each published book yields **1.5x Citations** and permanently compounds passive output by **+20%**. |
| **⚖️ Legal Scholar** | Constitutional chambers with checkered marble floors | Case Briefs | **Expedited Law Review Preemption** | Articles draft **28% faster** (`+32%` per step) and law review acceptances award **+35% bonus Citations** plus immediate Clinic Stipends. |

---

## 4. Built-In Quality Assurance & Telemetry Architecture (`Shift + Q`)

Pressing **`Shift + Q`** at any time during gameplay opens the embedded **32-Point QA & Bot Suite Drawer**, which provides three verification tools:

1. **4-Path Headless Monte Carlo Pacing Simulator (`simulateSingleDisciplineRun`):** Runs a deterministic background simulation of an active human player (~3 actions/second, refilling caffeine at `<40%`, greedily purchasing upgrades, and completing peer review) across all four disciplines in under a second, outputting a stage-by-stage completion time table.
2. **Visual AI Auto-Play Bot (`runVisualBotTick`):** An autonomous agent that physically plays the game on the live canvas at `1x`, `10x`, `25x`, or `50x` speed—walking between stations, clicking room anomalies, answering Reviewer #2 prompts, purchasing upgrades, and triggering promotions.
3. **32-Point Automated Unit & Integrity Checklist (`runUnitTests`):** Verifies state isolation, equipment prop bounding boxes (`y + h <= 245` so props never overlap workstation hitboxes at `y >= 258`), canvas edge clamping (`860x440`), disciplinary asymmetry math, and anomaly timer cleanup on path switches.
