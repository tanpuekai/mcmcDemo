# MCMC Explorer

An interactive web-based visualization tool for understanding Markov Chain Monte Carlo (MCMC) sampling algorithms. Designed for postgraduate engineering students to explore and learn MCMC concepts through hands-on experimentation.

## Overview

This project provides a self-contained, browser-based demonstration of three fundamental MCMC algorithms:

- **Metropolis-Hastings**: Random walk algorithm with proposal/accept/reject mechanism
- **Gibbs Sampling**: Sequential sampling from conditional distributions
- **Sequential Monte Carlo (SMC)**: Particle-based sampling with resampling

## Features

### Interactive Visualization
- Real-time animation of sampling processes
- Adjustable animation speed (1 to 20 samples per second)
- Toggleable trace visualization showing accepted/rejected proposals
- Target distribution heatmap overlay

### Diagnostic Panels
Three square diagnostic windows positioned to the left of the main visualization:

1. **Target Distribution**: Theoretical probability density function
2. **Sampled Distribution**: Empirical histogram built from collected samples
3. **Trace / Burn-in Analysis**: Time-series plot showing X and Y traces with burn-in period highlighted

Double-click any diagnostic panel to expand it to full size for detailed examination.

### Algorithm Parameters
Each algorithm has adjustable parameters:

**Metropolis-Hastings:**
- Proposal standard deviation (step size)
- Target distribution separation (bimodal mixture)

**Gibbs Sampling:**
- Correlation coefficient (rho)
- Conditional variance

**Sequential Monte Carlo:**
- Number of particles
- Resample threshold
- Tempering rate

## Usage

1. Open `mcmc-interactive-demo.html` in any modern web browser
2. Select an algorithm from the tabs at the top right
3. Adjust parameters using the sliders in the control panel
4. Click "Start" to begin sampling
5. Adjust animation speed as needed to observe the sampling process
6. Toggle visualization options (traces, proposal distribution) to explore different aspects

No server or installation required. All code is self-contained in a single HTML file.

## Files

- `mcmc-interactive-demo.html`: Main interactive demonstration
- `mcmcDemoCodex.html`: Reference documentation and implementation notes
- `README.md`: This file

## Credits

Conceived and designed by Peikai Chen, executed by AI.
