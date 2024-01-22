---
layout: archive
title: "Average Hazard with Survival Weight in Survival Analysis"
permalink: /Average_Hazard/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}
# Research Motivation

For decades, researchers have used the log-rank test/Cox’s hazard ratio (HR) test/estimation approach as the standard primary analysis for clinical trials with time-to-event outcomes. Despite its common use, the HR does not provide robust, reliable, and clinically interpretable quantitative information about the risks and benefits of a new treatment. To address this, we recently developed "Average Hazard" (AH) --- a new summary measure of the event time distribution (Uno and Horiguchi, Statistics in Medicine 2023), which has great potential to change the traditional analytic practice and significantly improve the interpretation of the magnitude of treatment effect on time-to-event outcomes. We aim to make AH-based methods available in various clinical research settings. 

# Research Context

We continued our study based on concept of Average Hazard with Survival Weight proposed by Uno, H., & Horiguchi, M. (2023) regarding [Ratio and difference of average hazard with survival weight: New measures to quantify survival benefit of new therapy](https://doi.org/10.1002/sim.9651).

The concept of Average Hazard with Survival Weight (AH-SW) serves as a summary metric of event time distribution and will use difference in AH-SW (DAH-SW) or ratio of AH-SW (RAH-SW) to quantify the treatment effect magnitude. The AH-SW is interpreted as a person-time incidence rate that does not depend on random censoring. It is defined as the ratio of cumulative incidence probability and restricted mean survival time (RMST), which can be estimated non-parametrically. 


# Research Output

•	Simulation study results about performance of AH-SW under different confounding adjustment methods, like Inverse Propensity Weighted Estimator
(IPTW), etc. We are preparing a paper to present the validity of our innovative summary metric in survival analysis.  

• Analytical variance of RAH-SW and DAH-SW adjusted by Inverse Propensity Weighted Estimators (IPTW) and Augmented Inverse Propensity Weighted Estimator (AIPTW). 

# Research Flowchart

![Flowchart](/images/AH_Flowchart_3.png)

* We are interested in 4 metrics under different experimental scenarios: Group 0 AH, Group 1 AH, Difference in AH, and Difference in log(AH), which can also be interpreted as ratio of AH in log term.
* We designed 2 event patterns: Different specifications of exponential-based hazard model.
* We designed 2 censoring patterns under each event pattern: Different generating mechanism of censoring time.
* We designed 5 settings under each event and covariate pattern: Whether outcome and treatment model are correctly specified. 

# Research Contribution

## Simulation Study about Performance of AH-SW under Different Confounding Adjustment Methods

### Cluster Computing

* Managed large computational workloads through distributed computing with parallel jobs on a cluster.
* Gained proficiency in data transfer, code integration on the cluster, and batch script writing.
* Self-learned the use of clusters, with a focus on the Kraken platform.
* Debugged batch scripts using system logs, achieving cluster proficiency.

### Data Generating Function Modification

* Identified Confidence Interval Coverage issues following cluster computation experiments.
* Re-examined the data-generating function to correct mathematical derivations.
* Addressed overlooked probabilistic correlations among variables.
* Adjusted variable generation from standard normal to beta distribution with IPTW to mitigate overlap issues in propensity score distributions.
* Collaborated in refining experimental scenarios to enhance data accuracy.

### Strategic Simulations

* Tackled matrix calculation errors in bootstrapped samples when using AIPTW method simulations.
* Identified error occurrence in a minimal number of bootstrapping cases, likely due to sample instability.
* Proposed and implemented a strategy to reduce iterations per job and increase the total number of jobs.
* This approach minimized the impact of errors, ensured sufficient iterations, and maintained the continuity and robustness of simulation experiments.

## Analytical Variance of RAH-SW and DAH-SW Adjusted by IPTW and AIPTW

Based on theorems proposed by Wei Guanghui (2008) regarding [Semiparametric methods for estimating cumulative treatment effects in the presence of non-proportional hazards and dependent censoring](https://www.semanticscholar.org/paper/Semiparametric-methods-for-estimating-cumulative-in-Wei/14e91a87507e83d47f33cd38ea518d7c63137b26) to derive analytical varaince upon ratio of cumulative hazards and difference in RMST, we followed the mathematical logic to derive analytical variance of RAH-SW and DAH-SW under IPTW. 

Based on work by Zhang, M., & Schaubel, D. E. (2012) regarding [Contrasting treatment-specific survival using double-robust estimators](https://doi.org/10.1002/sim.5511) about asymptotic distributions for Average Causal Effect (ACE) with respect to RMST, we followed the mathematical logic to derive analytical variance of RAH-SW and DAH-SW under AIPTW. 

# Research Presentation

Given confidentiality of our ongoing work, more findings will be presented after the publications. Thanks for the understanding.  
