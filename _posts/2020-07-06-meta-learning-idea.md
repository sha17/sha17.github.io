---
title: 1. Meta Learning 개념
categories: [Meta Learning, Contents]
date: 2020-07-06 23:19:59 +09:00
tags: [Meta Learning]
math: true
comments: true
---
Meta-Learning in Neural Networks 리뷰 논문을 읽고 메타러닝 개념과 구조/구성에 대해 공부.<br>
메타러닝을 잘 이해하기 위해서는 Learning to Learn 이라는 표현을 잊으면 안된다.

## Learning to Learn
여러 Task들의 데이터에 대한 학습과 검증의 경험을 통해 모델을 만드는 방법 자체를 학습.<br>
이때 얻는 경험을 Meta Knowledge라고 하고 이 Knowledge를 얻는 과정을 Meta Training이라 한다.<br>
Deep Learning: model learning + joint features<br>
Meta Learning: model learning + joint features + learning algorithm<br>
학습 알고리즘을 학습함으로써 유연한 모델을 만들어 data/resource efficiency, generalization 성능 향상 등을 기대할 수 있다.


## Bilevel Optimization
$$
\mathcal{w}^{*} = \mathop{argmin}_{\mathcal{w}}
\sum_{i=1}^{M} \mathcal{L}^{meta}(\theta^{*}(\mathcal{w),w, D_{source}^{val\ (i)}}) \\
\hspace{1.3cm} s.t. \ \theta^{*}(\mathcal{w}) =
\mathop{argmin}_{\theta} \mathcal{L^{task}(\theta, w, D_{source}^{train\ (i)})}
$$
$\hspace{1.3cm}$w: Meta Knowledge / M: Task들의 수 / $\theta$: Base Network의 weights

Meta Learning의 Learnign to Learning 개념은 위의 식으로 공식화할 수 있으며,<br>
이는 Bilevel Optimization의 형태로 구현할 수 있다.<br>
1. **Initialization**<br>
  Initial Meta Knowledge, $\mathcal{w_{0}}$의 정의<br>
  Source Dataset을 Support set과 Query set으로 분할.<br>
  Model Estimation을 위한 Test Dataset을 별도로 저장.
2. **Inner Loop: Leveraging Meta Knowledge** <br>
  현재 Meta Knolwedge, $\mathcal{w_t}$로 Support Set에 대하여 Base Task들을 학습하고 update한다.
3. **Outer Loop: Updating Meta Knowledge**  <br>
  Query Set을 사용하여 Meta Objective의 Loss를 최소화하는 방향으로 Meta Knowledge를 update한다.
4. **Model Estimation** <br>
  Source Dataset이 아닌 별도의 Test Dataset을 사용하여 모델을 평가하면 된다.

실질적으로 Meta Learning은 Outer Loop, 즉 Query Set에 대한 Validation 과정에서 이루어진다.

## Terms suggested in the paper
이전 meta learning의 category들은 일반적으로 optimization-based, model-based, metric-based로 나뉘어져 있었으나 현재 meta learning의 모든 관심부분들과 연결시키기 어렵다. 따라서 논문은 아래와 같은 새로운 terminology를 제시하고 있다.
1. **Meta Representation: What?**<br>
  Meta Knowledge, $\mathcal{w}$를 어떤 형태로 표현할 것인가?<br>
  Optimizer, Initialization, Metric 등의 예가 있다.
2. **Meta optimizer: How?**<br>
  Meta Knowledge를 어떤 방법을 통해 Optimize할 것인가?<br>
  Gradient Descent, Reinforcement Learning, Evolutionary Search 등이 있다.
3. **Meta Objective: Why?**<br>
  $\mathcal{L^{meta}}$: Meta Knowledge를 사용하여 무엇을 얻고자 하는가?<br>
  Few shot learning, adversarial attack, MAML 등이 있겠다.

## 내 생각
Meta Learning의 개념이나 전체적인 개요가 굉장히 애매모호해서 그전의 논문들이나 블로그 글 등을 읽어봐도 한번에 이해하기가 어려웠는데(내 이해력이 모자랐을수도), 이 논문은 Meta Learning에 대한 개념과 구성요소에 대해 정말 깔끔하게 정리하여 궁금했던 것들이 모두 해결되었다. 특히 다른 연관 분야와 구분점과 비슷한 점에 대하여 기술해 놓은 것이 후에 관련 필드를 찾을때 유익할 것 같다.

## Reference
1. Meta-Learning in Neural Networks: A Survey
    Timothy Hospedales, Antreas Antoniou, Paul Micaelli, Amos Storkey
