---
title: 2-1. Optimization as a model for few shot learning
date: 2020-07-11 21:42:31 +09:00
categories: [Meta Learning, Contents]
tags: [Meta Learning]
math: true
comments: true
---
## Summary
Few Shot Learning을 위하여 Optimizer를 RNN로 만들어 Meta Learning을 통해 Gradient Descent로 학습한다.<br>

## Components
1. **Meta Representation<br>**
   Gradient Descent(RNN Optimizer)
2. **Meta Optimizer<br>**
   Gradient Descent<br>
3. **Meta Objective<br>**
   $$
   \mathcal{L^{meta}}(\phi) = \mathbb{E}_{\tau\text{~}D}[L^{base}(\theta(f, \phi))]
   $$<br>
   여기서 $\mathcal{f}$는 base network, $\theta$는 base network의 weights, $\phi$는 RNN optimizer의 weights<br>


## Algorithm

## Reference
1. Optimization as a model for few shot learning
   Sachin Ravi and Hugo Larochelle
