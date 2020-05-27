---
title: kNN
date: 2020-05-27 22:19:14
tags: [python,kNN]
categories: 机器学习
---

# K-近邻算法

## 原理

入坑学的第一个算法，理论看不懂的我直接来实战了（枯）

其实k-近邻算法（以下简称knn）的原理蛮简单的。

比如说现在有一个训练样本集，并且都有标签。当我们遇到一个未标签过的新数据时，将新数据与每个已有的样本进行特征比较，然后选择其中特征差异最小的前k个，最后选择这k个相似数据中出现最多的标签作为新数据的标签。（通常$k<20$）

一句话概括其实就是谁近选谁。

## k-近邻算法的一般流程

1. 收集数据：可以使用任何方法。

2. 准备数据：距离计算所需要的数值，最好是结构化的数据格式。

3. 分析数据：可以使用任何方法。

4. 训练算法：此步骤不适用于k-近邻算法。

5. 测试算法：计算错误率。

6. 使用算法：首先需要输入样本数据和结构化的输出结果，然后运行k-近邻算法判定输
   入数据分别属于哪个分类，最后应用对计算出的分类执行后续的处理。

   ​																											——转自《机器学习实战》

## 算法实现

 对未知类别属性的数据集中的每个点依次执行以下操作： 

1.  计算已知类别数据集中的点与当前点之间的距离； 
2.   按照距离递增次序排序； 
3.  选取与当前点距离最小的k个点；  
4.   确定前k个点所在类别的出现频率； 
5.  返回前k个点出现频率最高的类别作为当前点的预测分类。  

```python
from numpy import *
import operator
def createDataSet():
    group=array([[1.0,1.1],[1.0,1.0],[0,0],[0,0.1]])
    labels=['A','A','B','B']
    return group,labels
def classify0(inX,dataSet,labels,k):
    #计算新数据与每个点的距离
    dataSetSize=dataSet.shape[0]
    diffMat=tile(inX,(dataSetSize,1))-dataSet
    sqDiffMat=diffMat**2
    sqDistances=sqDiffMat.sum(axis=1)
    distances=sqDistances**0.5
    #argsort返回下标
    sortedDistances=distances.argsort() 
    classcount={}
    #统计前k个group的label出现次数
    for i in range(k):
        voteIlabel=labels[sortedDistances[i]]
        classcount[voteIlabel]=classcount.get(voteIlabel,0)+1
   sortedclasscount=sorted(classcount.items(),key=operator.itemgetter(1),reverse=True)
    return sortedclasscount[0][0]
```

### 测试方法：

进入到包含这个KNN.py的文件夹的python工作模式下，运行

```python
import KNN
group,label=KNN.createDataSet()
KNN.classify0([0,0],group,label,3)
```

得到的结果为“B”标签

~未完待续

