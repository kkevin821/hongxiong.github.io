---
layout: archive
title: "interactionRCS R Package Development and Extensions"
permalink: /interactionRCS_Package/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}
# Research Initiative

Statistical interpretations in regression models often encounter intricate interactions with continuous covariates when modeled by restricted cubic splines. The interactionRCS R package, first developed in 2022, provides a refined tool to decode such complexities and facilitate interpretation of model results, with maximum number of knots to be three. Our ongoing research aims for a more adaptable package, capable of embracing a multitude of spline techniques and accommodating varying regression model, ensuring the package's adaptability to any knot configuration. This initiative is part of a broader exploration at the TIMI Study Group, Harvard Medical School, intersecting the domains of applied clinical research and advanced statistical methodologies.

# Research Output

Features from initial version of interactionRCS Package:
* Support for various regression models (linear, logistic, Cox) up to three knots 
* Support for confidence interval calculation under delta and bootstrapping methods up to three knots
* Support user-defined knot positions up to three knots

Features added to final version of interactionRCS Package:
* Flexibility to handle any number of knots
* Flexibility in the order of inputting regression formula for any number of knots
* Support for various regression models (linear, logistic, Cox) when number of knots exceeds three
* Support for confidence interval calculation under delta and bootstrapping methods when number of knots exceeds three
* Support user-defined knot positions when number of knots exceeds three

