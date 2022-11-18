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

As aforementioned, how to learn robust contextual image patterns effectively is one of the main theme of high-quality visual representation learning. In this section, I first categorize two types of significant operations that are bound up with the expression capacities: **regionality perception** and **context aggregation**. Here, we assume the input feature $X$ and the output $Z$ are in the same shape $\mathbb{R}^{C\times H\times W}$. 

#### 2.1.1 Regionality Perception

Since raw images are redundant signals, operations armed with local and structural inductive biases are fundamental components in DNNs, which ensure efficiency and stability during training. I would summarize these operations and network modules that *statically* extract contextual features as *regionality perception* and define it as $Z = \mathcal{S}(X, W)$, where $\mathcal{S}(\cdot,\cdot)$ can be an arbitrary binary operator (e.g., dot-product, convolution, element-wise product) and $W$ denotes the learnable weight.
Instances of *regionality perception* are locally connected and weight-sharing on different positions, such as all kinds of convolutions and even non-parametric operations like pooling. For intance, the convolution operation which is the most commonly used and thoroughly studied, can be written as $Z = \mathcal{S}(X, K)$, where $\mathcal{S}(\cdot,\cdot)$ is the convolution and the kernel $K\in \mathbb{R}^{M\times C\times k\times k}$ consists $M$ filters. To further boost the representation abilities, considerable efforts are spared to make convolution-based regionality perception lighter and more flexible. Some works tend to factorize vanilla convolution into depthwise and pointwise counterparts balancing the efficiency vs. accuracy trade-offs.

#### 2.1.2 Context Aggregation

Apart from *static* neighborhood correlations, high-level semantic context modelling is also vital for sound representation learning. Canonical CNNs tend to employ deep stacks of regionality perception modules to passively attain increasing theoretical receptive fields. However, such designs might be computationally inefficient and exhibit strong inability for discriminative self-relevant context recognition. To tackle this dilemma, *context aggregation* modules were proposed to *adaptively* emphasize the underlying contextual information and discard trivial redundancies of input feature. Formally, we summarize context aggregation as a family of network components that adaptively capture long-range interactions between two embedded features:

\begin{equation}
   O = \mathcal{S}\big(\mathcal{F}{\phi}(X), \mathcal{G}{\psi}(X)\big)
\end{equation}

where $\mathcal{F}{\phi}(X)$ and $\mathcal{G}{\psi}(X)$ are the aggregation and context branches with different parameters. Optionally, the output can be transformed to the input dimension by a linear projection, $Z = OW{\phi}$. In contrast to regionality perception, context aggregation modules model the importance of each position on $X$ by the aggregation branch $\mathcal{F}{\phi}(X)$ and reweights the embedded feature from the context branch $\mathcal{G}{\psi}(X)$ by $\mathcal{S}(\cdot,\cdot)$. Consequently, context aggregation can be viewed as a prototype operation for different modules by designating diverse instantiations of $\mathcal{S}(\cdot,\cdot)$, $\mathcal{F}(\cdot)$, and $\mathcal{G}(\cdot)$. 

### 2.2 Methodology and Expected Outcomes

Notably, the importance of each position on above-mentioned $X$ is calculated by global interactions of all other positions in $\mathcal{F}_{\phi}(\cdot)$ with a dot-product. This operation (e.g. self-attention mechanism) takes quadratic time and computational complexity leading to large computational overheads. T﻿o this end, how to perform context aggregation efficiently would be one of the main themes of my research.

Inspired by human visual systems w﻿here human eyes perform ﻿egional sensing and global context perception simultaneously and efficiently, I have planned to address this issue from two directions: **aggregation efficiency** and **region-context unity**.
As my first try, I design a Multi-order Gated Aggregation (Moga) in *Efficient Multi-order Gated Aggregation Network* with researchers from Prof. Stan Z. Li Lab, where discriminative local representations are modeled and contexutalized by assembled dilated $\mathrm{DWConv}$ and efficient gating mechanism in parellel mimicing what our human visual systems have done. Along this line, I plan to dig deep in more efficient, unified and discriminative visual recognition architecture following aforementioned aggregation efficiency and region-context unitydesign manner in the upcoming research career at Westlake University. 

## **3. Visual Pre-Training**

### 3.1 Preliminary

