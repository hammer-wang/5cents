---
layout: single
title:  "Decoupled Weight Decay Regularization."
date:   2020-09-15 17:44:12 -0400
categories: representation-learning
---

In DL literature, researchers often use weight decay and L2 regularization interchangeably. It’s because they are equivalent when using SGD as the regularizer. However, this paper pointed out that the best L2 regularization strength is coupled with the chosen learning rate, while weight decay following the original implementation is not. Moreover, the authors proved that, for adaptive learning rate optimizers, weight decay is no longer equivalent to L2 regularization. Based on this theoretical finding, the authors hypothesized that the widespread weight decay implementation (using \\(ell_2\\) regularizer) in most DL frameworks is suboptimal and leads to lower accuracy for deep neural networks trained with Adam. To resolve this problem, the authors proposed AdamW, which decouples weight decay with the learning rate. Through extensive experiments, the authors demonstrated that the weight decay is indeed decoupled from the learning rate when using the proposed algorithm. On CIFAR-10 and ImageNet32x32, AdamW outperforms Adam in terms of both convergence and generalization performance. Also, when combined with the warm restart method (Loshchilov & Hutter, 2016), the proposed algorithm can achieve better anytime performance. 

__Strengths__
This paper studied a critical problem, i.e., the generalization performance of adaptative learning rate optimizers, and pointed out a previously overlooks problem when using such optimizers. The theoretical claims of this paper are well supported by formal analysis. More importantly, the simple modification to existing Adam algorithms proposed by the authors significantly improved its convergence and generalization performance. Overall, the experiment results are extensive and convincing. 

__Shortcomings__
The authors only applied the proposed algorithm on CIFAR-10 and ImageNet32x32; both are not very challenging datasets. Although due to computation constraints, it’s costly to validate the proposed algorithm on ImageNet or other large-scale datasets, it would be interesting to see such results to further verify the performance boost of the proposed decoupling approach. Also, in figure 4, we observe that AdamWR still performs slightly worse than SGDWR; it would be nice if the authors could discuss potential reasons. More importantly, researchers recently found that more general optimizers never underperform special ones given careful hyperparameter tuning (Choi et al, 2020). It’s unclear whether the results from this paper is due to insufficient hyperparamter tuning. 

[paper link](https://arxiv.org/abs/1711.05101)