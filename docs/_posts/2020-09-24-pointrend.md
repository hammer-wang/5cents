---
layout: posts
title:  "PointRend: Image Segmentation as Rendering"
date:   2020-09-24 00:00:01 -0400
categories: representation-learning
katex: yes
---


## Summary
Image segmentation based on convolutional neural networks is often based on regular grids. However, because the label map for interior regions of detected objects should remain relatively smooth, using a regular grid will oversample the interior while undersampling the boundary. Due to this reason, existing image segmentation methods do not perform well on object boundaries. This paper borrows the subdivision idea from computer graphics to form non-uniform grids. On both instance segmentation and semantic segmentation tasks, the proposed approach significantly improved existing strong baseline methods, including Mask R-CNN and DeeplabV3, in terms of boundary label prediction. 

## Strengths
This method proposed by this paper is simple and effective. The segmentation maps from the proposed approach have much better boundary label maps than methods without non-uniform grids. It’s nice to see that combining simple ideas from computer graphics can help with computer vision tasks. I believe this would inspire more researchers to bridge computer graphics and computer vision. 

## Weaknesses
Overall this paper is pretty good. I didn’t notice a significant weakness of this paper. However, it would be nice if the authors could add some results, comparing different non-uniform sampling strategies. The current comparison with baseline methods is primarily based on qualitative evaluation because IoU is insensitive to boundary label predictions. It would be nice to design a performance metric that focuses on the boundary predictions to benchmark the segmentation performance on boundaries. 
