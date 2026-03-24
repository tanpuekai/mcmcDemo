# MCMC Explorer - Project Prompt

Create a fancy, self-contained web demo with HTML, CSS, and JavaScript to visualize Markov Chain Monte Carlo (MCMC) algorithms for engineering postgraduate students. The interface should be interactive, explorable, and educational.

## Requirements

### Algorithms to Implement
Include three common MCMC algorithms:
1. **Metropolis-Hastings** - Random walk with proposal/accept/reject mechanism
2. **Gibbs Sampling** - Sequential sampling from conditional distributions
3. **Sequential Monte Carlo (SMC)** - Particle-based sampling with resampling

### Layout Structure
Create a three-column layout:

**Left Column (280px width):** Three square diagnostic panels stacked vertically, each taking 1/3 of the main window height, perfectly aligned top-to-bottom:
- Top: Target Distribution (theoretical probability density heatmap)
- Middle: Sampled Distribution (empirical 2D histogram from collected samples)
- Bottom: Trace / Burn-in Analysis (time-series plot showing X and Y traces, with burn-in period highlighted in orange, covering first 20% of iterations)

Each diagnostic panel should be double-clickable to expand to a full-size modal view for detailed examination.

**Center Column:** Main sampling visualization window showing:
- Animated sampling process
- Target distribution heatmap background (toggleable)
- Current state with glow effect
- Transition traces/paths showing movement from point i to i+1
- For Metropolis-Hastings: proposal distribution circle and proposal point
- For SMC: particle cloud with weights

**Right Column (380px width):** Control panel containing:
- Algorithm selection tabs
- Playback controls (Start/Pause/Reset)
- Speed control slider (1 to 20 points per second, default at 1)
- Toggle switches for traces and proposal distribution
- Algorithm-specific parameter sliders
- Algorithm description with mathematical formulas
- Legend explaining visual elements
- Statistics display (iteration count, acceptance rate, particle count)

### Visualization Features
- Dark theme with modern UI using purple/cyan color accents
- Heatmap visualization of target distributions
- Gradient traces with glow effects showing accepted (green) and rejected (pink) proposals
- For Gibbs: color-code X updates (green) and Y updates (orange)
- Grid and axes overlays
- Real-time statistics overlay in top-left of main canvas

### Animation Speed
Implement time-based animation (not frame-based):
- Default: 1 sample per second
- Range: 1 to 20 samples per second
- Use requestAnimationFrame with delta time calculations

### Algorithm Parameters

**Metropolis-Hastings:**
- Proposal sigma (step size): 0.1 to 2.0
- Target separation: 0 to 6 (controls bimodal mixture distance)

**Gibbs Sampling:**
- Correlation (rho): 0 to 0.95
- Conditional variance: 0.1 to 1.0

**Sequential Monte Carlo:**
- Number of particles: 20 to 300
- Resample threshold: 0.1 to 1.0
- Tempering rate: 0.01 to 0.1

### Sample Storage and Diagnostics
- Store all samples (up to 5000) for empirical distribution visualization
- Track last 500 iterations for burn-in analysis
- Real-time updates to all diagnostic panels as samples are generated

### Target Distributions
- Metropolis-Hastings and SMC: Mixture of two Gaussians with adjustable separation
- Gibbs Sampling: Bivariate Gaussian with adjustable correlation

### Technical Requirements
- Single self-contained HTML file
- No external dependencies
- Responsive layout (gracefully degrade on smaller screens)
- Smooth 60fps animations
- Proper canvas resizing without stretching or flickering

### Attribution
Include the following attribution in the header:
"Conceived and designed by Peikai Chen, executed by AI."

## Implementation Notes

Use Box-Muller transform for normal random number generation. Implement proper coordinate transformations between world coordinates (for calculations) and screen coordinates (for rendering). Ensure canvases are only resized during initialization and window resize events, not during animation frames.

The demo should be immediately runnable by opening the HTML file in any modern web browser without requiring a server or build step.
