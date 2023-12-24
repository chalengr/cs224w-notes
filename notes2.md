# Measuring Networks and Random Graphs

在这一部分，我们研究四个关键的网络属性来描述一个图：度分布，路径长度，聚类系数和连通分量。定义将针对无向图进行介绍，但可以轻松扩展到有向图。

### 度分布

![image-20230817232807772](C:\Users\xwh1544123230\AppData\Roaming\Typora\typora-user-images\image-20230817232807772.png)

[地址](https://zhuanlan.zhihu.com/p/579667223)

### 图中的路径

图中两个节点之间的距离(distance)定义为两个点最短路径中的边数（如果两个点没有连通，距离通常定义为无穷大（或零））。

我们定义两两节点之间距离的最大值为图的直径（diameter）。

## ![image-20230818000525226](C:\Users\xwh1544123230\AppData\Roaming\Typora\typora-user-images\image-20230818000525226.png)

![image-20230818001547448](C:\Users\xwh1544123230\AppData\Roaming\Typora\typora-user-images\image-20230818001547448.png)



![image-20230818001602974](C:\Users\xwh1544123230\AppData\Roaming\Typora\typora-user-images\image-20230818001602974.png)

### 连通性

图的连通性衡量最大连通分量的大小。最大连通分量是一组最大的节点集合，其中任意两个节点都可以通过路径连接起来。

要找到连通分量：

1. 从一个随机节点开始执行广度优先搜索（BFS）。

2. 标记BFS访问的节点。

3. 如果所有节点都被访问，则网络是连通的。

4. 否则，找到一个未访问的节点并重复BFS。

   ### Erdős-Rényi随机图模型

   Erdős-Rényi随机图模型是最简单的图模型之一。这个简单的模型具有经过验证的网络属性，是与真实世界的图属性进行比较的良好基准。

   这个随机图模型有两个变种：

   1. 在$n$个节点上的无向图，每个边以概率$p$独立出现。
   2. 在$n$个节点上的无向图，随机选择$m$条边。

   注意，无论是$G(n,p)$还是$G(n,m)$，都不是唯一确定的，而是随机过程的结果。多次生成每个图会得到不同的图。

   关于$G(n,p)$的一些网络属性：

   1. ![image-20230818004001118](C:\Users\xwh1544123230\AppData\Roaming\Typora\typora-user-images\image-20230818004001118.png)

      ![image-20230818004324293](C:\Users\xwh1544123230\AppData\Roaming\Typora\typora-user-images\image-20230818004324293.png)

      

   2. 群聚系数：回顾一下，群聚系数的计算公式是
      ![image-20230818005100709](C:\Users\xwh1544123230\AppData\Roaming\Typora\typora-user-images\image-20230818005100709.png)

      这里的$\bar k$的意思是平均度

   3. 路径长度：对于$G(n,p)$，路径长度为$\ln n / \ln (1-p)$。这意味着，随着$n$的增加，路径长度以对数形式增加，但节点之间仍然只有几个跳跃的距离。

   4. 连通性：在$G(n,p)$中，存在一个临界概率$p_c = \frac{\ln n}{n}$，当$p < p_c$时，图通常是不连通的，而当$p > p_c$时，图通常是连通的。

   在网格网络中，我们可以实现三元闭包和高群聚性，但平均路径长度较长。

   在随机网络中，我们可以实现较短的平均路径长度，但群聚性较低。

   鉴于上述两种图结构，图可以同时具备Erdős-Rényi随机图模型和网格网络的特性。