---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

InteractionRCS R Package Development and Extensions
======

Statistical interpretations in regression models often encounter intricate interactions with continuous covariates. The interactionRCS R package, first developed in 2022, provides a refined tool to decode such complexities using restricted cubic splines. Our ongoing research aims for a more adaptable package, capable of embracing a multitude of spline techniques and accommodating varying regression model, ensuring the package's adaptability to any knot configuration. This initiative is part of a broader exploration at the TIMI Study Group, Harvard Medical School, intersecting the domains of applied clinical research and advanced statistical methodologies.

GitHub Repository: [https://github.com/gmelloni/interactionRCS]

### Example 1 from Initial Package Version: 

The first example is based on a study on drug relapse among 575 patients enrolled in a clinical trial of residential treatment for drug abuse. The main exposure of interest is the binary indicator of assigned treatment (0/1) and a treatment*age interaction is specified.

The following code provides an estimate of the treatment HR at different ages, when age is modeled with restricted cubic splines. The model is further adjusted for tumor site, race, and previous use of IV drug. It is recommended to check the distribution of $Z$ (here, age) to define a realistic range of `var2values`. Finally, the code is replicated by using the delta method or bootstrap for obtaining confidence intervals. Note that when `ci.method = "bootstrap"` is specified, additional options can be specified.

```{r , warning=FALSE, message=FALSE}

myformula <- Surv(time, censor) ~ treat*rcs(age, 3) + site + nonwhite + ivdrug
model_rcs <- cph(myformula , data = umaru , x = TRUE , y=TRUE)

HR_rcs_delta <- intEST( var2values = c(20:50)
                     , model = model_rcs , data = umaru , var1 ="treat", var2="age" ,ci.method = "delta")

plotINT(HR_rcs_delta , xlab = "Age")
```
<br>
<br>

![Package Visualization](/images/InteractionRCS_Example_knot_3_3.png)



### Extension 

The initial version of the package was designed to support a maximum of 3 knots for the cubic spline term. Building on equations from Chapter 2-23 of Harrell’s book, we have now enhanced the package to accommodate more than 3 knots in the cubic spline term. This enhancement is compatible with all three primary function types (linear, logistic, Cox). Additionally, in scenarios with more than 3 knots, the package now offers support for both delta and bootstrapping techniques for CI computation and allows users to specify hard-coded knot positions.



### Example 2 from Extended Package Version: 

The second example is based on the same data, but extended to support 4 knots for age modeled with restricted cubic splines in cph function, with CI constructed by delta method.

```{r , warning=FALSE, message=FALSE}

myformula <- Surv(time, censor) ~ treat*rcs(age, 4) + site + nonwhite + ivdrug
model <- cph(myformula , data = umaru)

umaru_knot4_delta <- rcsHR( var2values = 20:56
       , model = model , data = umaru , var1 ="treat", var2="age"
        , ci=TRUE , conf = 0.95 , ci.method = "delta")

plotINT2(umaru_knot4_delta , xlab = "Age",ylim=c(0,3))
```
![Package Visualization](/images/InteractionRCS_Example_knot_4_3.png)

### Example 3 from Extended Package Version: 

The third example is based on the same data, but extended to support 5 hard-coded knots for age modeled with restricted cubic splines in coxph function, with CI constructed by bootstrapping method.

```{r , warning=FALSE, message=FALSE}

myformula <- Surv(time, censor) ~ treat*rcs(age, c(23, 28, 32, 36, 43)) + site + nonwhite + ivdrug
model <- coxph(myformula , data = umaru)

umaru_coxph_hc_knot5_boot <- rcsHR( var2values = 20:56
       , model = model , data = umaru , var1 ="treat", var2="age"
        , ci=TRUE , conf = 0.95 , ci.method = "bootstrap")

plotINT2(umaru_coxph_hc_knot5_boot , xlab = "Age",ylim=c(0,3))
```
<br>
<br>

![Package Visualization](/images/InteractionRCS_Example_knot_5.png)







Outcome Prediction under Dynamic and Time-Varying Treatment Regimes
======
Healthcare often grapples with fluctuating treatment strategies. Tailoring treatment plans as dynamically as they evolve is crucial in maintaining the efficiency of patient care. Our research delves into developing deep learning techniques to realize this vision. A pivotal piece in this endeavor was established by a novel approach based on G-computation for outcome predictions under changing treatment regimes. We're currently pushing boundaries by integrating probabilistic models to further personalize these predictions, setting a new paradigm for patient care.

Inspired by G-Net Structure from Li, R., Hu, S., Lu, M., Utsumi, Y., Chakraborty, P., Sow, D.M., Madan, P., Li, J., Ghalwash, M., Shahn, Z. & Lehman, L.. (2021). [G-Net: a Recurrent Network Approach to G-Computation for Counterfactual Prediction Under a Dynamic Treatment Regime](https://proceedings.mlr.press/v158/li21a.html). *Proceedings of Machine Learning for Health*, in *Proceedings of Machine Learning Research* 158:282-299.:




We investigated two distinct values of p. Initially, we selected p equal to the count of modeled variables, leading to a method where each variable gets its own unique model, termed as the "one variable per box" method. In this strategy, each box is developed and refined independently of the others. Conversely, in our next approach, we set p at 2, which we will describe as the "two-box" architecture.

We implemented the 1-box model on the CVSIM dataset, contrasting it from the MIMIC data, to demonstrate the model's versatility and broad application. Our analysis allowed us to compare the 1-box and 2-box models, specifically looking at the individual-level RMSE for counterfactual predictions.



