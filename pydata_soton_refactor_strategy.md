# PyData Southampton Refactor Strategy
## NIMBYdex → Clean Energy Graveyard

**Talk description:** An open-source Python pipeline & interactive web visualisation that transforms the REPD into a story about what's blocking the energy transition.

**Audience:** Intermediate Python users, data scientists, civic/climate tech interested. No prior knowledge of energy policy or LLMs required.

**Core shift from current slides:** Less "fun side project with snarky AI", more "public good tool with honest technical depth." The Pokémon framing can stay lightly but can't carry the talk for a PyData crowd.

---

## Narrative Map Against Current Slides

The refactor plan defines 8 sections. Here's how each maps to what currently exists.

| Refactor Section | Status in slides.md |
|---|---|
| 1 — The Graveyard (hook) | **Partial** — numbers exist but not opened with |
| 1b — Years breakdown (how projects shifted) | **Missing** — data available, needs slides |
| 2 — The Suspect (NIMBY hypothesis) | **Present** — "Why's a NIMBYs" slide |
| 3 — The Evidence Locker (REPD) | **Present** — "The Foundational Data" slide |
| 4 — The Tool (NIMBYdex demo) | **Present** — NIMBYdex V1 + Live Demo + Tech Stack |
| 4b — Does the NIMBY analysis actually hold? | **Missing** — data analysis bridge before the crack |
| 5 — The Crack (large projects) | **Present** — Faw Side slide |
| 6 — The Real Shoggoth | **Present** — Shoggoth slide |
| 7 — The ML Attempt | **Missing** |
| 8 — The Handoff (open dataset + repo) | **Missing** |

---

## Step-by-Step Changes

### Step 1 — Retitle and reframe the opening slide

**Change:** Update the cover slide title and subtitle.

```
Current:  # NIMBYdex / Gotta ~~Build~~ 'Em All
Proposed: # The Clean Energy Graveyard / How Britain buries its renewable future — and what open data reveals
```

Keep NIMBYdex as the name of the tool; the *talk* is the Graveyard framing. The Pokémon joke survives but isn't the first thing the audience reads. Adjust the cover image if one more appropriate exists.

---

### Step 2 — Move the hook to slide 1 (currently buried)

**Add a new slide block immediately after the cover/about-me slides.** This is Section 1 from the refactor plan and doesn't exist as a dedicated opening beat.

Content to add:
- Open on the map (static screenshot or short video clip) before any explanation
- The number: **3,800+ cancelled projects** (align with the PyData description; the 6,584 MW figure can appear as a secondary stat)
- Average project lifetime before cancellation: **334 days**
- One closing line: "I wanted to know who killed them."

Then immediately follow with the **years breakdown slide** (data available — this is real, not a placeholder):
- A MW-by-technology-per-year chart (stacked/grouped bar: solar, onshore wind, offshore wind, other — filtered to operational/built projects, X=year, Y=MW)
- A cancellations-over-time layer or secondary chart showing how the shape of project failure has shifted — which technologies started declining, whether the rate is accelerating
- Let the chart speak without editorial. If there's a visible stall or decline in certain technologies, point at it and move on — "this is what 334 average days looks like at scale."
- This makes the graveyard number feel real by giving it a shape across time, not just a single total

This block should be 3–4 slides total. The years breakdown data is already available — just needs formatting into slides.

---

### Step 3 — Remove the LLM/Agents/RAG/MCP definitions slide

**Delete** the "LLM, Agents, RAG, & MCPs" definitions slide entirely.

Why: A PyData audience doesn't need one-liner definitions of LLMs and agents. This slide reads as filler and signals the wrong level. The MCP section later in the talk explains it in context — that's sufficient.

---

### Step 4 — Tighten the "About Me" slide

**Change:** Replace "mostly: a year of silly side projects" energy with framing that positions this as civic tech / public good work. The AI startup and wind turbine experience are directly relevant — lead with those. The "weird little tech art projects" line can stay but shouldn't be the first bullet.

Suggested reorder:
1. Led data analysis for large industrial decarbonisation projects
2. Developer in AI start-ups (CCTV object recognition, wind turbine timeseries modelling)
3. Software engineer & creative technologist

---

### Step 5 — Reframe the NIMBY hypothesis slide

**Change (not delete):** "Why's a NIMBYs" currently ends at the statistics and implies this is the whole story. Add a beat that signals the audience we're about to check the hypothesis — "this is where most analyses stop."

The `bash grep` joke can stay; it's earned. But add one more v-click after the bullet list:

```
- This is where most analyses stop. This talk doesn't.
```

---

### Step 6 — Expand the REPD data slide

**Change:** "The Foundational Data" slide is correct but thin. Add:

- A brief visual of what the raw CSV looks like (a screenshot of a few rows, ideally showing inconsistent fields and blanks)
- One concrete funny example of a bad/ambiguous field
- A note that this data covers every UK renewable project since the 1990s, maintained by DESNZ

