# Talk Plan: NIMBYdex — The Renewable Energy Graveyard

## Context

This is a data storytelling talk that starts with a simple, satisfying hypothesis (NIMBYs are killing renewables) and dismantles it to reveal something far messier: a systemic failure in British infrastructure planning. The emotional arc is detective fiction — the audience thinks they know the villain, then the real monster appears. The map and open dataset act as the payoff: "here's what I found, here's how you can go further."

The plan below is narrative-first. Each section has a single job.

---

## Narrative Arc

```
Hook (the graveyard)
  → The suspect (NIMBYs)
    → The data (REPD)
      → The tool (NIMBYdex map)
        → The crack in the theory (giant projects)
          → The real culprit (planning system / grid)
            → The evidence (stuck projects, grid queue)
              → The ML attempt (honest, incomplete — recruit the room)
                → The handoff (open dataset + map)
```

---

## Section 1 — The Graveyard (Hook)

**Job:** Land the scale of the problem emotionally before explaining anything technical.

**Beats:**
- Open on the map. Thousands of dead projects across the UK.
- Put a number on it: **6,584 MW of capacity lost since Jan 2022**. That's not a rounding error — that's equivalent to ~X coal plants / X million homes.
- Average project lived **334 days** before dying. These aren't pipe dreams — they got far enough to be tracked.
- **MW deployment by technology per year chart** — stacked or grouped bar chart: solar, onshore wind, offshore wind, other, broken down annually. This does two things at once:
  - Shows the actual deployment trajectory (where is the UK actually building?)
  - Makes the cancelled MW figure feel real by comparison — you can see what a gigawatt of solar looks like as a year's worth of progress, then point back to the graveyard number
  - If the data shows a stall or decline in certain technologies, let it speak — you don't need to editorialize yet
- One line: "I wanted to know who killed them."

**Tone:** Forensic. The audience should feel the weight of the number before they hear the word NIMBY.

---

## Section 2 — The Obvious Suspect (Hypothesis)

**Job:** Set up the hypothesis cleanly so the dismantling lands hard.

**Beats:**
- Define NIMBY crisply — organized, local opposition to developments.
- The numbers that make it feel like an open-and-shut case:
  - Wind power costs rise **10–29%** where NIMBY pressure is high.
  - **80% of EU renewable projects** stall due to local opposition.
- State the hypothesis explicitly: "NIMBYs are the root cause of renewable project failure in the UK."
- This is where most analyses stop. This talk doesn't.

**Tone:** Confident, then slightly conspiratorial — "let's check."

---

## Section 3 — The Evidence Locker (REPD Data)

**Job:** Explain the data source and why it's hard — build credibility, not boredom.

**Beats:**
- REPD: every UK renewable project since the 1990s, maintained by DESNZ.
- The catch: it's a mess. Inconsistent field definitions, council-by-council variation, human-entered free text, no unified schema.
- This is the forensic work nobody sees: cleaning data that was never designed to be analysed at scale.
- Keep this tight — 2–3 slides max. The audience needs to trust the data, not audit it.

**Tone:** Brief, honest about the ugliness. Show one example of a bad field if it's funny.

---

## Section 4 — The Tool (NIMBYdex V1)

**Job:** Show the thing. Make the audience want to use it.

**Beats:**
- Live demo or video: the interactive map at nimby.bemben.co.uk
- What it shows: every refused and withdrawn UK renewable project, plotted and searchable.
- The AI layer: Gemini scores each project (NIMBY Score, Petty Score, Political Leaning) and generates commentary.
- Show a good example: a genuinely petty refusal (Alan Tichmarsh / roundabouts).
- Show a bad example: AI called people "meatbags." Acknowledge limits quickly — move on.

**Tone:** Demo energy. Show the fun bits. Don't linger on tech stack.

---

## Section 5 — The Crack in the Theory (Large Projects)

**Job:** This is the pivot. Something doesn't add up.

**Beats:**
- While building NIMBYdex, some projects stood out not because they were cancelled — but because of how long they took.
- Case study: **Faw Side Community Wind Farm** — 315 MW, 45 turbines, **4.6 years to refuse**, **496 documents**.
- That's not a NIMBY pile-on. That's a planning system eating itself.
- Pull back to the dataset: look at projects by time-to-decision. The long tail is extraordinary.
- The hypothesis starts to wobble: if NIMBYs were the problem, why do approved projects also take years?

**Tone:** Slow realisation. "Wait a minute."

---

## Section 6 — The Real Shoggoth (Planning System + Grid)

**Job:** Name the actual villain. Make it feel appropriately huge and shapeless.

