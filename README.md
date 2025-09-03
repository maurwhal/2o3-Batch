# OECD 497 — 2-out-of-3 **Batch Helper** (now with raw metrics)

A single-file web app that ingests a CSV/XLSX of chemicals and produces **OECD TG 497 2-out-of-3** hazard calls in bulk. It works in two modes:

1) **Per-assay calls** (e.g., `1`, `0`, `Bp`, `Bn`, `1 (kDPRA)`, `BL not ass.`).  
2) **Raw metrics** — the app computes calls from your numbers:

- **DPRA (TG 442C):** mean % depletion (uses AVG if present, else mean of Cys/Lys). Default positive cutoff **6.38%**.
- **KeratinoSens (TG 442D):** positive if **Max fold ≥ 1.5** at **Viability ≥ 70%** (you map both columns).
- **h-CLAT (TG 442E):** positive if **CD86 ≥ 150%** *or* **CD54 ≥ 200%**, with **Viability ≥ 50%** (viability can be optional; if missing, confidence is Low).

Borderlines: you can set optional bands (e.g., DPRA 3.0–6.38%, KS fold 1.50–1.60, CD86 140–160, CD54 190–210, etc.). Values inside a band keep their direction but are marked **Low** confidence.

**2o3 hazard rule:** two Positives → **Positive**; two Negatives → **Negative**; otherwise **Inconclusive**. By default only High-confidence calls contribute (toggleable).

## How to use
- Open `index.html` in a modern browser (or host on GitHub Pages).
- Upload your spreadsheet.
- Pick **Input type** (Calls vs Raw).
- Map columns (CAS, Name + the assay fields needed for your mode).
- Click **Run** → results show in-page and can be **downloaded as CSV**.

## Templates
- Calls: `2o3_batch_template.csv` (simple 1/0/Bp/Bn style).  
- Raw: includes columns for DPRA %, KS fold + viability, and h-CLAT RFIs + viability.

## Notes
- Everything runs **in-browser**; no uploads or storage.
- This app covers **hazard (2o3)** only; not potency subclassification (1A/1B) or PoD.
- If your lab uses different thresholds/borderline windows, adjust the fields in **Advanced**.

---
This has been a Maura Lavelle production <(0.0)>
