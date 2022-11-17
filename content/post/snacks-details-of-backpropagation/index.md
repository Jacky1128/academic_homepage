---
title: Research Proposal towards Efficient Visual Representation Learning
subtitle: ""
date: 2022-04-14T10:21:33.473Z
draft: false
featured: false
authors:
  - ZedongWang
tags:
  - Westlake
categories:
  - Westlake
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
## **1. I﻿ntroduction**

Deep Neural Networks (DNNs) have been the de facto infrastructure in visual representation learning, which plays a pivotal role in the context of computer vision. Inspired by mammalian visual systems, Convolutional Neural Networks (CNNs), are first designed to capture neighborhood correlations hidden in observed images with convolutional inductive bias and nonlinear activations. By stacking hierarchical convolutional layers, CNNs are able to attain theoretically increasing receptive field for underlying image pattern recognition. Apart from CNNs, Vision Transformers (ViTs) are recently emerged and has achieved promising results on ImageNet. Specifically, ViT splits input images into non-overlapping fixed-size patches as visual tokens to capture long-range feature interactions among these tokens by self-attention mechanism. By introducing regional inductive bias, ViT and its variants have been extended to multifarious vision benchmarks.

Despite the remarkable advance of deep architectures in the past decade, there are still limitations of existing visual recognition pipelines, where the fundamental challenges to deal with **high image-inherent semantic sparsity** have not been well addressed. In particular, digital images are optical signals captured by sensors comprising numerous pixels as basic elements. These signals are able to reflect the real-world scenarios objectively, but accordingly own low information as well as semantic density. Correspondingly, natural language as a type of human-created data enjoys high intrinsic semantic density and expression efficiency, which has largely facilitated the development of NLP.

Therefore, the key for this problem is to improve the utilization of sparse data semantics. Accordingly, possible breakthroughs to the visual representation sparsity can be broadly divided into two aspects: **Efficient Deep Architecture Design (model-end)** and **Visual Pre-Training** **(data-end)**. 

## **2. Efficient Deep Architecture Design**

### 2.1 Preliminary

As aforementioned, how to learn robust contextual image patterns effectively is one of the main theme of high-quality visual representation learning. In this section, I first categorize two types of significant operations that are bound up with the expression capacities: *regionality perception* and *context aggregation*. Here, we assume the input feature $X$ and the output $Z$ are in the same shape $\mathbb{R}^{C\times H\times W}$. 

#### 2.1.1 Regionality Perception

Since raw images are redundant signals, operations armed with local and structural inductive biases are fundamental components in DNNs, which ensure efficiency and stability during training. I would summarize these operations and network modules that *statically* extract contextual features as *regionality perception* and define it as $Z = \mathcal{S}(X, W)$, where $\mathcal{S}(\cdot,\cdot)$ can be an arbitrary binary operator (e.g., dot-product, convolution, element-wise product) and $W$ denotes the learnable weight.
Instances of *regionality perception* are locally connected and weight-sharing on different positions, such as all kinds of convolutions and even non-parametric operations like pooling. For intance, the convolution operation which is the most commonly used and thoroughly studied, can be written as $Z = \mathcal{S}(X, K)$, where $\mathcal{S}(\cdot,\cdot)$ is the convolution and the kernel $K\in \mathbb{R}^{M\times C\times k\times k}$ consists $M$ filters. To further boost the representation abilities, considerable efforts are spared to make convolution-based regionality perception lighter and more flexible. Some works tend to factorize vanilla convolution into depthwise (DW) and pointwise (PW) counterparts balancing the efficiency vs. accuracy trade-offs.

#### 2.1.2 Context Aggregation

Apart from *static* neighborhood correlations, high-level semantic context modelling is also vital for sound representation learning. Canonical CNNs tend to employ deep stacks of regionality perception modules to passively attain increasing theoretical receptive fields. However, such designs might be computationally inefficient and exhibit strong inability for discriminative self-relevant context recognition. To tackle this dilemma, *context aggregation* modules were proposed to *adaptively* emphasize the underlying contextual information and discard trivial redundancies of input feature. Formally, we summarize context aggregation as a family of network components that adaptively capture long-range interactions between two embedded features:

\    O = \mathcal{S}\big(\mathcal{F}*{\phi}(X), \mathcal{G}*{\psi}(X)\big),


where $\mathcal{F}*{\phi}(\cdot)$ and $\mathcal{G}*{\psi}(\cdot)$ are the aggregation and context branches with parameters $\phi$ and $\psi$. Optionally, the output can be transformed to the input dimension by a linear projection, $Z = OW*{O}$.*
In contrast to *regionality perception*, *context aggregation* modules model the importance of each position on $X$ by the aggregation branch $\mathcal{F}{\phi}(X)$ and reweights the embedded feature from the context branch $\mathcal{G}_{\psi}(X)$ by $\mathcal{S}(\cdot,\cdot)$. Consequently, context aggregation can be viewed as a prototype operation for various mainstream modules by designating different designs $\mathcal{S}(\cdot,\cdot)$, $\mathcal{F}(\cdot)$, and $\mathcal{G}(\cdot)$.

### 2.2 Methodology

### 2.3 Expected Results and Impact

## **3. Visual Pre-Training**

### 3.1 Preliminary

The development of supervised pretraining is relatively clear. The ImageNet dataset, which laid the foundation for deep learning, was available long before the explosion of deep learning and is still in use today. the full ImageNet dataset of over 15 million has not been surpassed by other non-classified datasets and is therefore still the most commonly used data for supervised pretraining. Another reason is that image-level classification data introduces less bias and is therefore more favorable for downstream migration - further bias reduction is unsupervised pretraining. Unsupervised pretraining, on the other hand, has undergone a tortuous development. Starting from 2014, the first generation of geometry-based unsupervised pretraining methods emerged, such as judgment based on patched position relationships, based on image rotation, etc., while generative methods also evolved (generative methods can be traced back to an earlier period and are not repeated here). Unsupervised pre-training methods at this time are still significantly weaker than supervised pre-training methods. By 2019, contrast learning methods, with technical improvements, show the potential to outperform supervised pretraining methods on downstream tasks for the first time, and unsupervised learning really becomes the focus of the CV community. And starting in 2021, the rise of visual transformer spawned a special class of generative tasks, namely MIM, which gradually became the ruling method. In addition to purely supervised and unsupervised pretraining, there is a class of methods in between, namely cross-modal pretraining. It uses weakly paired images and text as training material, avoiding bias from image supervised signals on the one hand, and learning weak semantics better than unsupervised methods on the other. Moreover, with the addition of transformer, the integration of visual and natural language is more natural and reasonable.

### 3.2 Methodology

### 3.3 Expected Results and Impact

## 4. Conclusion

Herein, I present a summerized research proposal towards efficient visual representation learning for the admission of Ph.D. program at Westlake University.