---
title: 图
date: 2021-05-09 22:50:51
description: 图
# top_img: https://cdn.jsdelivr.net/gh/halo-blog/cdn-blog-img-a@main/img/704736.jpg # 页面顶部图片
cover: https://cdn.jsdelivr.net/gh/halo-blog/cdn-blog-img-c@master/wallhaven-g8reee.4ts0wc1e2740.png
mathjax: true
#katex: true
large: true
# sticky: 2
bilibili_banner: spring
categories: 数据结构
tags:
  - 数据结构
---

{% link C语言实现图数据结构, https://github.com/TheAlgorithms/C/tree/master/data_structures/graphs, https://cdn.jsdelivr.net/gh/halo-blog/cdn-blog-img-b@master/img/GithubIcon.jpg %}

## 图的基本概念

### 图的定义

图 $G$ 由顶点集 $V$ 和边集 $E$ 组成，记为 $G=(V,E)$，其中 $V(G)$ 表示图 $G$ 中顶点的有限非空集；$E(G)$ 表示图 $G$ 中顶点之间的关系 （边）集合。若 $V= \\{v_1,v_2,\dots v_n\\}$，则用 $|V|$ 表示图 $G$ 中顶点的个数，也称图 $G$ 的阶，$E= \\{(\mu,\nu)|\mu \in V,\nu \in V  \\} $，用 $|E|$ 表示图 $G$ 中边的条数。

注意：线性表可以是空表，树可以是空树，但图不可以是空图。就是说，图中不能一个顶点也没有，图的顶点集 $V$ 一定非空，但边集 $E$ 可以为空，此时图中只有顶点而没有边。

下面是图的一些基本概念及术语。

### 有向图和无向图

若 $E$ 是有向边（也称弧）的有限集合时，则图 $G$ 为有向图。弧是顶点的有序对，记为 $ \langle v,w\rangle $ ，其中 $v$，$w$ 是顶点，$v$ 称为弧尾，$w$ 称为弧头， $\langle v, w \rangle $  称为从顶点 $v$ 到顶点 $w$ 的弧，也称 $v$ 邻接到 $w$，或 $w$ 邻接自 $v$。

若 $E$ 是无向边（简称边）的有限集合时，则图 $G$ 为无向图。边是顶点的无序对，记为 $(v,w)$ 或 $(w,v)$，因为$(v, w)=(w,v)$ 其中 $v$，$w$ 是顶点。可以说顶点 $w$ 和顶点 $v$ 互为邻接点。边 $(v, w)$ 依附于顶点 $w$ 和 $v$ ，或者说边 $(v, w)$ 和顶点 $v$，$w$ 相关联。

### 简单图和多重图

一个图 $G$ 若满足：

1. 不存在重复边；
2. 不存在顶点到自身的边，则称图 $G$ 为简单图。

数据结构中仅讨论简单图。

若图 $G$ 中某两个结点之间的边数多于一条，又允许顶点通过同一条边和自己关联，则 $G$ 为多重图。多重图的定义和简单图是相对的。

### 顶点的度、入度和出度

图中每个顶点的度定义为以该顶点为一个端点的边的数目。

对于无向图，顶点 $v$ 的度是指依附于该顶点的边的条数，记为 $\mathrm{TD} (v)$。

在具有 $n$ 个顶点、$e$ 条边的无向图中$$ \sum\_{i=1}^{n} \mathrm{TD} (v_i)=2e $$即无向图的全部顶点的度的和等于边数的 2 倍，因为每条边和两个顶点相关联。

对于有向图，顶点 $v$ 的度分为入度和出度，入度是以顶点 $v$ 为终点的有向边的数目，记为 $\mathrm{ID}(v)$；而出度是以顶点 $v$ 为起点的有向边的数目，记为 $\mathrm{OD}(v)$。顶点 $v$ 的度等于其入度和出度之和，即 $\mathrm{TD} (v)=\mathrm{ID}(v)+\mathrm{OD}(v)$。

在具有 $n$ 个顶点、$e$ 条边的有向图中，$$\sum_{i=1}^{n} \mathrm{ID} (v_i)=\sum_{i=1}^{n} \mathrm{OD} (v_i)=e $$即有向图的全部顶点的入度之和与出度之和相等，并且等于边数。这是因为每条有向边都有一个起点和终点。

### 路径、路径长度和回路

顶点 $v_p$ 到顶点 $v_q$ 之间的一条路径是指顶点序列 $v_p,v_{i1},v_{i2},\dots ,v_{im},v_q$，当然关联的边也可以理解为路径的构成要素。

路径上边的数目称为路径长度。

第一个顶点和最后一个顶点相同的路径称为回路或环。若一个图有 $n$ 个顶点，并且有大于 $n-1$ 条边，则此图一定有环。

### 简单路径、简单回路

在路径序列中，顶点不重复出现的路径称为简单路径。

除第一个顶点和最后一个顶点外，其余顶点不重复出现的回路称为简单回路。

### 距离

从顶点 $u$ 出发到顶点 $v$ 的最短路径若存在，则此路径的长度称为从 $u$ 到 $v$ 的距离；若从 $u$ 到 $v$ 根本不存在路径，则记该距离为无穷( $∞$ )

### 连通、连通图

在无向图中，若从顶点 $v$ 到顶点 $w$ 有路径存在，则称 $v$ 和 $w$ 是连通的。若图 $G$ 中任意两个顶点都是连通的，则称图 $G$ 为<font color="#ea66a6">连通图</font>，否则称为非连通图。

若图 $G$ 是连通图，则至少有 $n-1$ 条边。若 $G$ 是非连通图，则至多可能有 $C_{n-1}^{2}$ 条边

### 强连通图

在有向图中，若从顶点 $v$ 到顶点 $w$ 和从顶点 $w$ 到顶点 $v$ 之间都有路径，则称这两个顶点是强连通的。若图中任何一对顶点都是强连通的，则称此图为强连通图。

若 $G$ 是强连通图，则最少有 $n$ 条边（形成回路）

注意：强连通图、强连通分量只是针对有向图而言的。一般在无向图中讨论连通性，在有向图中考虑强连通性。

### 子图

设有两个图 $G=(V,E)$ 和 $G'=(V',E')$ ，若 $V'$ 是 $V$ 的子集，且 $E'$ 是 $E$ 的子集，则称 $G'$ 是 $G$ 的子图。若有满足 $V(G')=V(G)$ 的子图 $G'$ ，则称其为 $G$ 的生成子图。

注意：并非 $V$ 和 $E$ 的任何子集都能构成 $G$ 的子图，因为这样的子集可能不是图，即 $E$ 的子集中的某些边关联的顶点可能不在这个 $V$ 的子集中。

### 连通分量、强连通分量

无向图中的极大连通子图称为连通分量。

![无向图及其连通分量](https://cdn.jsdelivr.net/gh/halo-blog/cdn-blog-img-a@main/img/无向图及其连通分量.png)

有向图中的极大强连通子图称为有向图的强连通分量。

> 注意：要区分极大连通子图和极小连通子图，极大连通子图是无向图的连通分量，极大即要求该连通子图包含其所有的边；极小连通子图是既要保持图连通又要使得边数最少的子图。

### 生成树、生成森林

连通图的生成树是包含图中全部顶点的一个极小连通子图。若图中顶点数为 $n$ ，则它的生成树含有 $n-1$ 条边。

对生成树而言，若砍去它的一条边，则会变成非连通图，若加上一条边则会形成一个回路。

在非连通图中，连通分量的生成树构成了非连通图的生成森林。

### 边的权和网

在一个图中，每条边都可以标上具有某种含义的数值，该数值称为该边的权值。这种边上带有权值的图称为带权图，也称网。

带权路径长度：当图是带权图时，一条路径上所有边的权值之和，称为该路径的带权路径长度

### 完全图

无向完全图：无向图中任意两个顶点之间都存在边，若无向图的顶点数 $|V|=n$ ，则 $|E|\in [0,C_n^2]=[0,\frac{n(n-1)}{2} ] $

有向完全图：有向图中任意两个顶点之间都存在方向相反的两条弧，若有向图的顶点数 $|V|=n$ ，则 $|E|\in [0,2C_n^2]=[0,n(n-1) ] $

### 稠密图、稀疏图

边数很少的图称为稀疏图，反之称为稠密图。

稀疏和稠密本身是模糊的概念，稀疏图和稠密图常常是相对而言的。一般当图 $G$ 满足 $|E| < |V|\log|V|$ 时，可以将 $G$ 视为稀疏图。

### 树、有向树

树：不存在回路，且连通的无向图。$n$ 个顶点的树，必有 $n-1$ 条边。

一个顶点的入度为 0，其余顶点的入度均为 1 的有向图，称为有向树。

## 图的存储及基本操作

### 邻接矩阵法

所谓邻接矩阵存储，是指用一个一维数组存储图中顶点的信息，用一个二维数组存储图中边的信息（即各顶点之间的邻接关系），存储顶点之间邻接关系的二维数组称为邻接矩阵。

<img src="https://cdn.jsdelivr.net/gh/halo-blog/cdn-blog-img-a@main/img/有向图、无向图及网的邻接矩阵.png" alt="有向图、无向图及网的邻接矩阵" style="zoom:200%;" />

图的邻接矩阵存储结构定义如下：

```c++
#define MaxVertexNum 100  // 顶点数目的最大值
typedef char VertexType;  // 顶点的数据类型
typedef int EdgeType;     // 带权图中边上权值的数据类型
typedef struct {
    VertexType Vex[MaxVertexNum];               // 顶点表
    EdgeType Edge[MaxVertexNum][MaxVertexNum];  // 邻接矩阵，边表
    int vexnum, arcnum;  // 图的当前顶点数和边数/弧数
} MGraph;
```

注意：

1. 在简单应用中，可直接用二维数组作为图的邻接矩阵（顶点信息等均可省略）。
2. 当邻接矩阵中的元素仅表示相应的边是否存在时，`EdgeType` 可定义为值为 0 和 1 的枚举类型。
3. 无向图的邻接矩阵是<font color="#faa755">对称矩阵</font>，对规模特大的邻接矩阵可采用[压缩存储](http://halo123.top/2021/05/02/DataStructure/C_StacksAndQueues/#对称矩阵)。
4. 邻接矩阵表示法的空间复杂度为 $O(n^2)$，其中 $n$ 为图的顶点数 $|V|$。

图的邻接矩阵存储表示法具有以下特点：

1. 对于无向图，邻接矩阵的第 $i$ 行（或第 $i$ 列）非零元素（或非 $∞$ 元素）的个数正好是第 $i$ 个顶点的度 $TD(v)$。时间复杂度 $O(|V|)$。
2. 对于有向图，邻接矩阵的第 $i$ 行（或第 $i$ 列）非零元素（或非 $∞$ 元素）的个数正好是第 $i$ 个顶点的出度 $OD(v)$ [或入度 $ID(v)$ ]。第 $i$ 行结点的度即为，第 $i$ 行和列的非零元素（或非 $∞$ 元素）的个数之和。时间复杂度 $O(|V|)$。
3. 设图 $G$ 的邻接矩阵为 $\mathbf{A} $，$\mathbf{A}^n$ 的元素 $A^n[i][j]$ 等于由顶点 $i$ 到顶点 $j$ 的长度为 $n$ 的路径的数目。（妙啊）
4. 稠密图适合使用邻接矩阵的存储表示。
5. 无向图的邻接矩阵一定是一个对称矩阵（并且唯一）。 因此，在实际存储邻接矩阵时只需存储上（或下）三角矩阵的元素。
6. 用邻接矩阵法存储图，很容易确定图中任意两个顶点之间是否有边相连。但是，要确定图中有多少条边，则必须按行、按列对每个元素进行检测，所花费的时间代价很大。

### 邻接表法

当一个图为稀疏图时，使用邻接矩阵法显然要浪费大量的存储空间，而图的邻接表法结合了顺序存储和链式存储方法，大大减少了这种不必要的浪费。

所谓邻接表，是指对图 $G$ 中的每个顶点 $v_i$ 建立一个单链表，第 $i$ 个单链表中的结点表示依附于顶点 $v_i$ 的边（对于有向图则是以顶点 $v_i$ 为尾的弧），这个单链表就称为顶点 $v_i$ 的边表（对于有向图则称为出边表）。边表的头指针和顶点的数据信息采用顺序存储（称为顶点表），所以在邻接表中存在两种结点：顶点表结点和边表结点。

```c++
#define MaxVertexNum 100 // 图中顶点数目的最大值
typedef char VertexType;  // 顶点的数据类型
// "边/弧"
typedef struct ArcNode {
    int adjvex;            // "边/弧"指向哪个结点
    struct ArcNode *next;  // 指向下一条弧的指针
    // InfoType info       // 边权值
} ArcNode;

// "顶点"
typedef struct VNode {
    VertexType data;  // 顶点信息
    ArcNode *first;   // 第一条边/弧
} VNode, AdjList[MaxVertexNum];

// 用邻接表存储的图
typedef struct {
    AdjList vertices;
    int vexnum, arcnum;
} ALGraph;
```

![无向图邻接表表示法实例](https://cdn.jsdelivr.net/gh/halo-blog/cdn-blog-img-a@main/img/无向图邻接表表示法实例.png)

![有向图邻接表表示法实例](https://cdn.jsdelivr.net/gh/halo-blog/cdn-blog-img-a@main/img/有向图邻接表表示法实例.png)

图的邻接表存储方法具有以下特点：

1. 若 $G$ 为无向图，则所需的存储空间为 $O(|V|+ 2|E|)$；若 $G$ 为有向图，则所需的存储空间为 $O(|V|+ |E|)$。前者的倍数 2 是由于无向图中，每条边在邻接表中出现了两次。
2. 对于稀疏图，采用邻接表表示将极大地节省存储空间。
3. 在邻接表中，给定一顶点，能很容易地找出它的所有邻边，因为只需要读取它的邻接表。在邻接矩阵中，相同的操作则需要扫描一行，花费的时间为 $O(n)$ 。 但是，若要确定给定的两个顶点间是否存在边，则在邻接矩阵中可以立刻查到，而在邻接表中则需要在相应结点对应的边表中查找另一结点，效率较低。
4. 在有向图的邻接表表示中，求一个给定顶点的<font color="#faa755">出度</font>只需计算其邻接表中的结点个数；但求其顶点的<font color="#faa755">入度</font>则需要遍历全部的邻接表。因此，也有人采用逆邻接表的存储方式来加速求解给定顶点的入度。当然，这实际上与邻接表存储方式是类似的。
5. 图的邻接表表示并不唯一，因为在每个项点对应的单链表中，各边结点的链接次序可以是任意的，它取决于建立邻接表的算法及边的输入次序。

### 十字链表法

十字链表是<font color="#faa755">有向图</font>的一种链式存储结构。在十字链表中，对应于有向图中的每条弧有一个结点，对应于每个顶点也有一个结点。

弧结点中有 5 个域：尾域（`tailvex`） 和头域（`headvex`）分别指示弧尾和弧头这两个顶点在图中的位置；链域 `hlink` 指向弧头相同的下一条弧；链域 `tlink` 指向弧尾相同的下一条弧；`info` 域指向该弧的相关信息。这样，弧头相同的弧就在同一个链表上，弧尾相同的弧也在同一个链表上。

顶点结点中有 3 个域：`data` 域存放顶点相关的数据信息，如顶点名称；`firstin` 和 `firstout` 两个域分别指向以该顶点为弧头或弧尾的第一个弧结点。

![有向图的十字链表表示](https://cdn.jsdelivr.net/gh/halo-blog/cdn-blog-img-a@main/img/有向图的十字链表表示.png)

在十字链表中，既容易找到 $V_i$ 为尾的弧，又容易找到 $V_i$ 为头的弧，因而容易求得顶点的出度和入度。图的十字链表表示是不唯一的， 但一个十字链表表示确定一个 图。空间复杂度：$O(|V|+|E|)$

TODO 代码实现十字链表法

### 邻接多重表法

邻接多重表是<font color="#faa755">无向图</font>的另一种链式存储结构。

在邻接表中，容易求得顶点和边的各种信息，但在邻接表中求两个顶点之间是否存在边而对边执行删除等操作时，需要分别在两个顶点的边表中遍历，效率较低。

与十字链表类似，在邻接多重表中，每条边用一个结点表示，其结构如下所示。

其中，`mark` 为标志域，可用以标记该条边是否被搜索过；`ivex` 和 `jvex` 为该边依附的两个顶点在图中的位置；`ilink` 指向下一条依附于顶点 `ivex` 的边；`jlink` 指向下一条依附于顶点 `jvex` 的边，`info` 为指向和边相关的各种信息的指针域。

每个顶点也用一个结点表示，它由如下所示的两个域组成。

其中，`data` 域存储该顶点的相关信息，`firstedge` 域指示第一条依附于该顶点的边。

在邻接多重表中，所有依附于同一顶点的边串联在同一链表中，由于每条边依附于两个顶点，因此每个边结点同时链接在两个链表中。对无向图而言，其邻接多重表和邻接表的差别仅在于，同一条边在邻接表中用两个结点表示，而在邻接多重表中只有一个结点。

![无向图的邻接多重表表示](https://cdn.jsdelivr.net/gh/halo-blog/cdn-blog-img-a@main/img/无向图的邻接多重表表示.png)

空间复杂度：$O(|V|+|E|)$。

### 图的基本操作

图的基本操作是独立于图的存储结构的。而对于不同的存储方式，操作算法的具体实现会有着不同的性能。在设计具体算法的实现时，应考虑采用何种存储方式的算法效率会更高。

图的基本操作主要包括（仅抽象地考虑，故忽略掉各变量的类型）：

- `Adjacent (G,x,y)`：判断图 $G$ 是否存在边 $ \langle x,y \rangle $ 或 $(x,y)$。邻接矩阵时间复杂度：$O(1)$，邻接表时间复杂度：$O(1)\sim  O(|V|)$。
- `Neighbors (G,x)`：列出图 $G$ 中与结点 $x$ 邻接的边。邻接矩阵时间复杂度：$O(|V|)$；邻接表无向图时间复杂度：$O(1)\sim  O(|V|)$，邻接表有向图出边时间复杂度：$O(1)\sim O(|V|)$，邻接表有向图入边时间复杂度：$O(|E|)$。
- `InsertVertex(G,x)`：在图 $G$ 中插入顶点 $x$ 。邻接矩阵和邻接表时间复杂度：$O(1)$
- `DeleteVertex(G,x)`：从图 $G$ 中删除顶点 $x$。邻接矩阵无向图时间复杂度：$O(|V|)$，邻接表无向图时间复杂度：$O(1)\sim O(|E|)$；邻接矩阵有向图时间复杂度：$O(|V|)$，邻接表删出边：$O(1)\sim O(|V|)$，邻接表删入边：$O(|E|)$
- `AddEdge (G,x,y)`：若无向边 $(x, y)$ 或有向边 $ \langle x,y \rangle $ 不存在，则向图 $G$ 中添加该边。邻接矩阵 $O(1)$，邻接表 $O(1)$
- `RemoveEdge(G,x,y)`：若无向边 $(x, y)$ 或有向边 $ \langle x,y \rangle $ 存在，则从图 $G$ 中删除该边。邻接矩阵 $O(1)$，邻接表 $O(1) \sim O(|V|)$
- `FirstNeighbor(G,x)`：求图 $G$ 中顶点 $x$ 的第一个邻接点，若有则返回顶点号。若 $x$ 没有邻接点或图中不存在 $x$ ，则返回 -1。邻接矩阵无向图 $O(1)\sim O(|V|)$，邻接表无向图 $O(1)$；邻接矩阵有向图 $O(1)\sim O(|V|)$，邻接表有向图找出边邻接点：$O(1)$，邻接表有向图找入边邻接点：$O(1)\sim O(|E|)$
- `NextNeighbor (G,x,y)`：假设图 $G$ 中顶点 $y$ 是顶点 $x$ 的一个邻接点，返回除 $y$ 外顶点 $x$ 的下一个邻接点的顶点号，若 $y$ 是 $x$ 的最后一个邻接点，则返回 -1。邻接矩阵 $O(1)\sim O(|V|)$，邻接表 $O(1)$；
- `Get_edge_value(G,x,y)`：获取图 $G$ 中边 $(x, y)$ 或 $ \langle x,y \rangle $ 对应的权值。时间复杂度同 `Adjacent (G,x,y)`
- `Set_edge_value(G,x,y,v)`：设置图 $G$ 中边 $(x, y)$ 或 $ \langle x,y \rangle $ 对应的权值为 $v$ 。时间复杂度同 `Adjacent (G,x,y)`

此外，还有图的遍历算法：按照某种方式访问图中的每个顶点且仅访问一次。图的遍历算法包括深度优先遍历和广度优先遍历。

TODO 分析十字链表法和邻接多重表法下的基本操作的时间复杂度

## 图的遍历

图的遍历是指从图中的某一顶点出发，按照某种搜索方法沿着图中的边对图中的所有顶点访问一次且仅访问一次。注意到树是一种特殊的图，所以树的遍历实际上也可视为一种特殊的图的遍历。图的遍历算法是求解图的连通性问题、拓扑排序和求关键路径等算法的基础。

图的遍历比树的遍历要复杂得多，因为图的任一顶点都可能和其余的顶点相邻接，所以在访问某个顶点后，可能沿着某条路径搜索又回到该顶点上。为避免同一顶点被访问多次，在遍历图的过程中，必须记下每个已访问过的顶点，为此可以设一个辅助数组 `visited[]` 来标记顶点是否被访问过。图的遍历算法主要有两种：广度优先搜索和深度优先搜索。

### 广度优先搜索

广度优先搜索（Breadth-First- Search, BFS）类似于二叉树的层序遍历算法。基本思想是：首先访问起始顶点 $v$ ，接着由 $v$ 出发，依次访问 $v$ 的各个未访问过的邻接顶点 $w_1,w_2,\dots ,w_i$ 然后依次访问 $w_1,w_2,\dots ,w_i$ 的所有未被访问过的邻接顶点；再从这些访问过的顶点出发，访问它们所有未被访问过的邻接顶点，直至图中所有顶点都被访问过为止。若此时图中尚有顶点未被访问，则另选图中一个未曾被访问的顶点作为始点，重复上述过程，直至图中所有顶点都被访问到为止。Dijkstra 单源最短路径算法和 Prim 最小生成树算法也应用了类似的思想。

换句话说，广度优先搜索遍历图的过程是以 $v$ 为起始点，由近至远依次访问和 $v$ 有路径相通且路径长度为 1，2，... 的顶点。广度优先搜索是一种分层的查找过程，每向前走一步可能访问一批顶点，不像深度优先搜索那样有往回退的情况，因此它不是一个递归的算法。为了实现逐层的访问，算法必须<font color="#faa755">借助一个辅助队列</font>，以记忆正在访问的顶点的下一层顶点。

广度优先遍历算法的伪代码如下：

```c++
bool visited[MaxVertexNum];  // 访问标记数组

void BFSTraverse(Graph G) {  // 对图G进行广度优先遍历
    for (int i = 0; i < G.vexnum; ++i) {
        visited[i] = false;  // 访问标记数组初始化
    }
    InitQueue(Q);                         // 初始化辅助队列Q
    for (int j = 0; j < G.vexnum; ++j) {  // 从0号顶点开始遍历
        if (!visited[j]) {  // 对每个连通分量调用一次 BFS
            BFS(G, j);
        }
    }
}

//广度优先遍历
void BFS(Graph G, int v) {  //从顶点v出发，广度优先遍历图G
    visit(v);               //访问初始顶点v
    visited[v] = true;      //对v做已访问标记
    Enqueue(Q, v);          //顶点v入队列Q
    while (!isEmpty(Q)) {
        DeQueue(Q, v);  //顶点v出队列
        for (w = FirstNeighbor(G, v); w >= 0; w = NextNeighbor(G, v, w)) {
            //检测v所有邻接点
            if (!visited[w]) {      // w为v的尚未访问的邻接顶点
                visit(w);           //访问顶点w
                visited[w] = true;  //对w做已访问标记
                EnQueue(Q, w);      //顶点w入队列
            }// if
        }// for
    }// while
}
```

- 同一个图的邻接矩阵表示方式唯一，因此广度优先历序列唯一
- 同一个图邻接表表示方式不唯一，因此广度优先遍历序列不唯一

辅助数组 `visited[]` 标志顶点是否被访问过，其初始状态为 `false` 。在图的遍历过程中，一旦某个顶点 $v_i$ 被访问，就立即置 `visited[i]` 为 `true` ，防止它被多次访问。

图的广度优先搜索的过程与二叉树的层序遍历是完全一致的， 这也说明了图的广度优先搜索遍历算法是二叉树的层次遍历算法的扩展。图的广度优先遍历还可用于求一些问题的最优解,

#### BFS 算法的性能分析

无论是邻接表还是邻接矩阵的存储方式，BFS 算法都需要借助一个辅助队列 `Q`，$n$ 个顶点均需入队一次，在最坏的情况下，空间复杂度为 $O(|V|)$ 。

采用邻接表存储方式时，每个顶点均需搜索一次（或入队一次）， 故时间复杂度为 $O(|V|)$ ，在搜索任一顶点的邻接点时，每条边至少访问一次，故时间复杂度为 $O(|E|)$ ， 算法总的时间复杂度为 $O(|V|+|E|)$。采用邻接矩阵存储方式时，查找每个顶点的邻接点所需的时间为 $O(|V|)$ ，故算法总的时间复杂度为 $O(|V|^2)$ 。

#### 广度优先生成树

在广度遍历的过程中，我们可以得到一棵遍历树，称为广度优先生成树。需要注意的是，一给定图的邻接矩阵存储表示是唯一的，故其广度优先生成树也是唯一的，但由于邻接表存储表示不唯一， 故其广度优先生成树也是不唯一的。

### 深度优先搜索

与广度优先搜索不同，深度优先搜索（Depth-First-Search，DFS）类似于树的先序遍历。如其名称中所暗含的意思一样，这种搜索算法所遵循的搜索策略是尽可能“深”地搜索一个图。

它的基本思想如下：首先访问图中某一起始顶点 $v$ ，然后由 $v$ 出发，访问与 $v$ 邻接且未被访问的任一顶点 $w_1$，再访问与 $w_1$ 邻接且未被访问的任一顶点 $w_2$ …… 重复上述过程。当不能再继续向下访问时，依次退回到最近被访问的顶点，若它还有邻接顶点未被访问过，则从该点开始继续上述搜索过程，直至图中所有顶点均被访问过为止。

一般情况下，其递归形式的算法十分简洁，算法过程如下：

```c++
bool visited[MaxVertexNum];  // 访问标记数组
void DFSTraverse(Graph G) {  // 对图 G 进行深度优先遍历
    for (int v = 0; v < G.vexnum; ++v) {
        visited[v] = false;  // 初始化已访问标记数据
    }
    for (int v = 0; v < G.vexnum; ++v) {
        if (!visited[v]) {
            DFS(G, v);
        }
    }
}

void DFS(Graph G, int v) {
    visit(v);           // 访问顶点 v
    visited[v] = true;  // 设已访问标记
    for (w = FirstNeighbor(G, v); w >= 0; w = NextNeighor(G, v, w)) {
        if (!visited[w]) {  // w 为 u 的尚未访问的邻接顶点
            DFS(G, w);
        }
    }
}
```

注意：图的邻接矩阵表示是唯一的，但对于邻接表来说，若边的输入次序不同，生成的邻接表也不同。因此，对于同样一个图，基于邻接矩阵的遍历所得到的 DFS 序列和 BFS 序列是唯一的，基于邻接表的遍历所得到的 DFS 序列和 BFS 序列是不唯一的。

#### DFS 算法的性能分析

DFS 算法是一个递归算法，需要借助一个递归工作栈，故其空间复杂度为 $O(|V|)$。

遍历图的过程实质上是对每个顶点查找其邻接点的过程，其耗费的时间取决于所用的存储结构。以邻接矩阵表示时，查找每个顶点的邻接点所需的时间为 $O(|V|)$ ，故总的时间复杂度为 $O(|V|^2)$。以邻接表表示时，查找所有顶点的邻接点所需的时间为 $O(E)$，访问顶点所需的时间为 $O(|V|)$，此时，总的时间复杂度为 $O(|V|+|E|)$ 。

#### 深度优先的生成树和生成森林

与广度优先搜索一样，深度优先搜索也会产生一棵深度优先生成树。当然，这是有条件的，即对连通图调用 DFS 才能产生深度优先生成树，否则产生的将是深度优先生成森林。与 BFS 类似，基于邻接表存储的深度优先生成树是不唯一的。

### 图的遍历与图的连通性

图的遍历算法可以用来判断图的连通性。

对于无向图来说，若无向图是连通的，则从任一结点出发，仅需一次遍历就能够访问图中的所有顶点；若无向图是非连通的，则从某一个 顶点出发，一次遍历只能访问到该顶点所在连通分量的所有顶点，而对于图中其他连通分量的顶点，则无法通过这次遍历访问。对于有向图来说，若从初始点到图中的每个顶点都有路径，则能够访问到图中的所有顶点，否则不能访问到所有顶点。

故在 `BFSTraverse()` 或 `DFSTraverse()` 中添加了第二个 for 循环，再选取初始点，继续进行遍历，以防止一次无法遍历图的所有顶点。对于无向图，上述两个函数调用 `BFS(G,i)` 或 `DFS(G,i)` 的次数等于该图的连通分量数；而对于有向图则不是这样，因为一个连通的有向图分为强连通的和非强连通的，它的连通子图也分为强连通分量和非强连通量，非强连通分量一次调用 `BFS(G,i)` 或 `DFS(G, i)` 无法访问到该连通分量的所有顶点。

## 图的应用

本节是历年考查的重点。图的应用主要包括：最小生成（代价）树、最短路径、拓扑排序和关键路径。一般而言，这部分内容直接以算法设计题形式考查的可能性很小，而更多的是结合图的实例来考查算法的具体操作过程，读者必须学会手工模拟给定图的各个算法的执行过程。此外，还需掌握对给定模型建立相应的图去解决问题的方法。

### 最小生成树

一个连通图的生成树包含图的所有顶点，并且只含尽可能少的边。对于生成树来说，若砍去它的一条边，则会使生成树变成非连通图；若给它增加一条边， 则会形成图中的一条回路。

对于一个带权连通无向图 $G=(V, E)$，生成树不同，每棵树的权（即树中所有边上的权值之和）也可能不同。设 $R$ 为 $G$ 的所有生成树的集合，若 $T$ 为 $R$ 中边的权值之和最小的那棵生成树，则 $T$ 称为 $G$ 的<font color="#ea66a6">最小生成树</font>（Minimum-Spanning-Tree, MST）。

不难看出，最小生成树具有如下性质：

1. 最小生成树不是唯一的，即最小生成树的树形不唯一，$R$ 中可能有多个最小生成树。当图 $G$ 中的各边权值互不相等时， $G$ 的最小生成树是唯一的；若无向连通图 $G$ 的边数比顶点数少 1，即 $G$ 本身是一棵树时，则 $G$ 的最小生成树就是它本身。
2. 最小生成树的边的权值之和总是唯一的， 虽然最小生成树不唯一，但其对应的边的权值之和总是唯一的，而且是最小的。
3. 最小生成树的边数为顶点数减 1。

构造最小生成树有多种算法，但大多数算法都利用了最小生成树的下列性质：假设 $G=(V, E)$ 是一个带权连通无向图，$U$ 是顶点集 $V$ 的一个非空子集。若 $(u, v)$ 是一条具有最小权值的边，其中 $u\in U$，$v \in V-U$，则必存在一棵包含边 $(u, v)$ 的最小生成树。

基于该性质的最小生成树算法主要有 Prim 算法和 Kruskal 算法，它们都基于贪心算法的策略。对这两种算法应主要掌握算法的本质含义和基本思想，并能够手工模拟算法的实现步骤。

#### Prim 算法

Prim（普里姆）算法的执行非常类似于寻找图的最短路径的 Djkstra 算法。

Prim 算法构造最小生成树的过程如下图所示。初始时从图中任取一顶点（如顶点 1）加入树 $T$，此时树中只含有一个顶点，之后选择一个与当前 $T$ 中顶点集合距离最近的顶点，并将该顶点和相应的边加入$T$，每次操作后 $T$ 中的顶点数和边数都增 1。以此类推，直至图中所有的顶点都并入 $T$，得到的 $T$ 就是最小生成树。此时 $T$ 中必然有 $n-1$ 条边。

![Prim算法构造最小生成树的过程](https://cdn.jsdelivr.net/gh/halo-blog/cdn-blog-img-b@master/img/Prim算法构造最小生成树的过程.png)

Prim 算法的步骤如下：

- 假设 $G= \\{V, E\\}$ 是连通图，其最小生成树 $T=(U,E_T)$，$E_T$ 是最小生成树中边的集合。
- 初始化：向空树 $T= (U, E_T)$ 中添加图 $G=(V, E)$ 的任一顶点 $u_0$，使 $U= \\{u_0\\}$ ，$E_T=\varnothing $。
- 循环（重复下列操作直至 $U=V$）：从图 $G$ 中选择满足 $\\{(u, v)|u \in U, v \in V-U\\}$ 且具有最小权值的边 $(u,v)$ 加入树 $T$，置 $U=U\cup \\{ v\\}$，$E_T= E_T \cup \\{(u,v) \\}$。

Prim 算法的时间复杂度为 $O(|V|^2)$，不依赖于 $|E|$，因此它适用于求解<font color="#faa755">边稠密</font>的图的最小生成树。虽然采用其他方法能改进 Prim 算法的时间复杂度，但增加了实现的复杂性。

```c++
// C++ program to implement Prim's Algorithm
// https://github.com/TheAlgorithms/C-Plus-Plus/blob/master/graph/prim.cpp
#include <iostream>
#include <queue>
#include <vector>

using PII = std::pair<int, int>;

int prim(int x, const std::vector<std::vector<PII> > &graph) {
    // priority queue to maintain edges with respect to weights
    std::priority_queue<PII, std::vector<PII>, std::greater<PII> > Q;
    std::vector<bool> marked(graph.size(), false);
    int minimum_cost = 0;

    Q.push(std::make_pair(0, x));
    while (!Q.empty()) {
        // Select the edge with minimum weight
        PII p = Q.top();
        Q.pop();
        x = p.second;
        // Checking for cycle
        if (marked[x] == true) {
            continue;
        }
        minimum_cost += p.first;
        marked[x] = true;
        for (const PII &neighbor : graph[x]) {
            int y = neighbor.second;
            if (marked[y] == false) {
                Q.push(neighbor);
            }
        }
    }
    return minimum_cost;
}

int main() {
    int nodes = 0, edges = 0;
    std::cin >> nodes >> edges;  // number of nodes & edges in graph
    if (nodes == 0 || edges == 0) {
        return 0;
    }

    std::vector<std::vector<PII> > graph(nodes);

    // Edges with their nodes & weight
    for (int i = 0; i < edges; ++i) {
        int x = 0, y = 0, weight = 0;
        std::cin >> x >> y >> weight;
        graph[x].push_back(std::make_pair(weight, y));
        graph[y].push_back(std::make_pair(weight, x));
    }

    // Selecting 1 as the starting node
    int minimum_cost = prim(1, graph);
    std::cout << minimum_cost << std::endl;
    return 0;

    // 6
    // 10
    // 0 1 6
    // 0 2 5
    // 0 3 1
    // 1 3 5
    // 1 4 3
    // 2 3 4
    // 4 5 6
    // 3 5 4
    // 2 5 2
    // 3 4 6
}
```

#### Kruskal 算法

与 Prim 算法从顶点开始扩展最小生成树不同，Kruskal （克鲁斯卡尔）算法是一种按权值的递增次序选择合适的边来构造最小生成树的方法。

Kruskal 算法构造最小生成树的过程如下图所示。初始时为只有 $n$ 个顶点而无边的非连通图 $T= \\{V, \\{\\}\\}$，每个顶点自成一个连通分量，然后按照边的权值由小到大的顺序，不断选取当前未被选取过且权值最小的边，若该边依附的顶点落在 $T$ 中不同的连通分量上，则将此边加入 $T$ ，否则舍弃此边而选择下一条权值最小的边。以此类推，直至 $T$ 中所有顶点都在一个连通
分量上。

![Kruskal算法构造最小生成树的过程](https://cdn.jsdelivr.net/gh/halo-blog/cdn-blog-img-b@master/img/Kruskal算法构造最小生成树的过程.png)

Kruskal 算法的步骤如下：

- 假设 $G=(V, E)$ 是连通图，其最小生成树 $T=(U, E_T)$。
- 初始化：$U=V$，$E_T=\varnothing$。即每个顶点构成一棵独立的树，$T$ 此时是一个仅含 $|V|$ 个顶点的森林。
- 循环（重复下列操作直至 $T$ 是一棵树）：按 $G$ 的边的权值递增顺序依次从 $E- E_T$ 中选择一条边，若这条边加入 $T$ 后不构成回路，则将其加入 $E_T$，否则舍弃，直到 $E_T$ 中含有 $n-1$ 条边。

根据图的相关性质，若一条边连接了两棵不同树中的顶点，则对这两棵树来说，它必定是连通的，将这条边加入森林中，完成两棵树的合并，直到整个森林合并成一棵树。

通常在 Kruskal 算法中，采用堆来存放边的集合，因此每次选择最小权值的边只需 $O(\log|E|)$ 的时间。此外，由于生成树 $T$ 中的所有边可视为一个等价类，因此每次添加新的边的过程类似于求解等价类的过程，由此可以采用并查集的数据结构来描述 $T$，从而构造 $T$ 的时间复杂度为 $O(|E|\log_{2}{|E|})$ 。因此，Kruskal 算法适合于<font color="#faa755">边稀疏而顶点较多</font>的图。

```c++
// https://github.com/TheAlgorithms/C-Plus-Plus/blob/master/graph/kruskal.cpp
#include <algorithm>
#include <array>
#include <iostream>
#include <vector>
//#include <boost/multiprecision/cpp_int.hpp>
// using namespace boost::multiprecision;
const int mx = 1e6 + 5;
using ll = int64_t;

std::array<ll, mx> parent;
ll node, edge;
std::vector<std::pair<ll, std::pair<ll, ll>>> edges;
void initial() {
    for (int i = 0; i < node + edge; ++i) {
        parent[i] = i;
    }
}

int root(int i) {
    while (parent[i] != i) {
        parent[i] = parent[parent[i]];
        i = parent[i];
    }
    return i;
}

void join(int x, int y) {
    int root_x = root(x);  // Disjoint set union by rank
    int root_y = root(y);
    parent[root_x] = root_y;
}

ll kruskal() {
    ll mincost = 0;
    for (int i = 0; i < edge; ++i) {
        ll x = edges[i].second.first;
        ll y = edges[i].second.second;
        if (root(x) != root(y)) {
            mincost += edges[i].first;
            join(x, y);
        }
    }
    return mincost;
}

int main() {
    while (true) {
        int from = 0, to = 0, cost = 0, totalcost = 0;
        std::cin >> node >> edge;  // Enter the nodes and edges
        if (node == 0 && edge == 0) {
            break;  // Enter 0 0 to break out
        }
        initial();  // Initialise the parent array
        for (int i = 0; i < edge; ++i) {
            std::cin >> from >> to >> cost;
            edges.emplace_back(make_pair(cost, std::make_pair(from, to)));
            totalcost += cost;
        }
        sort(edges.begin(), edges.end());
        std::cout << kruskal() << std::endl;
        edges.clear();
    }
    return 0;
}
```

### 最短路径

广度优先搜索查找最短路径只是对无权图而言的。当图是带权图时，把从一个顶点 $v_0$ 到图中其余任意一个顶点 $v_i$ 的一条路径（可能不止一条）所经过边上的权值之和，定义为该路径的带权路径长度，把带权路径长度最短的那条路径称为最短路径。

求解最短路径的算法通常都依赖于一种性质，即两点之间的最短路径也包含了路径上其他顶点间的最短路径。带权有向图 $G$ 的最短路径问题一般可分为两类：一是单源最短路径，即求图中某一顶点到其他各顶点的最短路径，可通过经典的 Dijkstra （迪杰斯特拉）算法求解；二是求每对顶点间的最短路径，可通过 Floyd（弗洛伊德）算法来求解。

#### BFS 算法求无权图的单源最短路径

无权图可以视为一种特殊的带权图，只是每条边的权值都为 1。

若图 $G=(V, E)$ 为非带权图，定义从顶点 $u$ 到顶点 $v$ 的最短路径 $d(u, v)$ 为从 $u$ 到 $v$ 的任何路径中最少的边数；若从 $u$ 到 $v$ 没有通路，则 $d(u,v)= \infty$ 。

使用 BFS，我们可以求解一个满足上述定义的非带权图的单源最短路径问题，这是由广度优先搜索总是按照距离由近到远来遍历图中每个顶点的性质决定的。

BFS 算法求解单源最短路径问题的伪算法如下：

```c++
#include <limits.h>

void BFS_MIN_Distance(Graph G, int u) {
    // d[i] 表示从 u 到 i 结点的最短路径
    for (int i = 0; i < G.vexnum; ++i) {
        d[i] = INT_MAX;  // 初始化路径长度
        path[i] = -1;    // 最短路径从哪个顶点过来
    }
    d[u] = 0;
    visited[u] = true;     // 标记已经访问过
    EnQueue(Q, u);         // 加入队列
    while (!isEmpty(Q)) {  // BFS 算法主过程
        DeQueue(Q, u);     // 顶点 u 出队列
        for (w = FirstNeighbor(G, u); w >= 0; w = NextNeighbor(G, u, w)) {
            //检测v所有邻接点
            if (!visited[w]) {      // w 为 u 的尚未访问的邻接顶点
                d[w] = d[u] + 1;    // 路径的长度加 1
                path[w] = u;        // 最短路径应从 u 到 w
                visited[w] = true;  // 对 w 做已访问标记
                EnQueue(Q, w);      // 顶点 w 入队列
            }
        }
    }
}
```

#### Dijkstra 算法求单源最短路径问题

Dijkstra 算法设置一个集合 $S$ 记录已求得的最短路径的顶点，初始时把源点 $v_0$ 放入 $S$ ，集合 $S$ 每并入一个新顶点 $v_i$，都要修改源点 $v_0$ 到集合 $V-S$ 中顶点当前的最短路径长度值。

在构造的过程中还设置了几个辅助数组：

- `dist[]` ：记录从源点 $v_0$ 到其他各顶点当前的最短路径长度，它的初态为：若从 $v_0$ 到 $v_i$ 有弧，则 `dist[i]` 为弧上的权值；否则置 `dist[i]` 为 $\infty$。
- `path[]` ：`path[i]` 表示从源点到顶点 $i$ 之间的最短路径的前驱结点。在算法结束时，可根据其值追溯得到源点 $v_0$ 到顶点 $v_i$ 的最短路径。
- `final[]`：标记各顶点是否已找到最短路径。

假设从顶点 0 出发，即 $v_0=0$ ，集合 $S$ 最初只包含顶点 0，邻接矩阵 `arcs` 表示带权有向图，`arcs[i][j]` 表示有向边 `<i, j>` 的权值，若不存在有向边 `<i,j>`, 则 `arcs[i][j]` 为 $\infty$。

Dijkstra 算法的步骤如下（不考虑对 `path[]` 的操作）：

1. 初始化：集合 $S$ 初始为 $\\{0\\}$，`dist[]` 的初始值 `dist[i]=arcs[0][i]`，$i=1,2,\cdots ,n-1$。
2. 从顶点集合 $V-S$ 中选出 $v_j$，满足 `dist[j]`$=\mathrm{Min}$ $\\{ $ `dist[i]` $| v_i \in V-S \\\}$，$v_j$ 就是当前求得的一条从 $v_0$ 出发的最短路径的终点，令 $S=S\cup \\{j\\}$。
3. 修改从 $v_0$ 出发到集合 $V- S$ 上任一顶点 $v_k$ 可达的最短路径长度：若 `dist[j]`$+$`arcs[j][k]`$<$`dist[k]`，则更新`dist[k]`$=$`dist[j]`$+$`arcs[j][k]`。
4. 重复 2 和 3 操作共 $n-1$ 次，直到所有的顶点都包含在 $S$ 中。

![Dijkatra算法](https://cdn.jsdelivr.net/gh/halo-blog/cdn-blog-img-b@master/img/Dijkatra算法.png)

算法执行过程的说明如下：

- 初始化：集合 $S$ 初始为 $\\{v_1\\}$，$v_1$可达以和 $v_2$，$v_5$ 不可达 $v_3$ 和 $v_4$，因此 `dist[]` 数组各元素的初值依次设置为`dist[2]=10`，`dist[3]=MAX_INF`，`dist[4]=MAX_INF`，`dist[5]=5`。
- 第一轮：选出最小值 `dist[5]`，将顶点 $v_5$ 并入集合 $S$ ，即此时已找到 $v_1$ 到 $v_5$ 的最短路径。当 $v_5$ 加入 $S$ 后，从 $v_1$ 到集合 $V-S$ 中可达顶点的最短路径长度可能会产生变化。因此需要更新 `dist[]` 数组。 $v_5$ 可达 $v_2$ ，因 $v_1$→ $v_5$→$v_2$ 的距离 8 比 `dist[2]=10` 小，更新 `dist[2]=8`； $v_5$ 可达 $v_3$， $v_1$→ $v_5$ → $v_3$ 的距离 14，更新 `dist[3]=14`； $v_5$ 可达$v_4$， $v_1$→$v_5$→$v_4$ 的距离 7，更新 `dist[4]=7`。
- 第二轮：选出最小值 `dist[4]`，将顶点 $v_4$ 并入集合 $S$。继续更新 `dist[]` 数组。$v_4$ 不可达$v_2$，`dist[2]` 不变；$v_4$ 可达$v_3$，$v_1$→$v_5$→$v_4$→$v_3$ 的距离 13 比 `dist[3]` 小，故更新 `dist[3]=13`。
- 第三轮：选出最小值 `dist[2]`，将顶点 $v_2$ 并入集合 $S$。继续更新 `dist[]` 数组。$v_2$ 可达 $v_3$，$v_1$→$v_5$→$v_2$→$v_3$ 的距离 9 比 `dist[3]` 小，更新 `dist[3]=9`。
- 第四轮：选出唯一最小值 `dist[3]`，将顶点 $v_3$ 并入集合 $S$，此时全部顶点都已包含在 $S$ 中。

显然，Dijkstra 算法也是基于贪心策略的。

使用邻接矩阵表示时，时间复杂度为 $O(|V|^2)$。使用带权的邻接表表示时，虽然修改 `dist[]` 的时间可以减少，但由于在`dist[]` 中选择最小分量的时间不变，时间复杂度仍为 $O(|V|^2)$。

人们可能只希望找到从源点到某个特定顶点的最短路径，但这个问题和求解源点到其他所有顶点的最短路径一样复杂，时间复杂度也为 $O(|V|^2)$。

值得注意的是，边上带有负权值时，Dijkstra 算法并不适用。若允许边上带有负权值，则在与 $S$ （已求得最短路径的顶点集，归入 $S$ 内的结点的最短路径不再变更）内某点（记为 a）以负边相连的点（记为 b）确定其最短路径时，其最短路径长度加上这条负边的权值结果可能小于 a 原先确定的最短路径长度，而此时 a 在 Dijkstra 算法下是无法更新的。

#### Floyd 算法求各顶点之间最短路径问题

求所有顶点之间的最短路径问题描述如下：已知一个各边权值均大于 0 的带权有向图，对任意两个顶点 $v_i\ne v_j$，要求求出 $v_i$ 与 $v_j$ 之间的最短路径和最短路径长度。

Floyd 算法的基本思想是：递推产生一个 $n$ 阶方阵序列 $ A^{(-1)}\\ ,A^{(0)},\\cdots ,A^{(k)},\\cdots A^{(n-1)}$，其中 $A^{(k)}[i][j]$ 表示从顶点 $v_i$ 到顶点 $v_j$ 的路径长度，$k$ 表示绕行第 $k$ 个顶点的运算步骤。

初始时，对于任意两个顶点 $v_i$ 和 $v_j$ ，若它们之间存在边，则以此边上的权值作为它们之间的最短路径长度；若它们之间不存在有向边，则以 $ \infty$ 作为它们之间的最短路径长度。以后逐步尝试在原路径中加入顶点 $k \ (k=0, 1,\cdots ,n-1)$ 作为中间顶点。若增加中间顶点后，得到的路径比原来的路径长度减少了，则以此新路径代替原路径。

```c
#include <limits.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Structure for storing a graph
struct Graph
{
    int vertexNum;
    int **edges;
};

// Constructs a graph with V vertices and E edges
void createGraph(struct Graph *G, int V)
{
    G->vertexNum = V;
    G->edges = (int **)malloc(V * sizeof(int *));
    for (int i = 0; i < V; i++)
    {
        G->edges[i] = (int *)malloc(V * sizeof(int));
        for (int j = 0; j < V; j++) G->edges[i][j] = INT_MAX;
        G->edges[i][i] = 0;
    }
}

// Adds the given edge to the graph
void addEdge(struct Graph *G, int src, int dst, int weight)
{
    G->edges[src][dst] = weight;
}

// Utility function to print distances
void print(int dist[], int V)
{
    printf("\nThe Distance matrix for Floyd - Warshall\n");
    for (int i = 0; i < V; i++)
    {
        for (int j = 0; j < V; j++)
        {
            if (dist[i * V + j] != INT_MAX)
                printf("%d\t", dist[i * V + j]);
            else
                printf("INF\t");
        }
        printf("\n");
    }
}

// The main function that finds the shortest path from a vertex
// to all other vertices using Floyd-Warshall Algorithm.
void FloydWarshall(struct Graph *graph)
{
    int V = graph->vertexNum;
    int dist[V][V];

    // Initialise distance array
    for (int i = 0; i < V; i++)
        for (int j = 0; j < V; j++) dist[i][j] = graph->edges[i][j];

    // Calculate distances
    for (int k = 0; k < V; k++)
        // Choose an intermediate vertex

        for (int i = 0; i < V; i++)
            // Choose a source vertex for given intermediate

            for (int j = 0; j < V; j++)
                // Choose a destination vertex for above source vertex

                if (dist[i][k] != INT_MAX && dist[k][j] != INT_MAX &&
                    dist[i][k] + dist[k][j] < dist[i][j])
                    // If the distance through intermediate vertex is less than
                    // direct edge then update value in distance array
                    dist[i][j] = dist[i][k] + dist[k][j];

    // Convert 2d array to 1d array for print
    int dist1d[V * V];
    for (int i = 0; i < V; i++)
        for (int j = 0; j < V; j++) dist1d[i * V + j] = dist[i][j];

    print(dist1d, V);
}

// Driver Function
int main()
{
    int V, E;
    int src, dst, weight;
    struct Graph G;
    printf("Enter number of vertices: ");
    scanf("%d", &V);
    printf("Enter number of edges: ");
    scanf("%d", &E);
    createGraph(&G, V);
    for (int i = 0; i < E; i++)
    {
        printf("\nEdge %d \nEnter source: ", i + 1);
        scanf("%d", &src);
        printf("Enter destination: ");
        scanf("%d", &dst);
        printf("Enter weight: ");
        scanf("%d", &weight);
        addEdge(&G, src, dst, weight);
    }
    FloydWarshall(&G);

    return 0;
}
```

Floyd 算法的时间复杂度为 $O(|V|^3)$ 。不过由于其代码很紧凑，且并不包含其他复杂的数据结构，因此隐含的常数系数是很小的，即使对于中等规模的输入来说，它仍然是相当有效的。空间复杂度：$O(|V|^2)$

Floyd 算法允许图中有带负权值的边，但不允许有包含带负权值的边组成的回路。Floyd 算法同样适用于带权无向图，因为带权无向图可视为权值相同往返二重边的有向图。

也可以用单源最短路径算法来解决每对顶点之间的最短路径问题。轮流将每个顶点作为源点，并且在所有边权值均非负时，运行一次 Dijkstra 算法，其时间复杂度为 $O(|V|^3) $ 。

### 有向无环图描述表达式

有向无环图：若一个有向图中不存在环，则称为有向无环图，简称 DAG 图。

有向无环图是描述含有公共子式的表达式的有效工具。例如表达式：$$((a+b)\ast (b\ast (c+d)>+(c +d)\ast e)\ast ((c+d)\ast e)$$可以用二叉树来表示。仔细观察该表达式，可发现有一些相同的子表达式 $(c + d)$ 和 $(c + d)\ast e$ ，而在二叉树中，它们也重复出现。若利用有向无环图，则可实现对相同子式的共享，从而节省存储空间。

![表达式描述](https://cdn.jsdelivr.net/gh/halo-blog/cdn-blog-img-b@master/img/表达式描述.png)

### 拓扑排序

AOV 网：若用 DAG 图表示一个工程，其顶点表示活动，用有向边 $\langle V_i,V_j\rangle $ 表示活动 $V_i$；必须先于活动 $V_j$；进行的这样一种关系，则将这种有向图称为顶点表示活动的网络，记为 AOV 网。在 AOV 网中，活动 $V_i$ 是活动 $V_j$ 的直接前驱，活动 $V_j$ 是活动 $V_i$ 的直接后继，这种前驱和后继关系具有传递性，且任何活动 $V_i$ 不能以它自己作为自己的前驱或后继。

拓扑排序：在图论中，由一个有向无环图的顶点组成的序列，当且仅当满足下列条件时，称为该图的一个拓扑排序：

- 每个顶点出现且只出现一次。
- 若顶点 A 在序列中排在顶点 B 的前面，则在图中不存在从顶点 B 到顶点 A 的路径。

或定义为：拓扑排序是对有向无环图的顶点的一种排序， 它使得若存在一条从顶点 A 到顶点 B 的路径，则在排序中顶点 B 出现在顶点 A 的后面。每个 AOV 网都有一个或多个拓扑排序序列。

对一个 AOV 网进行拓扑排序的算法有很多，下面介绍比较常用的一种方法的步骤：

1. AOV 网中选择一个没有前驱的顶点并输出。
2. 从网中删除该顶点和所有以它为起点的有向边。
3. 重复步骤 1 和 2 直到当前的 AOV 网为空或当前网中不存在无前驱的顶点为止。后一种情况说明有向图中必然存在环。

```c
bool TopologicalSort(Graph G) {
    InitStack(S);  //初始化栈，存储入度为0的顶点
    for (int i = 0; i < G.vexnum; i++) {
        if (indegree[i] == 0) {
            Push(S, i);  //将所有入度为0的顶点进栈
        }
    }
    int count = 0;           //计数，记录当前已经输出的顶点数
    while (!IsEmpty(S)) {    //栈不空，则存在入度为0的顶点
        Pop(S, i);           //栈顶元素出栈
        print[count++] = i;  //输出顶点i
        for (p = G.vertices[i].firstarc; pip = p->nextarc) {
            //将所有i指向的顶点的入度减1,并且将入度减为0的顶点压入栈s
            v = p->adjvex;
            if (!(--indegree[v])) {
                Push(S, v);  //入度为0， 则入栈
            }
        }
    }
    if (count < G.vexnum) {
        return false;  //排序失败，有向图中有回路
    } else {
        return true;  //拓扑排序成功
    }
}
```

由于输出每个顶点的同时还要删除以它为起点的边，故拓扑排序的时间复杂度为 $O(|V|+|E|)$。此外，利用深度优先遍历也可实现拓扑排序。

TODO 深度优先遍历代码实现拓扑排序

对一个 AOV 网，如果采用下列步骤进行排序，则称之为逆拓扑排序：

1. 从 AOV 网中选择一个没有后继（出度为 0 ）的顶点并输出。
2. 从网中删除该顶点和所有以它为终点的有向边。
3. 重复步骤 1 和 2 直到当前的 AOV 网为空。

用拓扑排序算法处理 AOV 网时，应注意以下问题：

1. 入度为零的顶点，即没有前驱活动的或前驱活动都已经完成的顶点，工程可以从这个顶点所代表的活动开始或继续。
2. 若一个顶点有多个直接后继，则拓扑排序的结果通常不唯一；但若各个顶点已经排在一个线性有序的序列中，每个顶点有唯一的前驱后继关系，则拓扑排序的结果是唯一的。
3. 由于 AOV 网中各顶点的地位平等，每个顶点编号是人为的，因此可以按拓扑排序的结果重新编号，生成 AOV 网的新的邻接存储矩阵，这种邻接矩阵可以是三角矩阵；但对于一般的图来说，若其邻接矩阵是三角矩阵，则存在拓扑序列；反之则不一定成立。

TODO 逆拓扑排序 DFS 算法实现及其对环路的判断

### 关键路径

在带权有向图中，以顶点表示事件，以有向边表示活动，以边上的权值表示完成该活动的开销（如完成活动所需的时间），称之为用边表示活动的网络，简称 AOE 网。AOE 网和 AOV 网都是有向无环图，不同之处在于它们的边和顶点所代表的含义是不同的，AOE 网中的边有权值；而 AOV 网中的边无权值，仅表示顶点之间的前后关系。AOE 网具有以下两个性质：

1. 只有在某顶点所代表的事件发生后，从该顶点出发的各有向边所代表的活动才能开始；
2. 只有在进入某顶点的各有向边所代表的活动都已结束时，该顶点所代表的事件才能发生。

在 AOE 网中仅有一个入度为 0 的顶点，称为开始顶点（源点），它表示整个工程的开始；网中也仅存在一个出度为 0 的顶点，称为结束顶点（汇点），它表示整个工程的结束。

在 AOE 网中，有些活动是可以并行进行的。从源点到汇点的有向路径可能有多条，并且这些路径长度可能不同。完成不同路径上的活动所需的时间虽然不同，但是只有所有路径上的活动都已完成，整个工程才能算结束。因此，从源点到汇点的所有路径中，具有最大路径长度的路径称为<font color="#ea66a6">关键路径</font>，而把关键路径上的活动称为关键活动。

完成整个工程的最短时间就是关键路径的长度，即关键路径上各活动花费开销的总和。这是因为关键活动影响了整个工程的时间，即若关键活动不能按时完成，则整个工程的完成时间就会延长。因此，只要找到了关键活动，就找到了关键路径，也就可以得出最短完成时间。下面给出在寻找关键活动时所用到的几个参量的定义。

#### 事件 $v_k$ 的最早发生时间 $ve(k)$

它是指从源点 $v_1$ 到顶点 $v_k$ 的最长路径长度。事件 $v_k$ 的最早发生时间决定了所有从 $v_k$ 开始的活动能够开工的最早时间。

#### 活动 $a_i$ 的最早开始时间 $e(i)$

它是指该活动弧的起点所表示的事件的最早发生时间。若边 $\langle v_k,v_j\rangle $  表示活动 $a_i$ ，则有 $e(i)=ve(k)$)。

#### 事件 $v_k$ 的最迟发生时间 $vl(k)$

它是指在不推迟整个工程完成的前提下，即保证它的后继事件 $v_j$ 在其最迟发生时间 $vl(j)$ 能够发生时，该事件最迟必须发生的时间。

#### 活动 $a_i$ 的最迟开始时间 $l(i)$

它是指该活动弧的终点所表示的事件的最迟发生时间与该活动所需时间之差。若边 $\langle v_k,v_j\rangle $  表示活动 $a_i$ ，则有 $l(i)=vl(j)-\mathrm{Weight} (v_k,v_j)$)。

#### 活动 $a_i$ 的时间余量

一个活动 $a_i$ 的最迟开始时间 $l(i)$和其最早开始时间 $e(i)$的差额 $d(i)= l(i)- e(i)$，它是指该活动完成的时间余量，即在不增加完成整个工程所需总时间的情况下，活动 $a_i$ 可以拖延的时间。若一个活动的时间余量为零，则说明该活动必须要如期完成，否则就会拖延整个工程的进度，所以称 $l(i)- e(i)= 0$ 即 $l(i)= e(i)$ 的活动 $a_i$ 是关键活动。

#### 求关键路径的步骤

求关键路径的算法步骤如下：

1. 求所有事件的最早发生时间 $ve()$，从源点出发，令 $ve(源点)=0$，按拓扑有序求其余顶点的最早发生时间 $ve()$
2. 求所有事件的最迟发生时间 $vl( )$，从汇点出发，令 $vl(汇点)= ve(汇点)$， 按逆拓扑有序求其余顶点的最迟发生时间 $vl()$
3. 求所有活动的最早发生时间 $e()$，根据各顶点的 $ve()$ 值求所有弧的最早开始时间 $e()$
4. 求所有活动的最迟发生时间 $l( )$，根据各顶点的 $vi()$ 值求所有孤的最迟开始时间的 $l()$
5. 求所有活动的时间余量 $d( )$，求 AOE 网中所有活动的差额 $d()$，找出所有 $d()=0$ 的活动构成关键路径。

![求解关键路径的过程](https://cdn.jsdelivr.net/gh/halo-blog/cdn-blog-img-b@master/img/求解关键路径的过程.png)

上图所示为求解关键路径的过程，简单说明如下：

1. 求 $ve()$ ：初始 $ve(1)=0$，在拓扑排序输出顶点过程中，求得 $ve(2)=3$，$ve(3)=2$，$ve(4)=max\\{ve(2)+2,ve(3)+4\\}=max\\{5,6\\}=6$，$ve(5)=6$，$ve(6)=max\\{ve(5)+1,ve(4)+2,ve(3)+3\\}=max\\{7,8,5\\}=8$。
2. 求 $vl()$：初始 $vl(6)=8$，在逆拓扑排序出栈过程中，求得 $vl(5)=7$，$vl(4)=6$，$vl(3)=min\\{vl(4)-4,vl(6)-3\\}=min\\{2,5\\}=2$，$vl(2)=min\\{vl(5)-3,vl(4)-2\\}=min\\{4,4\\}=4$，$vl(1)=0$
3. 弧的最早开始时间 $e()$ 等于该弧的起点的顶点 $ve()$，求得结果如上表所示
4. 弧的最迟开始时间 $l(i)$ 等于该弧的终点的顶点 $vl()$ 减去该弧持续的时间，求得结果如上表所示
5. 根据 $l(i)-e(i)=0$ 的关键活动，得到的关键路径为 $(v_1,v_3,v_4,v_6)$

对于关键路径，需要注意以下几点：

1. 关键路径上的所有活动都是关键活动，它是决定整个工程的关键因素，因此可通过加快关键活动来缩短整个工程的工期。
2. 但也不能任意缩短关键活动，因为一旦缩短到一定的程度，该关键活动就可能会变成非关键活动。
3. 网中的关键路径并不唯一，且对于有几条关键路径的网，只提高一条关键路径上的关键活动速度并不能缩短整个工程的工期，只有加快那些包括在所有关键路径上的关键活动才能达到缩短工期的目的。
