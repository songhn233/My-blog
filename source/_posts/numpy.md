---
title: numpy_矩阵
date: 2020-05-23 21:58:10
tags: [python,矩阵]
categories: 机器学习
---

入坑机器学习的第一篇博客。

有一说一，机器学习入门真的好硬核，对数学的要求好高。由于笔者数学水平有限，在这就不做公式原理上的证明（埋个坑，学完线代随缘补罢）。

所以这篇主要是记录一下numpy里的矩阵相关基础操作。

#### 基础操作

```python
import numpy as np
#生成一个元素为[-6,6]的int型3*3矩阵
A=np.random.randint(-6,6,(3,3))
B=np.random.randint(-6,6,(3,3))
#转置矩阵
A_T=A.T
#逆矩阵
A_inv=np.linalg.inv(A)
#逐元素乘积
A_elemdot_B = A*B
#点积
A_dot_B = A.dot(B)
#矩阵迹
trace_A = np.trace(A)
#行列式
det_A = np.linalg.det(A)
#特征分解
vals,vecs = np.linalg.eig(A)
print("矩阵A的特征值=",vals)
print("矩阵A的特征向量=",vecs)
#奇异值分解
A = np.mat('4 8 9;3 5 8')
U, sv, V = np.linalg.svd(A, full_matrices=False)  # full_matrices可以保证逆向生成原方阵，针对的是V
print(U * np.diag(sv) * V) #还原
```

#### 奇异值分解

任何$m\times n$矩阵都可以分解为$A=U\times \sum\times V^T$

关于奇异值的理解贴一篇笔者认为写的较好的文章：[SVD](http://redstonewill.com/1529/)

