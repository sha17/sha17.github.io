---
title: 2. Learning to learn gradient descent by gradient descent
date: 2020-07-11 19:00:29 +09:00
categories: [Meta Learning, Contents]
tags: [Meta Learning]
math: true
comments: true
---

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

## Summary
Base Network들의 평균 Loss를 최소화 하는 Optimizer를 Meta Learning을 통해 Gradient Descent로 학습한다.<br>

## Algorithm
   task distribution에 최적화된 optimizer를 meta learning을 사용하여 학습하는 것이다.<br>
   이때 optimizer는 RNN을 사용하고 각 base network들은 이 RNN에서 Gradient 값을 얻어<br>
   Base Network의 Parameter **$\theta$에 대하여 Gradient Descent**를 한다.<br>
   Meta Learning 과정에서 Meta Knowledge인 RNN은 Query Set의 평균 Loss가 최소화가 되도록<br>
   Meta Objective의 parameter인 **$\phi$에 대하여 Gradient Descent**를 통해 Update된다.<br>
   알고리즘의 제목이 Learning to learn gradient descent by gradient descent인 이유를 알 수 있다.

## Implementation
... 구현중



## Reference
1. Hands-on meta learning with python
