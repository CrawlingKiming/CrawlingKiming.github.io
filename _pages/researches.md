---
title: "Research"
layout: posts
permalink: /Researches/
author_profile: true
---

# Fast Compartment Calibration Using Annealed and Transformed Variational Inference

>[Arxiv](http://arxiv.org/abs/2211.12200)
> 
>[GitHub](https://github.com/CrawlingKiming/AdVI)

<hr/>
<p align="center"><img src="/assets/img/Model_Outline4.PNG" width="80%" height="60%" title="ATVI Outline" alt="RubberDuck" /></p>

Compared to the standard MCMC algorithms, VI approaches scale well to larger datasets or high-dimensional problems. Furthermore, with the well-trained NF model, we can construct a complicated form of variational distribution without depending on restrictive parametric assumptions. However, the direct application of these methods to compartment model calibration is challenging due to the following reasons:

- Parameter Constraints 

The support of approximate distribution should be inside the constrained parameter space. The standard VI suffers from boundary effect problems due to parameter constraints in compartment models. The most common approach is to use "bijective transformation", however, it truncates the posterior near the parameter constraints. This is especially problemetic at the calibration tasks, as parameter constraints are frequently used. 

- Poor local optmia 

If the approximate density does not cover (i.e., mismatch) all of the high-density regions of the target at the beginning
of the training, the mismatched region may never be discovered during optimization. 
Although several alternatives or employing different divergences have been proposed, they are computationally expensive and require some simplifying assumptions in the form of variational density.

We propose a Novel Framework: **Annealed and Transformed Variational Inference (ATVI)**, fusing modern advancements of MCMC, deep learning, and variational inference. 

### ATVI

- Boundary Surjection 

<p align="center"><img src="/assets/img/BoundarySurjection.PNG" width="120%" height="90%" title="BS smaple" alt="RubberDuck" /></p>

Here, I propose a novel transformation, **boundary surjection**, that deals the first issue.

A mapping between unconstrained space and constrained space, is a deterministic one side and probabilistic mapping 
on the other side. With the proposed conditons and theoretical justifications, the boundary surjection is easy to implement, and deals boundary truncation. (See Section 4.1 and 4.2 for more details)


- Sequentially Annealed Posteriors 

Here, I propose a new temperature annealing scheme. Unlike other temperature annealing shcemes, it is an natural extension of the deep generative model, normalizing flow. 

Main idea is to introduce a block layer, a composite of multiple NF layers, that targets annealed target distribution. The block itself, is not a target distribution. However, a *composite* of block layers, becomes a target distribution. 

We sequentially train each block. At the end of the training, the compostie of sequentailly trained blocks becomes the target distribution. See theoretical details in Section 4.3. 


### Result 

<p align="center"><img src="/assets/img/ATVI_Comparision.PNG" width="120%" height="90%" title="BS smaple" alt="RubberDuck" /></p>

While MCMC took 15 hours, ATVI recovered true posterior within two hours, perserving its reliability. 
