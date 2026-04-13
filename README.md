# SAPM Monte Carlo — Aviation Emissions / Altitude Forcing Floor

**Public replication repository for quantitative results in:**

> Postnieks, E. (2026). *Aviation Emissions (Altitude Forcing Floor).* SAPM Working Paper. SSRN.

This repository provides everything needed to independently reproduce, audit,
and extend the Monte Carlo simulation underlying the paper's core results.
The paper is available on SSRN.

---

## Results (N = 100,000 draws, seed = 42)

| Statistic | Value |
|-----------|-------|
| **β_W median** | **4.97** |
| β_W mean | 5.08 |
| β_W std | 1.0 |
| **90% CI** | **[3.6, 6.9]** |
| 99% CI | [3.2, 7.9] |
| P(β_W < 1) | 0.0000% |
| **ΔW median** | **$497.5B/yr** |
| Π (revenue) | $100.0B/yr |

**β_W = 4.97** means the aviation emissions industry destroys **$4.97 in system
welfare for every $1.00 in revenue** — across 5 channels and 100,000 Monte Carlo draws.

**Classification**: Class 1 — Impossibility

---

## What Is β_W?

```
β_W = ΔW / Π
```

- **ΔW** = total annualized welfare destruction ($B/yr) across all channels
- **Π** = annual industry **revenue** ($B/yr) — not profit

β_W > 1: industry destroys more welfare than it captures in revenue.
β_W > 3: Strong Intractability threshold — reform requires structural replacement.

---

## Quick Start

```bash
git clone https://github.com/epostnieks/sapm-mc-aviation.git
cd sapm-mc-aviation
pip install numpy scipy
python mc_simulation.py
```

Expected output: `β_W median : 4.97` and `ΔW median : $497.5B/yr`

---

## Welfare Channels

| Channel | Median ($B/yr) | 90% CI | Distribution |
|---------|---------------|--------|--------------|
| C1_co2_climate_damage | $195.8B | [$118.6B, $322.0B] | Lognormal |
| C2_non_co2_climate | $122.4B | [$74.3B, $202.2B] | Lognormal |
| C3_air_quality_mortality | $98.0B | [$78.4B, $117.5B] | Normal |
| C4_community_noise | $49.0B | [$29.7B, $80.9B] | Lognormal |
| C5_governance_capture | $24.5B | [$14.8B, $40.4B] | Lognormal |
| **Total ΔW** | **$497.5B** | **[$363.8B, $689.9B]** | Correlated (ρ=0.3) |

---

## Impossibility Floor

The floor β_W ≥ 2.7 cannot be breached by any policy while the
industry continues to operate. In 100,000 draws, only **0.0340%**
fall below this floor — confirming the structural constraint.

## Repository Contents

| File | Description |
|------|-------------|
| `mc_simulation.py` | Self-contained simulation — no private pipeline imports |
| `mc_results.json` | Pre-run results (100K draws, seed=42) — matches paper |
| `mc_histogram.json` | Binned β_W distribution (80 bins) for companion chart |
| `assumptions.md` | Every parameter: value, derivation, source |
| `data_sources.md` | Full citation list for all empirical inputs |

---

## Replication Notes

Results are seeded and deterministic. Tested with:
```
numpy==1.26.4  scipy==1.12.0  Python 3.11.9
```

The `median` and `ci_90` (to 1 decimal) match exactly across compatible versions.

---

## License

CC BY 4.0. Cite as:

> Postnieks, E. (2026). *SAPM Monte Carlo — Aviation Emissions (Altitude Forcing Floor)*.
> GitHub: epostnieks/sapm-mc-aviation.
> https://github.com/epostnieks/sapm-mc-aviation
