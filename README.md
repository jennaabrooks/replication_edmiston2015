# Replication of Study: *What Makes Words Special? Words as Unmotivated Cues* (Edmiston & Lupyan, 2015, *Cognition*)

**Replication Author**: Jenna Brooks ([j8brooks@ucsd.edu](mailto:j8brooks@ucsd.edu))  
**Date**: May 27, 2025  

---

## Overview

This repository contains materials, code, and documentation for a replication of *Edmiston & Lupyan (2015)*. The original study examined whether verbal labels (e.g., "dog") activate broader conceptual knowledge compared to environmental sounds (e.g., a dog bark) in an image recognition task. This replication was conducted online using jsPsych and hosted on Prolific.

---

## Resources

- **[GitHub Repository](https://github.com/ucsd-psych201a/edmiston2015)**
- **[Pre-Registration](https://github.com/ucsd-psych201a/edmiston2015/tree/main/prereg)**
- **[Experiment Paradigm](https://ucsd-psych201a.github.io/edmiston2015/)**

---

## Introduction

This study investigates the "label advantage": whether verbal labels lead to faster, more abstract conceptual activation than environmental sounds. Participants were presented with auditory cues (labels or sounds) followed by an image, and asked to judge if they matched the same basic category. Reaction time was the primary measure.

---

## Methods

### Power Analysis
Sample size (n = 50) was selected to achieve 80% power based on an a priori analysis using the `simr` package.

### Participants
- Recruited via Prolific
- English speakers
- No hearing impairments

### Materials
- Cues: Spoken words and environmental sounds for 6 categories (e.g., bird, guitar)
- All audio normalized to 600ms
- Stimuli from: http://sapir.psych.wisc.edu/stimuli/MotivatedCuesExp1A-1B.zip

### Procedure
- jsPsych implementation of Experiment 1A
- Participants respond using keyboard (not game controller)
- Audio check included before trials
- 384 test trials per participant
- 50% of trials were matches

---

## Design Overview

- **Design**: 2x2 within-subjects  
  - **Cue Type**: Label vs. Sound  
  - **Match**: Yes vs. No  
- **DV**: Reaction Time (RT)

---

## Analysis Plan

### Pre-Registered Plan
- Exclude RTs < 250ms or > 1500ms
- Use Linear Mixed-Effects Regression (with `lme4`)
- Use Chi-square tests for model comparisons

### Hypotheses
- Labels will elicit fastest RTs
- Congruent sounds faster than incongruent
- Incongruent sounds elicit slowest RTs

---

## Deviations from Original Study

- Conducted online, not in lab
- Keyboard used instead of controller
- Audio environment controlled through instructions only
- Slight variations in instructions due to lack of access to originals

---

## Results Overview

### Sample
- 50 participants collected
- 42 passed QA (accuracy > 90%)

### Data Cleaning Steps
- Removed trials with RT < 250ms or > 1500ms
- Excluded incorrect or unmatched responses
- Created new `congruency` column
- Final dataset filtered and structured for modeling

### Confirmatory Analysis
- Modeled RTs for "Yes" responses on matching trials
- Condition (label, congruent sound, incongruent sound) was main predictor
- Mixed-effects model included random effects for participants and items
- Pairwise contrasts evaluated condition differences

---

## 📂 Folder Structure

```bash
├── data/
│   └── complete/           # Raw CSV data from participants
├── prereg/
│   └── preregistration.md  # Pre-registered plan
├── scripts/
│   └── analysis.R          # R analysis script
├── README.md               # This file
└── index.qmd               # Replication report (Quarto)
