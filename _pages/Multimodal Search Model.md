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

The ability to quickly and accurately retrieve histological patterns from a vast database like TCGA based on specific textual descriptions can significantly streamline the workflow of pathologists and researchers. This model would not only expedite the review of relevant cases, potentially improving the speed and accuracy of diagnoses but also facilitate a deeper understanding of the disease by correlating specific histopathological features with clinical outcomes.

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

As the foundational step in building search model, data preprocessing was necessary to sample patches from each WSI based on unsupervised machine learning techniques to build the search base. Due to high inter-dependencies between packages, the original lab code for sampling was error prone. After delving into the underlying logic of this code, I rewrote the sampling script from scratch, successfully procuring the samples needed with K-means Clustering for an arbitrary number of clusters and patches.

## Constructing Multimodal Search Model Architecture 

I integrated a CoCa image encoder alongside a text encoder to generate corresponding embeddings, establishing a robust architecture for our search model. Initially, my code's inefficiency led to frequent GPU memory crashes. Under guidance from professor, I refined the code, introducing a save frequency to periodically log embedding results into an h5 file and associated slide information into a pickle file, minimizing runtime memory usage 

## Establishing Ranking System to Retrieve Top-Similar Patches

I implemented a ranking system that precisely matches WSI patches to captions based on dot similarity scores from statistical computation, enabling us to identify and retrieve the most relevant patches accurately. This application of deep learning techniques expanded my former biostatistical research and gave me a deeper understanding of the significant transformation artificial intelligence brings to healthcare.


# Research Presentation

Given we are considering to expand the scope of current research progress, more findings will be presented after further exploration. Thanks for the understanding.  
