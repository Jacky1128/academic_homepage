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
***[Get to know me and my academic blog.](https://zedongwang.netlify.app/post/getting-started/)***

With going deep into my recent few-shot segmentation research, I have come across something interesting about the application of Norm, which prompted me to delve into it again.
A series of normalization methods have bursted for years and have greatly propelled the development of deep algorithm applications. Armed with powerful packages like PyTorch and Tensorflow, it is quite normal and effortless to apply these Norm function in various types of deep learning models. However, we may not fully fathom how it works and may remain have some misunderstood concepts. Therefore, I would try to explain the details behind Norm operations here.

I will propel the blog based on the following questions:

* **Why we apply Norm in deep algorithms?**
* **How many types of Norm we commonly use and how do they work in detail?**
* **Do we really solve the problems with Norm?**
* **Why don't we apply Norm in Few-Shot learning tasks like others?**

## Ⅰ. ICS Problem

[Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift](https://arxiv.org/pdf/1502.03167.pdf) revealed the problem of Internal Covariate Shift (ICS) and proposed a normalized-based method, Batch Normalization, to address this issue. Before we kick off the explanation of ICS, I would make a brief recall of the backpropagation process first, which will be illustrated elaborately in \[Snacks] pattern of my blog soon. 

Define there is a three-layer neural network and a mid-layer-unit in the forward propagation as below:
$$\gamma*{k} =\sum*{i=1}^{h} W*{ik}^{T}x*{i} + b_{k}$$

where $\gamma*{k}$ indicates the $k^{th}$ output of the hidden-layer, $W*{ik}$, $x*{i}$, $b*{k}$ and $h$ are the weights, the $i^{th}$ independent variable (input), the $k^{th}$ bias and the number of hidden-layer units, respectively. 

$$x*i^t=x_i^{t-1}-lr\nabla f*{x_i}(x_i^{t-1})$$

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