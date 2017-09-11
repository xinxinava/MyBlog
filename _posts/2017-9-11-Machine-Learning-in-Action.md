---
layout: post
title:  "Machine Learning in Action"
date:   2017-09-11 17:25:00 +0800
categories: MachineLearning
tags: MachineLearning Python
author: SteveDevin
mathjax: true
---
* content
{:toc}

1.tile(A, reps)
    A:array like
    reps: A沿各个维度重复的次数

  ```py
    from numpy import *

    A = [1, 2]
    tile(A, 3)
    ...array([1, 2, 1, 2, 1, 2])
    tile(A, (2, 3))
    ...array([[1, 2, 1, 2, 1, 2],
              [1, 2, 1, 2, 1, 2]])

  ```


