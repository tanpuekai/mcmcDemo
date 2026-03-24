# Prompt For Reproducing This Project

Create a new standalone HTML file named `mcmcDemoCodex.html` in the `mcmcDemo` project. Do not overwrite the existing `mcmc-interactive-demo.html`; treat that file only as inspiration and preserve it untouched.

The goal is to turn the current MCMC demo into an "absolute banger" for education: polished, visually intentional, high-signal, and genuinely useful for teaching intuition. The page should feel like a premium interactive teaching lab rather than a generic dark dashboard.

## Product Goal

Build a single-file interactive educational demo for Monte Carlo methods that:

- teaches MCMC intuition visually
- is strong enough to present or teach from directly
- emphasizes the chain behavior, proposal behavior, diagnostics, and narrative interpretation
- includes contrast between MCMC samplers and a particle-based method
- is saved as `mcmcDemoCodex.html`

## Design Direction

Use a distinctive, editorial, warm visual language rather than default "AI slop" styling.

Requirements:

- avoid purple-on-white or generic dark-mode defaults
- use a more memorable visual identity with intentional typography, color, and spacing
- make it feel handcrafted, expressive, and presentation-ready
- support both desktop and mobile layouts
- keep it self-contained in one HTML file with embedded CSS and JS

The implemented direction that should be reproduced is:

- warm parchment / studio style background
- serif-forward typography
- high-end interactive article / teaching-lab feel
- clean cards for controls, diagnostics, formulas, and teaching notes

## Core Structure

The page should have:

1. A strong hero section introducing the purpose of the demo.
2. A left control rail with sampler selection, presets, run controls, sliders, and view toggles.
3. A center canvas area for the main visualization.
4. A right rail with teaching narration, diagnostics, formula text, and teaching notes.
5. A short footer credit line.

## Samplers To Include

The final sampler choice list should contain exactly four options:

- `MH` for Metropolis-Hastings
- `Gibbs`
- `Indep.` for Independence sampler
- `SMC` for Sequential Monte Carlo / Particle Filter

The visible button labels should be abbreviated because long labels do not fit well in the button layout, but full names should still be available through titles/tooltips and surrounding explanatory text.

## Educational Positioning

This is not just a visualization. It should actively teach.

Include:

- a dynamic explanation banner that tells the viewer what to notice
- formulas that change with the selected sampler
- teaching notes for each algorithm
- live diagnostic summaries such as acceptance, ESS-style summaries, autocorrelation, mode hops, resampling count, or temperature where appropriate
- "teaching presets" that intentionally create good and bad behavior

The page should help users understand:

- proposal scale tradeoffs
- poor mixing
- multimodality
- correlation and conditional updates in Gibbs
- proposal mismatch in independence sampling
- weight degeneracy and resampling in particle methods

## Presets

Include these teaching presets:

- `Balanced`
- `Sticky Chain`
- `Too Wild`
- `Mode Barrier`

These should meaningfully alter parameters so the behavior changes in ways that are useful for teaching.

## Diagnostics

Include at least these live diagnostics:

- trace plot
- sample histogram
- autocorrelation plot

These should update as the simulation runs.

## Main Visualization Requirements

The main panel should show the target density and the sampler behavior in a visually readable way.

For MCMC samplers, the visualization should make the mechanics of each step explicit.

For the particle method, show a weighted particle cloud and a representative mean/current estimate.

## Proposal / Decision Animation Requirements

This part is critical and should be reproduced carefully.

For proposal-based samplers (`MH` and `Indep.`), do not jump directly to accepted states.

Instead, each step must have a staged decision process:

1. At time `t`, the head circle is at the current point `pt`.
2. A proposal is generated from `pt`.
3. Draw a dashed green line from `pt` to the proposed point.
4. Pause and show the decision process.
5. If accepted:
   - turn that line into a solid green line
   - pause briefly so the acceptance is visible
   - then move the head circle to the proposed point
6. If rejected:
   - keep the head circle at `pt`
   - turn the dashed proposal line brown
   - then make the next proposal from the same `pt`

Important clarifications:

- during the proposal phase, the head must stay at the current point
- do not draw the proposal point as if it were already the new state
- accepted moves should visibly pass through a proposal phase and then a decision phase before the head moves
- rejected moves should visibly remain rejected from the old position

This sequencing was refined over several iterations and is essential to the final behavior.

## Gibbs Behavior

For Gibbs:

- use a correlated Gaussian target
- ensure the Gibbs conditionals are internally consistent with the displayed target
- show alternating coordinate-wise movement clearly
- acceptance should effectively be 100%, but the diagnostics should still teach that high acceptance does not automatically mean fast mixing

## Independence Sampler Behavior

For the independence sampler:

- proposals should come from a fixed proposal distribution rather than local random walk steps
- include a control for proposal center mismatch
- use the visualization and narration to teach that proposal quality is everything

## SMC / Particle Filter Behavior

Add Sequential Monte Carlo / Particle Filter as a fourth mode and make it feel native to the page rather than bolted on.

Requirements:

- its own mode in the sampler selector
- particle-specific controls, at least:
  - particle count
  - resample threshold
- particle cloud visualization
- mode-specific formula copy
- mode-specific narration
- mode-specific stats such as:
  - ESS ratio
  - resamples
  - temperature

Teaching focus:

- particle methods are not one-chain MCMC
- show weighted population behavior
- explain ESS collapse / weight degeneracy
- explain why resampling helps and what diversity tradeoff it introduces

## Copy / Credits

The footer line must be:

`Conceived and designed by Peikai Chen, executed by AI.`

## Constraints

- keep everything in a single HTML file
- use embedded CSS and JavaScript only
- do not rely on external libraries
- preserve the original `mcmc-interactive-demo.html`
- save the improved output as `mcmcDemoCodex.html`

## Deliverable

Produce `mcmcDemoCodex.html` implementing all of the above.

Also ensure the page is coherent enough that someone can open the file directly in a browser and use it as a teaching demo without any build step.
