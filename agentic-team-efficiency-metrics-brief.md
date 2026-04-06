# Agentic Team Efficiency Metrics — Context Brief

## What we are building

We are adding new slides to an existing HTML presentation called "The Agentic Team — Reimagining Delivery in the Age of AI." The presentation makes the case that AI-enabled delivery teams of 2-5 people can replace traditional 8-12 person scrum teams by having each person orchestrate AI agents across multiple disciplines. The original presentation covers the team model, role consolidation, a "Human Power" unit of measurement, team configurations, and a closing CTA.

The new slides (currently slides 5, 6, and 7 in a 10-slide deck) focus on one specific gap: how do you actually measure the efficiency gains of agentic team members? This is the credibility layer that makes the rest of the presentation defensible rather than aspirational.

## The problem we identified

Traditional delivery teams have always struggled to measure what actually matters. Most organizations track activity metrics (story points, test cases written, deploys executed) because those are easy to count — they leave digital exhaust in tools like Jira, GitHub, and CI/CD pipelines. But activity metrics measure busyness, not impact.

The metrics that genuinely indicate whether a role is performing well — cycle time, downstream rework rate, defect detection rate, MTTR, on-time delivery rate, iteration cycles to approval — are either inconsistently tracked or not tracked at all. The further you move from engineering toward strategy, design, and coordination roles, the worse the measurement gets. Architects, PMs, and designers are largely measured on vibes.

This problem compounds in the agentic model. When one person orchestrates agents across development, QA, and DevOps, all the traditional activity metrics explode in volume because agents amplify output. PRs merged, test suites run, deploys executed — all go to infinity. Measuring an agentic engineer by PRs merged is like measuring a manager by emails sent. Volume becomes noise, and the old metrics become meaningless.

## What we figured out

### Step 1: Traditional role metrics — activity vs. impact

For each of the six traditional delivery roles (Software Engineer, Software Architect, QA Tester, DevOps Engineer, PM/PO/Scrum Master, UI/UX Designer), we identified:

