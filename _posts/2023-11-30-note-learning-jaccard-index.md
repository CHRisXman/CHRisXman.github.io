---
layout: post
title: "Jaccard Index"
date: 2023-11-30
description: "Jaccard Index的理解"
tag: 学习笔记
category: 机器学习
---

给定两个句子，如何量化他们的相似程度？
Jaccard Index可以衡量，它是NLP中用于计算相似度或样本距离时非常基础的选择之一。

#### 概念
计算交集（Intersect）在并集（Union）中占的比例
![jaccard_index.png](/images/posts/2023/jaccard_index.png)

#### 公式
$J(A,B) = \frac{|A \cap B|}{|A \cup B|} = \frac{|A \cap B|}{|A| +|B| - |A \cap B|}$
其中，分子是集合的交集、分母是并集；值介于0~1，等于1表示两者完全重合

#### 例子
+ 计算以下两个例句的Jaccard Index
	- $s_1 = \text{数学好好玩}$
	- $s_2 = \text{大学好好玩}$
+ 如果以每个字符为单位，则 $J(s1, s2)$:
	- $s_1 \cap s_2 = \{\text{学}, \text{好}, \text{玩} \}$
	- $s_1 \cup s_2 = \{\text{大}, \text{数}, \text{学}, \text{好}, \text{玩} \}$
	- $J(s_1, s_2) = \frac{3}{5} = 0.6$
+ 如果考虑汉语分词：
	- $s_1 \cap s_2 = \{\text{好好玩}\}$
	- $s_1 \cup s_2 = \{\text{数学}, \text{大学}, \text{好好玩}\}$
	- $J(s_1, s_2) = \frac{1}{3} = 0.3333$

#### Jaccard Distiance
计算两个样本或集合的距离，定义为： $1 - \text{Jaccard Index}$，即：
$d_J(A,B) = 1 - J(A,B) = \frac{|A \cup B| - |A \cap B|}{|A\cup B|}$
