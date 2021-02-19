---
layout: post
title: Network classification with applications to brain connectomics
gh-repo: daattali/beautiful-jekyll
tags: [Statistics]
comments: true
---

The field of brain image analysis is quite similar to Hi-C, and there are a lot of methods that can be directly applied here. I recently saw this very inspiring paper in that field, and wrote a summary. I am thinking about working on a clustering model for a set of networks, which could be an extension of this method. Using this kind of clustering technique, we can directly work on this "tensor" structure.

## Background

Brain networks are generated from imaging data to represent connectivity of brain regions. Different brain disorders have different networks, and a classification model is necessary to diagnose if a patient is diseased or healthy, and what kind of disease s/he has.

It seems that this is the first paper focusing on the classification of networks, and I believe this has some potential to a wide range of fields.

## Method

We have adjacency matrices $$ A $$ for an undirected matrix, and labels $$ Y $$ for each matrix. One direct thought on a linear classifier is: $$ Y = tr(B^TA) $$. Since they also want to do variable selection, a lasso-like constraint is necessary here. We can then write the loss function as: $$ \hat{B} = argmin\{l(B)+\Omega(B)\} $$, which the loss is logistic, $$ l(Y_k, A^{(k)};B,b) = log(1+exp(-Y_ktr(B^TA^{(k)})+b)) $$, and the penalty is $$ \lambda(\sum \Vert B_{(i)} \Vert_2 + \rho\Vert B \Vert_1) $$. The first penalty means that the edge between $$ i $$ and $$ j $$ is selected only if both nodes are activited. They use ADMM to optimize the parameter.

## Thought

$$ \lambda, \rho $$ can only be chosen by cross-validation, which is a hit on computational speed, although the result is not sensitive to the value of $$ \lambda $$. What's more, I personally think that restricting ourselves to a linear classifier is not wise, but for now I don't have a better option in mind. A bayesian setting might also be interesting to think about. In single-cell Hi-C setting, there might be 21 matrices to estimate, since there are 21 chromosome contact matrices.

## Reference

Arroyo Relión, Jesús D. et al. “Network Classification with Applications to Brain Connectomics.” The Annals of Applied Statistics 13.3 (2019): 1648–1677. Crossref. Web.
