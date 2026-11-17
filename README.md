# FrontierLitBench FB-1.1

Five literature-search agents evaluated on the same 15 tasks (video / world models / LLM agents),
3 runs each, scored against a **757-paper** frontier literature library.

**Live dashboard → https://conmuyan.github.io/frontierlitbench/**

## Headline results (main protocol)

| Agent | nDCG@5 | WeightedHit@5 | S-Tier Hit@5 |
|---|---|---|---|
| ChatGPT Chat | **0.6610** | **63.56** | 1.36 |
| ScholarGuide | 0.6388 | 58.58 | **1.58** |
| PaperSeek·ds | 0.4088 | 39.02 | 0.64 |
| PaperSeek·gpt | 0.3567 | 35.73 | 0.38 |
| Ai2Asta | 0.3507 | 32.27 | 0.49 |

## What is in the dashboard

- **Overview** — three-metric grouped bars with per-task breakdown, 9-axis radar, track × agent matrix
- **Stability** — mean ± 1 SD ribbons per metric
- **Trace** — every non-S position with its shortfall reason and evidence
- **Library** — all 757 papers (S 127 / A 351 / B 279), filterable and exportable

Everything is a single offline HTML file (ECharts and data inlined, no network requests).
The language button cycles 简体中文 → 繁體中文 → English.

## Data

- `data/frontierlit-v1.1-library.{csv,json}` — 757 eligible papers with track, venue, year, tier, Q, citations, stars
- `data/frontierlit-v1.1-rejected.{csv,json}` — 31 rejected candidates with reasons

## Scoring

Tier score `Q = 0.55·citations + 0.30·repo + 0.15·institution`; gains S/A/B = 5/3/1 with a log2
position discount; IDCG fixed at 14.7423.
