# Data Sources — Aviation Emissions Monte Carlo Simulation

Channel parameters in `mc_simulation.py` trace to the sources listed here.
The paper (Aviation Emissions: Altitude Forcing Floor) is available on SSRN and contains the full
reference list and §4 calibration narrative.

---

## Channel Sources

### `C1_co2_climate_damage`

CO₂ emissions ~1Gt/yr at EPA SCC $190/t. 2.5% of global emissions. Sources: EPA, ICAO, Lee et al. 2021.

*Full citations: paper §4 (available SSRN).*

### `C2_non_co2_climate`

Contrails, NOx, aerosols. Effective radiative forcing 2-4× CO₂ alone. Lee et al. 2021 Nature. Sources: Lee et al. 2021, IPCC AR6.

*Full citations: paper §4 (available SSRN).*

### `C3_air_quality_mortality`

Airport and flight-path PM2.5/NOx mortality. 16,000 deaths/yr (Yim et al. 2015). Sources: Yim et al., Masiol & Harrison, EPA.

*Full citations: paper §4 (available SSRN).*

### `C4_community_noise`

Aircraft noise health impacts: CVD, sleep disruption, cognitive impairment in children. 2M+ affected near major airports. Sources: WHO, Basner et al., FAA.

*Full citations: paper §4 (available SSRN).*

### `C5_governance_capture`

ICAO industry capture, CORSIA offsetting loophole, Annex 16 inadequacy. $35B/yr in foregone fuel tax. Sources: ICAO, T&E, ICCT.

*Full citations: paper §4 (available SSRN).*

---

## Industry Revenue (Π)

The private payoff Π = $100.0B/yr is global annual industry revenue.
Source: paper §2 and §4. See paper §DA-1 (Decision Audit Field 7) for full
revenue source documentation.

---

## SAPM Framework

- Postnieks, E. (2026). *The Private Pareto Theorem*. SAPM Foundation Paper. SSRN.
- Postnieks, E. (2026). *Aviation Emissions (Altitude Forcing Floor)*. SAPM Working Paper. SSRN.

---

## Distribution Methodology

- Iman, R. L., & Conover, W. J. (1982). A distribution-free approach to
  inducing rank correlation among input variables. *Communications in
  Statistics — Simulation and Computation*, 11(3), 311–334.
- Cooke, R. M. (1991). *Experts in Uncertainty*. Oxford University Press.
