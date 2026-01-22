# JobShock Navigator (Hex-a-Thon Submission)

**JobShock Navigator** is an early-intervention decision tool that detects labor-market stress signals using Google Trends, then recommends resilient job transition options tailored to the user’s occupation.

Instead of reacting *after* layoffs happen, this project helps users **pivot earlier** using weak signals that often appear before official unemployment statistics change.

---

## What it does

1. **Collects early signals** from Google Trends search interest:
   - `laid off`
   - `unemployment benefits`
   - `jobs near me`

2. **Computes a weekly Job Shock Score**
   - Uses week-to-week deltas (changes)
   - Applies simple, interpretable weights
   - Smooths noise with a 3-week moving average

3. **Classifies current labor-market risk**
   - `CALM` / `WATCH` / `ALERT`

4. **Generates personalized “escape routes”**
   - User enters any job title (no fixed category required)
   - The tool maps it into a job family (retail, office, manufacturing, etc.)
   - Recommendations change based on both:
     - current risk status
     - the user’s occupation

---

## Why this matters (Problem → Insight → Action)

**Problem:** Most people react too late after layoffs happen.  
**Insight:** Early signals (search interest spikes) can reflect rising job insecurity before official numbers move.  
**Action:** Convert those signals into **practical next steps**, including job transition suggestions that minimize retraining.

This is designed as an **early intervention tool**, not just another job board.

---

## Data Source

- **Google Trends**
  - Weekly interest-over-time for the past 12 months
  - Region: United States (`geo="US"`)
  - Accessed via `pytrends`

---

## Job Shock Score (High-level)

The score is computed using the week-to-week changes of the three signals:

- Δ(`laid off`)
- Δ(`unemployment benefits`)
- Δ(`jobs near me`)

Example weighted sum:

- 0.5 × Δ(laid_off)
- 0.3 × Δ(unemployment_benefits)
- 0.2 × Δ(jobs_near_me)

Then smoothed with a moving average to reduce noise.

---

## How recommendations work

The user provides a free-form job title (e.g., `office admin`, `retail cashier`).

The system:
1. Classifies it into a job family using lightweight keyword rules
2. Chooses “escape routes” based on the current risk state

**Design goal:**  
- resilient roles during downturns
- minimal retraining (skill proximity)
- fast, interpretable logic (no black-box dependency)

---

## Built With

- **Hex** (data app + analysis + visualization)
- **Python**
- **pytrends** (Google Trends access)
- **pandas**

---

## Demo

- **Hex Project (Public Link):** *(add your published Hex URL here)*
- **Demo Video (≤ 3 minutes):** *(add your video URL here)*

---

## How to use (inside Hex)

1. Open the published Hex project
2. Find the `job_input` parameter
3. Enter any occupation (examples):
   - `office admin`
   - `retail cashier`
   - `factory operator`
4. Observe:
   - Job Shock Score trend
   - CALM/WATCH/ALERT status
   - updated recommended escape routes

---

## Notes / Limitations

- This is a prototype focused on **early signal detection + decision support**
- It does not aim to be a full job search platform
- Real-time job listings can be integrated later, but the hackathon version prioritizes:
  - **clarity**
  - **explainability**
  - **interactive behavior in Hex**

---

## Summary

**JobShock Navigator** turns weak labor-market signals into a practical, interactive tool:

> **Early signals → Risk status → Personalized transition suggestions**

Built as a shareable Hex app for fast decision-making.

