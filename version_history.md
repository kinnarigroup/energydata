# Dataset Version History

## v1.4 — 2026-04-19
**Updated by:** KC (Kinnari Claw)

### Changes
- `vertiv-vrt-2026-rally-snapshot.md` — **NEW FILE**: Full headless-browser capture of AlphaStreet Vertiv (VRT) analysis
  - Q4 2025 financials: revenue $2.88B (+22.7%), adj EPS $1.36 (+37%), FCF $910M (+151%)
  - Backlog $15B (+109% YoY), book-to-bill 2.9x, orders +252% YoY
  - FY2025 net sales $10.23B, organic growth 26%, adj FCF $1.9B
  - 2026 guidance: revenue $13.25-13.75B, adj EPS $5.97-6.07
  - Peer comparison tables: VRT vs Eaton, Schneider, Hubbell (revenue, growth, liquid cooling, software tools, market cap)
  - Rally drivers, risks, bull case, analyst consensus
  - Direct links to Vertiv Q4 FY2025 earnings release and presentation PDF

### Source
- AlphaStreet: https://news.alphastreet.com/vertiv-holdings-nysevrt-extends-2026-rally-after-64-surge-ai-data-center-demand-and-cooling-backlog-in-focus/

---

## v1.3 — 2026-04-19
**Updated by:** KC (Kinnari Claw)

### Changes
- `zestlab-datacenter-energy-snapshot.md` — **NEW FILE**: Full JS-rendered article capture from ZestLab via headless browser
  - Key stats: >1,000 TWh global DC power, 6 GW PJM shortfall, 12% AI grid share by 2028
  - Per-operator power table: AWS 95 TWh, Azure 72 TWh, Google 64 TWh, Meta 28 TWh
  - US energy mix breakdown, grid stress by region, crisis drivers, solutions status
  - Backend API endpoints discovered: `https://zestlab.whammytech.com/api/trends?status=published&slim=1`
- `zestlab-energy-articles-index.csv` — **NEW FILE**: 24 energy/grid/nuclear/renewables articles indexed from ZestLab API (of 384 total)
  - API hit directly via headless browser network inspection
  - Covers AI data center, EU renewables milestones, Iran oil/Hormuz, jet fuel crisis, IMF energy outlook

### Method
- Used headless Chromium (CDP) to fully render ZestLab article with JS
- Captured DOM snapshot + performance.getEntriesByType('resource') for full network resource list
- Identified and queried ZestLab's backend API directly

---

## v1.2 — 2026-04-19
**Updated by:** KC (Kinnari Claw)

### Changes
- `grid-macro-indicators.csv` — **NEW FILE**: macro grid demand stats from Zestlab (March 2026)
  - Global data center electricity >1,000 TWh projected for 2026
  - PJM grid shortfall: 6 GW by 2027
  - AI = 12% of US electricity grid
  - 60% of data center power from fossil fuels
- `ai-datacenter-capacity-timeline.csv` — updated 2026 row notes to cross-reference global TWh figure and Zestlab source
- `README.md` — added new file entry; added Zestlab to sources

### Source
- Zestlab: https://zestlab.io/en/trends/ai-data-center-energy-crisis-2026 (published March 19, 2026)

---

## v1.1 — 2026-04-01
**Updated by:** KC (Kinnari Claw)

### Changes
- `ai-hardware-efficiency.csv` — added two new columns:
  - `utilization_pct_training` — typical GPU utilization for training workloads (90-95%)
  - `utilization_pct_inference` — typical GPU utilization for inference (45-65%, spiky)
  - Added `memory_bandwidth_tbps` column (key bottleneck metric)
  - Added NVIDIA A100 as historical baseline
  - Added source URLs and notes from TokenPowerBench paper
- `tokenpowerbench-findings.csv` — **NEW FILE**: measured J/token data from TokenPowerBench (arxiv:2512.03024)
  - Covers Llama3 8B/70B/405B, Mistral 7B, Falcon 40B
  - Measured on 4x H100 SXM node with vLLM and TensorRT-LLM
  - Key finding: batch size has ~3-4x efficiency impact; INT8 quantization ~15-20% improvement
- `version_history.md` — this file

### Key insights from TokenPowerBench
- Decode phase (output tokens) dominates energy vs prefill (input tokens): ~5-10x more J/token
- Energy scales faster than parameter count within model families
- Batch size matters enormously: batch=32 vs batch=1 = ~3-4x better efficiency
- Production inference at scale gets batching efficiency; single-user benchmarks don't

---

## v1.0 — 2026-03-31
**Updated by:** KC (Kinnari Claw)

Initial dataset release.
- `ai-datacenter-operators.csv`
- `ai-datacenter-power-sources.csv`
- `ai-hardware-efficiency.csv`
- `ai-model-energy.csv`
- `ai-datacenter-capacity-timeline.csv`
- `README.md`
