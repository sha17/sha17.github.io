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
   \mathcal{L}(\phi) = \mathbb{E}_f[f(\theta(f, \phi))]
   $$<br>
   여기서 $\theta$는 base network의 weights, $\phi$는 RNN optimizer의 weights<br>

## Summary
   정리하면 task distribution에 최적화된 optimizer를 meta learning을 사용하여 학습하는 것이다.<br>
   이때 optimizer는 RNN을 사용하고 각 base network들은 이 RNN에서 Gradient 값을 얻어 Gradient Descent를 한다. Meta Knowledge인 RNN은 Meta Learning 과정에서 Query Set의 평균 Loss에 대하여 Gradient Descent를 통해 Update된다. 따라서 알고리즘의 제목이 Learning to learn gradient descent by gradient descent다.



## Reference
1. Hands-on meta learning with python