CRAN Package: [InteractionRCS](https://cran.r-project.org/web/packages/interactionRCS/index.html)

GitHub Repository: [InteractionRCS](https://github.com/gmelloni/interactionRCS)

# Research Procedure

## Mathematical Derivation

As demonstrated by [vignette](https://raw.githack.com/gmelloni/interactionRCS/main/inst/extdata/vignette.html) here, interactionRCS requires results from a regression model where an interaction between a main predictor (binary or continuous) X and a continuous predictor Z has been specified. We are interested in the interaction setting where the continuous covariate Z is flexibly modeled by restricted cubic splines, with more than 3 knots.

Based on Harrell’s book (chapter 2-23), we derived equations for generic Cox model with more than 3 knots. 

![Math Visualization](/images/InteractionRCS_Math.png)

Then, the Cox model results where interaction with continuous covariate Z modeled by restricted cubic splines can be derived as following:

![Math Visualization 2](/images/InteractionRCS_interaction.png)

** Linear and Logistic models will follow the similar pattern. ** 

## Package Development

### Complex Mathematical Modeling
To overcome the intricacies involved with complex mathematical expressions when the knot count exceeded three, I engineered a way to translate intricate expressions into executable R code by harnessing nested loops and iterative computations. More details could be referred from [InteractionRCS GitHub Repository](https://github.com/gmelloni/interactionRCS).

### User-defined Knot Positions
The rcs() function in R only requires the number of knots to be specificied, and sets knots location automatically. However, we understand users might hope to define their own knots locations in order to be more aligned with their research context. I continued to add support to this customization when number of knots exceeded three. To parse user-input equations, I applied regular expression through previous self-learning in Python and translate the logic into R. Based on whether the equation for knot locations was customized or not, corresponding analyses were performed. 

### Confidence Interval Calculation under Delta and Bootstrapping Method
The confidence interval calculation under delta and bootstrapping method becomes more complicate as number of knots exceeded three, as we can see from the mathematical derivation above. I followed the logic from original package and extended the function to extract corresponding terms given an arbitrary number of knots, with global variable setting and iterative computation. 

### Performance Testing
After finalizing the package, I compiled a comprehensive report to test package performance under various regression model types (linear, logistic, Cox), number of knots (from three to six), type of knot configuration (hard-coded or not), different datasets (umaru,etc), under both delta and bootstrapping methods. The validity of our package was confirmed. 

## Outcome and Impact
The culmination of our efforts was the launch of an upgraded "interactionRCS" package on CRAN. This upgrade has notably refined the interpretation and presentation of regression models, particularly those that entail interactions with continuous covariates via restricted cubic splines. Our research product now significantly aids users in deciphering and applying complex statistical models.

# Research Presentation

## Example 1 from Initial Package Version [cph function with 3 Knots under Delta Method]: 

As demonstrated by [vignette](https://raw.githack.com/gmelloni/interactionRCS/main/inst/extdata/vignette.html), the first example is based on a study on drug relapse among 575 patients enrolled in a clinical trial of residential treatment for drug abuse. The main exposure of interest is the binary indicator of assigned treatment (0/1) and a treatment*age interaction is specified.

The following code provides an estimate of the treatment HR at different ages, when age is modeled with restricted cubic splines. The model is further adjusted for tumor site, race, and previous use of IV drug. It is recommended to check the distribution of $Z$ (here, age) to define a realistic range of `var2values`. Finally, the code is replicated by using the delta method or bootstrap for obtaining confidence intervals. Note that when `ci.method = "bootstrap"` is specified, additional options can be specified.

```r

myformula <- Surv(time, censor) ~ treat*rcs(age, 3) + site + nonwhite + ivdrug
model_rcs <- cph(myformula , data = umaru , x = TRUE , y=TRUE)

HR_rcs_delta <- intEST( var2values = c(20:50)
                     , model = model_rcs , data = umaru , var1 ="treat", var2="age" ,ci.method = "delta")

plotINT(HR_rcs_delta , xlab = "Age")
```

<br>
<br>

![Package Visualization](/images/InteractionRCS_Example_knot_3_3.png)


## Example 2 from Extended Package Version [cph function with 4 Knots under Delta Method]: 

The second example is based on the same data, but extended to support 4 knots for age modeled with restricted cubic splines in cph function, with CI constructed by delta method.

```r 

myformula <- Surv(time, censor) ~ treat*rcs(age, 4) + site + nonwhite + ivdrug
model <- cph(myformula , data = umaru)

umaru_knot4_delta <- rcsHR( var2values = 20:56
       , model = model , data = umaru , var1 ="treat", var2="age"
        , ci=TRUE , conf = 0.95 , ci.method = "delta")

plotINT2(umaru_knot4_delta , xlab = "Age",ylim=c(0,3))
```
![Package Visualization](/images/InteractionRCS_Example_knot_4_3.png)

## Example 3 from Extended Package Version [coxph function with 5 Hard-coded Knots under Bootstrapping Method]: 

The third example is based on the same data, but extended to support 5 hard-coded knots for age modeled with restricted cubic splines in coxph function, with CI constructed by bootstrapping method.

```r

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


** The package provides similar support for Linear and Logistic models. ** 






Outcome Prediction under Dynamic and Time-Varying Treatment Regimes
======
Healthcare often grapples with fluctuating treatment strategies. Tailoring treatment plans as dynamically as they evolve is crucial in maintaining the efficiency of patient care. Our research delves into developing deep learning techniques to realize this vision. A pivotal piece in this endeavor was established by a novel approach based on G-computation for outcome predictions under changing treatment regimes. We're currently pushing boundaries by integrating probabilistic models to further personalize these predictions, setting a new paradigm for patient care.

Inspired by G-Net Structure from Li, R., Hu, S., Lu, M., Utsumi, Y., Chakraborty, P., Sow, D.M., Madan, P., Li, J., Ghalwash, M., Shahn, Z. & Lehman, L.. (2021). [G-Net: a Recurrent Network Approach to G-Computation for Counterfactual Prediction Under a Dynamic Treatment Regime](https://proceedings.mlr.press/v158/li21a.html). *Proceedings of Machine Learning for Health*, in *Proceedings of Machine Learning Research* 158:282-299.:

![G-Net Visualization](/images/G-Net.png)


We investigated two distinct values of p. Initially, we selected p equal to the count of modeled variables, leading to a method where each variable gets its own unique model, termed as the "one variable per box" method. In this strategy, each box is developed and refined independently of the others. Conversely, in our next approach, we set p at 2, which we will describe as the "two-box" architecture.

We implemented the one-box model on the CVSIM dataset, contrasting it from the MIMIC data, to demonstrate the model's versatility and broad application. Our analysis allowed us to compare the one-box and two-box models, specifically looking at the individual-level RMSE for counterfactual predictions. For MIMIC dataset, we make both one and two box model supportive of pre-training on larger dataset, and also delayed predictions. This results in an organized model performance comparison, 



