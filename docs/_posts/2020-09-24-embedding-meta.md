---
layout: posts
title:  "Rethinking Few-Shot Image Classification: a Good Embedding Is All You Need?"
date:   2020-09-24 00:00:01 -0400
categories: representation-learning
katex: yes
---


## Summary
This paper investigated meta-learning for few-shot learning from the perspective of learning a good embedding model. From this understanding, the authors proposed a simple baseline algorithm, i.e., learn feature embedding using a feature extraction model trained on a classification task rather than using sophisticated meta-learning algorithms. To train such a feature extraction model, the authors simply aggregated all few-shot learning tasks into a single dataset for training with the cross-entropy loss. After the feature extraction model is trained, a logistic regression base-learner is trained on top of the extracted features for any meta-test task at the meta-testing time. Overall, the idea is almost identical to most previous transfer learning algorithms except that the authors added a sequential knowledge distillation stage to refine the feature extractor and freeze the feature extraction model during meta-test training. Surprisingly, this simple baseline achieved state-of-the-art performance on popular few-shot-learning benchmarks. Based on their findings, the authors concluded that learning a useful embedding is critical for few-shot learning.

## Strengths
This paper proposed a simple and effective baseline for few-shot learning. The experiment section is very extensive, and the results support the authors' hypothesis well. More importantly, the proposed simple method may potentially lead to a paradigm shift for few-shot learning. Instead of designing new sophisticated meta-learning algorithms, it might be more important to design good representation learning algorithms that can extract transferable features. If all the experiment results are valid in this paper, it could be a seminal paper.

## Shortcomings
The proposed method seems exactly the same as transfer learning, i.e., train a feature extractor on a large dataset and transfer all but the last layers for new downstream tasks. From this paper, it seems to me that, by introducing engineering tricks such as freezing feature extractor, introducing knowledge distillation, etc., the performance of such a simple transfer learning can work pretty well. Overall, I feel that there is not sufficient discussion in this paper to support all these engineering choices and the reasoning behind them; thus, a minimal take-away message can be learned by readers. I hope that the authors could add more discussion on the reasoning behind all critical designs choices rather than simply stacking many such tricks with a seemingly meaningful ablation study.

