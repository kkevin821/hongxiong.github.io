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

For decades, researchers have used the log-rank test/Cox’s hazard ratio (HR) test/estimation approach as the standard primary analysis for clinical trials with time-to-event outcomes. Despite its common use, the HR does not provide robust, reliable, and clinically interpretable quantitative information about the risks and benefits of a new treatment. To address this, we recently developed "average hazard" (AH) --- a new summary measure of the event time distribution (Uno and Horiguchi, Statistics in Medicine 2023), which has great potential to change the traditional analytic practice and significantly improve the interpretation of the magnitude of treatment effect on time-to-event outcomes. We aim to make AH-based methods available in various clinical research settings. 

# Research Context

We continued our study based on concept of Average Hazard with Survival Weight proposed by Uno, H., & Horiguchi, M. (2023) regarding [Ratio and difference of average hazard with survival weight: New measures to quantify survival benefit of new therapy](https://doi.org/10.1002/sim.9651).

The concept of Average Hazard with Survival Weight (AH-SW) serves as a summary metric of event time distribution and will use difference in AH-SW (DAH-SW) or ratio of AH-SW (RAH-SW) to quantify the treatment effect magnitude. The AH-SW is interpreted as a person-time incidence rate that does not depend on random censoring. It is defined as the ratio of cumulative incidence probability and restricted mean survival time (RMST), which can be estimated non-parametrically. 


# Research Output

•	Simulation study results about performance of AH-SW under different confounding adjustment methods, like Inverse Propensity Weighted Estimator
(IPTW), etc. We are preparing a paper to present the validity of our innovative summary metric in survival analysis.  

• Analytical variance of RAH-SW and DAH-SW adjusted by Inverse Propensity Weighted Estimators (IPTW) and Augmented Inverse Propensity Weighted Estimator (AIPTW). 

# Research Flowchart

![Flowchart](/images/AH_Flowchart_2.png)

* We are interested in four metrics under different experimental scenarios: Group 0 Average Hazard (AH), Group 1 (AH), Difference in AH, and Difference in log(AH), which can also be interpreted as ratio of AH in log term.
* We designed two event patterns: Whether exponential-based hazard model is correctly specified
* We designed two covariate patterns under each event pattern: Whether certain covariates are generated through normal distribution
* We designed five settings under each event and covariate pattern: Whether outcome and treatment model are correctly specified 

# Research Contribution

## Simulation Study about Performance of AH-SW under Different Confounding Adjustment Methods

### Cluster Computing

Due to the large computational workload, I needed to perform distributed computing using parallel jobs on a cluster. This required a proficient understanding of data transfer, code integration on the cluster, and writing batch scripts. However, I had not previously worked with clusters. Immediately, I took the initiative to self-learn official documents online, supplemented my understanding of the Kraken platform, and continuously debugged batch scripts based on system logs. This allowed me to utilize the cluster proficiently within two days. 

### Data Generating Function Modification

After successfully obtaining experimental results via cluster computing, my professor and I noticed that the Confidence Interval Coverage based on bootstrapping did not meet the expected 95% level. We revisited the data-generating function's underlying mathematical derivations for corrections. I realized that we had overlooked the inherent probabilistic correlations among variables. Furthermore, I assisted in identifying that the variables generated using a standard normal distribution, when adjusted with the Inverse Propensity Weighted Estimator (IPTW) method, could lead to a lack of overlap in the tail area of propensity score distributions between the treatment and non-treatment groups. This discrepancy could result in disproportionately large weights for certain subjects within the model. Consequently, I, together with my professor, explored and implemented data generation through beta distribution to refine the experimental scenarios. 

### Strategic Simulations

While working with simulations adjusted by the Augmented Inverse Propensity Weighted Estimator (AIPTW) method, I encountered errors due to matrix calculation issues in some bootstrapped samples. This problem was more severe on the cluster because it involved C++ code, which is a lower-level error that is difficult to handle directly in R code. After repeated experiments, I found that it only occurred in a very small number of bootstrapping cases and was likely due to the instability of samples. However, it would cause the entire job loop to be interrupted on the cluster, severely affecting our ability to obtain enough iterations. Since our function was based on a pre-writing package and the time cost of debugging the underlying code, I proposed to reduce the number of iterations per job and increase the number of jobs as much as possible, which would minimize the impact of crashes caused by the error and ensure that we obtain enough iterations. This adjustment proved successful and ensured the continuity and robustness of our simulation experiments.

## Analytical Variance of RAH-SW and DAH-SW Adjusted by IPTW and AIPTW

Based on theorems proposed by Wei Guanghui (2008) regarding [Semiparametric methods for estimating cumulative treatment effects in the presence of non-proportional hazards and dependent censoring](https://www.semanticscholar.org/paper/Semiparametric-methods-for-estimating-cumulative-in-Wei/14e91a87507e83d47f33cd38ea518d7c63137b26) to derive analytical varaince upon ratio of cumulative hazards and difference in RMST, we followed the mathematical logic to derive analytical variance of RAH-SW and DAH-SW under IPTW. 

Based on work by Zhang, M., & Schaubel, D. E. (2012) regarding [Contrasting treatment-specific survival using double-robust estimators](https://doi.org/10.1002/sim.5511) about asymptotic distributions for Average Causal Effect (ACE) with respect to RMST, we followed the logic to derive analytical variance of RAH-SW and DAH-SW under AIPTW. 

# Research Presentation

Given confidentiality of our ongoing work, more findings will be presented after the publications. Thanks for the understanding.  
