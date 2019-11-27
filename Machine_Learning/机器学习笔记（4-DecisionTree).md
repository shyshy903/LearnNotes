
---
title: 《机器学习实战》《西瓜书》笔记（四）- 决策树
date: 2019-11-27 15:30
categories: Machine_Learning
tags: ML
---
# 决策树
决策树本质上是一种流程图，长方形代表**判断模块**，椭圆代表**终止模块**，左右箭头指引**节点的上下分支**
决策树相比较于KNN，其重要的原因就是其数据形式非常容易理解，而KNN的数据形式所包含的内在含义却不是很容易理解
<div align = center>
<img src = " https://img.vim-cn.com/10/8d6b3cb5f550b03b25681ed2bdc0f7cc424005.png">
</div>

**优点**
计算复杂度不高，可以处理不相关特征数据，对中间数据的缺省值不敏感
**缺点**
会产生过度匹配问题

## 信息论划分数据集
```python
"""划分数据集的伪代码"""
检测数据集是否属于同一类：
    if so  return 类标签
    else:
        寻找划分数据集的最好特征
        划分数据集
        创建分支节点
            for 每个划分的子类
                调用函数createBranch并增加返回节点到结果上
        return 分支节点
```
## 决策树的流程
1. 收集数据：可以使用任何方法
2. 准备数据：**树构造算法适用于标称型数据，如果数据是数值型数据，需要先把数据进行离散化**
3. 分析数据：构造树完成，进行检查
4. 训练算法：构造树的数据结构
5. 测试算法：使用经验树计算错误率
6. 使用算法

## 信息增益与信息熵

**划分数据集的最大原则是，将无序的数据变得更加有序**
**信息增益**：划分数据集前后信息发生的变化称为信息增益
计算每个特征划分数据集获得的信息增益，获得信息增益最高的特征就是最好的选择
**如何计算信息增益？**
集合信息的度量方式称为**香农熵**
熵定义为信息的期望值：
符号$x_i$的信息定义为$l(x_i) = -log_2p(x_i)$，p(x_i)是选择该分类的概率
则信息熵为：$H = -\sum\nolimits_{i=1}^{n}p(x_i)log_2p(x_i)$,其中n是分类的数目

## 计算信息熵的源代码
```python
"""
用于计算给定的信息熵
"""
"""
函数说明：计算给定数据集的经验熵（香农熵）
        H = -SUM（kp*Log2（kp））

Parameters:
    dataSet - 数据集
    
Returns:
    shannonEnt - 经验熵（香农熵）
"""

def calcShannonEnt(dataSet):
    # 返回数据集的行数
    numEntires = len(dataSet)
    # 保存每个标签（Label）出现次数的“字典”
    labelCounts = {}
    # 对每组特征向量进行统计
    for featVec in dataSet:     # 按行进行遍历
        # 提取标签（Label）信息
        currentLabel = featVec[-1]    # 取每一行最后一列特征值
        # 如果标签（Label）没有放入统计次数的字典，添加进去
        if currentLabel not in labelCounts.keys():
            # 创建一个新的键值对，键为currentLabel值为0
            labelCounts[currentLabel] = 0
        # Label计数
        labelCounts[currentLabel] += 1
    # 经验熵（香农熵）
    shannonEnt = 0.0
    # 计算香农熵
    for key in labelCounts:
        # 选择该标签（Label）的概率
        prob = float(labelCounts[key]) / numEntires
        # 利用公式计算
        shannonEnt -= prob*log(prob, 2)
    # 返回经验熵（香农熵）
    return shannonEnt

```
**创建数据集**
```python
def createDataSet()：
    dataSet = [[1, ,1 , 'yes'],[1, 1, 'yes'],[1, 0, 'no'],[0, 1, 'no'],[0, 1, 'no']]
    labels = ['no surfacing', 'flippers']
    return dataSet, labels

>> reload(trees.py)
>> myDat, labels = trees.createDataSet()
>> trees.calcShannonEnt(mydata)
```

## 划分数据集的算法与代码
一般可用二分法划分数据集，这里采用**ID3算法**进行划分数据集
香农熵可用来度量数据集的无序度，数据无序度越大，香农熵值越大。
分类算法除了需要测量信息熵还需要一个**度量数据划分准确度的熵值**，这就像在二维坐标中画直线进行划分平面坐标系、

