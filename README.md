# matlab-statistics-correlation-analysis
MATLAB neuroscience project analyzing whether simulated neuron firing rates are related. It generates Gaussian data, computes mean, variance, covariance, and correlation with custom functions and built in MATLAB tools, and visualizes positive, negative, and weak relationships through labeled scatter plots.

A MATLAB script that simulates neuron firing rate data and implements core statistical measures — variance, covariance, and correlation — from scratch, verified against MATLAB's built-in functions.


---

## What It Does

Generates a simulated dataset of neuron firing rates and analyzes the relationships between a reference neuron X and three response neurons (Y1, Y2, Y3) using custom-built statistical functions. Each function is verified against MATLAB's native equivalents to confirm correctness.

---

## Dataset

A base firing rate variable `X` is generated as 100 randomly distributed values (mean = 3, std = 3), simulating a reference neuron's activity. Three response neurons are derived from it:

| Variable | Relationship to X | Interpretation |
|---|---|---|
| `Y1` | `3X + noise` | Strong positive correlation |
| `Y2` | `-3X + noise` | Strong negative correlation |
| `Y3` | `4 + noise` | No correlation (independent) |

---

## Scatter Plots

The script produces a 3-panel figure showing each neuron's firing rate plotted against X:

![X vs Y1, Y2, Y3](Godoi_01.png)

- **Y1 (blue)** — tight upward slope, strong positive linear relationship
- **Y2 (red)** — tight downward slope, strong negative linear relationship
- **Y3 (green)** — flat scattered cloud, no relationship with X

---

## Custom Functions Implemented

### `myVariance(x)`
Computes sample variance from first principles:

```
variance = Σ(xᵢ - x̄)² / (n - 1)
```

Verified against MATLAB's `var()`.

### `myCovariance(X, Y)`
Computes the sample covariance between two variables:

```
covariance = Σ(Xᵢ - X̄)(Yᵢ - Ȳ) / (n - 1)
```

Verified against MATLAB's `cov()`.

### `myCorrelation(X, Y)`
Computes the Pearson correlation coefficient — covariance normalized by the product of standard deviations:

```
r = covariance(X, Y) / (std(X) × std(Y))
```

Produces a value between -1 and +1. Verified against MATLAB's `corrcoef()`.

---

## Key Results

| Pair | Covariance | Correlation |
|---|---|---|
| X & Y1 | Large positive | ≈ +1.0 (strong positive) |
| X & Y2 | Large negative | ≈ -1.0 (strong negative) |
| X & Y3 | Near zero | ≈ 0.0 (no relationship) |

**Variance vs. Covariance:** Both measure dispersion, but variance does so for a single variable while covariance measures the joint variability of two variables.

---

## How to Run

Open `Godoi.m` in MATLAB or Octave and run the script. No additional toolboxes are required.

```matlab
% In MATLAB command window:
run('Godoi.m')
```

Expected console output:
```
--- Display size of Y and X variables ---
Size of X:  [100, 1]
Size of Y1: [100, 1]
...
Covariance X & Y1: 27.XXXX
Covariance X & Y2: -27.XXXX
Covariance X & Y3: ~0.XXXX
...
---Built in function and our function return the same result---
```

---

## Requirements

- MATLAB R2018b or later (or GNU Octave 6+)
- No additional toolboxes required
