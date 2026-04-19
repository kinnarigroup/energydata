# AI Data Center Energy Dataset
**Compiled by Kinnari Group | Version 1.0 | 2026-03-31**
**License: CC BY 4.0 — free to use with attribution**

## About
This dataset tracks AI compute infrastructure, power commitments, hardware efficiency, and model energy consumption. Compiled from public filings, press releases, earnings calls, and published research.

**⚠️ Important caveats:**
- Many AI providers do not publicly disclose energy consumption
- Estimates marked `LOW` confidence are derived from model size + hardware benchmarks
- `HIGH` = official disclosure or confirmed filing | `MED` = credible press/analyst | `LOW` = estimate
- This is a living dataset — update frequency: monthly or when major news breaks

## Files

| File | Description | Rows | Updated |
|------|-------------|------|---------|
| `ai-datacenter-operators.csv` | Per-operator summary: capacity, hardware, capex, clean% | 8 | 2026-03-31 |
| `ai-datacenter-power-sources.csv` | Specific power deals/contracts by operator | 13 | 2026-03-31 |
| `ai-hardware-efficiency.csv` | GPU/chip specs: TDP, tokens/kWh, efficiency vs baseline | 9 | 2026-03-31 |
| `ai-model-energy.csv` | LLM energy estimates: J/token, kWh/1M tokens, REC math | 8 | 2026-03-31 |
| `ai-datacenter-capacity-timeline.csv` | US AI DC power capacity 2020-2030 (actual + projected) | 10 | 2026-04-19 |
| `grid-macro-indicators.csv` | Macro grid demand indicators: global TWh, PJM shortfall, AI grid share, fossil % | 4 | 2026-04-19 |

## Key Columns Reference

### operators
- `committed_capacity_mw` — total planned/contracted power capacity
- `clean_energy_pct_estimate` — estimated % of power from clean sources
- `tokens_per_month_trillion_estimate` — estimated monthly token throughput

### power-sources
- `source_type` — one of: `nuclear`, `solar_btm`, `solar_wind_portfolio`, `gas_onsite`, `gas_mobile`, `storage_btm_gwh`, `nuclear_smr`, `grid`
- `status` — one of: `active`, `contracted`, `under_construction`, `announced`, `ordered`

### hardware-efficiency
- `efficiency_vs_h100_baseline` — tokens/kWh relative to H100 = 1.0
- `tokens_per_kwh_millions` — millions of output tokens per kWh

### model-energy
- `joules_per_output_token` — most direct energy unit (output tokens cost ~4-10x more than input)
- `recs_per_million_tokens` — how many RECs needed to certify 1M tokens as "clean"
- `tokens_per_rec_millions` — how many clean tokens 1 REC (1 MWh) covers

## Suggested Visualizations
1. **Power source mix by operator** (stacked bar: nuclear/solar/gas/grid)
2. **Capacity timeline 2020-2030** (area chart: actual + projected, BTM vs grid)
3. **Hardware efficiency progression** (line: tokens/kWh over time H100→Rubin)
4. **Model energy comparison** (bar: kWh/1M tokens by model)
5. **Clean token potential** (scatter: operator capacity × clean% × model efficiency)
6. **Geographic map** of major facility locations with power source color coding

## Data Gaps (help wanted)
- Anthropic energy disclosure (none public)
- OpenAI per-request energy data (none public)
- CoreWeave power source mix detail
- xAI Colossus actual vs claimed capacity
- Per-facility breakdowns for Stargate sites

## Updates & Contributing
Maintained at: `/root/.openclaw/workspace/kinnari/datacenter-db/publish/`
Contact: Kinnari Group

## Sources Used
- EIA Grid Monitor: https://www.eia.gov/electricity/gridmonitor/
- Data Center Dynamics: https://www.datacenterdynamics.com
- SemiAnalysis: https://newsletter.semianalysis.com
- S&P Global Sustainable1: https://www.spglobal.com/sustainable1
- Tech Insider AI Power Crisis: https://tech-insider.org/ai-data-center-power-crisis-2026/
- Google Cloud sustainability blog: https://cloud.google.com/blog/products/infrastructure/measuring-the-environmental-impact-of-ai-inference/
- LLM Power Tracker: https://llm-tracker.info/_TOORG/Power-Usage-and-Energy-Efficiency
- Zestlab AI Data Center Energy Crisis 2026: https://zestlab.io/en/trends/ai-data-center-energy-crisis-2026
- OpenAI Stargate announcement: https://openai.com/index/five-new-stargate-sites/
