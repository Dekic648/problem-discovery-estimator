# Problem Discovery Estimator

An interactive calculator that estimates how many usability problems remain undiscovered in your study — and how many more participants you need to find them.

**[Try it live →](https://dekic648.github.io/problem-discovery-estimator/)**

## What it does

UX researchers run formative usability studies to find problems in a design. A common question is: *"Have we tested with enough people?"* This tool answers that using established statistical methods.

Given a **participant × problem matrix** (which participants found which problems), the estimator calculates:

- **Coverage %** — proportion of discoverable problems you've likely found
- **Estimated total problems** — how many problems exist in the design
- **Still hidden** — how many problems remain undiscovered
- **Optimal sample size** — how many more participants to reach 85% or 95% coverage

It also renders a **discovery curve** showing cumulative detection probability and marginal gain per additional participant.

## Method

The estimator implements two well-established techniques from the usability measurement literature:

| Component | Source |
|---|---|
| **Adjusted-p correction** | Lewis, J.R. (2001). *Evaluation of procedures for adjusting problem-discovery rates estimated from small samples.* International Journal of Human–Computer Interaction, 13(4), 445–479. |
| **Formative sample-size framework** | Sauro, J. & Lewis, J.R. (2016). *Quantifying the User Experience* (2nd ed.). Morgan Kaufmann. |

**Core formula:**

```
P(discover) = 1 − (1 − p_adj)^n
```

Where `p_adj = 0.9 × p_obs − 0.046` corrects for the small-sample overestimation bias that inflates raw detection rates in typical 5–8 participant studies.

## How to use

1. Open the tool and set up your participant × problem matrix
2. Click cells to mark which participants encountered which problems
3. Results update in real time — coverage, estimates, recommendations, and the discovery curve

## Tech

Single-file HTML/CSS/JS with [Chart.js](https://www.chartjs.org/) for the discovery curve. No build step, no dependencies to install. Supports light and dark mode.

## License

MIT
