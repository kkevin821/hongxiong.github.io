---
layout: archive
title: "interactionRCS R Package Development and Extensions"
permalink: /interactionRCS_Package/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}
# Research Motivation

Statistical interpretations in regression models often encounter intricate interactions with continuous covariates when modeled by restricted cubic splines. The interactionRCS R package, first developed in 2022, provides a refined tool to decode such complexities and facilitate interpretation of model results, with a limitation of up to three knots. Our ongoing research aims for a more adaptable package, capable of embracing a multitude of spline techniques and accommodating varying regression model, ensuring the package's adaptability to any knot configuration. This initiative is part of a broader exploration at the TIMI Study Group, Harvard Medical School, intersecting the domains of applied clinical research and advanced statistical methodologies.

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

# Research Context

## Mathematical Derivation

As demonstrated by [vignette](https://raw.githack.com/gmelloni/interactionRCS/main/inst/extdata/vignette.html) here, interactionRCS requires results from a regression model where an interaction between a main predictor (binary or continuous) X and a continuous predictor Z has been specified. We are interested in the interaction setting where the continuous covariate Z is flexibly modeled by restricted cubic splines, with more than 3 knots.

Based on Harrell’s book (chapter 2-23), we derived equations for generic Cox model with more than 3 knots. 

![Math Visualization](/images/InteractionRCS_Math.png)

Then, the Cox model results where interaction with continuous covariate Z modeled by restricted cubic splines can be derived as following:

![Math Visualization 2](/images/InteractionRCS_interaction.png)

**Linear and logistic models will follow the similar pattern.** 

# Research Contribution

## Package Development

### Complex Mathematical Modeling

* Addressed the complexities of mathematical expressions with more than three knots
* Developed a technique to convert complex expressions into executable R code using nested loops and iterative computations
* Further information is available at the [InteractionRCS GitHub Repository](https://github.com/gmelloni/interactionRCS)

### User-defined Knot Positions

* Implemented custom knot location functionality for when the number of knots exceeds three
* Utilized regular expressions, leveraging Python skills, to interpret user-input equations and implemented the logic in R
* Conducted analyses based on whether knot locations were user-defined or automatically set

### Confidence Interval Calculation under Delta and Bootstrapping Method

* Tackled the complexity of confidence interval calculations when the knot count surpasses three
* Extended the existing package's logic to accommodate an arbitrary number of knots
* Employed global variable settings and iterative computations to facilitate the extended functionality

### Performance Testing

* Compiled a detailed report evaluating the package’s performance across:
  * Different regression model types: linear, logistic, Cox
  * A range of knot numbers: from three to six
  * Various knot configurations: both preset and user-defined
  * Multiple datasets, such as umaru
* Conducted tests using both delta and bootstrapping methods to verify the package's accuracy and reliability

# Research Presentation

## Example 1 from Initial Package Version 
### Cph function with 3 Knots under Delta Method

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


## Example 2 from Extended Package Version 
### Cph function with 4 Knots under Delta Method 

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

## Example 3 from Extended Package Version 
### Coxph function with 5 Hard-coded Knots under Bootstrapping Method 

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


**The package provides similar support for linear and logistic models.** 

# Research Impact

The culmination of our efforts was the launch of an upgraded "interactionRCS" package on CRAN. This upgrade has notably refined the interpretation and presentation of regression models, particularly those that entail interactions with continuous covariates via restricted cubic splines. Our research product now significantly aids users in deciphering and applying complex statistical models.

**Please visit our CRAN Package [here](https://cran.r-project.org/web/packages/interactionRCS/index.html). We hope our package will contribute meaningfully to your research and look forward to your feedback.**
