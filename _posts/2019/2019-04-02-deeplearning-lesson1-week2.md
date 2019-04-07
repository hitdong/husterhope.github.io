---
layout: post
title: 第二周：神经网络的编程基础(Basics of Neural Network Programming)
categories:
- Deep Learning, 
tags:
- Deep Learning, Neural Network
---
[TOC]
### 2.1 二分类(Binary Classification) 
逻辑回归是一个用于二分类(**Binary regression**)的算法。假如你有一张图片作为输入，比如这只猫，如果识别这张图片是猫，则输出标签1作为结果; 如果识别不是猫这输出标签为0作为结果。我们用字母$y$来表示输出结果的标签, 如下图所示:
 ![](/media/pic2019/deeplearning_Andrew/lesson1/binary_classification_cat.png)

如果你的图片大小为64x64像素的彩色图片，可以用64x64x3的矩阵来表示
![](/media/pic2019/deeplearning_Andrew/lesson1/cat_pixel.png)

如果把这些像素用特征向量$x$表示，那么向量的的总维度是64x64x3=12,288。我们用$n_x=12,288$表示输入特征向量的维度。所以二分类问题的目标就是习的一个分类其，它以特征向量作为输入，然后预测输出结果$y$为1还是0,也就是预测图片中是否有猫
![](/media/pic2019/deeplearning_Andrew/lesson1/binary_classification_cat_cv.png)

后续课程需要用到的一些符号
**符号定义**:  
$x$:表示一个$n_x$为数据，为输入数据，维度为$(n_x, 1)$;  
$y$: 表示输出结果，取值为$(0, 1)$  
$(x^{(i)}, y^{(i)})$:表示第$i$组数据，可能是训练数据，也可能是测试数据，此处默认为训练数据  
$X=(x^{(1)}, x^{(2)},...,x^{(m)})$: 表示所有的训练数据的输入值，放在一个$n_x×m$的矩阵中，其中$m$表示样本数目;  
$Y=(y^{(1)}, y^{(2)},...,y^{(m)})$: 对应表示所有训练数据集的输出值，维度为$1×m$

最后为了能把训练集表示得更紧凑一点，我们会定义一个矩阵用大写$X$的表示，它由输入向量$x^{(1)}$、$x^{(2)}$等组成，如下图放在矩阵的列中，所以现在我们把$x^{(1)}$作为第一列放在矩阵中，$x^{(2)}$作为第二列，$x^{(m)}$放到第$m$列，然后我们就得到了训练集矩阵$X$。所以这个矩阵有$m$列，$m$是训练集的样本数量，然后这个矩阵的高度记为$n_x$，注意有时候可能因为其他某些原因，矩阵$X$会由训练样本按照行堆叠起来而不是列，如下图所示：$x^{(1)}$的转置直到$x^{(m)}$的转置，但是在实现神经网络的时候，使用左边的这种形式，会让整个实现的过程变得更加简单：
![](/media/pic2019/deeplearning_Andrew/lesson1/matrix_note.png)



