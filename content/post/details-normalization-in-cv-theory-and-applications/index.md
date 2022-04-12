---
title: "[Details] Normalization in CV: What indeed happens in it"
subtitle: Coming soon
date: 2022-04-12T08:10:49.824Z
draft: false
featured: false
authors:
  - ZedongWang
tags:
  - Details
categories:
  - Details
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
A series of normalization methods have bursted for years and have greatly propelled the development of deep algorithm applications. Armed with powerful packages like PyTorch and Tensorflow, it is quite normal and effortless to apply these Norm function in various types of deep learning models. However, we may not fully fathom how it works and may remain have some misunderstood concepts. Therefore, I would try to explain the details behind Norm operations here.

I will the blog on the following questions:

* **Why we apply Norm in deep algorithms?**
* **How many types of Norm we commonly use and how do they work in detail?**
* **Do we really solve the problems with Norm?**
* **Why don't we apply Norm in Few-Shot learning tasks like others?**

## Ⅰ. ICS Problem

[Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift](https://arxiv.org/pdf/1502.03167.pdf) revealed the problem of Internal Covariate Shift (ICS) and proposed a normalized-based method, Batch Normalization, to address this issue.Before we kick off the explanation of ICS, I would like to make a brief recall of the middle-layer unit in the backpropagation process here, which will be illustrated elaborately in \[Snacks] pattern of my blog. 

Define a mid-layer-unit in the backprop as below:
$$\gamma_{i} =\sum_{k=1}^{n} W_{ik}^{T}x_{k} + b$$

where $\gamma_{i}$ indicates the outputs of this middle-layer, $W_{ik}$, $x_{k}$ and $b$ are the weights, independent variables (inputs) and bias, respectively.

## Ⅱ. Normalization Principle

### 1. General Normalization

### 2. Batch Normalization

### 3. Layer Normalization

### 4. Instance Normalization

### 5. Group Normalization

### 6. Switchable Normalization

### 7. Weight Normalization

### 8. Cosine Normalization

## Ⅲ. Drawbacks in specific cases