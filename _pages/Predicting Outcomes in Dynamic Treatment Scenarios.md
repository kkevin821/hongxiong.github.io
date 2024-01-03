---
layout: archive
title: "Patient Outcomes Predictions under Dynamic and Time-Varying Treatment Regimes"
permalink: /Outcome_Predictions/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}
# Research Motivation

Healthcare often grapples with fluctuating treatment strategies. Tailoring treatment plans as dynamically as they evolve is crucial in maintaining the efficiency of patient care. Our research delves into developing deep learning techniques to realize this vision. A pivotal piece in this endeavor was established by a novel approach based on G-computation for patient outcome predictions under changing treatment regimes. We're currently pushing boundaries by integrating probabilistic models to further personalize these predictions, setting a new paradigm for patient care.

# Research Context

We continued our study based on G-Net framework proposed by Li, R., Hu, S., Lu, M., Utsumi, Y., Chakraborty, P., Sow, D.M., Madan, P., Li, J., Ghalwash, M., Shahn, Z. & Lehman, L.. (2021) regarding [G-Net: a Recurrent Network Approach to G-Computation for Counterfactual Prediction Under a Dynamic Treatment Regime](https://proceedings.mlr.press/v158/li21a.html):

![G-Net Visualization](/images/G-Net.png)

In our research, we apply G-computation within observational studies to achieve two main goals: (1) to learn how patient data variables, known as covariates, distribute over time based on past information, and (2) to estimate what might happen under different treatment plans using this learned information. The G-Net framework, based on G-computation mechanism, uses deep learning models to determine these covariate distributions.

We've approached the analysis of covariate distributions by dividing the data into separate groups. In one method, each covariate is modeled individually — this is the 'one variable per box' approach. In another, we've grouped covariates into two categories, which we refer as the 'two variable per box' approach, to model joint distribution from continuous and categorical covariates respectively.

# Research Output

•	Megan Su*, Stephanie Hu*, Hong Xiong*, Amelia Hu, Elias Baedorf Kassis, Zach Shahn, Li-wei Lehman. *Counterfactual Sepsis Outcome Prediction Under Dynamic and Time-Varying Treatment Regimes*. In AMIA 2024 Informatics Summit. [Regular Paper] [Accepted].                                           
                                  (* Indicates co-first authorship)

• Ongoing paper about Transformer and GPT Architecture in Outcome Prediction under Dynamic and Time-Varying Treatment Regimes.

# Research Contribution

## Generalizability of "One Variable Per Box" Long Short-Term Memory (LSTM) framework from MIMIC dataset to CVSim Dataset

### Technical Challenges

* Adapted a "one variable per box" LSTM framework, initially based on the G-Net framework, for the CVSim dataset.
* Achieved counterfactual predictions and confirmed the model's generalizability.
* Faced a significant challenge due to dataset differences between MIMIC and CVSim.
  * Training involved one-step ahead prediction on both datasets.
  * MIMIC's test dataset required single timestamp predictions, while CVSim required predicting a later segment of multi-dimensional data.

### Solutions 

* Overhauled the model's data preprocessing and Monte Carlo simulation structure.
* Conducted extensive rewriting and iterative testing.
* Identified two key issues through in-depth analysis of LSTM structure:
  * Inconsistencies in data features and statistical distributions necessitated adjustments during data preprocessing.
  * The need to update the hidden state with complete historical data to avoid bias.
* Reworked the model to ensure full historical timeline consideration in predictions.
* Achieved successful application of the sequential LSTM framework to the CVSim dataset.

## Applications of Natural Language Processing (NLP) Techniques in Time-Series Counterfactual Predictions on Patient Outcomes

* Implemented a sequential Transformer and GPT framework, termed "two variable per box" Transformer and GPT, for the CVSim dataset.
* Attained counterfactual predictions with lower individual-level RMSE than the "two variable per box" LSTM.
* Demonstrated the effective cross-disciplinary application of NLP techniques in time-series analysis.
* Emphasized the importance of model adaptability across databases for enhancing medical treatment strategies and patient outcomes.

# Research Presentation

Given confidentiality of our ongoing work, more findings will be presented after the publications. Thanks for the understanding.  
