---
layout:     post
title:      系列目录 | 深度学习的生物物理化学原理
subtitle:   共同的底层结构、理论和算法
date:       2019-02-16
author:     TablewareBox
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - 笔记目录
    - DL & BioPhysChem
    - 深度学习
    - 生物物理化学
    - 统计力学
    - 无序系统
---

## 序言

> More is different. ——P. W. Anderson，1977年诺贝尔物理学奖得主

**深度学习**是机器学习和人工智能研究的最新趋势之一。强大的**表达能力**，相对较低的**优化和训练难度**，优秀的**泛化能力**，使它在计算机视觉、自然语言处理、语音识别、自动驾驶、图像和文本生成、智能控制等任务上已经获得了广泛的工业应用，并成为学术界和媒体的热门话题。近年来，新的硬件、新的模型架构、新的训练方法、新的数据集不断涌现，推动着深度学习领域的高速发展。

然而，深度学习为何具有如此优异的表现，仍然缺乏**统一的理论**来描述。这使它的运行过程像一个“**黑箱**”，设计新的网络架构也是一个需要创造力、经验和运气，而非科学的工作。

在当前深度学习理论研究成为焦点时，我们回望深度学习的发展历程，会发现**物理化学、统计力学**，和神经科学一样，起着不可或缺的作用。就连被称为 “The Godfather of Deep Learning” 的 Geoffrey Hinton 教授，他的 PhD 导师 Christopher Longuet-Higgins 教授，也同时是一位理论化学家（后来从事认知科学研究）。这一思想在当前深度学习理论的研究中已经复兴，但究其来源，则是在上世纪 80 年代，以“**联结主义**”为名的神经网络第二次浪潮中。

**联结主义 (connectionism)** 认为，当网络将**大量简单的计算单元**连接在一起时可以实现智能行为。这正是复杂系统中的典型现象——大量相互作用的基本个体，可以随时间演化而产生**自组织**，展现出宏观的**集体行为**，使得在新的时间和空间尺度上，**涌现**出新的规律。代表性工作，Hopfield 联想记忆神经网络的论文题目“Neural networks and physical systems with emergent collective computational abilities” 便是这一思想最直观的体现。连接大量微观个体的动力学与宏观性质的，便是**统计力学**。

![complex system](https://tablewarebox.files.wordpress.com/2018/11/complex-system.jpg?w=768&h=769)
<div align="center">图1 复杂系统</div>

上世纪70年代起，统计力学研究开始从**有序系统**，如晶体、均匀液体和气体，转而更多地关注**无序系统**，如自旋玻璃、结构玻璃、高聚物网络等。无序系统的统计力学理论在神经科学、进化生物学、系统生物学、软物质科学、信息论与编码、组合优化，甚至社会学、经济学中获得了广泛成功，这些领域和深度学习具有**类似的底层结构**：大量相互关联的随机变量或微观个体。预印本 arXiv 网站中的领域分类，凝聚态物理下的一项就是 disordered system and neural network。

为此，我们花费了半年多的时间，整理了网络上零散的论文、讲座、问答、博客，试图勾勒出生物和物理化学思想在深度学习中的隐秘轮廓：

> 相比统计学，深度学习似乎更像统计力学。

希望这份笔记能为不同相关领域从业者提供新的视角。欢迎讨论和批评指正。

![knowledge atlas](https://tablewarebox.files.wordpress.com/2018/11/concept-map-81.png)
<div align="center">图2 深度学习与物理化学</div>

## 目录预告

### [引言：复杂无序系统的崎岖势能面和多尺度现象](https://tablewarebox.github.io/2019/04/24/DL_BioPhysChem_01_Introduction/)

* 蛋白质折叠、生物进化、结构玻璃和自旋玻璃
* 信息论与编码、压缩感知、组合优化、神经网络

### 深度学习简介

* 物理视角下的深度学习历史回顾
* 有监督学习、深度神经网络简介
  * 计算图
  * 反向传播算法
  * 正则化方法
  * 卷积、循环和图神经网络
* 基于能量的模型
* 概率图模型简介
  * 有向图模型（贝叶斯网络）
  * 无向图模型（马尔可夫随机场）
  * 因子图
  * 图模型中的推断
  * 概率图模型与深度神经网络的关系
* 无监督学习和生成模型简介
  * 联想记忆：Hopfield 网络
  * 玻尔兹曼机
  * 变分自编码器（VAE）
  * 生成对抗网络（GAN）
  * 深度生成模型的概率图模型和能量视角

### 自旋玻璃与消息传递：Hopfield 网络到 RBM

* Hopfield 网络与自旋玻璃模型
* 热力学（静态）性质
  * 平均场、变分法和微扰法
  * 复本对称平均场解与信念传播：Hopfield 网络存储容量相变
  * 一阶复本对称破缺（1RSB）与概观传播
* 动力学（动态）性质
  * Langevin 方程
  * 响应函数、关联函数、涨落-耗散定理
  * 生成泛函（路径积分）方法
  * 动力学相变
* 深度前馈网络的自旋玻璃建模
* 图神经网络中的消息传递
* 生物大分子和进化动力学的自旋玻璃建模

### [深度平均场理论与统计神经动力学](https://tablewarebox.github.io/2019/04/15/DL_BioPhysChem_04_DeepMFT/)

* [Part I - 理论基础](https://tablewarebox.github.io/2019/04/15/DL_BioPhysChem_04_DeepMFT/)
  * 动态平均场理论回顾
  * 深度平均场：理论假设与高斯过程视角
  * 深度网络的指数级表达能力
  * 深度信息传播：训练中的有序-混沌相变
* Part II - 训练技巧
  * 训练技巧 I: 临界初始化 - 动态等距与普适类
  * 训练技巧 II: 残差网络的运行原理
  * 训练技巧 III: 层宽度变化、层方差变化的运行原理
  * 训练技巧 IV: 批归一化的运行原理
* Part III - 网络结构
  * CNN 的平均场理论
  * RNN, LSTM, GRU 的平均场理论
  * 图网络的平均场理论

### 重整化群、临界现象和信息瓶颈理论

* RBM 与变分重整化群的对应关系
* 信息瓶颈原理与重整化群
* 重整化群理论的其他启示

### 高斯过程与贝叶斯神经网络

* DNN 作为高斯过程
* 贝叶斯神经网络
* 扩散概率模型与非平衡统计力学