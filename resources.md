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
| [respyra](#respyra) | Respiratory motor tracking for interoception research |
| [GastroPy](#gastropy) | Electrogastrography signal processing and gastric-brain coupling |
| [metadpy](#metadpy) | Bayesian modeling of behavioral metacognition |
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

**Citation:** Legrand & Allen (2022). [Systole: A python package for cardiac signal synchrony and analysis](https://doi.org/10.21105/joss.03832). *JOSS*, 7(69), 3832.

---

### Cardioception

<a href="https://github.com/embodied-computation-group/Cardioception"><i class="fab fa-github"></i> GitHub</a>

A Python package implementing validated psychophysical tasks for measuring cardiac interoception—how accurately people perceive their own heartbeats. Includes:

- **Heartbeat Counting Task**: Participants count heartbeats during timed intervals for accuracy assessment
- **Heart Rate Discrimination Task**: Adaptive psychophysical procedure measuring accuracy and precision of interoceptive beliefs using auditory feedback

Designed for minimal hardware requirements (computer + pulse oximeter), with flexible integration for ECG, M/EEG, and fMRI setups. Includes R-based hierarchical Bayesian modeling tools for analysis.

**Citation:** Legrand, N., Nikolova, N., Correa, C., Brændholt, M., Stuckert, A., Kildahl, N., Vejlø, M., Fardo, F., & Allen, M. (2022). [The heart rate discrimination task: A psychophysical method to estimate the accuracy and precision of interoceptive beliefs](https://doi.org/10.1016/j.biopsycho.2021.108239). *Biological Psychology*, 168, 108239.

---

### respyra

<a href="https://github.com/embodied-computation-group/respyra"><i class="fab fa-github"></i> GitHub</a> &nbsp; <a href="https://pypi.org/project/respyra/"><i class="fas fa-box"></i> PyPI</a>

A Python toolbox for respiratory motor tracking experiments in interoception research. respyra integrates a wireless chest-mounted force sensor with PsychoPy to create closed-loop breathing paradigms with real-time visual feedback.

- **Real-Time Display**: Scrolling waveform with target dot and participant trace with graded color-coded feedback
- **Visuomotor Perturbation**: Configurable gain manipulation for studying respiratory motor recalibration
- **Automated Calibration**: Percentile-based range calibration with outlier rejection and saturation warnings
- **Crash-Resilient Logging**: Row-level CSV flushing ensures no data loss mid-session
- **Post-Session Visualization**: `respyra-plot` command for generating 6-panel summary figures

High split-half reliability (r = .86 Spearman-Brown corrected), suitable for individual-differences research.

**Citation:** Allen, M. (2026). [respyra: A General-Purpose Respiratory Tracking Toolbox for Interoception Research](https://osf.io/preprints/psyarxiv/wjuce_v1). *PsyArXiv*.

---

### GastroPy

<a href="https://github.com/embodied-computation-group/gastropy"><i class="fab fa-github"></i> GitHub</a>

A Python package providing a modular pipeline for electrogastrography (EGG) signal processing and gastric-brain coupling analysis. Designed for researchers studying gastric electrical activity and its relationship to brain imaging data.

- **Signal Processing**: Power spectral density, bandpass filtering (FIR/IIR), Hilbert-transform phase extraction, cycle detection, and artifact handling
- **Metrics & Analysis**: Gastric frequency band classification, instability coefficients, cycle statistics, and quality assessment
- **fMRI Integration**: Scanner trigger detection, volume windowing, confound regression, voxelwise BOLD phase extraction, and PLV map computation with NIfTI support
- **Coupling Analysis**: Phase-locking values, surrogate testing, and circular statistics (Rayleigh tests, resultant length)
- **High-Level Pipeline**: One-liner `egg_process()` function for complete workflow automation
- **Visualization**: Publication-ready PSD plots, 4-panel EGG overviews, cycle histograms, and brain coupling maps

**Citation:** Allen, M. (2026). GastroPy: A Python Package for Electrogastrography Signal Processing and Gastric-Brain Coupling Analysis. GitHub. [https://github.com/embodied-computation-group/gastropy](https://github.com/embodied-computation-group/gastropy)

---

### metadpy

<a href="https://github.com/embodied-computation-group/metadpy"><i class="fab fa-github"></i> GitHub</a>

A Python library for Bayesian modeling of behavioral metacognition, providing the Python equivalent to the hMeta-d toolbox. Computes standard signal detection theory indices and metacognitive efficiency measures from trial-level performance and confidence ratings.

- **Signal Detection Theory**: d-prime, criterion, hit/false alarm rates, ROC-AUC
- **Meta-d' Estimation**: Maximum likelihood estimation of metacognitive sensitivity
- **Hierarchical Bayesian Models**: Hierarchical meta-d' via Hamiltonian Monte Carlo (NUTS), powered by PyMC and PyTensor
- **Simulation Tools**: Response simulation for generating synthetic metacognition datasets
- **Visualization**: Specialized plotting functions for metacognitive data
- **Pandas Integration**: Statistical functions callable directly as DataFrame methods

**Citations:**
- Fleming, S. M. (2017). [HMeta-d: hierarchical Bayesian estimation of metacognitive efficiency from confidence ratings](https://doi.org/10.1093/nc/nix007). *Neuroscience of Consciousness*, 3(1), nix007.
- Maniscalco, B. & Lau, H. (2012). [A signal detection theoretic approach for estimating metacognitive sensitivity from confidence ratings](https://doi.org/10.1016/j.concog.2011.09.021). *Consciousness and Cognition*, 21(1), 422--430.

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

**Citation:** Courtin, A. S., Ehmsen, J. F., Banellis, L., Fardo, F., & Allen, M. G. (2025). [Hierarchical Bayesian Modelling of Interoceptive Psychophysics](https://doi.org/10.1101/2025.08.27.672360). *bioRxiv*.

---

### Respiratory Resistance Sensitivity Task (RRST)

<a href="https://github.com/embodied-computation-group/RespiroceptionMethodsPaper"><i class="fab fa-github"></i> GitHub</a>

An automated method for measuring respiratory interoception using a fully 3D-printable apparatus. Key features:

- **Psychophysical Assessment**: Forced-choice discrimination task comparing breaths with varying airway obstruction
- **Efficient Measurement**: Bayesian staircase procedure (Psi) achieves threshold convergence in 20-50 trials
- **Metacognitive Assessment**: Evaluates confidence in perceptual judgments
- **Accessible Design**: 3D-printable components eliminate need for expensive medical equipment

High test-retest reliability with minimal participant discomfort, completing full assessment in 30-45 minutes.

**Citation:** Nikolova, N., Harrison, O., Toohey, S., Brændholt, M., Legrand, N., Correa, C., Vejlø, M., Jensen, M. S., Fardo, F., & Allen, M. (2022). [The respiratory resistance sensitivity task: An automated method for quantifying respiratory interoception and metacognition](https://doi.org/10.1016/j.biopsycho.2022.108325). *Biological Psychology*, 170, 108325.

---

### Raincloud Plots

<a href="https://github.com/RainCloudPlots/RainCloudPlots"><i class="fab fa-github"></i> GitHub</a> &nbsp; <a href="https://github.com/jorvlan/raincloudplots"><i class="fab fa-github"></i> R Package</a>

A data visualization method combining raw data, probability density, and summary statistics into a single plot. Created by Micah Allen, Raincloud Plots offer a robust alternative to bar charts and box plots that reduces information loss while maintaining clarity.

- **Multi-language Support**: Available in R (`ggrain`, `raincloudplots`), Python (`PtitPrince`), and MATLAB
- **Publication-Ready**: Produces beautiful, statistically valid visualizations with minimal code
- **Repeated Measures**: Supports individually linked data points across conditions and time points
- **Flexible Designs**: Handles 1x1, 2x2, 2x3, and between/within-subject experimental designs

**Citations:**
- Allen, M., Poggiali, D., Whitaker, K., et al. (2021). [Raincloud plots: a multi-platform tool for robust data visualization](https://doi.org/10.12688/wellcomeopenres.15191.2). *Wellcome Open Research*, 4:63.
- Judd, N., Langen, J. van, Poggiali, D., Whitaker, K., Marshall, T. R., Allen, M., & Kievit, R. (2024). [ggrain—A ggplot2 extension for raincloud plots](https://doi.org/10.1101/2024.12.13.628294). *bioRxiv*.

---

## Contact

For questions about our tools and resources:

- **General inquiries:** [micah@cfin.au.dk](mailto:micah@cfin.au.dk)
- **Bluesky:** [@the-ecg.org](https://bsky.app/profile/the-ecg.org)
- **Twitter:** [@visceral_mind](https://twitter.com/visceral_mind)