Visual Pre-Training techniques improve visual representations f﻿rom the view of data utilization, w﻿hich can be divided mainly into three categories: **supervised**, **unsupervised**, and **cross-modal** pretraining. The development of supervised pretraining is relatively mature and clear. The ImageNet dataset with about 15 million data scale, which laid the foundation for deep learning, is still the most commonly used dataset and has largely propelled the development of supervised visual pretraining. Although many current datasets have already provided extremely fine-grained pixel-level annotations, there is still a large amount of human-recognizable semantic information that fail to be annotated. More importantly, even with massive human labor, it is difficult for us to define a standardized set of criteria to complete the annotation of all human-recognizable semantic information. Therefore, it is not enough to solely conduct supervised pre-training using existing vision data. This appetite for data utilization has been first addressed in 
NLP by self-supervised pretraining.

Unsupervised pretraining, on the other hand, has undergone a long-lasting p﻿rocess of development. Starting from 2014, the first generation of geometry-based unsupervised pretraining methods emerged, such as judgment based on patched position relationships, based on image rotation, etc., while generative methods also evolved (generative methods can be traced back to an earlier period and are not repeated here). Unsupervised visual pre-training methods at this time are still significantly weaker than the fully-supervised ones. By 2019, contrast learning manners, with technical improvements, show the potential to outperform supervised counterparts on multifarious downstream benchmarks, and triggers most attentions of computer vision community. In 2021, the rise of visual transformer spawned a special class of generative tasks, namely Masked Image Modeling (MIM), which gradually became the ruling method. It is an autoencoding
 approach that reconstructs the original image from the latent representation given its
 partial masked observation.

Unlike pure supervised and unsupervised pretraining paradigm, there is a class of methods in between, namely cross-modal pretraining. It uses weakly paired images and text as training material, avoiding bias from image supervised signals on the one hand, and learning weak semantics better than unsupervised methods on the other. Moreover, with the addition of transformer, the integration of visual and natural language is more natural and reasonable.

### 3.2 Problem Analysis

From my perspective,unsupervised visual pre-training might be  promising direction that best reflects the essence of computer vision, that is, **learning from degradation**. Specifically, natural language as  human-created data is semantically strong. However, image signals captured by objective sensors owns inherent low semantic density. Therefore, it is tough yet significant for visual recognition to boost the efficiency of data utilization rather than just conduct naive supervised learning. Degradation here refers to removal of partial information that is already presented and commands the model to recover it. Notice that the idea of visual pre-training is heavily influenced by natural language pre-training, but I believe that the two are fundamentally different and thus cannot be generalized. 

However, such degradation-based approaches have an insurmountable bottleneck, **the conflict between degradation strength and semantic consistency**. Since there is no supervised signal and the representation quality is solely dependent on degradation, the degradation level must be strong enough. Nonetheless, images before and after degradation may not be semantically consistent, leading to pathological visual pre-training outcomes.  For example, If the information with key representative features is removed in Masked Image Modeling tasks, strong misleading information will be introduced during the reconstruction processs, which can substantially decrease the representation capacity of target models.

Moreover, there exists a non-negligible **disparity between large-scale pre-training and target domain fine-tuning**: large pre-trained models are inclined to perceive comprehensive distribution of observed data and pursue corresponding optimal solutions, while fine-tuning tend to target a specific domain. Thus, the larger the model size, the more difficult it is to achieve domain adaptation, especially for the scenarios with large domain gap. 

In conclusion, how to design a unified pre-training pipeline to release deep networks' capabilities and better resolve the conflict between degradation intensity and semantic consistency, while allowing the upstream large models smoothly adapt to downstream tasks may be the main topic in the field of visual pre-training. Personally, it is worth trying to combine all the above v﻿isual pre-training paradigms into a mixed dataset containing a small amount of p﻿recisely labeled data, a medium amount of paired graphical data, and a large amount of images without corresponding labels and specially-designed pre-training strategies should be equipped on such mixed datasets. 

## **4. Conclusion**

Herein, I present a summerized research proposal towards efficient visual representation learning for my admission of Ph.D. program at Westlake University. Due to content limitations, I decide to mainly focus on the most familiar the context of computer vision. What I would like to emphasize here is that **I am also willing and desired to pursue constructive cross-disciplinary AI research** (e.g. AI for Science) in my research career at Westlake University. I do believe that with my research attitude, skills and experience in deep learning, I am capable of making positive contributions to cross-disciplinary AI research as well.