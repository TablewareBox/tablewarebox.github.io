---
layout:     post
title:      引言 | 复杂无序系统的崎岖势能面和多尺度现象
subtitle:   生物大分子、深度前馈网络的自旋玻璃建模
date:       2019-04-24
author:     TablewareBox
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - DL & BioPhysChem
    - 深度学习
    - 生物物理化学
    - 统计力学
    - 无序系统
---

## [深度学习的生物物理化学原理 - Notes Project Overview](https://tablewarebox.github.io/2019/02/16/DL_BioPhysChem_content/)

![knowledge atlas](https://tablewarebox.files.wordpress.com/2018/11/concept-map-81.png)

深度学习和蛋白质、染色质的折叠和相分离有什么共同的底层结构，又有什么不同？

## 一个例子

乍一听到这样的问题，即使同时熟悉两个领域，也很难想象它们有着极其紧密的联系。而发掘这些，也许更需要一个历史的视角。让我们从蛋白质折叠的一个**早期模型**[^1][^2][^3]，以及同时期的神经网络第二次浪潮——**Hopfield 联想记忆神经网络**[^4]谈起。

* Under construction:
- [ ] 蛋白折叠自旋玻璃模型和简单相图（折叠态、玻璃态、无规态）
- [ ] Hopfield 网络（自旋玻璃模型）存储容量相图
- [ ] Hopfield 网络作为蛋白折叠的一种“序列编码结构”模型

而 **Hopfield 联想记忆神经网络**的核心思想同样是，将目标数据存储在神经元间的**相互作用强度(权重)** 中，让它成为总能量的极小值点。实际运行中，相似数据 **“唤醒”记忆**的过程，也就是通过神经元状态的**时间演化**一步步修正，**联想**出目标数据的过程，这同时对应着势能面上的**能量极小化**[^5]。

![hopfield](https://tablewarebox.files.wordpress.com/2019/04/intro_1_hopfield.png)

<div align="center"><b>图1</b>  25×25的 Hopfield 网络权重矩阵中存储了4个25像素的<b>目标数据(模式)</b>。</div>
<div align="center">网络运行的时间演化中，任意的输入都会向目标数据(模式)靠近。因此名为“联想记忆”</div>

而蛋白折叠与自旋玻璃、结构玻璃不同的一点在于，蛋白折叠更多地表现出**漏斗状势能面**[^6]，或是不同构象有不同功能的蛋白质表现为 **“多漏斗”势能面**[^7]；而在不同种类的自旋玻璃模型中，往往有更多能量相近的**亚稳态**，并不一定有明显的“漏斗”[^8]。

![rugged](https://tablewarebox.files.wordpress.com/2019/04/intro_2_rugged.png)
<div align="center"><b>图2</b>  典型的<b>粗粒化蛋白质</b>和<b>自旋玻璃模型</b>势能面。</div>

![multifunnel](https://tablewarebox.files.wordpress.com/2019/04/intro_3_multifunnel.png)
<div align="center"><b>图3</b>  某多功能泛素蛋白的多漏斗势能面，用不连通图(disconnectivity graph) 表示。</div>

## 三个领域

现在我们回望整个发展历程，会发现**自旋玻璃模型**，不仅完全精确地描述了早期的**无向神经网络**结构和性质，同时是一个近似描述基本相互作用的**粗粒化的物理模型**，又是一个原始的**统计势函数**——给许多已知的结构赋予更低的能量（更高的**打分**），从而统计性地预测未知分子的结构。

在今天，早期的**自旋玻璃类无向神经网络**（笔记第3章），现代结构中已经演变为拥有不同架构的**有向神经网络**，但是基本的组成——拥有不同状态的**神经元**、神经元间的传递**权重和偏置**、引发非线性和概率性质的**激活函数**没有变，因此可以和早期神经网络找到对应：无向神经网络的**时间演化、动态问题**类似于有向神经网络的**层间传递、深度问题**。从而我们仍可以用发展成熟的自旋玻璃**静态、动态**理论，研究深度神经网络前向传播、反向传播中的问题（[笔记第4章](https://tablewarebox.github.io/2019/04/15/DL_BioPhysChem_04_DeepMFT/)）；或者直接建模网络的**损失曲面**[^9]，通过曲面上极小值的分布，给出为什么深度网络**较易训练**，梯度下降收敛到**局部极小值**也接近**全局最小值**（回忆上图自旋玻璃模型的势能面特点），同时还有一定**泛化能力**的原因。此外，随机性更强的**概率图模型**和**贝叶斯神经网络**中，自旋玻璃模型等统计力学的理论和算法也发挥着更大的作用（笔记第3章、第6章）。

现代的**统计势函数**（也可称为 **Knowledge-based**，或 **Data-driven** 方法），已经比自旋玻璃模型复杂许多，加入了概率方法、最大熵乃至深度学习方法，现代的**统计势函数(打分函数)** 和**物理的能量函数(如力场)** 共同使用时，已经能在较短时间内很好地预测蛋白质结构（如 **AlphaFold** 和蛋白设计领域所用的 **Rosetta 力场**）和染色质三维结构，但统计势函数天然在预测动力学上有所欠缺。

而在**物理模型**方面，人们为了更精准地从**第一性原理(First-principle)** 出发预测系统的热力学和动力学性质，逐渐发展了不同尺度和层级的物理模型：原子和小分子尺度的**量子力学**；大分子尺度的**分子动力学**和**粗粒化分子动力学**[^10]；介观尺度的**动理学方程、Boltzmann方程**和**耗散粒子动力学**；宏观尺度的**流体力学**。较低时间、空间尺度的理论能为上一层级提供**核心的信息**以简化运算，同时用多尺度方法处理好**不同尺度的耦合**[^11]。这种尺度变换同时**保留核心信息**的思路，物理中由**重整化群理论**、**动态重整化群理论**（笔记第5章）精确处理。

而在深度学习中，人们熟悉的一种理解是，训练后的网络能一层层提取数据中的核心特征，并且从小到大组合起来。这和重整化群理论有什么对应关系？现在理论已经能证明**受限玻尔兹曼机(RBM)** 和**变分重整化群**完全等价[^12]，然而要利用**无向和有向神经网络的联系**，将重整化群理论用于定量理解现代网络结构的**层级特征提取**，还需要付出许多努力。

![multiscale](https://tablewarebox.files.wordpress.com/2019/04/intro_4_multiscale.png)
<div align="center"><b>图4</b>  粗粒化、多尺度建模与计算</div>

## 自旋玻璃模型的其他应用

经过这样的多尺度处理，一般**能量函数**会比自旋玻璃模型中的形式复杂许多，涉及空间，非线性，以及比二次项更高的相互作用。如分子动力学中的**力场**，就需要拟合键长变化、键角变化、二面角变化、范德华相互作用、静电相互作用、溶剂影响等对能量的贡献。但在更大的尺度上，如**蛋白相互作用**、**染色质的折叠**等问题上，自旋玻璃模型的简单势能函数仍不失为一种很好的近似，并且能成功预言许多性质。

### 染色质三维结构模拟的统计方法（Under improvement）

染色质的三维结构及其动态变化在基因调控，乃至整个生命过程中扮演着重要的角色。简单的染色质三维结构统计预测遵循着预测蛋白折叠一样的思路：序列编码结构。只不过为了达到预测效果，使用的并不是 DNA 序列，而是染色质上不同性质的区段——主要是表观遗传修饰、染色质紧密程度等。一个重要的基于实验的假设是，相同性质的染色质区段可以通过特定蛋白的交联从而实现相互作用。



### 染色质三维结构模拟的物理方法（Under improvement）

与统计方法不同的是，物理方法直接考虑相互作用强度：设定几种染色质状态，给定它们的相互作用强度（通过调节参数，或者），直接在面心立方的格点模型中进行 Monte Carlo 模拟，在不同的平均相互作用强度下，可以模拟出从无序的“混相”状态到逐渐微观相分离的变化。这样的结果与两嵌段共聚物的自洽场理论模拟非常相似。（嵌段共聚物的自洽场理论、动态自洽场理论模拟，同时就是[笔记第4章](https://tablewarebox.github.io/2019/04/15/DL_BioPhysChem_04_DeepMFT/)的动态平均场、深度平均场）。模拟还能表现出染色质的非平衡动力学。

![microsep1](https://tablewarebox.files.wordpress.com/2019/04/intro_5_microsep1.png)

![microsep2](https://tablewarebox.files.wordpress.com/2019/04/intro_6_microsep2.png)

### 小区域内的“超级增强子”基因调控：蛋白聚集与高聚物凝胶化



* Under construction:
- [ ] 进化的种群动力学与势能面的多尺度结构
- [ ] 作为多体问题的干细胞分化
- [ ] 过冷液体、结构玻璃；自旋玻璃的动态理论重现结构玻璃的 Mode Coupling Theory
- [ ] 信息论与编码、压缩感知、组合优化

## 参考文献

[^1]: Joseph D. Bryngelson, and Peter G. Wolynes. **Spin glasses and the statistical mechanics of protein folding.** *Proc. Nati. Acad. Sci. USA* **1987**, *84(21)*, 7524-7528. DOI: 10.1073/pnas.84.21.7524

[^2]: Joseph D. Bryngelson, and Peter G. Wolynes. **Intermediates and barrier crossing in a random energy model (with applications to protein folding).** *J. Phys. Chem.* **1989**, *93*, 6902-6915. DOI: 10.1021/j100356a007

[^3]: Richard A. Goldstein, Zaida A. Luthey-Schulten, and Peter G. Wolynes. **Optimal protein-folding codes from spin-glass theory.** *Proc. Nati. Acad. Sci. USA* **1992**, *89*, 4918-4922. DOI: 10.1073/pnas.89.11.4918

[^4]: J. J. Hopfield. **Neural networks and physical systems with emergent collective computational abilities.** *Proc. Nati. Acad. Sci. USA* **1982**, *79*, 2554-2558. DOI: 10.1073/pnas.79.8.2554

[^5]: David J.C. MacKay. **Information Theory, Inference, and Learning Algorithms (ITILA).**

[^6]: José Nelson Onuchic, Zaida Luthey-Schulten and Peter G. Wolynes. **Theory of protein folding: the energy landscape perspective.** *Annu. Rev. Phys. Chem.*  **1997**, *48*, 545–600. DOI: 10.1146/annurev.physchem.48.1.545

[^7]: Konstantin Röder, Jerelle A. Joseph, Brooke E. Husic, and David J. Wales. **Energy Landscapes for Proteins: From Single Funnels to Multifunctional Systems.** *Adv. Theory Simul.* **2019**, 1800175. DOI: 10.1002/adts.201800175

[^8]: Wolfhard Janke (Ed.) **Rugged Free Energy Landscapes: Common Computational Approaches to Spin Glasses, Structural Glasses and Biological Macromolecules.** *Lect. Notes Phys.* 736 (Springer, Berlin Heidelberg 2008), DOI: 10.1007/978-3-540-74029-2

[^9]: Choromanska, Anna, Henaff, Mikael, Mathieu, Michaël, Arous, Gérard Ben, and LeCun, Yann. **The loss surface of multilayer networks.** *JMLR*, 38, 2015.

[^10]: Sebastian Kmiecik, Dominik Gront, Michal Kolinski, Lukasz Wieteska, Aleksandra Elzbieta Dawid, and Andrzej Kolinski. **Coarse-Grained Protein Models and Their Applications.** *Chem. Rev.* **2016**, *116*, 7898−7936. DOI: 10.1021/acs.chemrev.6b00163

[^11]: Weinan E. **Principles of Multiscale Modeling.** **2011**

[^12]: Pankaj Mehta, and David J. Schwab. **An exact mapping between the Variational Renormalization Group and Deep Learning.** arXiv:1410.3831v1