- The top activity metrics that orgs actually track
- How those metrics are tracked (specific tools, reliability, adoption)
- The single impact metric that best indicates real performance
- How that impact metric is tracked (or more often, why it isn't)

The key findings per role:

| Role | Activity (what orgs track) | How tracked | Impact (what matters) | How tracked |
|------|---------------------------|-------------|----------------------|-------------|
| Software Engineer | Story points, PR throughput | Jira velocity, GitHub analytics | Cycle time | Git + CI/CD via LinearB/Sleuth — rare in mid-market |
| Software Architect | Design docs, tech debt scores | Confluence page counts, SonarQube | Downstream rework rate | Requires tracing Jira rework to ADRs — almost nobody does this |
| QA Tester | Test cases written, coverage % | TestRail/Zephyr, Istanbul/JaCoCo | Defect detection rate | Jira tagging (QA vs. production) — achievable but needs triage discipline |
| DevOps Engineer | Deploy frequency, provisioning time | CI/CD logs, rarely formal for provisioning | MTTR | PagerDuty/Opsgenie — data exists but "recovery" defined inconsistently |
| PM/PO/SM | Sprint completion, overhead hours | Jira sprint reports, Harvest/Toggl (rare) | On-time delivery rate | Jira/Smartsheet planned vs. actual — common but manipulated |
| UI/UX Designer | Screens per sprint, design system coverage | Figma history, Jira tickets | Iteration cycles to approval | Figma version history — observable but not tracked as KPI |

The pattern: engineering roles have decent measurement through tooling exhaust. Strategy, design, and coordination roles are largely unmeasured.

### Step 2: Why old metrics break in the agentic model

Three fundamental shifts make traditional metrics obsolete:

1. **"How busy are you?" → "Did the outcome stick?"** — Activity volume is meaningless when agents can generate infinite output. The question shifts to whether the output survived contact with reality.

2. **Per-role silos → End-to-end ownership** — When one person owns dev + QA + DevOps, measuring each silo separately is pointless. The metric must span the full pipeline.

3. **Volume = performance → Durability = performance** — A fast bad architectural decision or a high-coverage but shallow test suite creates more damage than value. What matters is whether the work held up.

### Step 3: New impact metrics for agentic roles

For each of the five agentic archetypes, we defined:

| Agentic Role | Absorbs | Noise (agent-amplified) | Signal (impact metric) | How to track |
|-------------|---------|------------------------|----------------------|-------------|
| Agentic Engineer | Dev + QA + DevOps | Agent tasks, PRs, deploys, test suites | Feature cycle time + quality gate | Git + CI/CD with QA pass rate and deploy stability as integrated gates. No rollback within 48h = clean. |
| Agentic Architect | System Arch + Tech Lead + Security | ADRs, code reviews, security scans, perf profiles | Decision durability | Correlate ADRs in Confluence to downstream rework/security/perf tickets in Jira. AI can auto-tag relationships. |
| Agentic PO/Designer | PO + UX + BA | Research reports, design concepts, specs, competitive analyses | Spec-to-build fidelity | Count clarification requests, design revisions, and scope changes post-handoff via Jira threads and Figma versions. |
| Agentic QA | Dedicated quality (larger teams) | AI-generated tests, visual regressions, perf benchmarks | Escaped defect cost | Production incidents (PagerDuty) weighted by severity and business impact. Sum of (severity x weight) per release. |
| Agentic Delivery Engineer | PM + SM + Release Mgmt | Auto-generated status reports, stakeholder updates | Delivery predictability index | Standard deviation of sprint completion rates over a rolling 6-sprint window. Jira already has the data. |

### The key insight

Some of these impact metrics were nearly impossible to track in the old model because they required correlating data across role boundaries (e.g., tracing an architectural decision through to implementation rework). In the agentic model, one person owns both sides of the correlation — which means AI doesn't just make people faster, it makes previously unmeasurable work measurable for the first time.

## How this fits in the presentation

The three new slides create a narrative bridge between slide 4 (role consolidation / Venn diagram) and slide 8 (Human Power metric):

- **Slide 5** — "We measured activity, not impact." Shows the six traditional roles in a 2x3 grid, each with activity metrics, tracking details, impact metric, and tracking reality. Establishes the baseline problem.

- **Slide 6** — "Old metrics break in the agentic model." The pivot slide. Shows three before/after shifts on the left and a visual funnel (activity noise → impact signals) on the right.

- **Slide 7** — "Each agentic role owns an end-to-end outcome." Maps each of the five agentic archetypes to their noise metrics and signal metric with inline tracking details. The Delivery Engineer card spans full width at the bottom.

This arc sets up the Human Power slide (slide 8) by giving the audience a concrete framework for what "10x" actually means — not 10x the activity, but dramatically better outcomes on the metrics that matter, measured by tooling that the agentic model itself enables.

## Design system notes

The presentation uses a specific design system: DM Serif Display for headings, DM Mono for labels/eyebrows, Instrument Sans for body text. Color palette uses `--paper` (#f5f3ee) backgrounds, `--ink` (#0e0f0d) text, `--rail` (#1a3a5c) for emphasis, `--ember` (#c94f1e) and `--sage` (#3d6b52) for eyebrow colors, and role-specific colors (sage green for engineers, rail blue for architects, gold for PO/designers, ember for QA, purple for delivery). Each agentic role has an SVG icon with concentric dashed circles representing the AI amplification field around a human core.

Slides use scroll-snap, reveal animations with staggered delays, and a fixed progress bar / nav dot system. New slides must match all of these patterns exactly.

## What might come next

- Adding a slide that shows the measurement toolchain visually (what tools feed into which metrics)
- Creating a client-ready version that strips internal Zeal branding for co-branded use with Livefront
- Building an interactive calculator that lets prospects input their team size and see projected efficiency gains
- Connecting this to the GitHub Copilot peer-reviewed study data that anchors the Human Power slide