This slide doesn't need to grow much — keep it to 2–3 slides max. The goal is credibility, not audit.

---

### Step 7 — Add a GeoPandas / spatial analysis slide

**Add new slide** between REPD data and the NIMBYdex V1 slide. The PyData description explicitly mentions GeoPandas as a key tool — it's currently invisible in the slides.

Content:
- How the pipeline uses GeoPandas to convert REPD coordinates into spatial objects
- One code snippet or visual showing a .sjoin() or boundary overlay (e.g., matching project coordinates to council/constituency boundaries)
- Why spatial analysis matters here: planning authority attribution, regional patterns, identifying which councils appear most in the graveyard

Keep this tight — one slide with a code example or a map output.

---

### Step 8 — Retitle and reframe the NIMBYdex V1 slide

**Change:** The subtitle "(NON-NINTENDO RELATED)" is charming but undersells for PyData. Change to emphasise the public good angle:

```
Current:  Cancelled Project Tracker (NON-NINTENDO RELATED)
Proposed: Cancelled Project Tracker — open data, open source
```

Also add a card or line about the **pipeline** being open-source and accessible — this is a key takeaway from the talk description.

---

### Step 9 — Trim the MCP section to the essentials

**Keep:** The "Model Context Protocol — Why?" motivation slide and the magic-move code snippet (it's the best pedagogical moment in the current deck).

**Change:** Remove or drastically shorten the "Tech Stack With MCP (TBD)" mermaid diagram slide — it's still marked TBD and is dense without adding narrative value. Either complete it or cut it.

**Rename the section framing:** MCP should be introduced as "how the pipeline talks to the AI enrichment layer" rather than as a standalone technology explainer.

---

### Step 9b — Add the NIMBY data analysis bridge (new slides)

**Add a new slide block** after the AI good/ugly slides and before the Shoggoth. This is the moment where the hypothesis gets tested against the actual data — the audience has seen the tool, seen some examples, and now you show them what the numbers actually say.

This is a short section (2 slides max) whose only job is to make the pivot to the Shoggoth feel earned rather than asserted.

Content:
- One chart or breakdown: of the projects categorised as refused/withdrawn, what fraction actually cite local objection as the primary reason? What fraction cite other reasons — grid connection, financial viability, planning authority delays?
- The data analysis doesn't need to be exhaustive. A simple bar chart of cancellation reasons (bucketed from REPD free-text fields or the AI enrichment layer) is enough.
- If the NIMBY categorisation from NIMBYdar is usable here: what does the distribution of "NIMBY scores" across refused projects look like? Is it concentrated or spread thin?
- The point to land: **NIMBYs account for a real but surprisingly small fraction of the cancellations at scale.** The outliers that get press attention are not representative of the graveyard.
- Close with a question, not a conclusion: "So if it's not mostly NIMBYs — what is it?"

This slide data comes from the same NIMBY analysis work already done — this is surfacing the findings in the narrative, not new analysis. Frame it as "here's what I found when I actually looked."

---

### Step 10 — Add Section 7: The ML Attempt (new slides)

**Add a new slide block** after the Shoggoth/Faw Side section. This is entirely missing and is a core PyData audience hook.

Content (3–4 slides):
- "So naturally I thought: I'll just run some ML on this."
- What was tried: model(s) to predict project cancellation likelihood from REPD traits
  - Features used: technology type, planning authority, size/MW, region, time in planning
  - Show whatever outputs exist — rough is fine, that's the point
- One or two counterintuitive findings or things the model couldn't explain
- Honest limits: "I'm a software engineer who has watched too many Kaggle tutorials. This data deserves a real analysis."
- Hard pivot: **"But you might be."** Directly address the PyData audience. What questions would they ask? What would they do differently?
- Leave space for 1–2 audience responses if time allows.

This section needs real outputs from an ML attempt on the REPD data — if these don't exist yet, placeholder slides with "TBD — show model outputs here" are fine to draft now.

---

### Step 11 — Add Section 8: The Handoff (new slides)

**Add a closing slide block** before the final "thanks" slide. Currently the talk jumps from Shoggoth/future improvements straight to a closing slide — there's no payoff beat.

Content (3–4 slides):

**Slide A — Return to the map**
- Show the map again. It looks different now — not a graveyard of NIMBY victories, but a map of a system eating its own progress.
- One line of commentary, no more.

**Slide B — Show the open source repo (concrete, not abstract)**
- Show the actual GitHub repository: README, folder structure, or a key notebook
- What the pipeline contains: REPD ingestion, cleaning steps, GeoPandas spatial joins, Gemini enrichment
- How to run it: one-command install or a brief code snippet showing entry point
- This is the most practical slide in the deck for a PyData audience — make it scannable from the back of the room (large font, minimal words)
- Include the repo URL and/or a QR code

**Slide C — The open dataset**
- What the cleaned dataset contains: fields, schema, how it differs from raw REPD
- Where to access it (link / QR code)
- What it's good for: cancellation analysis, spatial clustering, authority-level patterns, timeline modelling

**Slide D — Calls to action**
1. Use the dataset. Build something. Find what I missed.
2. If you're building in this space — share what you know about the grid queue.
3. If you want to contribute to the pipeline — PRs open.

- The final statement slide (currently "AI isn't the interesting part...") is the right closer and should stay — move it here, after the calls to action.

---

### Step 12 — Replace the "Future Improvements" slide

**Remove** the current "Future Improvements" slide — it reads as a personal to-do list and doesn't belong in a PyData talk closing. The "NIMBY Trainer" and "Alan Tichmarsh card" are fun but undercut the civic tech seriousness at exactly the wrong moment.

Replace with the Section 8 handoff content above (open dataset + calls to action).

---

### Step 13 — Update the closing slide

**Change:** The final slide lists "total project cost: £3.70" — this works for a lighthearted meetup but may land oddly at PyData. Keep it if the tone has been established, but ensure the **primary CTA is the dataset/tool link**, not the substack or LinkedIn.

Add: a slide showing the **data format/schema** and access link for the open dataset. This is a concrete deliverable the audience can walk away with.

---

## What Stays Unchanged

- **"What's a NIMBY?" slide** — clean definition, needed for context, keep as-is.
- **Faw Side Community Wind Farm** slide — strong case study, core narrative beat, keep.
- **"The Good" / AI output examples** slide — the planning objection quotes are excellent and the Alan Tichmarsh example is the best single moment in the current talk. Keep both.
- **"Not Quite AGI: The Ugly"** slide — the meatbags / "moons NIMBY" examples humanise the AI section well. Keep.
- **The MCP code magic-move** — best technical demonstration in the deck. Keep.
- **The Shoggoth slide** — the framing works and it's a good image. Keep as the pivot moment.
- **The "AI isn't the interesting part" statement slide** — correct closing line. Keep, just move it to sit after the open dataset reveal.

---

## New Assets Required

| Asset | Section | Status | Notes |
|---|---|---|---|
| Years breakdown chart (cancellations + deployments over time) | Section 1b | **Available** | Shape of how project types/outcomes have shifted; needs formatting into slides |
| MW by technology/year bar chart | Section 1 | **Available** | Solar / onshore wind / offshore wind / other, built projects only |
| Static map screenshot or short clip | Section 1 | Needs capturing | Opening hook — the graveyard at a glance |
| Raw REPD screenshot (a few rows) | Section 3 | Needs capturing | Show ugly/inconsistent fields |
| GeoPandas code snippet or output | Step 7 | Needs writing | `.sjoin()` or boundary overlay example |
| NIMBY analysis breakdown chart | Step 9b | **Available** | Cancellation reason distribution / NIMBY score spread — surfaces existing analysis in narrative |
| ML model output charts | Section 7 | TBD | Whatever exists — rough is intentional |
| "Stuck projects" breakdown chart | Section 6 | Needs building | Accepted/under construction vs cancelled — shows non-NIMBY graveyard |
| Grid connection queue slide | Section 6 | Needs building | Queue length, average wait — source from National Grid ESO data |
| Open source repo screenshot | Section 8 | **Available** | README / folder structure / entry point — large font, scannable |
| Open dataset schema/access slide | Section 8 | **Available** | Format, provenance, link, QR code |

---

## Slide Count Delta

| | Current | After refactor |
|---|---|---|
| Remove | — | LLM definitions, Future Improvements, TBD MCP diagram |
| Add | — | Hook/graveyard (3–4), years breakdown (1–2), NIMBY analysis bridge (2), GeoPandas (1), ML attempt (3–4), Handoff/repo/dataset (3–4) |
| Net change | ~22 slides | ~30–32 slides |

Fits a 40-minute talk per the timing guide in the refactor plan. If trimming is needed, cut GeoPandas to a single code callout on an existing slide, and compress the ML attempt to 2 slides rather than 4.

---

## Key Framing Shifts (Talk Description → Slides)

| Talk description says | Current slides say | Fix |
|---|---|---|
| "Open-source Python pipeline" | Barely mentioned | Add pipeline framing to opening and tech stack |
| "GeoPandas for spatial analysis" | Not present | Add Step 7 slide |
| "Techniques for messy government data" | One thin REPD slide | Expand Step 6 |
| "AI for public good" | "Mostly a year of silly side projects" | Adjust About Me + retitle opener |
| "Practical API patterns at scale" | MCP section exists but framed as tech | Reframe as "how to enrich datasets with APIs" |
| "Human stories, not statistics" | Faw Side, AI quotes | Already present — reference explicitly in closing |
| "How to collaborate on open-source projects" | Not present | Show the actual repo in the Handoff — README, structure, PR-open CTA |
| "Practical patterns for using APIs to enrich datasets" | MCP section but abstract | NIMBY analysis bridge: show what the enrichment produced at scale, not just how it works |

---

