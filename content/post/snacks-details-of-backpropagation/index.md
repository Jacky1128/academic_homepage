---
title: Research Proposal
subtitle: Research proposal for admission
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
## **E﻿fficient Visual Representation Learning**

### 1. I﻿ntroduction

If the visual recognition task does not change significantly, then neither automatic design, nor the addition of more complex computational modules, will be able to push CV to new heights. Possible changes to the visual recognition task can be broadly divided into two parts: input and output. The possible changes in the input part, such as event camera, may change the status quo of regularized processing of static or temporal visual signals, giving rise to specific neural network structures; the possible changes in the output part are some kind of framework for unifying various recognition tasks, which may allow visual recognition to move from independent tasks to a grand unification, thus giving rise to a network architecture more suitable for visual prompts. If there is a trade-off between convolution and transformer, then transformer has more potential, mainly because it can unify different data modalities, especially text and image, which are the two most common and important modalities. Interpretability is an important research direction, but I am personally pessimistic about the interpretability of deep neural networks, and the success of NLP is not based on interpretability, but on overfitting a large corpus. This may not be too good a sign for real AI.

### 2. **Deep Architecture Design**

How to learn contextual and robust features effectively is the main theme of visual representation learning. We categorize two types of significant operations that are bound up with the expression capacities: *regionality perception* and *context aggregation*. Here, we assume the input feature $X$ and the output $Z$ are in the same shape $\mathbb{R}^{C\times H\times W}$.

Since raw images are redundant signals, operations armed with local and structural inductive biases are fundamental components in DNNs, which ensure efficiency and stability during training. 

### 3. **Pretraining**

The development of supervised pretraining is relatively clear. The ImageNet dataset, which laid the foundation for deep learning, was available long before the explosion of deep learning and is still in use today. the full ImageNet dataset of over 15 million has not been surpassed by other non-classified datasets and is therefore still the most commonly used data for supervised pretraining. Another reason is that image-level classification data introduces less bias and is therefore more favorable for downstream migration - further bias reduction is unsupervised pretraining. Unsupervised pretraining, on the other hand, has undergone a tortuous development. Starting from 2014, the first generation of geometry-based unsupervised pretraining methods emerged, such as judgment based on patched position relationships, based on image rotation, etc., while generative methods also evolved (generative methods can be traced back to an earlier period and are not repeated here). Unsupervised pre-training methods at this time are still significantly weaker than supervised pre-training methods. By 2019, contrast learning methods, with technical improvements, show the potential to outperform supervised pretraining methods on downstream tasks for the first time, and unsupervised learning really becomes the focus of the CV community. And starting in 2021, the rise of visual transformer spawned a special class of generative tasks, namely MIM, which gradually became the ruling method. In addition to purely supervised and unsupervised pretraining, there is a class of methods in between, namely cross-modal pretraining. It uses weakly paired images and text as training material, avoiding bias from image supervised signals on the one hand, and learning weak semantics better than unsupervised methods on the other. Moreover, with the addition of transformer, the integration of visual and natural language is more natural and reasonable.