# Interactive Hypothesis Testing: Analytical vs. Bootstrap Methods

## Overview
This repository contains an interactive Python tool for spatial data analytics. It allows users to visualize and compare two methods of hypothesis testing for the difference in means between two datasets:
1.  **Analytical Method:** Welch's t-test (assumes Gaussian distribution).
2.  **Empirical Method:** Bootstrap resampling (non-parametric).

This workflow is essential for determing if two extracted sample sets come from the same population or two different populations, particularly in contexts like geological or agricultural spatial analysis.

## Methodology

### The Problem
When comparing two extracted sample sets ($x_1$ and $x_2$) with different means, we must determine if this difference is statistically significant or simply due to sampling variability.

### Method 1: Welch's t-test (Analytical)
We calculate the t-statistic assuming the variances are unequal.
* **Assumption:** Data is Gaussian distributed.
* **Statistic:**
    $$t = \frac{\overline{x}_1 - \overline{x}_2}{\sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}}$$
* **Degrees of Freedom:** Calculated using the Welch-Satterthwaite equation.

### Method 2: Bootstrap (Empirical)
Bootstrap is a powerful resampling procedure to calculate uncertainty without assuming a specific parametric distribution.
* **Workflow:**
    1. Shift both sample sets to share the global mean (enforcing the null hypothesis).
    2. Perform $L$ Monte Carlo simulations (draws with replacement).
    3. Calculate the t-statistic for every realization.
    4. Construct the sampling distribution empirically.
    5. Compare the observed t-statistic against this empirical distribution.

## Interactive Features
The Jupyter Notebook included in this repo utilizes `ipywidgets` to allow users to dynamically adjust:
* Sample sizes ($n_1, n_2$)
* Sample means ($\overline{x}_1, \overline{x}_2$)
* Sample variances ($s_1, s_2$)
* Number of bootstrap realizations ($L$)
* Significance level ($\alpha$)

## Getting Started

### Prerequisites
You will need Python installed along with the following libraries:
* `matplotlib`
* `ipywidgets`
* `numpy`
* `scipy`

### Installation
1. Clone this repository:
   ```bash
   git clone [https://github.com/YOUR_USERNAME/interactive-hypothesis-testing.git](https://github.com/YOUR_USERNAME/interactive-hypothesis-testing.git)
