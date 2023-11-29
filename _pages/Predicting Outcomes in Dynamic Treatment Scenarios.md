---
layout: archive
title: "Outcome Prediction under Dynamic and Time-Varying Treatment Regimes"
permalink: /Outcome_Predictions/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}
# Research Initiative

Healthcare often grapples with fluctuating treatment strategies. Tailoring treatment plans as dynamically as they evolve is crucial in maintaining the efficiency of patient care. Our research delves into developing deep learning techniques to realize this vision. A pivotal piece in this endeavor was established by a novel approach based on G-computation for outcome predictions under changing treatment regimes. We're currently pushing boundaries by integrating probabilistic models to further personalize these predictions, setting a new paradigm for patient care.

Based on G-Net framework from Li, R., Hu, S., Lu, M., Utsumi, Y., Chakraborty, P., Sow, D.M., Madan, P., Li, J., Ghalwash, M., Shahn, Z. & Lehman, L.. (2021). [G-Net: a Recurrent Network Approach to G-Computation for Counterfactual Prediction Under a Dynamic Treatment Regime](https://proceedings.mlr.press/v158/li21a.html). *Proceedings of Machine Learning for Health*, in *Proceedings of Machine Learning Research* 158:282-299.:

![G-Net Visualization](/images/G-Net.png)

Given data under the observational regime, G-computation allows
## (1) learns the distribution of covariates at each
timestep conditioned on the history of covariates and treatments up until that timestep, and (2) estimates the counter-
factual outcomes by simulating the data forward in time under different treatment strategies [1

we can see he G-Net framework we present here enables the use of sequential
deep learning models to estimate conditional covariate distributions in step (1), which can then be used to predict
covariate trajectories in step (2)

We have developed two types of sequential deep learning approaches to estimate expected patient trajectories and treatment outcomes under dynamic and time-varying treatment strategies. The main takeaway is to The first one is referred as "one-box" archiecture,  We investigated two distinct values of p. Initially, we selected p equal to the count of modeled variables, leading to a method where each variable gets its own unique model, termed as the "one variable per box" method. In this strategy, each box is developed and refined independently of the others. Conversely, in our next approach, we set p at 2, which we will describe as the "two-box" architecture.

# Research Output


# Research Procedure


# Research Presentation
