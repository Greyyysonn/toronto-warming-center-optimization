# Toronto Warming Center Optimization
**Stochastic Optimization for Emergency Warming Center Allocation**
> Team project (7 members) — Final deliverable for MMA 861 Analytical Decision Making, Smith School of Business, Queen's University, March 2026. Repository maintained by Greyson Bao (team lead).

## Overview
Toronto's warming centers face a recurring winter crisis: when temperatures drop unexpectedly, demand surges and vulnerable people get turned away. This project builds a data-driven framework to answer two questions for city decision-makers:

1. **Operational**: How should staff be allocated across 7 warming centers?
2. **Strategic**: If 10 additional beds can be funded, where should they go?

Using three years of Toronto Open Data and weather records, we tested our plan against 5,000 simulated winter nights.

## Key Finding
**The system's bottleneck is not staffing — it's beds.** Adding 5 beds each to the Elizabeth and Scarborough centers reduces nightly turn-aways by **67%** and increases net social welfare by **5.7%**, all within the existing $33,000 nightly budget.

## Methodology
A three-stage pipeline:

| Stage | Method | Purpose |
|-------|--------|---------|
| 1. Estimate | Poisson Monte Carlo (1,000 iterations) | Model nightly demand under moderate (-5°C) and extreme (-15°C) scenarios |
| 2. Optimize | Mixed-Integer Linear Programming | Maximize expected social welfare subject to budget, capacity, and staffing-ratio constraints |
| 3. Stress-Test | Monte Carlo (5,000 iterations) | Compare MILP vs. Safety Buffer vs. Proportional Allocation policies |

## Results
- **Optimal staffing**: Elizabeth: 4, George: 2, Scarborough: 4, North York: 3, Spadina: 2, Cecil: 2, Jimmie Simpson: 2
- **Targeted bed expansion** (Elizabeth +5, Scarborough +5) outperforms equal and proportional allocation in both expected welfare and turn-away reduction.

## Tech Stack
Python (NumPy, pandas, PuLP, matplotlib, seaborn), Excel Solver

## Repository Structure
```
├── notebooks/      Jupyter notebooks for each stage
├── reports/        Full technical report and presentation slides
└── excel/          MILP model in Excel Solver
```

## How to Run
```bash
pip install -r requirements.txt
jupyter notebook notebooks/
```
Run notebooks in numerical order (01 → 04).

## Data Sources
- [Toronto Open Data — Daily Shelter Occupancy](https://open.toronto.ca/dataset/daily-shelter-overnight-service-occupancy-capacity/)
- [Environment Canada — Historical Climate Data](https://climate.weather.gc.ca/)
- [Toronto Auditor General — Warming Centres Audit](https://www.torontoauditor.ca/)

## Recognition
Final grade: 90/100. Instructor feedback highlighted the problem framing as "one of the strongest in the class" and the bed-capacity finding as "exactly the kind of strategic insight that makes analytical work valuable to decision-makers."

## Team

**Decision Modeling Architects**
- Greyson Bao (team lead)
- Nitya Srivastava
- Vithushan Umaputhiran

**Data Analysts**
- Gabriella Selestiyanta
- Nazmus Shakib
- Livia Liu
- Lambert Tan

**Special Consultant**: Dr. Guang Li

## My Contributions (Greyson)
As team lead and one of three Decision Modeling Architects, I was responsible for:

- **MILP formulation (Stage 2)**: defined decision variables, constraints, and the asymmetric welfare objective; implemented the model in Excel Solver and validated results
- **Stress-testing framework (Stage 3)**: designed the 5,000-iteration Monte Carlo benchmark comparing MILP, Safety Buffer, and Proportional Allocation policies
- **Capacity expansion analysis (Final Stage)**: led the pivot from staffing optimization to bed-allocation strategy after identifying the infrastructure bottleneck
- **Demand simulation refinement (Stage 1)**: contributed to calibrating the Poisson arrival-rate parameters and validating the moderate/extreme weather scenario logic
- **Final presentation deck**: designed and built the full slide deck used for the final project presentation
- **Project leadership**: coordinated 7-person team, integrated outputs across stages, owned final presentation delivery

## AI Disclosure
Google Gemini and OpenAI ChatGPT were used for brainstorming, code debugging, and language editing. All modeling decisions, analysis, and conclusions were developed by the team.