**Beats:**
- Introduce the framing: this isn't a NIMBY problem, it's a structural problem — a shapeless bureaucratic mass with no single face.
- **Two heads of the shoggoth:**
  1. **Planning bureaucracy** — no unified schema across councils, hundreds of documents per project, no standardised process. A 150 kW solar farm can generate the same paperwork as a 315 MW wind farm.
  2. **Grid connection queue** — projects that get approved can't connect. The queue to get an electrical connection stretches years. Ask anyone trying to build right now.
- The data backs this: majority of non-cancelled projects are sitting **under construction** or **accepted but awaiting connection** — not blocked by NIMBYs, blocked by the system.
- This is the section where the audience (especially practitioners) will nod hard.

**Tone:** Revelatory, a little angry, grounded in evidence.

---

## Section 7 — The ML Attempt (I Am Dumb, Please Help)

**Job:** Show honest, incomplete ML work — then hand the problem to the room.

**Beats:**
- "So naturally I thought: I'll just run some ML on this."
- Show what you tried: a model (or a few) to predict project cancellation likelihood from REPD traits.
  - Feature choices you made and why — technology type, planning authority, size, region, time in planning.
  - Show the outputs. Let them look a bit rough or inconclusive. That's the point.
- One or two specific examples where the model produced something interesting but you weren't sure what to make of it — a counterintuitive feature weight, an odd cluster, a result that didn't match your expectations.
- Name the limits honestly: "I'm a software engineer who has watched too many Kaggle tutorials. This data deserves a real analysis and I am not the person to do it."
- Hard pivot to the audience: **"But you might be."**
  - You're at a PyData conference. There are people in this room who know exactly what to do with this.
  - What questions would you ask of this data? What would you do differently?
  - Brief pause — genuinely invite a few responses if time allows. Even one or two hands changes the energy.

**Tone:** Self-deprecating but not apologetic. The incompleteness is the setup, not the failure. The audience should feel recruited, not pitied.

---

## Section 8 — The Handoff (Map + Open Dataset)

**Job:** Close with something the audience can use. Leave the door open.

**Beats:**
- Return to the map. It looks different now — not a graveyard of NIMBY victories, but a map of a system that keeps eating its own progress.
- Announce the open dataset: processed, cleaned REPD data, ready to analyse.
  - What it contains, how it was cleaned, what questions it's good for.
  - Where to get it / how to contribute.
- Two calls to action:
  1. Use the dataset. Build something. Find what I missed.
  2. If you're building in this space — share what you know about the grid queue. That's the part that's hardest to see from the data alone.
- Final line: "The interesting part isn't the AI. The interesting part is what the data shows us we've been ignoring."

**Tone:** Generous, open-ended. This is an invitation, not a conclusion.

---

## Timing Guide (40-minute talk)

| Section | Time |
|---|---|
| 1 — The Graveyard | 3 min |
| 2 — The Hypothesis | 4 min |
| 3 — The Data | 4 min |
| 4 — The Tool (demo) | 7 min |
| 5 — The Crack | 5 min |
| 6 — The Shoggoth | 7 min |
| 7 — The ML Attempt | 5 min (incl. ~1 min audience interaction) |
| 8 — The Handoff | 5 min |
| **Total** | **40 min** |

Adjust: cut Section 3 to 2 min and Section 7 to 3 min if running short. Sections 5 and 6 are the core — protect those.

---

## Slide Gaps to Fill

These are things mentioned in the narrative that may need new or strengthened slides:

- **MW by technology per year** — stacked/grouped bar chart from REPD operational data. X-axis: year, Y-axis: MW, series per technology (solar, onshore wind, offshore wind, other). Filter to operational/built projects only — this is deployment, not approval. Colour-code consistently with any other technology breakdowns in the talk.

- **Grid connection queue** — needs a dedicated slide with concrete numbers (queue length, average wait). Source from National Grid ESO data or practitioner quotes.
- **"Stuck projects" breakdown** — one chart: accepted/under construction vs cancelled, showing the non-NIMBY graveyard.
- **ML attempt** — show the model outputs you have, however rough. One or two charts is enough. The goal is to show honest work, not clean results — include something counterintuitive or uncertain as the hook for the audience question.
- **Open dataset** — a slide showing the data format, provenance, and access link.

---

## Tone Principles Throughout

- **Detective, not lecturer.** The audience should feel like they're solving it with you.
- **Show the mess honestly.** The data is ugly. The AI was sometimes wrong. That's part of the story.
- **Respect the audience's time.** Every section earns its place by advancing the theory.
- **End on action, not summary.** The last thing they remember should be the map and the dataset link, not a bullet-point recap.
