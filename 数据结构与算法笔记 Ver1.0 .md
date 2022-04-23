[到最后](#EOF)



# 序言

- 现在是2022年4月13日，大二下的期中。我于大二上学完了学校的数据结构和算法课，力扣上刷了200多道题（100多简单，100多中等，几道困难）。得出结论：
	- 我基本没有学会贪心、分治和动态规划这三大算法范式
	- 学习算法只靠填鸭是无用的——也许上学校的课用处也不太大
	- 经典的数据结构和算法必须自己实现
- 于是，我准备在算法之路上重新开始求索，以一个初学者的姿态。
- 源代码都在[这里](https://github.com/el-nino2020/DS-A)



# 版本一览

- Ver1.0 ，学习的视频为[【尚硅谷】数据结构与算法（Java数据结构与算法）](https://www.bilibili.com/video/BV1E4411H73v)，韩顺平老师讲的。完成时间为2022年4月23日



# 目录

[toc]







# 第1章：引入



## 数据结构和算法的关系

- 程序 = 数据结构 + 算法
- 数据结构是算法的基础



## 数据结构的分类

1. 数据结构包括：**线性结构和非线性结构**



2. 线性结构
	- 特点为数据元素之间存在**一对一**的线性关系
	- 有两种不同的**存储**结构：顺序存储结构和链式存储结构
		- :one:顺序存储的线性表称为顺序表，其中存储的元素是地址连续的
		- :two:链式存储的线性表称为链表，其中存储的元素地址不一定是连续的，元素节点中存放数据元素以及相邻元素的地址信息
	- 常见线性结构有：数组、队列、链表和栈



3. 非线性结构
	- 包括：多维数组，广义表，树结构，图结构



# 第2章：稀疏数组和队列



## 稀疏数组 sparse array

1. 需求：
	- 五子棋程序实现（1）存盘退出和（2）续上盘的功能
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204131456218.png" alt="image-20220413145603486" style="zoom: 50%;" />
	- 使用二维数组，会记录大量的0，浪费空间



2. 基本介绍
	- 当一个数组中大部分值都相同时，可以使用稀疏数组来保存该数组
	- 处理方法是将这些不同的值单独记录
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204131500297.png" alt="image-20220413150006052" style="zoom:50%;" />



3. 实现
	- 遍历2维数组，求出有`x`个数字不为0
	- 创建稀疏数组，大小为`x + 1`行，`3`列
	- 再次遍历2维数组，将不为0的位置和值存入稀疏数组



4. 代码：https://github.com/el-nino2020/DS-A/tree/main/data_structures/sparse_array



## 队列 queue

1. 介绍
	- 队列是一个**有序**列表，可以通过数组和链表来实现
	- 遵循**先入先出**的原则
	- ![队列](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204140654430.jpeg)



2. 使用数组模拟队列
	- 使用`front`、`rear`两个索引控制队列首尾的元素
	- 实现`isEmpty`、`isFull`、`add`、`get`、`peek`等方法



3. 实现
	- `ArrayQueue`模拟了队列的基本功能，但存在问题：`rear == capacity - 1`但`size()  < capacity`时已经不能添加了，不合理



4. 环形队列
	- ![](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204140727305.jpeg)
	- 将`arr`视作一个环，来解决（3）中的问题
	- 环形数组需要**空出一个存储空间**，这是**关键**
	- 记`front + 1`为队首元素，`rear`为队尾元素，两个属性的初始值都为`0`，则
		- 当`front == rear`时，队列为空
		- 当`(rear + 1) % capacity == front`时，队列满
	- `add`、`get`方法需要在`front`、`rear`达到`capacity`时，将它们的值置0，不然就索引越界了



5. 实现
	- 代码在`CircleArrayList`中

6. 代码：https://github.com/el-nino2020/DS-A/tree/main/data_structures/queue





# 第3章：链表 

## 单链表 single linked list

1. 基本介绍
	- 链表是以节点的方式来存储的
	- 每个节点包括data域和next域
	- 各个节点的内存地址不一定是连续的
	- 链表分为带头结点的和不带头结点的
	- 带头结点的单链表的逻辑结构如图：
	- ![image-20220414090208261](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204140902401.png)



2. 实现
	- 设计`Node`类
	- 单链表有`head`和`tail`属性
	- `boolean add(int val)`：新的节点加在链表尾部
	- `boolean replace(int oldVal, int newVal)`：将链表中第一个值为`oldVal`的节点的值更新为`newVal`，并返回`true`；找不到则返回`false`。如果要将所有值为`oldVal`的节点更改，可以实现`replaceAll`方法
	- `boolean remove(int val)`：删除某个节点。注意，要用`current.next.val == val`来判断，如果结果为`true`，则`current.next = current.next.next`，被删除的节点将由gc来处理



3. 代码：https://github.com/el-nino2020/DS-A/tree/main/data_structures/linked_list





## 双向链表 double linked list

1. 引入：
	- 单向链表只能向后查找，而双向链表可以向前或向后查找
	- 单向链表删除某一节点时不能自我删除，需要依靠该节点的前一节点作为辅助节点，而双向链表可以**自我删除**



2. 实现
	- 设计`Node`类
	- 实现增删查改



3. 代码：https://github.com/el-nino2020/DS-A/tree/main/data_structures/linked_list



## 约瑟夫环 Josephus problem 

1. 问题
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204141341868.png" alt="image-20220414134131773" style="zoom: 70%;" />



2. 思路：
	- 使用环形链表实现
	- 为了能够自我删除，使用双向环形链表



3. 代码：https://github.com/el-nino2020/DS-A/tree/main/data_structures/linked_list

# 第4章：栈



## 栈stack

1. 引入
	- 输入一个表达式，例如`7 * 3 + 5 - 2 `，计算机是如何计算该表达式的？（表达式对计算机而言只是一个字符串）



2. 基本介绍
	- 栈是一个先入后出的有序列表
	- 栈是这样一种特殊的线性表——它限制元素的插入与删除只能在线性表的**同一端**进行。允许插入和删除的一端，为变化的一端，称为栈顶（top)，另一端称为栈底（bottom）
	- 插入元素为入栈（push），删除元素为出栈（pop）



3. 应用场景
	- 子程序的调用
	- 函数递归调用
	- 表达式的转换（中缀表达式转后缀表达式）与求值
	- 二叉树的遍历
	- DFS



4. 代码：https://github.com/el-nino2020/DS-A/tree/main/data_structures/stack



## 综合计算器（中缀表达式）

1. 需求：设计计算器，能够根据表达式，进行**自然数**的**加减乘除**运算



2. 思路：
	- 表达式视为字符串
	- 创建一个数栈`numStk`，一个符号栈`opStk`
	- 遍历字符串
	- 假如为数字，放入`numStk`
	- 假如为符号：
		- :one:如果`opStk`为空，直接放入`opStk`
		- :two:如果`opStk`不为空，且当前运算符优先级小于等于`opStk`顶的符号的优先级，取出`numStk`顶的两个数，使用`opStk`顶的符号进行运算，得到的结果放入`numStk`；再把当前运算符入栈
		- :three:如果`opStk`不为空，且当前运算符优先级大于`opStk`顶的符号的优先级，直接入栈
	- 遍历完毕，将`opStk`中剩余的运算符进行运算，最终返回`numStk`中剩下的一个数字
	- 注意输入的自然数有多位的情况



3. 代码：https://github.com/el-nino2020/DS-A/blob/main/data_structures/stack/Calculator.java





## 前缀、中缀、后缀表达式

1. 前缀表达式（波兰表达式）
	- 前缀表达式的运算符位于操作数之前
	- `(3 + 4) * 5 - 6`对应的前缀表达式为`- * + 3 4 5 6`
	- 前缀表达式计算方法：
		- 从右至左扫描
		- 如果为数字，压入栈；如果为运算符，则取出栈顶的两个数，计算后将结果压入栈



2. 中缀表达式
	- 常见的运算表达式，如`(3 + 4) * 5 - 6`
	- 人类熟悉，但计算机却难以操作，参考之前实现的[综合计算器](#综合计算器（中缀表达式）)



3. 后缀表达式（逆波兰表达式）
	- `(3 + 4) * 5 - 6`对应的后缀表达式为`3 4 + 5 * 6 -`
	- 后缀表达式计算方法：
		- 从左至右扫描
		- 如果为数字，压入栈；如果为运算符，则取出栈顶的两个数，计算后将结果压入栈




4. 实现逆波兰计算器
	- 输入一个逆波兰表达式，支持对自然数的加减乘除，并计算结果
	- 代码：https://github.com/el-nino2020/DS-A/blob/main/data_structures/stack/RPNCalculator.java



5. 中缀表达式转后缀表达式

	- ![image-20220415085156555](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204150851932.png)

	1. 初始化运算符栈`stk`和后缀表达式`ans`（类型为`StringBuilder`）
	2. 从左至右扫描中缀表达式
	3. 遇到数字，调用`ans.append`
	4. 遇到操作符：
		- 如果`stk`为空，或`stk`栈顶元素为`(	`，则把该操作符入栈
		- 如果其优先级比栈顶元素优先级高，把该操作符入栈
		- 否则，`ans.append(stk.pop())`，重新执行步骤（4）：将该操作符与`stk`栈顶的元素再次比较
	5. 遇到括号：
		- 如果是`(`，直接入栈
		- 如果是`)`，不断执行`ans.append(stk.pop())`，直到出栈的元素为`(`为止，此时丢弃这一段括号
	6. 循环结束后，不断执行`ans.append(stk.pop())`，直到栈为空
		1. 后缀表达式即为`ans.toString()`	



6. 代码：https://github.com/el-nino2020/DS-A/blob/main/data_structures/stack/InfixCalculator.java

# 第5章：回溯



## 递归

1. 基本介绍就免了，递归的概念是学习编程语言时很基本的东西
2. 用处
	- 解决各种数学问题：八皇后问题、汉诺塔、阶乘、迷宫和不少排列组合的问题
	- 各种算法：快排、二分查找、分治算法
	- 将用栈解决的问题转化为用递归解决，简化代码



## 八皇后问题

1. 介绍
	- ![image-20220415130652483](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204151306740.png)
	- 思路：
		- 使用一维数组`int arr[9]`来记录八个皇后的位置，`arr[i]`表示第`i`个皇后在第`i`行位于第`i`列
		- 一开始，第一个皇后位于第一行第一列，然后将第二个皇后放上棋盘；当第二个皇后找到合适的位置（即与第一个皇后不会相互攻击），再摆第三个皇后；以此类推。。。
		- 当找到一个解时，从第八个皇后开始向上回溯，调整第七个皇后的位置，再判断；如果不行，再回溯到第六个皇后。以此类推。。。
		- 最终有92种解法



2. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/backtracking/NQueens.java



## 马踏棋盘 knight's tour problem

1.  介绍
	- ![image-20220423134315069](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204231343341.png)
	- 游戏：http://www.maths-resources.com/knights/

2. 原理
	- 使用回溯实现
	- 使用DFS：马在任意一格时，下一步的可能性最多有八种（排除在棋盘之外的情况），递归地前往这八个格子即可
	- 效率优化：递归时，马应该前往的格子，是当前能够前往的格子中下一步的可能性最少的那个点。即，假如马当前位于格子`A`，下一步能够前往的格子的集合为$next(A) = \set{B, C, D}$，则下一步前往的格子应该是`X`，其满足$next(X) = min\set{next(B), next(C), next(D)}$且$X\in \set{B,C,D}$。这样一来，该算法能够在短时间内走完更多的路径。



3. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/backtracking/KnightTourProblem.java

# 第6章：排序算法 sort algorithm



## 一些知识

1. 基本介绍
	- 排序是将一组数据，依指定的顺序进行排列的过程
	- 排序的分类：
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204151436015.png" alt="image-20220415143635832" style="zoom:60%;" />
	- 内部排序：将需要处理的所有数据都加载到内部存储器进行排序
	- 外部排序：数据量过大，无法全部加载到内存中，需要借助外部存储进行排序



2. 度量程序（算法）执行时间的两种方法
	- 事后统计：存在如下两个问题：
		- 需要实际运行程序，可能花费很多时间
		- 要求一台计算机在相同（软硬件）状态下执行不同的算法
	- 事前估算：使用时间复杂度进行判断



3. 时间频度
	- 一个算法花费的时间与算法中语句的执行次数成正比例，语句执行次数多的算法花费时间多。一个算法中的语句执行次数称为语句频度或时间频度，记为`T(n)`
	- 考虑计算`1 + 2 + ... + n`，一种算法为使用循环，循环`n`次得出结果，则`T(n) = n`；另一种方法为使用公式`sum = n * (1 + n) / 2`，只要算一次，则`T(n) = 1`



4. 时间复杂度 time complexity
	- 一般来说，算法中的基本操作语句的重复次数是问题规模`n`的某个函数，用`T(n)`表示；若有某个辅助函数`f(n)`，当`n`趋于无穷大时，`T(n) / f(n)`的极限是不为零的常数，则称`T(n)`与`f(n)`同数量级，记作`T(n) = O(f(n))`，称`O(f(n))`为算法的渐进时间复杂度，简称时间复杂度
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204151509020.png" alt="image-20220415150902790" style="zoom:60%;" />



5. 平均时间复杂度和最坏时间复杂度
	- 平均时间复杂度是指所有可能的输入实例都以等概率出现的情况下，该算法的运行时间
	- 一般讨论时间复杂度，都是讨论最坏时间复杂度，以保证算法的运行时间不会比最坏时间复杂度还要长



6. 空间复杂度space complexity
	- 与时间复杂度类似，算法的空间复杂度定义为算法所耗费的存储空间，它也是问题规模`n`的函数
	- 空间复杂度是一个算法在运行过程中临时占用存储空间大小的量度。有的算法需要占用的空间随着问题规模`n`的增大而增大，例如快速排序和归并排序
	- 做算法分析时，主要讨论的是时间复杂度。因为从用户体验上看，更看重的是程序执行的速度。一些缓存产品（redis，memcache）和算法（基数排序）本质就是用空间换时间



## 冒泡排序 bubble sort

1. 原理：
	- 假设数组长度为`n`
	- 循环`n - 1`次。每一次循环，按顺序**两两比较**数组中的元素，把大的元素移到小的元素后面。这样，每一次循环，未排序部分中最大的数都会移到该部分的最后面（如同气泡上浮一样），加入到已经排序的部分中。当遍历完成，整个数组就排序完毕了





2. 一个例子：https://www.geeksforgeeks.org/bubble-sort/
	- **First Pass:** 
		( **5** **1** 4 2 8 ) –> ( **1** **5** 4 2 8 ), Here, algorithm compares the first two elements, and swaps since 5 > 1. 
		( 1 **5** **4** 2 8 ) –> ( 1 **4** **5** 2 8 ), Swap since 5 > 4 
		( 1 4 **5** **2** 8 ) –> ( 1 4 **2** **5** 8 ), Swap since 5 > 2 
		( 1 4 2 **5** **8** ) –> ( 1 4 2 **5** **8** ), Now, since these elements are already in order (8 > 5), algorithm does not swap them.
	- **Second Pass:** 
		( **1** **4** 2 5 8 ) –> ( **1** **4** 2 5 8 ) 
		( 1 **4** **2** 5 8 ) –> ( 1 **2** **4** 5 8 ), Swap since 4 > 2 
		( 1 2 **4** **5** 8 ) –> ( 1 2 **4** **5** 8 ) 
		( 1 2 4 **5** **8** ) –> ( 1 2 4 **5** **8** ) ——这一步其实是没必要的，因为`8`已经是整个数组最大的元素了
		Now, the array is already sorted, but our algorithm does not know if it is completed. The algorithm needs one **whole** pass without **any** swap to know it is sorted.——这是对冒泡排序的一个优化
	- **Third Pass:** 
		( **1** **2** 4 5 8 ) –> ( **1** **2** 4 5 8 ) 
		( 1 **2** **4** 5 8 ) –> ( 1 **2** **4** 5 8 ) 
		( 1 2 **4** **5** 8 ) –> ( 1 2 **4** **5** 8 ) 
		( 1 2 4 **5** **8** ) –> ( 1 2 4 **5** **8** ) 



3. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/sort/BubbleSorting.java
	- 时间复杂度为$O(n^2)$



## 选择排序 selection sort

1. 原理
	- 循环`n - 1`次
	- 第一次循环，从`arr[0]`到`arr[n - 1]`中选出最小值，与`arr[0]`交换
	- 第二次循环，从`arr[1]`到`arr[n - 1]`中选出最小值，与`arr[1]`交换
	- 以此类推



2. 一个例子：https://www.geeksforgeeks.org/selection-sort/

	- ```
		arr[] = 64 25 12 22 11
		
		// Find the minimum element in arr[0...4] 为11，
		// and place it at beginning
		11 25 12 22 64
		 
		// Find the minimum element in arr[1...4] 为12
		// and place it at beginning of arr[1...4]
		11 12 25 22 64
		
		// Find the minimum element in arr[2...4] 为22
		// and place it at beginning of arr[2...4]
		11 12 22 25 64
		
		// Find the minimum element in arr[3...4] 为25
		// and place it at beginning of arr[3...4]
		11 12 22 25 64 
		```



3. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/sort/SelectionSort.java
	- 时间复杂度为$O(n^2)$
	- 由于数组元素交换的次数比冒泡排序少，速度更快



## 插入排序 insertion sort

1. 原理
	- 把`n`个待排序的元素分为一个有序表和一个无序表。开始时有序表中只包含1个元素。每次从无序表中取出一个元素，将它插入到有序表中的适当位置。循环`n - 1`次后，排序完成



2. 一个例子：https://www.geeksforgeeks.org/insertion-sort/
	- ![](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204151920988.png)



3. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/sort/InsertionSort.java
	- 时间复杂度为$O(n^2)$



## 希尔排序 shell sort

1. 引入
	- 对于插入排序，当需要插入的数较小时，后移的次数很多，影响效率。例如`2, 3, 4, 5, 6, 1`这个数组，插入`1`需要将它之前的所有元素进行后移。

2. 介绍
	- 希尔排序也是一种插入排序，由简单插入排序改进而来，也称为缩小增量排序

3. 原理
	- 把数组按下标的一定增量分组（如果增量为`5`，那么`arr[0]`与`arr[5]`与`arr[10]`一组，`arr[1]`与`arr[6]`与`arr[11]`一组，一次类推），对每组使用简单插入排序算法排序。
	- 随着增量的逐渐减少，每组满足最终排序结果的元素越来越多（即使该元素没有在最终排序好后的位置上，也在该位置附近，而不像简单插入排序那样可能离得很远）。当增量减至1时，整个数组恰好被分为一组，再执行一次插入排序，整个数组就排序完成了。

4. 例子
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204160803952.png" alt="image-20220416080352618" style="zoom:50%;" />



5. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/sort/ShellSort.java





## 快速排序 quick sort

1. 原理
	- 每一趟排序，将需要排序的元素分成独立的两部分，其中一部分的所有元素都比另一部分小。再递归地处理各个部分，直到某一部分只有一个元素。递归结束后，排序完成

2. 例子
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204160851375.png" alt="image-20220416085105207" style="zoom: 50%;" />



3. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/sort/QuickSort.java
	- 如何实现在每一次的递归中，将数组分为两部分，使得右边部分都大于左边部分，且花费的时间为`O(n)`，花费的空间为`O(1)`，每个人的方法是不一样的，找到适合自己的就可以了



## 归并排序 merge sort

1. 原理（用例子阐明）
	- 使用分治策略
	- 分主要是将数组拆分成一个个单独的子序列
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204160951218.png" alt="image-20220416095149063" style="zoom:70%;" />
	- 合并子序列的方法：将两个排序好的子序列合并成一个排序好的序列
	- ![image-20220416095359786](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204160954084.png)





2. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/sort/MergeSort.java





## 基数排序 radix sort

1. 介绍
	- 基数排序属于“分配式排序”（distribution sort），又称“桶子法”（bucket sort 或 bin sort)
	- 基数排序法是效率高的稳定排序法（stable sort，即相等的元素在排序后的相对位置不发生变化）
	- 基数排序是桶排序的拓展

2. 原理

	- 设置十个“桶”，代表`0`至`9`十个数字

	- 将所有数字统一为同样的数位长度，数位较短的补零。从最低位开始，依次进行排序。
	- 每一位的排序方法如下：
		- 遍历数组，将每个元素按照该位的值顺次放入桶中
		- 遍历完毕，按桶的顺序顺次取出其中的元素放回数组中。
	- 循环所有位，完成排序



3. 例子
	1. 这个例子有助于理解基数排序的原理
		- ![image-20220416113419064](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204161134239.png)
		- ![image-20220416113451555](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204161134728.png)
		- ![image-20220416113520450](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204161135619.png)
	2. 可视化排序。它是对桶的优化，实际上没必要将每个桶都设置为一个数组
		- https://www.cs.usfca.edu/~galles/visualization/RadixSort.html



4. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/sort/RadixSort.java
	- 该代码只支持对自然数的排序，不支持负数排序
	- 基数排序**仅能对数字进行排序**（这个算法基于数字本身的特性），而不能像之前的排序算法那样支持对象的排序
	- 对于`int[]`进行排序时，由于`Integer.MAX_VALUE = 2147483647`只有`10`位长，基数排序的时间复杂度为`O(n)`，当`n`充分大时，基数排序的效率高于其他排序算法



## 常用排序算法总结

<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204161335166.png" alt="image-20220416133538973" style="zoom: 70%;" />

- in-place是指不占用额外内存，out-place是占用额外内存；k指桶的个数





# 第7章：查找算法 search



## 线性查找 linear search

1. 原理：字面意思，按顺序一个一个地找，没啥好讲的

	```java
	public static void int linearSearch(int[] arr, val){
	    for(int i = 0; i < arr.length; i++){
	        if (arr[i] == val){
	            return i;
	        }
	    }
	    return -1;
	}
	```





## 二分查找 binary search

1. 原理：
	- 前提：数组`arr`必须是**有序**的。我们要查找`arr`中是否存在`val`
	- 对于索引`left`、`right`，令`mid = (right + left) / 2`，
		- 如果`arr[mid] < val`，说明`val`只可能在`arr[mid + 1, right]`中
		- 如果`arr[mid] > val`，说明`val`只可能在`arr[left, mid - 1]`中
		- 如果两者相等，说明找到



2. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/search/BinarySearch.java
	- 二分查找可以用递归和非递归实现。



## 插值查找 interpolation search

1. 引入
	- 在`1`至`100`连续的数组中，使用二分查找查找`1`，需要递归至少6次，似乎有些不合理

2. 介绍
	- 插值查找类似于二分查找，不同的是插值查找每次从自适应`mid`处开始查找
	- `mid`的公式如下：![image-20220416151106200](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204161511277.png)
	- 可以看出，每次更新，`mid`的值更接近想要查找的值`key`，而不只是单纯地二分
	- 以`key = 1, arr[0] = 1, arr[99] = 100`为例，第一次查找，`key - a[low] = key - a[0] = 0`，两次查找就能找到`1`

3. 注意事项

	- 插值查找也需要保证查找的数组是有序的

	- 对于元素分布均匀的数组来说，插值查找速度较快

		- > Interpolation search works better than Binary Search for **a Sorted and Uniformly Distributed** array.

	- 如果元素分布不均匀，插值查找效率不一定比二分查找高



4. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/search/InterpolationSearch.java

## 斐波那契查找 Fibonacci search

1. 一些知识
	- 黄金分割点：将一条线段分为两部分，比如`|------x-------|---y----|`，使其中一部分与全场之比等于另一部分与该部分之比，即`x / (x + y) = y / x`，解方程得到相应的值。该比例被称作黄金分割，或中外比，约等于`0.618`
	- 斐波那契数列：1、1、2、3、5、8、13、21、34、……
	- 发现，斐波那契数列相邻两个数的比例，无限接近黄金分割比

2. 原理
	- 斐波那契查找与前两种查找类似，要求数组有序。它仅改变中间节点`mid`的位置，使其位于黄金分割点附近
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204171104579.png" alt="image-20220417110427506" style="zoom: 67%;" />
	- 假设数组长度为`n`，等于某一个斐波那契数，不妨为`F(k)`，由`F(k) = F(k - 1) + F(k - 2)`，得`mid = low + F(k - 1) - 1`。同理，长度为`F(k - 1)`和`F(k - 2)`的部分也可以用相同方法再次分割
	- 如果`n`不等于`F(k)`，只需找到一个`k`，使得`F(k) `恰好大于`n`即可。由此产生了一个初始长度为`F(k)`的数组，将多余的部分用`arr[n - 1]`填补



3. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/search/FibonacciSearch.java



# 第8章：哈希表



## 哈希表 hash table

1. 基本介绍
	- 散列表（hash table），也叫哈希表，是根据关键码值（key value）而直接进行访问的数据结构。
	- 哈希表通过把关键码值映射到表中一个位置来访问记录，从而加快访问速度
	- 这个映射函数叫做**散列函数**，存放记录的数组叫做**散列表**
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204171322225.png" alt="image-20220417132221059" style="zoom: 50%;" />

2. 原理
	- ![image-20220417132358758](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204171323957.png)
	- 一个哈希表有这样一些组成部分：散列函数和散列表。
		- 散列表在这里是一个链表数组，链表中的一个节点才是真正的数据
		- 散列函数负责找到需要进行操作的数据位于哪一条链表上



3. 实现
	- 需求如下：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204171329129.png" alt="image-20220417132956940" style="zoom:33%;" />



4. 代码：https://github.com/el-nino2020/DS-A/tree/main/data_structures/hash_table



# 第9章：树基础



## 一些基础知识

1. 为什么需要树这种数据结构
	1. 数组：
		- 优点：可以通过下标访问元素，速度快
		- 缺点：插入或删除时需要将其后的元素整体移动，效率较差。插入时可能达到容量上限，这时需要扩容
	2. 链表：
		- 优点：插入和删除不需要移动其他元素
		- 缺点：访问、查找元素需要逐个访问，效率低
	3. 树：
		- 能提高数据的存储、读取效率。对于二叉排序树，crud的效率都不错



2. 一些概念
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204171728218.png" alt="image-20220417172846010" style="zoom:50%;" />
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204171729037.png" alt="image-20220417172903903" style="zoom: 50%;" />
	- ![image-20220417172929899](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204171729090.png)



## 前序、中序、后序遍历 preOrder、inOrder、postOrder

1. 介绍
	- 前序：pre order，中、左、右
	- 中序：in order，左、中、右
	- 后序：post order，左、右、中



2. 代码：https://github.com/el-nino2020/DS-A/blob/main/data_structures/tree/BinaryTree.java



## 查找二叉树中的值

1. 原理

	- 假设要查找的值为`val`

	- 对于每一个节点`node`，如果`node.val == val`。则返回`node`
	- 如果它的左子树查找成功，则返回该结果
	- 如果它的右子树查找成功，则返回该结果
	- 否则返回`null`
	- 故这个查找是递归进行的，终止条件为`node == null`



2. 代码：https://github.com/el-nino2020/DS-A/blob/main/data_structures/tree/BinaryTree.java中的`search(Node , int)`方法



## 顺序存储二叉树

1. 基本介绍
	- 从数据存储方式来看，数组和树可以相互转换——通过对树的层序遍历完成转换
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204180848824.png" alt="image-20220418084826656" style="zoom:33%;" />
	- 顺序存储二叉树通常只考虑完全二叉树——一般的二叉树往往要求数组容量很大（第`i`层要求$2^{i - 1}$个元素空间），造成空间浪费
	- 索引为`n`的节点的**左子节点**的索引为`2 * n + 1`
	- 索引为`n`的节点的**右子节点**的索引为`2 * n + 2`
	- 索引为`n`的节点的**父节点**的索引为`(n - 1) / 2`



2. 需求：对以数组形式存储的树进行前序遍历



3. 代码：https://github.com/el-nino2020/DS-A/blob/main/data_structures/tree/BinaryTree.java中的`preOrder(int[] , int)`方法



4. 实际应用
	- 该小结的内容将在[堆排序](#堆排序 heap sort)中起到作用



## 线索化二叉树 threaded binary tree

1. 引入
	- 对于如下的一棵树：
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204180922116.png" alt="image-20220418092246978" style="zoom:50%;" />
	- 对这颗树进行中序遍历时，结果为`8 3 10 1 14 6`
	- 但是`8`、`10`、`14`、`6`的子节点在遍历时没有充分利用——中序遍历在遇到`null`的节点时直接返回：`if(node == null) return;`
	- 如何充分利用各个节点的左右节点，使得各个节点指向自己遍历时的前后节点？



2. 介绍
	- 节点数为`n`的二叉树有`n + 1`个空的子节点（节点数为`n`的二叉树有`2n`个子节点位置，其中`n - 1`个是非空的（排除根节点，它不是任何节点的子节点），故空的子节点数量为$2n-(n-1)=n+1$）
	- 利用二叉树中的这些空的子节点，存放每个节点在**某种遍历次序**下的**前驱和后继**节点。这种**附加**的节点信息被称为**线索**
	- 这种加上线索的二叉链表称为线索链表，相应的二叉树称为线索二叉树。根据线索性质的不同，线索二叉树可以分为**前序**线索二叉树、**中序**线索二叉树和**后序**线索二叉树



3. 原理——线索化二叉树
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204181049402.png" alt="image-20220418104941303" style="zoom:70%;" />
	- 设置一个`prev`指针，指向上一个遍历的节点，以设置前驱和后继节点
	- 由于在线索化后，`left`可能指向左子树，也可能指向前驱节点，需要在`Node`类设置额外的属性来确定`left`的功能；`right`同理
	- 对于当前节点`node`，它的前驱节点为`node.left  = prev`
	- 对于`prev`，它的后继节点为`prev.right = node`—— 无法在本轮递归中设置`node`的后继节点





4. 原理——遍历线索化二叉树，以中序遍历为例
	- :eight_pointed_black_star: 线索化后，各个节点指向有变化，因而不能使用原有遍历方式。新的遍历方式可以线性地进行，无需使用递归，因而提高效率
	- :one:对于节点`node`，先找到其子树中最左边的那个节点（第一个`leftType`为`1`的节点）
	- :two:只要该节点有后继节点（`rightType`为`1`），则访问其后继节点——左
	- :three:否则，访问当前节点——中
	- :four:然后，令当前节点指向其右节点，即`node = node.right`，重复开始:one:，直到遍历结束——右
	- :eight_spoked_asterisk: 这种遍历方式有点像利用栈模拟二叉树的递归遍历，即尽量往左走，走到头了再访问各个节点的右子树

5. 代码：https://github.com/el-nino2020/DS-A/blob/main/data_structures/tree/ThreadedBinaryTree.java



# 第10章：树应用



## 堆排序 heap sort

1. 堆
	- 堆是具有以下性质的**完全二叉树**：**每个**节点的值都大于等于其子节点的值。这样的堆称为大顶堆；如果每个节点的值都小于等于其子节点的值。那么，称这样的堆为小顶堆
	- 大顶堆的例子：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204181311825.png" alt="image-20220418131120732" style="zoom:50%;" />
		- 数组表示为`50 45 40 20 25 35 30 10 15`
		- 因此，大顶堆的特点为`arr[i] >= arr[2 * i + 1] && arr[i] >= arr[2 * i + 2]`
	- 小顶堆的例子：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204181313006.png" alt="image-20220418131356905" style="zoom: 50%;" />
		- 数组表示为`10 20 15 25 50 30 40 35 45`
		- 因此，小顶堆的特点为`arr[i] <= arr[2 * i + 1] && arr[i] <= arr[2 * i + 2]`



2. 堆排序
	- 堆排序是利用**堆**这种数据结构而设计的一种排序算法。它是一种选择排序，它的时间复杂度为`O(nlog(n))`，是一种不稳定排序
	- 如果排序结果为升序，会先将数组构造为大顶堆；如果结果为降序，会先将数组构造为小顶堆



3. 原理
	- 堆排序可以分为两个部分
	- :one:将数组**构建**成一个大顶堆
	- :two:将以下步骤循环`n - 1`次：
		- 将根节点的元素与堆数组最后的元素进行交换，此时堆的大小减小1，而待排序的数组后部的有序表大小增加1
		- 将交换后的堆**调整**为大顶堆。以便下一次循环
	- 循环完毕，整个数组都成为有序表
	- :eight_pointed_black_star:我们先定义这样一个函数，叫做`sinkNode`，它的功能是选中一个节点，**如果**它的值小于它的子节点的值，则将它与子节点中值较大的那个节点**交换**。**循环往复**，直到它下沉到堆最底下（没有子节点），或者它的值比它子节点的值都要大。
	- 对于:one:，我们只要从后往前对数组中的节点进行`sinkNode`的操作，就可以构建一个大顶堆。由于叶节点不必再下沉，所以从索引为`2 * n - 1`开始往前遍历，这个索引代表最后一个非叶节点
	- 对于:two:，我们只要在每次循环中，让堆顶节点——即索引为`0`的节点——下沉即可
	- 某个节点和它子节点的索引的关系参考[顺序存储二叉树](#顺序存储二叉树)



4. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/sort/HeapSort.java



## 赫夫曼树 huffman tree

1. 一些概念
	- <img src="C:\Users\Morgan\AppData\Roaming\Typora\typora-user-images\image-20220418190710908.png" alt="image-20220418190710908" style="zoom:50%;" />
	- :one:路径：在一棵树中，从一个节点往下到达其子节点的通路，称为路径。
	- :two:路径长度：一条通路中边（edge）的数量，也等于节点数减去1。若规定根节点的层数为1，则从根节点到第`L`层节点的路径长度为`L - 1`。例如，根节点到节点`13`的路径长度为2
	- :three:节点的权：若将一个有着某种含义的数值赋给某个节点，则该数值称为该节点的权
	- :four:节点的带权路径长度：根节点到该节点的路径长度 `×` 该节点的权
	- :five:树的带权路径长度：树的所有**叶节点**的带权路径长度**之和**，记为WPL（weight path length）
	- :six:赫夫曼树：给定`n`个权值作为`n`个**叶节点**的值，构造一棵**WPL最小**的树，这样的二叉树称为最优二叉树，也称为赫夫曼树
	- 例子：赫夫曼树汇总，权值较大的叶节点应该距离根节点较近
	- ![image-20220418193439030](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204181934159.png)



2. 原理——创建赫夫曼树

	- :bulb:基本思想：赫夫曼树要求WPL最小。直观来说，权值较大的叶节点应该距离根节点较近，反之，权值较小的叶节点应该距离根节点较远。我们只要保证权值越小的叶节点在树的越底层即可。

	- 输入是一个数组，其每个元素代表一个权值
	- 将该数组转化为一个节点数组，节点的值即为元素的值
	- 循环以下操作，直至数组只剩一个节点：
		- 将数组按从小到大排序
		- 取出前两个节点`n1`、`n2`，其值分别为`val1`、`val2`。生成一个新节点，值为`val1 + val2`，其子节点为`n1`、`n2`。将该节点放入数组



3. 代码：https://github.com/el-nino2020/DS-A/blob/main/data_structures/tree/HuffmanTree.java





## 赫夫曼编码 huffman coding

1. 引入：

	  - 对于字符串`hello`

	  - 如果使用定长编码，将每一个字母转为ASCII值，那么总长度为`5 * 8 = 40 bits`

	  - 如果使用变长编码，如`h: 0; e: 1; l: 10; o:11`，则产生的编码为`01101011`，解码时存在歧义





2. 赫夫曼编码
	- 赫夫曼编码是一种编码方式，它是赫夫曼树在电信通信中的经典应用
	- 赫夫曼编码是可变字长编码（VLC）的一种，同时也是前缀编码——每个字符的编码都不会是其他字符编码的前缀——因此不会产生歧义
	- 赫夫曼编码是一种无损压缩



3. 原理——字符串转二进制数据
	- 输入：一个字符串（例如"I like apple"）；输出：二进制编码
	- :one:统计字符串中每个字符出现了几次，例如`p`两次、`k`一次
	- :two:生成赫夫曼树，叶节点的权值为字符的出现次数（节点中应额外保存该字符的信息）
	- :three:根据赫夫曼树，给每个字符编码。方法为：从根节点出发，向左编码追加`0`，向右编码追加`1`
	- :four:根据编码处理输入的字符串，转为二进制
	- :exclamation:注意事项：赫夫曼树根据排序方式不同，生成的树不一定唯一。因此，输入一个字符串，其赫夫曼编码也不一定是唯一的。但由于不同的赫夫曼树都是WPL最小的，即使一个字符串有不同的赫夫曼编码，它们的长度都是一样的



4. 原理——二进制数据转字符串
	- 输入：:one:二进制编码和:two:编码与字符的映射关系；输出：一个字符串（例如"I like apple"）
	- 基本思路：遍历二进制编码数据，由于赫夫曼编码是前缀编码，每匹配到一个字符就加入要输出的字符串中



5. 需求：
	1. 压缩：输入一个字符串，使用赫夫曼编码输出`byte[]`
	2. 解压：输入一个压缩后的`byte[]`，输出原来的字符串



6. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/coding/HuffmanCoding.java
	- 这里只实现了字符串的压缩与解压
	- 在加入IO后，可以实现任何文件的压缩和解压


7. 赫夫曼编码压缩注意事项
	- 如果文件本身是经过压缩处理的，如`.zip`、`.pptx`等，使用赫夫曼编码压缩的文件大小不会有明显变化
	- 赫夫曼编码是按字节处理的，因此可以处理所有类型的文件（二进制文件和文本文件）
	- 如果文件中重复的数据不多，压缩效果不会很明显



## 二叉排序树 binary sort tree

1. 基本介绍
	- BST，binary sort（search） tree，二叉排序树是这样一棵二叉树：其每一个非叶节点，该节点的左子节点的值比它的小，右子节点的值比它的大
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204191627328.png" alt="image-20220419162740180" style="zoom:50%;" />
	- 如果有相同值的节点，可以将该节点放在另外一个节点的左边或右边。但应尽量避免出现重复的值
	- 由BST的性质，中序遍历BST的结果是一个升序的数组
	- BST是一种高效地执行curd操作的结构



2. 原理——增加节点
	- 递归地遍历节点：
	- 如果当前节点的值**等于**要加入的值，则停止递归——假定当前BST不允许重复值
	- 如果当前节点的值**大于**要加入的值，则递归**左**子节点
	- 如果当前节点的值**小于**要加入的值，则递归**右**子节点
	- 如果递归到的节点为空，则说明应该在此处添加一个新的节点，添加后停止递归



3. 原理——删除节点
	- ![image-20220419171807276](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204191718341.png)
	- 如果删除叶子节点，如`2`、`5`、`9`等，直接删除该节点即可
	- 如果删除的节点有一个子节点，如`1`，让该节点的父节点指向它的非空子节点，即`3`的左节点应该指向`2`
	- 如果删除的节点有两个子节点，如`7`，则:one:先找到该节点右子树中最小的元素，即以`10`为根节点的子树中最小的值——`9`；:two:删除`9`这一节点，同时，:three:将`7`的值变为`9`
	- 如果BST中没有要删除的节点，则无事发生



4. 代码：https://github.com/el-nino2020/DS-A/blob/main/data_structures/tree/BinarySortTree.java



##  AVL树

1. 引入：

	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204201058714.png" alt="image-20220420105801625" style="zoom:33%;" />

	- 这是一棵BST，但其查询的效率与链表接近。可以说，它退化成了链表，故效率低



2. 平衡二叉搜索树 balanced BST
	- 平衡二叉搜索树是这样一棵BST：它的左右子树的高度差的绝对值不超过1，且它的左右子树都是平衡二叉搜索树
	- 常见的平衡二叉树有：AVL树、红黑树、替罪羊书、Treap等



3. 原理

	- 在往AVL树中添加或删除节点时，有可能造成不平衡，此时需要进行调整

	- 我们先定义两个函数`leftRotate`和`rightRotate`：

	- ```
		T1, T2 and T3 are subtrees of the tree rooted with y (on the left side) or x (on 
		the right side)           
		     y                               x
		    / \     Right Rotation          /  \
		   x   T3   - - - - - - - >        T1   y 
		  / \       < - - - - - - -            / \
		 T1  T2     Left Rotation            T2  T3
		Keys in both of the above trees follow the following order keys(T1) < key(x) < keys(T2) < key(y) < keys(T3)
		So BST property is not violated anywhere.
		旋转的操作是对左边的y和右边的x进行的
		```

	- 树不平衡时，有以下四种情况

	- :one:**Left Left Case**

	- ```
		T1, T2, T3 and T4 are subtrees.
		         z                                      y 
		        / \                                   /   \
		       y   T4      Right Rotate (z)          x      z
		      / \          - - - - - - - - ->      /  \    /  \ 
		     x   T3                               T1  T2  T3  T4
		    / \
		  T1   T2
		```

	- :two:**Left Right Case** 

	- ```
		      z                               z                           x
		    / \                            /   \                        /  \ 
		   y   T4  Left Rotate (y)        x    T4  Right Rotate(z)    y      z
		  / \      - - - - - - - - ->    /  \      - - - - - - - ->  / \    / \
		T1   x                          y    T3                    T1  T2 T3  T4
		    / \                        / \
		  T2   T3                    T1   T2
		```

	- :three:**Right Right Case** 

	- ```
		    z                                y
		 /  \                            /   \ 
		T1   y     Left Rotate(z)       z      x
		    /  \   - - - - - - - ->    / \    / \
		   T2   x                     T1  T2 T3  T4
		       / \
		     T3  T4
		```

	- :four:**Right Left Case** 

	- ```
		      z                            z                            x
		  / \                          / \                          /  \ 
		T1   y   Right Rotate (y)    T1   x      Left Rotate(z)   z      y
		    / \  - - - - - - - - ->     /  \   - - - - - - - ->  / \    / \
		   x   T4                      T2   y                  T1  T2  T3  T4
		  / \                              /  \
		T2   T3                           T3   T4
		```

	- 具体实现中，:two:可以转化为:one:，同理，:four:可以转化为:three:
	
	- 这个原理参考https://www.geeksforgeeks.org/avl-tree-set-1-insertion/



4. 代码：https://github.com/el-nino2020/DS-A/blob/main/data_structures/tree/AVLTree.java





# 第11章：多路查找树（概念）

1. 引入
	- 二叉树的操作效率高，但当节点很多时，存在以下问题：
	- 构建二叉树时，需要进行多次IO操作（要从数据库或文件中读数据），因此速度有影响
	- 大量节点造成二叉树高度很大，影响效率



2. 多叉树 multiway tree
	- 在二叉树中，每个节点有一个数据项，最多有两个子节点。在多叉树中，每个节点允许有**更多数据项**和**更多子节点**

3. 2 - 3树
	- 2 - 3树是最简单的B树（在后面定义）
	- B树中，**所有叶节点都在同一层**
	- 2 - 3树是由二节点和三节点构成的树
	- 二节点要么没有子节点，要么有两个子节点。一个节点存放一个数据
	- 三节点要么没有子节点，要么有三个子节点。一个节点允许存放两个数据
	- 2 - 3树是一棵多路查找树，即子节点的数据与本节点的数据存在大小关系
	- <img src="C:\Users\Morgan\AppData\Roaming\Typora\typora-user-images\image-20220420195821689.png" alt="image-20220420195821689" style="zoom:50%;" />
	- 以`[26, 23]`节点为例，它的左子节点的数据都比`26`小，中间子节点的数据介于`26`和`32`之间，右子节点的数据大于`32`



4. B树 B - tree
	- B是balanced的意思
	- B树的阶 $\overset{\text{def}}{=}$ 节点中（理论）最多子节点个数。 2 - 3树的阶是3， 2 - 3 - 4树的阶是4
	- B树是一种多路搜索树
	- B树的搜索，从根节点开始，对节点内的数据序列进行二分查找，如果找到则结束。否则进入相应子节点进行查找，直到找到节点或递归到叶节点
	- 所有节点——叶节点和非叶节点——都存放数据
	- 每一次查找，相当于对全体数据进行一次二分查找
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204202010063.png" alt="image-20220420201020830" style="zoom:50%;" />





5. B+ 树
	- B+树的搜索与B树类似：每次查找，在3个子节点中找出一个进行递归遍历，范围缩小至原先的$\frac 1 3$，因而优于二分查找。而且B+树的高度比二叉树的小，因而效率更高
	- 但B+树所有的数据都存放在叶节点的有序链表中（稠密索引）
	- 非叶节点存储的是叶节点的索引（稀疏索引），而不存放数据本身
	- B+树更适合文件索引系统
	- 子节点会有索引指向别的子节点
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204202017879.png" alt="image-20220420201738733" style="zoom:75%;" />



6. B*树
	- B*树是B+树的变体，在B+树的基础上增加非叶节点指向同一层的别的节点
	- B*树的空间使用率比B+树高
	- ![image-20220420202419254](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204202024473.png)

  

# 第12章：图

## 图 graph

1. 引入
	- 线性表局限于一个直接前驱和一个直接后继的关系
	- 树也只有一个直接前驱
	- 当我们需要**多对多的关系**时，我们就用到了图



2. 基本介绍
	- 图是一种数据结构
	- 图的节点可以具有零个或多个相邻元素。两个节点之间的连接称为边。节点也可以称为顶点
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204210931196.png" alt="image-20220421093130089" style="zoom: 50%;" />



3. 一些概念
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204210932029.png" alt="image-20220421093213882" style="zoom:50%;" />
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204210932528.png" alt="image-20220421093234378" style="zoom: 50%;" />



4. 图的表示（存储）方式
	- 图有两种表示方式：邻接矩阵（二维数组）和邻接表（链表）
	- :one:邻接矩阵：邻接矩阵是表示图中节点之间相邻关系的矩阵。对于有`n`个顶点的图，邻接矩阵是一个`n`阶方阵
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204210937483.png" alt="image-20220421093751321" style="zoom: 50%;" />
	- :two:邻接表：邻接矩阵需要为每个顶点分配长度为`n`的数组。其中的边有很多都是不存在的，故会造成空间损失。邻接表只关心节点存在的边，因此没有空间浪费。邻接表由数组 + 链表组成
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204210941190.png" alt="image-20220421094140958" style="zoom:50%;" />
	- 邻接矩阵侧重于查看两个节点之间是否有边（数组的访问速度是`O(1)`），而邻接表侧重于得到节点的所有邻居。要视具体情况使用

5. 代码：https://github.com/el-nino2020/DS-A/blob/main/data_structures/graph/Graph.java



## 深度优先遍历 depth first search

1. 引入
	- 对于图的遍历方式有两种：深度优先遍历和广度优先遍历

2. 原理——DFS
	- :one:给定初始节点，从该节点出发，**每访问**一个节点，标记其为已访问
	- :two:查找当前节点的所有邻接节点
		- 如果某一邻接节点未被访问，则访问它，并以它为当前节点，重复:two:的过程
	- 当所有节点都被访问，DFS结束
	- 该原理需要用递归实现
	- 这种访问策略是优先往纵向挖掘深入，而不是对一个节点的所有邻接节点进行横向访问

3. 例子
	- ![image-20220421110110377](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204211101513.png)
	- 从A开始执行DFS，结果为`A B C D E`

4. 代码https://github.com/el-nino2020/DS-A/blob/main/data_structures/graph/Graph.java



## 广度优先遍历 breath first search

1. 基本介绍
	- 图的BFS，类似于一个分层搜索过程。BFS需要使用一个队列来记录当前层的节点顺序，以访问这些节点的邻接节点

2. 原理——BFS
	- 将初始节点放入队列，不断重复以下操作，直至队列为空：
		- 取出队首节点，标记其为已访问，再将队首节点的所有未访问节点存入队列



3. 例子：
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204211137720.png" alt="image-20220421113713639" style="zoom:33%;" />
	- 从`A`开始执行BFS，结果为`A B C D E F G`

4. 代码：https://github.com/el-nino2020/DS-A/blob/main/data_structures/graph/Graph.java





# 第13章： 分治 

## 分治 divide and conquer

1. 基本介绍
	- 所谓“分治”，即“分而治之”，是把一个复杂的问题分成若干个相同或相似的子问题，再把这些子问题分解为更小的子问题……直到最后的子问题可以简单求解。原问题的解即子问题的解的合并
	- 该方法可以解决一些经典问题：
		- 二分查找
		- 合并排序
		- 快速排序
		- 傅里叶变换
		- 汉诺塔



2. 基本步骤
	- 分治法在**每一层递归**上有三个步骤
		- :one:分解：将原问题分解为若干个规模较小，相互独立，与原问题形式相同的子问题
		- :two:解决：若子问题能够被直接解决，则直接解，否则递归地解各个子问题
		- :three:合并：将各个子问题的解合并为原问题的解



3. 利用分治法设计算法：
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204211741611.png" alt="image-20220421174136367" style="zoom:50%;" />
	- `|P|`表示问题的规模，`n0`为某一阈值。当`|P| < n0`时，问题可以直接解出，这时调用`ADHOC`函数直接解出该子问题，不必再递归
	- `MERGE`用于将各个子问题（`Pi`）的解合并为原问题（`P`）的解



## 汉诺塔 Hanoi tower

1. 介绍：
	- https://www.mathsisfun.com/games/towerofhanoi.html



2. 原理
	- 如果只有一个要移动的盘，那直接A -> C
	- 否则，将A上的盘视作两部分，最底下的一个为一部分，上面的其他所有盘为另一部分。执行以下操作：
		- 将上面所有盘A->B
		- 将最底下的盘A->C
		- 再将上面所有盘B->C
	- 注意，这里的A、B、C是变量名，不是指三座塔的名称。从A移动盘子到C，可以是在任意两座塔之间，而剩余的第三座塔B作为中转塔使用



3. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/divide_and_conquer/HanoiTower.java



# 第14章：动态规划

## 动态规划 dynamic programming

1. 介绍
	- 该方法的核心思想：将大问题分为小问题进行解决，从而一步步获取最优解的处理方法
	- 动态规划与分治的不同之处在于：
		- 分治的子问题是相互独立的
			- 在动态规划中，下一个子阶段的求解是建立在上一个子阶段的解的基础上的，从而进行进一步的求解
	- 动态规划通过**填表**的方式逐步推进，得到最优解



## 背包问题 knapsack problem

1. 介绍
	- 背包问题指：给定一个**容量固定**的背包、若干个具有一定重量和价值的物品，如何选择物品放入背包，在**不超过背包容量**的前提下，使背包中的**物品价值最大**。
	- 输出通常为物品的最大价值
	- 背包问题又分为01背包和无限背包，前者指每件物品最多放一个，后者指每件物品有无限个可以放



2. 例子——问题
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204220935543.png" alt="image-20220422093556440" style="zoom:70%;" />
	- 这是个01背包



3. 原理：

	- 假设总共有`n`个物品，第`i`个物品的重量和价值分别为`w[i]`和`v[i]`，背包的容量为`c`

	- `ans[i][j]`表示当背包容量为`j`时，在前`i`个物品中选择，放入背包使得价值最大。其中，$i \in \set{0,1,...,n}$，$j \in \set{0, 1, ...,c}$

	- 如何求得`ans[i][j]`：

		1. 如果`w[i] > j`，即第`i`个物品的重量超过背包的容量，那么`ans[i][j] = ans[i - 1][j]`——即使有`i`个物品可选，第`i`个物品是肯定无法放进当前背包的，等效于只有`i - 1`个物品可选

		2. 如果`w[i] <= j`，有两种选择：
			- :one:不考虑第`i`个物品，从前`i - 1`个物品中挑选，使容量为`j`的背包价值最大，即`ans[i - 1][j]`
			- :two:选择第`i`个物品，那么当前背包剩余的容量为`j - w[i]`，再从前`i - 1`个物品中挑选，使得容量为`j - w[i]`的背包价值最大，两者的价值相加，得`v[i] + ans[i - 1][j - w[i]]`
			- 选择:one:和:two:中的较大值即可

	- 边界条件：`ans[i][0] = ans[0][j] = 0`



4. 例子——解答
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204220935543.png" alt="image-20220422093556440" style="zoom:70%;" />
	
	- | `ans[i][j]` | `j = 0` | `j = 1` | `j = 2` | `j = 3` | `j = 4` |
		| ------- | ---- | ---- | ---- | ---- | ------- |
		| `i = 0`                    | 0       | 0       | 0       | 0       | 0       |
		| `i = 1` ：吉他             | 0       | 1500    | 1500    | 1500    | 1500    |
		| `i = 2` ：吉他、音响       | 0 | 1500 | 1500 | 1500 | 3000 |
		| `i = 3` ：吉他、音响、电脑 | 0 | 1500 | 1500 | 2000 | 3500 |
		
	- 这张表应该**按行**来填



5. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/dynamic_programming/KnapsackProblem.java



# 第15章 字符串匹配



## KMP算法

1. 引入：

	- 需求：进行字符串匹配，已知`s`、`target`，求`target`在`s`中的索引，不存在则返回`-1`

	- 一种解决方法——暴力匹配：

	- ```java
			public static int find(String s, String target) {
		        int n1 = s.length();
		        int n2 = target.length();
		        if (n2 > n1) return -1;
		
		        for (int i = 0; i <= n1 - n2; i++) {
		            if (s.charAt(i) != target.charAt(0))
		                continue;
		            int j = 0;
		            for (; j < n2; j++) {
		                if (s.charAt(i + j) != target.charAt(j)) break;
		            }
		            if (j == n2) //匹配成功
		                return i;
		        }
		
		        return -1;
		    }
		```

	- 如果`target = "ababa"`，`s="abaababbbbabababa"`，那么每次匹配失败都会从头开始匹配，不管当前匹配是部分成功，还是完全失败（两者明显有区别）。由此造成了这种暴力匹配的低效率



2. 原理

	- 要在`text`中查找`pattern`

	- 主要分为两步：
		- :one:根据`pattern`构建LPS数组（这一步与`text`无关）
		- :two:利用LPS数组在`text`中高效地进行查找

	- 参考这个视频：https://www.bilibili.com/video/BV18k4y1m7Ar
	- 或者原视频：https://www.youtube.com/watch?v=GTJr8OvyEVQ



3. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/KMP.java
	- 写得时候思路并不清晰，有空再尝试自己写一次



# 第16章 贪心算法

## 贪心算法 greedy algorithm

1. 介绍
	- 贪心算法指对问题求解时，在**每一步**选择中都采取**当前最优**的选择，从而**希望**取得**结果最优**的选择
	- 贪心算法取得的结果**不一定是最优解**。如果不是，该结果也是**近似最优解**



## 集合覆盖问题 Set Covering Problem, SCP

1. 介绍

	- > 给定全集U，以及一个包含n个集合且这n个集合的并集为全集U的集合S 。集合覆盖问题要找到S的一个最小的子集，使得它们的并集等于全集U。——百度百科

	- “这n个集合的并集为全集U”保证了这个问题有解

	- “最小的子集”是指子集中的集合数量最小

	- 这个问题是NP问题——不存在多项式时间的解，即求出最优解的时间复杂度为$O(2^n)$，其中`n`为问题规模——所以贪心算法解SCP只是求近似最优解，但是效率更高



2. 例子
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204221501445.png" alt="image-20220422150113300" style="zoom:50%;" />



3. 原理：
	- :one:：遍历所有广播台，找到一个覆盖了**最多未覆盖地区**的广播台
	- :two:：将这些地区标记为已覆盖
	- :three:：重复:one:，直至所有地区都被覆盖



4. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/greedy_algorithm/SetCoveringProblem.java



# 第17章：最小生成树 minimum spanning tree

1. 引入：修路问题
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204221735466.png" alt="image-20220422173526305" style="zoom:50%;" />
	- `A`至`G`表示七个村庄，边表示村庄之间的距离
	- 现在需要修路，使这7个村庄**连通**，如何修路才能使总里程最短？
	- 连通：connected，是图的概念，即两个节点之间存在一条路径，不一定是相邻



2. 最小生成树
	- 修路问题本质就是最小生成树问题，minimum spanning tree
	- 概念：给定一个带权的无向连通图，选取一棵生成树，**包含图中所有顶点**，且使得树上所有边的**权重之和最小**
	- 如果图中有`n`个顶点，只要选出图中的`n - 1`条边，就能成为一棵树
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204221742496.png" alt="image-20220422174239401" style="zoom:50%;" />
	- 求出最小生成树的算法有：**Prim算法和Kruskal算法**




## Prim算法



1. 原理
	- 从任意点出发。查询所有距离当前的树的节点中距离最小的那个节点，将它加入当前树。不断重复此过程，直至把`n`个点都加入树。
	- Starting from any vertex in the graph, treat it as a tree, repeat the following process until all vertices are included in the MST: include a vertex into the current tree, whose distance to some vertex in the current tree is smallest among all the vertices not included into the current tree



2. 例子
	-  <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204221735466.png" alt="image-20220422173526305" style="zoom:50%;" />
	-  从`A`出发，当前与树相邻的边有`AB = 5, AG = 2, AC = 7`，其中`AG`最小，则把`G`加入当前树
	-  现在树中节点为`A`、`G`，当前与树相邻的边有`AB = 5, AC = 7, BG = 3, EG = 4, GF = 6`，其中`BG`最小，则把`B`加入树中
	-  以此类推。最终，MST的边为AG, BG, EG, EF, DF, AC，总权值之和为25  



3. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/minimum_spanning_tree/Prim.java



## Kruskal算法

1. 原理：
	- 将边按照权值从小到大进行排序
	- 选出`n - 1`条边，且这些边不构成回路
		- 判断是否构成回路的方法：
		- 让每棵树有一个终点，终点可以是这棵树的任意一个节点
		- 一开始，每个节点都是自己这棵树的唯一节点，因为也是终点
		- 如果两个节点所在树的终点相同，那么连接这两个节点后，树会出现回路，:x:
		- 如果两个节点所在树的终点不同，那么连接这两个节点后，结果还是一棵树
2. 例子
	-  <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204221735466.png" alt="image-20220422173526305" style="zoom:50%;" />
	-  按边的大小一次选择AG（2）、BG（3）、EG（4）、DF（4）
	-  AB（5）不能选，因为A和B已经在一棵树中，选择则会构成回路
	-  选择EF（5）
	-  同理，GF（6）不能选
	-  选择AC（7）
	-  MST完成



3. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/minimum_spanning_tree/Kruskal.java
	- 可以使用并查集优化代码，以判断是否构成回路







# 第18章 最短路径 shortest path

1. 引入
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204221735466.png" alt="image-20220422173526305" style="zoom:50%;" />
	- 从G出发，我们需要前往其他所有节点，边表示每条路的长度。那么，G到其他各个节点的最短路径是多少？



## Dijkstra算法

1. 原理
	- Dijkstra算法是一种贪心算法，具体做法如下：
	- 假设有`n`个节点，起始点为`G`，记`d[i]`为`G`到第`i`个节点的最短路径长度，`pre[i]`为第`i`个节点到`G`的最短路径上的第一个前驱节点（假如`G`到`A`的最短路径为`G-C-B-A`，那么`pre[A] = B, pre[B] = C, pre[C] = G`）
	- 从`G`出发，由于一开始没有与任何节点形成最短路径，`d[i]`都为正无穷，只有`D[G] = 0`
	- 选取当前**未访问过**的节点中`d[i]`最小的节点
		- 标记其为已访问
		- 对于所有与它相邻的节点，如果`d[i] + edge(i, u) < d[u]`（`u`为任意邻居节点），那么`d[u] = d[i] + edge(i, u)`，使`pre[u] = i`
	- 重复这一过程`n`次

2. 例子
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204221735466.png" alt="image-20220422173526305" style="zoom:50%;" />


3. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/shortest_path/Dijkstra.java





## Floyd算法

1. 介绍
	- Floyd算法是求出一张图中，**每个节点**到其他节点的最短距离
	- 而Dijkstra算法是求出一张图中，**某一个节点**到其他节点的最短距离
2. 原理
	- 设共有`n`个顶点，即`d[i][j]`为顶点`i`到`j`的最短路径长度。`d`的初始值为图的邻接矩阵（不相邻的点用无穷表示距离）
	- 如果`d[i][j]`已经是最小的，那么对于任意一个其他顶点`k`，`d[i][k] + d[k][j] > d[i][j]`
	- 如果`d[i][j]`不是最小的，使用`d[i][k] + d[k][j]`更新`d[i][j]`
	- 需要注意，$i,j,k \in \set{0,1,...,n-1}$
3. 例子
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204221735466.png" alt="image-20220422173526305" style="zoom:50%;" />



4. 代码：https://github.com/el-nino2020/DS-A/blob/main/algorithms/shortest_path/Floyd.java



# EOF

[返回顶部](#序言) 