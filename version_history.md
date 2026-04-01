# Dataset Version History

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
