---
layout: post
title: "ML：池化与卷积"
date: 2024-11-13
description: "池化与卷积"
tag: Data Science
category: 机器学习
---


### 池化 Pooling
+ 池化的本质是一种**下采样**（Down Sampling），主要目的是减少特征tensor的尺寸，降低计算复杂度、减少内存；一定程度上提升**模型鲁棒性**
+ 目的
    - 降维
    - 特征提取
    - 抗噪声
+ 常见类型
    - Max Pooling：选择窗口的最大值；优点是放大窗口中的显著特征；缺点是容易丢失非敏感细节
    - Avg Pooling：计算窗口的平均值；优点是平滑窗口特征、降低过拟合风险
    - Global Avg Pooling：对整个特征图进行平均池化，输出一个**单一的值**；一般用于最后一层
+ 参数
    - 窗口大小 Kernal Size
    - 步长/步幅 Stride
    - 填充 Padding
    ![Pooling层超参的影响](/images/posts/2024/11/1113_ml_pooling_hyperparameters.png)
+ 池化层没有参数，BP阶段不参与更新，只负责Forward


### 卷积 Convolutional
+ 提取输入tensor的空间、时间上的局部特征
+ 通过卷积核（或滤波器）在输入特征图上**滑动**，计算局部区域的**加权和**。
+ 数学表达式：  $ (f\*g)(x, y) = \Sum_{i}\Sum_{j}f(i, j)\cdot g(x-i,y-j) $，其中 $f$输入tensor、$g$是卷积核函数
+ 参数
    - 卷积核 Filter：通常是一个小矩阵（3x3、5x5），用于特征提取，卷积核的数量决定了输出特征图的**深度**
    - 步长 Stride
    - 填充 Padding
+ 卷积层的可学习参数是卷积核（滤波器）的权重和偏置Bias
