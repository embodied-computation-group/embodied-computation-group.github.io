---
title: Resources
permalink: /resources/
---

## Open Science Commitment

**100% of our publications include a GitHub repository** containing full data, code, experimental tasks, stimuli, and analysis pipelines. We believe reproducible science requires transparent sharing of all research materials.

Browse all our repositories at our [GitHub Organization](https://github.com/embodied-computation-group).

---

## Open Source Software

| Repository | Description |
|------------|-------------|
| [Systole](#systole) | Cardiac signal analysis for psychophysiology |
| [Cardioception](#cardioception) | Cardiac interoception measurement tasks |
| [Hierarchical Interoception](#hierarchical-interoception-toolkit) | Bayesian analysis for interoceptive psychophysics |
| [RRST](#respiratory-resistance-sensitivity-task-rrst) | Respiratory interoception measurement |
| [Raincloud Plots](#raincloud-plots) | Multi-platform tool for robust data visualization |

---

### Systole

<a href="https://github.com/embodied-computation-group/systole"><i class="fab fa-github"></i> GitHub</a>

A Python package for cardiac signal analysis in psychophysiology research. Systole provides comprehensive tools for:

- **Signal Processing**: Pre-processing, visualization, and artefact detection/correction for cardiac data
- **Heart Rate Variability**: Time-domain, frequency-domain, and non-linear HRV indices
- **Peak Detection**: Automated R-peak detection using the Pan-Tompkins method with interactive correction
- **Experimental Integration**: Synchronization of stimulus presentation with cardiac phases via PsychoPy

Features BIDS-format compatibility, native hardware integration with Nonin pulse oximeters and BrainVision amplifiers, and web-based viewers for annotating cardiac data.

---

### Cardioception

<a href="https://github.com/embodied-computation-group/Cardioception"><i class="fab fa-github"></i> GitHub</a>

A Python package implementing validated psychophysical tasks for measuring cardiac interoception—how accurately people perceive their own heartbeats. Includes:

- **Heartbeat Counting Task**: Participants count heartbeats during timed intervals for accuracy assessment
- **Heart Rate Discrimination Task**: Adaptive psychophysical procedure measuring accuracy and precision of interoceptive beliefs using auditory feedback

Designed for minimal hardware requirements (computer + pulse oximeter), with flexible integration for ECG, M/EEG, and fMRI setups. Includes R-based hierarchical Bayesian modeling tools for analysis.

---

### Hierarchical Interoception Toolkit

<a href="https://github.com/embodied-computation-group/Hierarchical-Interoception"><i class="fab fa-github"></i> GitHub</a>

Hierarchical Bayesian psychometric function models for analyzing interoceptive psychophysics data. This toolkit provides:

- Statistical modeling using Stan and BRMS for the Heart Rate Discrimination Task (HRDT) and Respiratory Resistance Sensitivity Task (RRST)
- Parameter and model recovery validation analyses
- Normative priors derived from large datasets
- Power analysis tools for study planning
- Interactive Shiny app for exploring power across design choices

Includes comprehensive R Markdown workflows demonstrating data simulation, model specification, fitting, diagnostics, and visualization.

---

### Respiratory Resistance Sensitivity Task (RRST)

<a href="https://github.com/embodied-computation-group/RespiroceptionMethodsPaper"><i class="fab fa-github"></i> GitHub</a>

An automated method for measuring respiratory interoception using a fully 3D-printable apparatus. Key features:

- **Psychophysical Assessment**: Forced-choice discrimination task comparing breaths with varying airway obstruction
- **Efficient Measurement**: Bayesian staircase procedure (Psi) achieves threshold convergence in 20-50 trials
- **Metacognitive Assessment**: Evaluates confidence in perceptual judgments
- **Accessible Design**: 3D-printable components eliminate need for expensive medical equipment

High test-retest reliability with minimal participant discomfort, completing full assessment in 30-45 minutes.

---

### Raincloud Plots

<a href="https://github.com/RainCloudPlots/RainCloudPlots"><i class="fab fa-github"></i> GitHub</a> &nbsp; <a href="https://github.com/jorvlan/raincloudplots"><i class="fab fa-github"></i> R Package</a>

A data visualization method combining raw data, probability density, and summary statistics into a single plot. Created by Micah Allen, Raincloud Plots offer a robust alternative to bar charts and box plots that reduces information loss while maintaining clarity.

- **Multi-language Support**: Available in R (`ggrain`, `raincloudplots`), Python (`PtitPrince`), and MATLAB
- **Publication-Ready**: Produces beautiful, statistically valid visualizations with minimal code
- **Repeated Measures**: Supports individually linked data points across conditions and time points
- **Flexible Designs**: Handles 1x1, 2x2, 2x3, and between/within-subject experimental designs

**Citation:** Allen, M., Poggiali, D., Whitaker, K., et al. (2021). "Raincloud plots: a multi-platform tool for robust data visualization." *Wellcome Open Research*, 4:63.

---

## Contact

For questions about our tools and resources:

- **General inquiries:** [micah@cfin.au.dk](mailto:micah@cfin.au.dk)
- **Bluesky:** [@the-ecg.org](https://bsky.app/profile/the-ecg.org)
- **Twitter:** [@visceral_mind](https://twitter.com/visceral_mind)
