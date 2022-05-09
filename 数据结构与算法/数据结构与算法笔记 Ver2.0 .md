

[前往末尾](#EOF)

# 序言

- 从Ver 2.0 开始，每个笔记在内容上是对之前所有笔记的增补，但不排除某一概念需要重新学习
- 代码还是写在[这里](https://github.com/el-nino2020/DS-A)
- 这份笔记基于MIT的算法导论。这门课将内容分为三部分：:one:数据结构、:two:图和:three:动态规划。笔记的记录与课时对应



# 目录

[toc]



# 版本一览

- 这是Ver 2.0，基于[MIT公开课：6.006算法导论_2020年春季](https://www.bilibili.com/video/BV1sf4y1P7t9)；在MIT的网站上有该课程的所有资料，网站为[这个](https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-spring-2020/)。开始学习的时间为2022年4月23日，结束于2022年5月9日
- Ver 1.0 的笔记在[这里](https://github.com/el-nino2020/note-of-learning/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E7%AC%94%E8%AE%B0%20Ver1.0%20.md)，基于[【尚硅谷】数据结构与算法（Java数据结构与算法）](https://www.bilibili.com/video/BV1E4411H73v)



# Lecture 1: introduction

## Word - RAM model

- word即数据的基本单位，包含`w` bits。对于32位的机器来说，word为32位；对于64位的机器来说，word为64位
- RAM，random access memory，随机访问内存。随机访问指内存可以像C语言中的数组一样，**给定地址就能访问其中的数据**，花费的时间为`O(1)`
- 这个模型用来定义哪些操作花费的时间为`O(1)`，为之后计算时间复杂度奠定基础：
- 如下的操作是`O(1)`的：
	- 整数运算：加减乘除
	- 逻辑（比较）运算符
	- 位运算符
	- 向内存读写一个word大小的数据



# Lecture 2: Data Structures

## Interfaces VS data structures

- 数据结构是一种存放数据的形式，支持一定的操作（方法）。不同的数据结构有不同的方法
- 接口（API/ADT）**描述了**一种数据结构支持哪些方法，而不去关注细节的实现
- 数据结构表示这些方法是**如何实现的**



# Lecture 4: hashing

## 引入

1. 需求：
	- 一个集合接口（set interface）应支持CRUD操作
	- 假设我们往这个集合中添加`n`个整数，整数的范围为`[0, u - 1]`（`u`是一个很大的正整数）。添加完后，如何使之后的crud操作的时间复杂度尽可能小

2. 方法：
	- 可以利用Word - RAM模型，建立一个长度为`u`的数组，存放这`n`个整数
	- 但如果$u \gg m$，会造成空间浪费



## 哈希

1. 概念
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204271057649.png" alt="image-20220427105734443" style="zoom:50%;" />



2. hash函数的选择
	1. Division
		- 公式为$h(k) = k \, mod\, m$
		- 添加的值需要**均匀分布**，不然哈希表的某些索引处的元素会过多
	2. Universal
		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204271105249.png" alt="image-20220427110557120" style="zoom:50%;" />
		- 在创建哈希表时，先选定一个大于`u`的素数`p`，然后在$\set{0,...,p-1}$中**随机**选出`a`和`b`，这样，我们每次都会得到一个不同的哈希函数
		- 如此确定哈希函数的好处在于：不管输入为何种分布，哈希表每个索引处的元素数量的**期望都为`O(1)`**，因此可以保证crud的效率。证明如下：
			- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204271111476.png" alt="image-20220427111147334" style="zoom:50%;" />
		- 由于哈希函数的选定是随机的，用户也无法得知到底使用了哪个哈希函数



# Lecture 5: Linear Sorting

## Direct Access Array Sort

1. 原理

	- 假设数组有`n`个元素，元素之间互不相同，这些元素的范围为$\set{0,1,...,u-1}$且$ u = O(n)$

	- 我们只需要声明一个长度为`u`的新数组，遍历原有数组，把元素放在与其值相同的索引处

	- 再遍历新数组，将所有非空元素依次放入原数组即可

	- 这样，这个排序的时间复杂度为`**O(1)**`



2. 例子：
	- 原数组为：
	
	- | 索引 | 0    | 1    | 2    | 3    |
	  | ---- | ---- | ---- | ---- | ---- |
	  | 值   | 6    | 2    | 4    | 0    |
	
	- `n`为`4`，`u`为`7`
	
	- 将这些元素放入新数组中

	- | 索引 | 0    | 1    | 2    | 3    | 4    | 5    | 6    |
	| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
	| 值   | 0    | -1   | 2    | -1   | 4    | -1   | 6    |
	
	- 依次取出非空的值，存入原数组



## 基数排序 r

1. - 如果$u = O(n^c)$，
	- 我们可以将每个元素拆分为`c`部分，即$key = \set{k_c, k_{c-1} ,...,k_1}$，其中$k_i = key / c^ {i - 1} \,mod\, c$，即以`c`为基数表示每一个`key`
	- 对每一个元素的第$i$位进行排序的时间为`O(n)`，由于`c`为常数，**对整个数组排序的时间也为`O(n)`——一个线性时间复杂度的排序算法**！！！
	- 排序的具体做法为：
		- `i`从小到大遍历，每一次对所有元素的第`i`位进行稳定排序（stable sort），即低位先排序，再对高位排序
	- 一个例子：
		- 原数组：`[32, 03, 44, 42, 22]`
		- 在这里，`n`为`5`，即基数为`5`
		- 对低位排序：`[32, 42, 22, 03, 44]`
		- 对高位排序：`[03, 22, 32, 42, 44]`，排序完毕



# lecture 7 AVL tree



## 使用AVL树实现`List`接口

1. AVL树的性质
	- 通常，使用`AVL`树实现`Map`接口，继而实现`Set`接口。这时，AVL具有BST的性质，使得给定一个键，能在`O(log(n))`的时间内对该键值对进行crud
	- 而实现`List`接口时，AVL不需要具有BST的性质，只需要有自平衡的性质。`List`表示一个有序序列，索引处存放的值的大小是无关的。我们对该序列的crud操作的时间复杂度都为`O(log(n))`——与之相对，`ArrayList`等底层为数组的实现方式在索引时花费`O(1)`，但在插入和删除时花费`O(n)`
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205020841061.png" alt="image-20220502084140974" style="zoom:50%;" />
	- `List`接口的**索引**与节点在AVL**中序遍历的顺序**一致



1. `get(int index)`、`set(int index, E e)`
	- 每个节点保存其左右子树中节点的数量
	- 调用这两个方法时，每一次递归，我们将左右子树的数量与`index`进行比较，直到找到`index`对应的节点。
	- 花费的时间为`O(log(n))`
	- 实现方法如下：
		- 假设当前节点为`node`，其左子树中节点的数量为`leftSize`
		- 如果`leftSize == index`，则返回当前节点的值
		- 如果`index < leftSize`，递归遍历`node.left`
		- 如果`index > leftSize`，递归遍历`node.right`，此时查找的索引为`index - leftSize -1`



2. `insert(int index, E e)`
	- 只在空的叶节点位置才插入新的节点，即`node == null`时才插入，因为这样做最方便；如果当前节点非空，则执行以下操作：
	- 如果`index < leftSize`，递归遍历`node.left`
	- 如果`index > leftSize`，递归遍历`node.right`，此时查找的索引为`index - leftSize -1`
	- 参考了这个代码：https://www.nayuki.io/res/avl-tree-list/AvlTreeList.java



3. `remove(int index)`
	- 与实现`Map`接口的AVL的`remove`方法基本相同



4. `max(int from)`
	- 效果为$max\set{e_{from},e_{from+1},...,e_{size -1}}$，由于这是个泛型容器，需要传入`Comparator`对象来确定比较规则
	- 每个节点需要保存这个信息：以该节点为根节点的树中所有元素的最大值，即为`node.max`
	- 按照`get`方法递归。直观来说，从根节点到索引为`from`的节点形成一条路径，从路径中各个节点右子树的最大值（该信息保存在各个右子节点中）中和各个节点的最大值中找出最大值，并返回。假设路径为$\set{u_0,u_1,...,u_k}$，则$max(from) = max\set{u_0.val,u_1.val,...,u_k.val,u_0.right.max,u_1.right.max,...,u_k.right.max}$；当然，代码是以递归的方式实现的
	- 虽然这个方法不是实现`List`接口必须重写的方法，但它体现了List AVL真正的用处：**在`O(log(n))`时间内返回无序列表某一区间的最大值**（最大值也可以替换为其他信息）



5. 代码：https://github.com/el-nino2020/DS-A/blob/main/data_structures/tree/AVLTreeList.java



# Lecture 8 heap sort



## binary heap

1. 插入元素——节点“上浮”
	- 将新的元素放在大顶堆的最后，如果其值比起父节点值大，则与父节点交换，不断上浮直至条件不再满足
	- 花费的时间为`O(log(n))`，`n`为堆中元素数量



2. 删除堆顶元素
	- 删除大顶堆堆顶的元素，将最后一个元素放在堆顶的位置，如果子节点的值比它大，则与值更大的子节点交换——节点“下沉”
	- 不断下沉直至条件不再满足
	- 花费的时间为`O(log(n))`，`n`为堆中元素数量



3. 数组堆化——`O(n)`时间
	- 对每一个节点执行下沉操作。由于没有子节点的节点没必要下沉，应该从最后一个非叶节点，即`arr[n / 2 - 1]`开始下沉，再依次对之前的节点执行下沉操作
	- 由于每一层节点下沉的层数不同，如倒数第二层下沉`1`次，倒数第三层下沉`2`次，最终的时间复杂度为`o(n)`，优于`o(nlog(n))`

4. 节点与数组索引的关系
	- 假如某一节点的索引为`i`，则其父节点的索引为`(i - 1) / 2`，其子节点的索引为`i * 2 + 1`和`i * 2 + 2`——写代码时没有注意，吃了苦头:anger:



5. 代码：https://github.com/el-nino2020/DS-A/blob/main/data_structures/heap/BinaryHeap.java



# Lecture 10 : DFS

## topological sort 拓扑排序

1. topological order
	- 一个图是有向无环图（directed acyclic graph, DAG）的**充要条件**是该图存在拓扑排序
	- 假设图中节点排序为$v_0,v_1,v_2,...,v_k$，如果对于任意一条有向边$(v_i,v_j)\in E$，都有$i<j$，即$v_i$总是出现在$v_j$前面，那么这样的排序称为拓扑排序
	- 一个例子：
		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205021917887.png" alt="image-20220502191741722" style="zoom: 33%;" />
		- 该图的拓扑排序为`1 2 3 4 5`或`1 2 3 5 4`，故拓扑排序不唯一



2. 原理：
	- 统计每个节点的入度（in-degree）
	- 从入度为0的节点开始访问
	- 每次访问当前节点的邻居节点时，将后者的入度减`1`，如果入度减至`0`，则访问该邻居节点
	- 时间复杂度为$O(|V|+|E|)$：统计入度花费`O(|E|)`，访问各个节点花费`O(|V|)`，访问各个节点的邻居花费`O(|E|)`
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205021949753.png" alt="image-20220502194910601" style="zoom:50%;" />
	- 参考https://www.sciencedirect.com/topics/computer-science/topological-sort



3. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/graph/TopologicalSort.java



# Lecture 11: Weighted Shortest Paths

## 单源最短路径问题 single source shortest path, SSSP

1. 各种算法
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205021725057.png" alt="image-20220502172533965" style="zoom:50%;" />
	- for a general graph, it can be weighted, negatively weighted, directed and cyclic
	- 不同的算法对于求SSSP使用的图有限制

2. BFS
	- BFS求解SSSP只适用于**没有权重**的图，或者说所有边的**权重都为1**
	- 最短距离即为距离起点的层数（BFS是逐层扩散遍历的）



## DAG Relaxation 

- :one:原理：
	- 假设从节点`s`出发，对于任意其他节点$v \in V$，设真实的最短距离为$\delta(s,v)$，我们使用估计值$d(s,v)$来估计$\delta(s,v)$，使$d(s,v)\ge \delta(s,v)$恒成立。宽泛地说，$d(s,v)$初始值为$\infty$，然后逐渐减小至$\delta(s,v)$
	- 根据三角不等式，对于任意节点$u,v,x \in V$，$\delta(u,v) \le \delta(u,x) + \delta(x,v)$
	- 假设存在$(u,v) \in E$，使得$d(s,v) > d(s,u) + w(u,v)$，此时三角不等式不再成立，我们需要更新$d(s,v)$的值，使得$d(s,v) = d(s,u) + w(u,v)$
	- 最终，对于任意节点$v \in V$，$d(s,v) = \delta(s,v)$，即求得了最小路径
- :two:实现
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205022039902.png" alt="image-20220502184845356" style="zoom: 50%;" />
- :three:例子：
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205022039739.png" alt="Shortest_path_with_direct_weights.svg" style="zoom: 33%;" />
	- 图片来自https://en.wikipedia.org/wiki/Shortest_path_problem#/media/File:Shortest_path_with_direct_weights.svg
- :four:代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/graph/shortest_path/DAGRelaxation.java

# Lecture 12 Bellman-Ford

1. 原理

	- 该算法适用于general graph: negatively weighted edge, cycle (whose weight may be negative)

	- ```pseudocode
		function BellmanFord(list vertices, list edges, vertex source) is
		
		    distance := list of size n
		    predecessor := list of size n
		
		    // Step 1: initialize graph
		    for each vertex v in vertices do
		        distance[v] := inf             // Initialize the distance to all vertices to infinity
		        predecessor[v] := null         // And having a null predecessor
		    
		    distance[source] := 0              // The distance from the source to itself is, of course, zero
		
		    // Step 2: relax edges repeatedly
		    
		    repeat |V|−1 times:
		         for each edge (u, v) with weight w in edges do
		             if distance[u] + w < distance[v] then
		                 distance[v] := distance[u] + w
		                 predecessor[v] := u
		
		    // Step 3: check for negative-weight cycles
		    for each edge (u, v) with weight w in edges do
		        if distance[u] + w < distance[v] then
		            error "Graph contains a negative-weight cycle"
		
		    return distance, predecessor
		```



2. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/graph/shortest_path/BellmanFord.java



# Lecture 14 Johnson's algorithm

## All-Pairs Shortest Paths (APSP)

1. 概念
	- 给定一张图，返回图中所有两点之间的最短距离



2. 引入
	- 对每个点求SSSP，[不同的算法有不同的时间复杂度](#单源最短路径问题 single source shortest path, SSSP)：
		- 对于general graph, Bellman-Ford的时间为`O(|V||E|)`
		- 对于边权重非负的general graph, dijkstra的时间为`O(|V|log|V| + |E|)`（使用fibonacci heap优化）
	- 如果要对每个点求SSSP，使用dijkstra的效率更高，总的时间复杂度为`|V| * O(|V|log|V| + |E|)`



## Johnson's algorithm

1. 原理
	1. 假设存在ASAP，那么图中不存在权重为负的环路。我们要在**保持各点最短路径**的情况下，将所有边的权重更新为非负值，从而对每个点用Dijkstra求SSSP
	2. 如何将所有边的权重更新为非负值:question:
		- 一个错误的做法是将每条边的权重加上一个固定大小，使所有边的权重非负。:unamused:反例：从`s`到`t`有两条路径，一条为$s \overset {-2} {----} a \overset {-1} {----} b \overset {2} {----} t$， 另一条为$s\overset 1  {----}t$，前者的路径更短。如果我们给每条边的权重加2，前者的路径和为`5`，后者的路径和为`3`，没有保持各点的最短路径
		- 正确的做法是$\forall \,\, v \in V$，将所有指向`v`的边的权重减去一个定值`h`，将所有从`v`出发的边的权重加上同一个`h`
		- 对于经过`v`的任意一条路径，如果`v`在路径的两个端点上，路径长度都变化了`h`；如果`v`不再路径的端点上，路径长度不发生变化。两种情况都保证了最短路径没发生变化
		- 我们假设端点为$v$的边的权重变化$h(v)$，那么$\forall \,\,u,v\in V, w'(u,v) = w(u,v) +h(u)-h(v)$。易证，修改所有边的权重后，原有各点的最短路径没有变化
		- 我们要使$\forall \,\,u,v\in V, w'(u,v) \ge 0$，对不等式做一些变形，得$h(v) \le w(u,v) + h(u)$。这个式子像极了三角不等式
		- 于是，我们**新建一个节点`s`，将`s`与原图`G`中所有点相连接**（每条边都从`s`出发，且权重为`0`），得到新图G~s~。令$h(v) = \delta(s,v)$，则在新图中，$\forall \,\,u,v\in V, \delta(s,v) \le w(u,v) + \delta(s,u)$恒成立
		- 因此，我们可以将G~s~中的所有边的权重更新为非负值
		- 这样就可以对各点使用Dijkstra求SSSP了
	3. 实现
	
		  - 已知`G`，创建新的节点`s`，从`s`出发，与$\forall v \in V$相连，且边的权重为`0`，得到一张新图G~s~ 
		  - 使用Bellman-Ford求出从`s`出发的SSSP，得到$\delta(s,v)\text{   }\forall v\in V$。同时，Bellman-Ford可以检测G中是否存在权重的负的环路
		  - 使用$w'(u,v) = w(u,v) + \delta(s,u) - \delta(s,v)$更新G
		  - 对G中每一个节点使用Dijkstra求SSSP
	4. 总时间复杂度为`|V| * O(|V|log|V| + |E|)`，且该算法适用于general graph
	5. :bulb:创建一个新节点的方法在图的算法中很常见
	



2.代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/graph/shortest_path/Johnson.java



## Floyd-Warshall 

- 另一种求APSP的方法，时间复杂度为$O(|v|^3)$，不如Johnson's algorithm
- 在笔记Ver 1.0中已经实现，这里不赘述了

​	

# Quiz 2 (graph part) review

1. 一道题目
	- ![image-20220505184740004](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205051847122.png)
	- 建模：
		- 一张图有`n`个节点，有`O(n)`条边
		- 在`n`个节点中，有`d`个特殊节点(doughnut shop)，距离这些特殊节点的路径长度需要大于`k`
		- 求出一条从`p`到`h`的最短路径，满足上述条件



2. 解法：**super node**的思想
	- 向图中插入新节点`s`，将`d`个特殊节点与该节点相连，边的权重都为`0`
	- 由于所有边的权重非负，对`s`使用Dijkstra，时间为`O(nlogn)`
	- 删除节点中所有距离`s`小于`k`的节点
	- 对`p`使用Dijkstra，求出到`h`的最短路径



# Lecture 15 - 18 Dynamic Programming

## SRT BOT 模型

1. SRT BOT
	- **Subproblem** definition:
		- 使用参数来**定义子问题**，比如$x(i, j)\in X$
		- 如果输入是一个数组，那么子问题通常可以定义为前缀数组`x[0 : i]`、后缀数组`x[i : n]`或子数组`x[i : j]`
	- **Relate** subproblem solutions recursively:
		- **写出子问题的递归关系**，$x(i) = f(x(j_1),x(j_2),...), j<i$:eight_spoked_asterisk:
		- 这个递归表达式是一个**严谨**的数学递归式，因为这决定了算法的正确性
		- 严谨一词不保证绝对的运行效率。假设子问题定义为前缀数组，在有的问题中，$x(i)=f(x(i-1))$，而在别的问题中，$x(i) =g(x(i-1),x(i-2),...,x(0))$。只要这些递归式能解决各自的问题，那么在效率上都是**合理**的
		- 对于:eight_spoked_asterisk:，$x(j_1),x(j_2),...$是已知的，我们要利用这些已知的信息求出$x(i)$的值
	- **Topological** order on subproblems:
		- 这是要求递归关系能够停止，而不是陷入死循环。:eight_spoked_asterisk:中，`i`就是逐渐增大的
	- **Base** case of relation
		- 递归的起始条件。没有条件，递归就是无止境的。
	- **Original** problem solution via subproblems
		- 子问题的解如何转化为原问题的解
	- **Time** analysis
		- 以检验算法是否高效



## 动态规划 DP

1. 概念
	- DP = recursive relation + memoization
	-  recursive relation是指递归关系，数学的递归式。分治也需要定义递归关系，才能实现
	- memoization指记录已经计算过的某些值，使其能够被复用，以节省时间。以下图计算fibonacci数为例：
		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205091420005.png" alt="image-20220509142006819" style="zoom: 33%;" />
		- 对于已经计算过的结果，在别的递归路径上不用再次计算，直接使用该结果即可
	- memoization是区分DP和分治的标准。
	- 虽然memoizaiton使得DP比分治更快地解出问题，但两者的**关键都在于定义子问题和写出递归式**，因为这样才能**正确地解出问题**

2. 各种DP题
	- https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-spring-2020/resources/mit6_006s20_lec15/
	- https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-spring-2020/resources/mit6_006s20_lec16/
	- https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-spring-2020/resources/mit6_006s20_lec17/
	- https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-spring-2020/resources/mit6_006s20_lec18/
	- DP是一种编程范式，真正掌握得靠自己刷题

# EOF

[返回顶部](#序言)