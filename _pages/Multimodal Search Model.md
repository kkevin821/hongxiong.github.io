---
layout: archive
title: "Multimodal Search Model for Patches from Whole Slide Imaging (WSI) Based on Pathological Captions"
permalink: /Search_Model/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}
# Research Motivation

The motivation for developing a search model that evaluates the similarity of WSI patches stems from the pressing need to enhance the precision and efficiency of histopathological assessments in cancer research and diagnostics. Lung adenocarcinoma, being one of the most common and deadly forms of lung cancer, presents vast histological heterogeneity, making the identification of prognostic and diagnostic markers a complex task.

The ability to quickly and accurately retrieve histological patterns from a vast pathological database based on specific textual descriptions can significantly streamline the workflow of pathologists and researchers. This model would not only expedite the review of relevant cases, potentially improving the speed and accuracy of diagnoses but also facilitate a deeper understanding of the disease by correlating specific histopathological features with clinical outcomes.

# Research Context

My prior advanced coursework at Harvard's School of Engineering on computer vision and NLP, coupled with a project applying transfer learning with VGG16 to classify patient brain CT tumor types with 95% accuracy, laid the groundwork for this research. However, the complexity of the data escalated as we dealt with WSI in pathology, demanding proficient feature extraction via computer vision neural networks.

We continued our study based on Contrastive Captioners (CoCa) architecture proposed by Yu, J., Wang, Z., Vasudevan, V., Yeung, L., Seyedhosseini, M., & Wu, Y. (2022) regarding [CoCa: Contrastive Captioners are Image-Text Foundation Models](https://arxiv.org/abs/2205.01917):

![CoCa Visualization](/images/Coca.png)

In our research, we aim to develope a multimodal search model to retrieve top-similar WSI patches based on given pathological captions and
similarity score rankings, utilizing a pre-trained CoCa image encoder to create image embeddings and a pertained tokenizer, along with CoCa text encoder, to generate text embeddings.

# Research Output

•	Multimodal search model architecture based on pre-trained CoCa encoder. 

• Search result report based on sampled patches from WSI slides, containing pathological captions, annotated slide names, similarity rank within search base, and extracted top 3 most similar patches for each caption.

# Research Contribution

## Building Search Base through Unsupervised Machine Learning Techniques

* Initiated the search model creation by preprocessing data to sample patches from WSIs using unsupervised learning.
* Tackled the high inter-dependency errors in the original lab sampling code.
* Rewrote the sampling script to improve reliability, utilizing K-means Clustering for variable cluster and patch numbers.

## Constructing Multimodal Search Model Architecture 

* Integrated a CoCa image encoder with a text encoder to produce corresponding embeddings, enhancing the search model's architecture.
* Addressed the initial inefficiencies causing GPU memory overloads.
* Optimized the code based on professorial guidance by:
  * Implementing a save frequency for embeddings into an h5 file.
  * Logging slide information into a pickle file to reduce memory usage during runtime. 

## Establishing Ranking System to Retrieve Top-Similar Patches

* Developed a ranking system that accurately aligns WSI patches with captions using dot similarity scores.
* Facilitated precise identification and retrieval of relevant patches.
* Broadened my biostatistical research to include deep learning applications, recognizing AI's transformative potential in healthcare.

# Research Presentation

Given we are considering to expand the scope of current research progress, more findings will be presented after further exploration. Thanks for the understanding.  
