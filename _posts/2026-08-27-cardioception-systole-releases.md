---
title: "Cardioception 0.7.0 and systole 0.3.2"
description: "New releases of cardioception and systole with simple pip installation, current Python and PsychoPy support, practical HRD tutorials, and an important heart-rate correction."
categories: blog
author: Micah G. Allen
author_url: /people/micah_allen/
header-img: images/post/toolbox-releases-2026/combined-logos.png
---

<div class="hero">
<p><img src="/images/post/toolbox-releases-2026/combined-logos.png" alt="The cardioception and systole logos side by side" /></p>
</div>

Today we are releasing new versions of both of our open-source cardiac interoception toolboxes. [**cardioception 0.7.0**](https://github.com/embodied-computation-group/Cardioception) provides the Heart Rate Discrimination task and the Heartbeat Counting task in PsychoPy. [**systole 0.3.2**](https://github.com/embodied-computation-group/systole) handles the cardiac and respiratory signal processing underneath them.

Both packages now install with one pip command each on current Python. Cardioception works with the current PsychoPy release, and its documentation now covers the full route from running a task to fitting a model. There is also an important fix to systole's cardiac signal processing, which we describe below.

## Installing

Installation should be boring. It now is, thanks to two new package releases on PyPI:

```bash
pip install cardioception-toolbox
pip install systole-core
```

The import names have not changed. `import cardioception` and `import systole` work exactly as before, so existing task and analysis code does not need to be edited. Only the installation command is different.

Cardioception now runs on **Python 3.10 or 3.11 with PsychoPy 2026.2.2**. The Python bounds are now declared properly, so pip will reject an unsupported version immediately instead of failing halfway through a build.

There is also a new `cardioception-check` command for testing your recording device before a participant is sitting in front of it. A new CI job follows the documented installation route on every change, which should stop those instructions quietly drifting out of date again.

## Documentation, rebuilt

The larger job in this release was the cardioception documentation. The new documentation is organised around the questions people actually bring to it:

- [**User guide**](https://www.the-ecg.org/Cardioception/user_guide.html): installation, conda environments, dependencies, recording devices, and running a task.
- [**Theory**](https://www.the-ecg.org/Cardioception/measuring.html): what the two tasks measure, and why we recommend the HRD rather than heartbeat counting for new studies.
- [**Tutorials**](https://www.the-ecg.org/Cardioception/tutorials/): four practical analyses that run from raw task output through fitted models.
- [**API**](https://www.the-ecg.org/Cardioception/api.html) and [**Cite**](https://www.the-ecg.org/Cardioception/cite.html): task functions and parameters, plus the references to use in a publication.

The tutorials run in sequence:

- **Inspecting and plotting data**: load sessions, check missing data, and inspect the staircase and confidence distributions, in both Python and R.
- **The psychophysical model**: understand threshold, slope, and lapse rate, then fit a single participant.
- **Hierarchical modelling**: fit all participants together and test covariates and between-group effects.
- **Metacognition**: model confidence ratings and test whether confidence tracks accuracy.

For the modelling itself, the tutorials use the [Hierarchical Interoception toolbox](https://github.com/embodied-computation-group/Hierarchical-Interoception), which we describe in our recent paper in *Behavior Research Methods* (Courtin et al., 2026). It provides hierarchical psychometric models for HRD and RRST data in Stan and brms, tested with parameter recovery. It also includes normative priors from large reference datasets and a power-analysis suite for deciding how many participants and trials you need.

The site now has working search and cross-references, and a much cleaner structure. Systole's documentation received the same overdue clean-up: broken images and stale badges are fixed, examples are cached so the site builds quickly, and everything now lives at [the-ecg.org](https://www.the-ecg.org/).

## Please check old `heart_rate()` analyses

One systole fix deserves more than a line in a changelog because it can affect results.

`heart_rate()` was applying a samples-to-milliseconds conversion to interval inputs that were already expressed in milliseconds. At any sampling rate other than 1000 Hz, that silently rescaled the resulting heart-rate series. For example, a true 60 bpm signal could be returned as 30 bpm at 500 Hz.

The function now handles each input type correctly and raises an error rather than guessing when a combination is ambiguous.

**If you used `heart_rate()` with interval input and a sampling rate other than 1000 Hz, please rerun that analysis with systole 0.3.2.**

## Other systole fixes

Systole had also accumulated several compatibility problems as the scientific Python stack moved on. Bokeh 3, NumPy 2.5, and pandas 3.0 each removed an API that systole depended on, breaking the plotting backend, frequency-domain analysis, and respiration peak detection. Those paths are working again.

We also fixed a crash on short respiration recordings and a misaligned rejection mask in `to_epochs`. Thanks to [@m-guggenmos](https://github.com/m-guggenmos) for reporting the latter.

## Links

- cardioception: [GitHub](https://github.com/embodied-computation-group/Cardioception) · [documentation](https://www.the-ecg.org/Cardioception/) · [installation guide](https://www.the-ecg.org/Cardioception/installation.html)
- systole: [GitHub](https://github.com/embodied-computation-group/systole) · [documentation](https://www.the-ecg.org/systole/)

Issues and pull requests are very welcome. Several fixes in these releases began with users reporting behaviour that we had missed. Please keep them coming.

## Citation

> Legrand, N., Nikolova, N., Correa, C., Brændholt, M., Stuckert, A., Kildahl, N., Vejlø, M., Fardo, F., & Allen, M. (2022). The heart rate discrimination task: A psychophysical method to estimate the accuracy and precision of interoceptive beliefs. *Biological Psychology*, 168, 108239. [https://doi.org/10.1016/j.biopsycho.2021.108239](https://doi.org/10.1016/j.biopsycho.2021.108239)

> Legrand, N., & Allen, M. (2022). Systole: A Python package for cardiac signal synchrony and analysis. *Journal of Open Source Software*, 7(69), 3832. [https://doi.org/10.21105/joss.03832](https://doi.org/10.21105/joss.03832)

> Courtin, A. S., Ehmsen, J. F., Banellis, L., Fardo, F., & Allen, M. G. (2026). Hierarchical Bayesian modeling of interoceptive psychophysics. *Behavior Research Methods*, 58(9), 260. [https://doi.org/10.3758/s13428-026-03137-3](https://doi.org/10.3758/s13428-026-03137-3)
