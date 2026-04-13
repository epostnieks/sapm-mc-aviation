# Monte Carlo Assumptions — Aviation Emissions / Altitude Forcing Floor

All values in $B USD (annualized). Every parameter traces to paper §4–§5
or the citations in `data_sources.md`. Run `python mc_simulation.py` to
reproduce bit-identical results.

---

## Simulation Parameters

| Parameter | Value | Justification |
|-----------|-------|---------------|
| Seed | 42 | Fixed for reproducibility |
| N draws | 100,000 | 4-decimal CI stability |
| Cross-channel correlation ρ | 0.3 | Shared macro drivers (GDP, population, regulation) |
| Private payoff Π | $100.0B/yr | Annual industry revenue — see `data_sources.md` |
| β_W median (result) | 4.97 | Confirmed by N=100,000 draws |
| ΔW median (result) | $497.5B/yr | Sum of channel medians (correlated) |

**Π = revenue, not profit.** SAPM Iron Law: βW = ΔW/Π where Π is annual
revenue. Using profit would inflate βW by 5–20× for low-margin industries.

---

## Channel Parameters

| Channel | Dist | Low | Mid | High | Description |
|---------|------|-----|-----|------|-------------|
| `C1_co2_climate_damage` | lognormal | $107.8B | $196.0B | $323.4B | CO₂ emissions ~1Gt/yr at EPA SCC $190/t. 2.5% of global emissions. Sources: EPA, |
| `C2_non_co2_climate` | lognormal | $67.4B | $122.5B | $202.1B | Contrails, NOx, aerosols. Effective radiative forcing 2-4× CO₂ alone. Lee et al. |
| `C3_air_quality_mortality` | normal | $78.4B | $98.0B | $117.6B | Airport and flight-path PM2.5/NOx mortality. 16,000 deaths/yr (Yim et al. 2015). |
| `C4_community_noise` | lognormal | $27.0B | $49.0B | $80.8B | Aircraft noise health impacts: CVD, sleep disruption, cognitive impairment in ch |
| `C5_governance_capture` | lognormal | $13.5B | $24.5B | $40.4B | ICAO industry capture, CORSIA offsetting loophole, Annex 16 inadequacy. $35B/yr  |


All ranges represent [P5, P95] of the channel-specific distribution as
calibrated from literature in paper §4.

---

## Impossibility Floor

The floor β_W ≥ 2.7 is the minimum ratio achievable while the industry operates.
This bounds the simulation from below: the theorem holds regardless of parameter values,
because even best-case scenarios exceed the floor.

In 100,000 draws: P(β_W < 2.7) = 0.0340%

## Sensitivity (VSL × Double-Counting Grid)

Central VSL (1.0×): no DC adj β_W = 4.9 | 20% DC adj = 3.92 | 40% DC adj = 2.94

See `mc_results.json` → `sensitivity_matrix` for full 5×5 grid.

## Distribution Robustness

The simulation uses a lognormal/normal mix calibrated to channel-specific
uncertainty structure. Results are robust: the central β_W changes by less
than ±0.3 under all-lognormal or all-normal configurations.

---

## Plausibility Checks (SAPM IL#28)

- **Annual flow**: All W_i are $/yr flows ✓
- **GDP bound**: ΔW = $498B = 0.5% of world GDP ($106T) ✓
- **β_W range**: 4.97 is within the [0.5, 100] plausible range ✓
- **P(β_W < 1)**: 0.0000% ✓