1. **按照给定特征划分数据集**
```python
"""
函数：按照给定的特征划分数据集
输入：
    dataSet,数据集
    axis, 划分数据集的特征
    value, 需要返回的特征值
Return:
    retDataSet,划分的数据集

"""
def splitDataSet(dataSet, axis, value):
    retDataSet = []
    for featVec in dataSet:  # 按行遍历数据集
        if featVec[axis] == value:   # 去掉特征为axis的数据集
            reducedFeatVec = featVec[:axis]
            reducedFeatVec.extend(featVec[axis+1:])  # 扩展列表元素
            retDataSet.append(reducedFeatVec)  # 添加嵌套列表
    return retDataSet

>> import DecisionTree as DT
>> mydat, labels = DT.createDataSet()
>> DT.splitDataSet(mydat, 0, 0)
>> DT.splitDataSet(mydat, 0, 1)
```
2. 选择最好的数据集划分方式
```python
"""
函数：选择最好的数据集划分方式
Para:
    dataSet:数据集
return:
    bestFeature:最好的特征的索引值

"""
def chooseBestFeatureToSplit(dataSet):

    numFeatures = len(dataSet[0]) - 1  # 特征的个数-1
    baseEntropy = calcShannonEnt(dataSet)  # 计算数据集的香农熵
    bestInfoGain = 0.0 ; bestFeature = -1  # 最大信息增益和最优划分特征的索引值
    for i in range(numFeatures): # 遍历特征
        featList = [example[i] for example in dataSet] # 列表生成式生成特征所有的取值
        uniqueVals = set(featList) # 删去重复值
        newEntropy = 0.0 # 香农熵
        for values in uniqueVals:  # 遍历特征值
            subDataSet = splitDataSet(dataset, i , value)  # 划分数据集
            prob = len(subDataSet) / float(len(dataSet))  # 计算概率
            newEntropy += prob * calcShannonEnt(subDataSet)  # 计算经验条件熵
        infoGain = baseEntropy - newEntropy  # 信息增益值
        print("第%d个特征的增益为%.3f" % (i, infoGain)) # 打印每个特征的信息增益，取正
        if(infoGain > baseEntropy):    # 找到对应最大信息增益的特征
            baseInfoGain = infoGain
            bestFeature = i
    return bestFeature

>> DecisionTree.chooseBestFeaturToSplit(mydat)
```
## 递归构建决策树
<div align = center>
<img src = "https://img.vim-cn.com/81/18e71a83e22a268a8899ee9aff50fe083ddbd4.png">
</div>

当特征值多与两个的时候，就可能存在大于两个分支的数据集划分，这时我们就通过递归调用来实现它！
**递归结束的条件**
程序遍历完所有划分数据的属性，或者每个分支下的所有实例都具有相同的分类。如果所有实例都具有相同的分类，则得到一个叶子节点或者终止快。任何到达叶子结点所属的分类必然属于叶子节点的类。
```python
"""
函数说明：统计classList中出现次数最多的元素（类标签）

Parameters:
    classList - 类标签列表
    
Returns:
    sortedClassCount[0][0] - 出现次数最多的元素（类标签）
    
"""   
def majorityCnt(classList):
    classCount = {}
    # 统计classList中每个元素出现的次数
    for vote in classList:
        if vote not in classCount.keys():
            classCount[vote] = 0
        classCount[vote] += 1
    # 根据字典的值降序排序
    # operator.itemgetter(1)获取对象的第1列的值
    sortedClassCount = sorted(classCount.items(), key = operator.itemgetter(1), reverse = True)
    # 返回classList中出现次数最多的元素
    return sortedClassCount[0][0]
```
**创建决策树的代码**
```python
"""
函数说明：创建决策树（ID3算法）
        递归有两个终止条件：1、所有的类标签完全相同，直接返回类标签
                        2、用完所有标签但是得不到唯一类别的分组，即特征不够用，挑选出现数量最多的类别作为返回

Parameters:
    dataSet - 训练数据集
    labels - 分类属性标签
    featLabels - 存储选择的最优特征标签
    
Returns:
    myTree - 决策树
"""
def createTree(dataSet, labels, featLabels):
    classList = [example[-1] for example in dataSet]   # 取分类标签（是否放贷：yes or no）
    if classList.count(classList[0]) == len(classList):  # 如果类别完全相同则停止继续划分
        return classList[0]
    if len(dataSet[0]) == 1:  # 遍历完所有特征时返回出现次数最多的类标签
        return majorityCnt(classList)
    bestFeat = chooseBestFeatureToSplit(dataSet) # 选择最优特征
    bestFeatLabel = labels[bestFeat]  # 最优特征的标签
    featLabels.append(bestFeatLabel)
    myTree = {bestFeatLabel:{}} # 根据最优特征的标签生成树
    del(labels[bestFeat])      # 删除已经使用的特征标签
    featValues = [example[bestFeat] for example in dataSet] # 得到训练集中所有最优解特征的属性值
    uniqueVals = set(featValues) # 去掉重复的属性值
    for value in uniqueVals: # 遍历特征，创建决策树
        myTree[bestFeatLabel][value] = createTree(splitDataSet(dataSet, bestFeat, value), labels, featLabels)
    return myTree

>> my tree = DecisionTree.createTree(mydata,labels)
>> my tree
```
## 测试算法与分类器
### 测试算法构造分类器
```python
"""
函数：使用决策树的分类函数
para:
    inputree,
    featLabels,
    testVec
return:
    classlabel,分类器
"""
def classify(inputTree, featLabels, testVec):
    # 获取决策树结点
    firstStr = next(iter(inputTree))
    # 下一个字典
    secondDict = inputTree[firstStr]
    featIndex = featLabels.index(firstStr)
    for key in secondDict.keys():
        if testVec[featIndex] == key:
            if type(secondDict[key]).__name__ == 'dict':
                classLabel = classify(secondDict[key], featLabels, testVec)
            else:
                classLabel = secondDict[key]
    return classLabel

```
### 使用算法
```python

"""
函数说明：存储决策树

Parameters:
    inputTree - 已经生成的决策树
    filename - 决策树的存储文件名
    
Returns:
    None
"""   
def storeTree(inputTree, filename):
    with open(filename, 'wb') as fw:
        pickle.dump(inputTree, fw)


"""
函数说明：读取决策树

Parameters:
    filename - 决策树的存储文件名
    
Returns:
    pickle.load(fr) - 决策树字典
""" 
def grabTree(filename):
    fr = open(filename, 'rb')
    return pickle.load(fr)
```