---
layout: archive
title: "Multimodal Search Model for Patches from Whole Slide Imaging (WSI) Based on Pathological Captions"
permalink: /Search_Model/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}
# Research Initiative


The motivation for developing a search model that evaluates the similarity of WSI patches stems from the pressing need to enhance the precision and efficiency of histopathological assessments in cancer research and diagnostics. Lung adenocarcinoma, being one of the most common and deadly forms of lung cancer, presents vast histological heterogeneity, making the identification of prognostic and diagnostic markers a complex task.

The ability to quickly and accurately retrieve histological patterns from a vast database like TCGA based on specific textual descriptions can significantly streamline the workflow of pathologists and researchers. This model would not only expedite the review of relevant cases, potentially improving the speed and accuracy of diagnoses but also facilitate a deeper understanding of the disease by correlating specific histopathological features with clinical outcomes.

# Research Context

We continued our study based on Contrastive Captioners (CoCa) architecture proposed by Yu, J., Wang, Z., Vasudevan, V., Yeung, L., Seyedhosseini, M., & Wu, Y. (2022) regarding [CoCa: Contrastive Captioners are Image-Text Foundation Models](https://arxiv.org/abs/2205.01917):


![G-Net Visualization](/images/G-Net.png)

In our research, we apply G-computation within observational studies to achieve two main goals: (1) to learn how patient data variables, known as covariates, distribute over time based on past information, and (2) to estimate what might happen under different treatment plans using this learned information. The G-Net framework, based on G-computation mechanism, uses deep learning models to determine these covariate distributions.

We've approached the analysis of covariate distributions by dividing the data into separate groups. In one method, each covariate is modeled individually — this is the 'one variable per box' approach. In another, we've grouped covariates into two categories, which we refer as the 'two variable per box' approach, to model joint distribution from continuous and categorical covariates respectively.

# Research Output

•	Megan Su*, Stephanie Hu*, Hong Xiong*, Amelia Hu, Elias Baedorf Kassis, Zach Shahn, Li-wei Lehman. Counterfactual Sepsis Outcome Prediction Under Dynamic and Time-Varying Treatment Regimes. In AMIA 2024 Informatics Summit. [Regular Paper] [Submitted]. (* Indicates co-first authorship)

• Ongoing paper about Transformer and GPT Architecture in Outcome Prediction under Dynamic and Time-Varying Treatment Regimes


# Research Contribution

## Generalizability of "One Variable Per Box" Long Short-Term Memory (LSTM) framework from MIMIC dataset to CVSim Dataset

Leveraging my understanding of deep learning and Python programming skills, I adapted a sequential LSTM framework, known as "one variable per box" LSTM in our research context, based on G-Net framework, for use with the CVSim dataset, thereby achieving counterfactual predictions and demonstrating the model's generalizability. Originally designed for the MIMIC database, the biggest challenge in adapting the model to the CVSim dataset was the test dataset difference. While the model training utilized a one-step ahead prediction approach on both datsets, the test dataset for MIMIC only provided a single timestamp, requiring prediction across all time points for patients. For the CVSim dataset expansion I was tasked with, the downstream task evolved to predict a later segment of multi-dimensional data based on a history of timestamps.

This change necessitated a complete overhaul of the original model's data preprocessing and Monte Carlo simulation structure, requiring extensive rewriting and iterative testing. Initially, I could not achieve the desired prediction curves, but after a deep dive into the LSTM structure and overall model architecture, I pinpointed two key issues. The first was the inconsistency in data features and statistical distributions between the two datasets, which required informing the model of the corresponding historical timeline length during data preprocessing. The second issue was that the original model on the MIMIC data analyzed only the most recent time points, leading to an oversight of the complete historical timeline in the CVSim adaptation and resulting biases. By further dissecting and reworking the model, I ensured that each prediction updated the hidden state with both historical data and predicted values, thus considering the full past timeline. Following these improvements, we successfully applied the sequential LSTM framework from the MIMIC database to the CVSim dataset, validating the model's generalizability and practical application value.


## Applications of Natural Language Processing (NLP) Techniques in Time-series Counterfactual Predictions on Patient's Outcomes

Furthering the previous work, I adapted a sequential Transformer framework, known as "two variable per box" Transformer in our research context for the CVSim dataset, achieving counterfactual predictions with a lower individual-level Root Means Square Error (RMSE) than the sequential LSTM framework, known as "two variable per box" LSTM in our research context. This highlighted the cross-disciplinary application of natural language processing models in time-series analysis, a significant aspect of my work. The ability to broadly apply models across different databases and maintain high accuracy in counterfactual predictions is vital for transforming medical practice and supporting physicians in offering optimal treatment strategies to improve patient survival rates.


# Research Presentation

Given confidentiality of our ongoing work, more findings will be presented after the publications. Thanks for the understanding.  
