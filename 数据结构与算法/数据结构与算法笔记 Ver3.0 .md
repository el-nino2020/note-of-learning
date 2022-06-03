[前往最后](#EOF)



# 序言

- 现在是2022年5月9日，我于同一天学习完了MIT 6.006 算法导论的内容。不愧是MIT，让我开始**从根本上去理解**算法，真正地把我领进了门:thumbsup:
- 只是听课并不够，还得自己刷题，正好之前看到了**代码随想录**。代码随想录整理了[力扣](https://leetcode.cn/)的题目，使我能够按照不同的版块刷题，很不错
- 该笔记的目录索引与代码随想录里的一致
- 笔记里记录的题目，有的是我不会做的，也有的是我为了记录当时的想法而写的。
- 代码随想录推荐至少二刷。不论如何，千里之行始于足下，先开始第:one:刷吧
- 第一次做到某题时不会写，这很正常，没必要因此自卑。之后多练几次就可以了:muscle:
- 现在是2022年6月3日，我做完了**单调栈**的第四题：接雨水，这也标志着第:one:刷的结束。:tada:
- 之后应该是要学MIT 算法设计与分析（6.046J）了。继续加油吧:muscle:



# 版本一览

- 这是Ver 3.0，基于[《代码随想录》LeetCode 刷题攻略](https://github.com/youngyangyang04/leetcode-master)，第:one:刷。开始的时间为2022年5月9日，结束于2022年6月3日
- Ver 2.0的笔记在[这里](https://github.com/el-nino2020/note-of-learning/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E7%AC%94%E8%AE%B0%20Ver2.0%20.md)，基于[MIT公开课：6.006算法导论_2020年春季](https://www.bilibili.com/video/BV1sf4y1P7t9)；在MIT的网站上有该课程的所有资料，网站为[这个](https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-spring-2020/)。开始学习的时间为2022年4月23日，结束于2022年5月9日
- Ver 1.0 的笔记在[这里](https://github.com/el-nino2020/note-of-learning/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E7%AC%94%E8%AE%B0%20Ver1.0%20.md)，基于[【尚硅谷】数据结构与算法（Java数据结构与算法）](https://www.bilibili.com/video/BV1E4411H73v)



# 目录

[toc]





# 数组

## 2. 二分查找

- 二分查找的前提是数组有序

- 如果要二分查找元素的索引，需要确保元素唯一

- 代码方面：

	- ```java
		mid = left + (right - left) >> 1; //防止整数溢出
		```

	- ```java
		while(left <= right){//注意 = 号
		    if(...){
		        left = mid + 1;//注意 + 1
		    }else if (...){
		        right = mid - 1;//注意 - 1
		    }else{
		        ...
		    }
		}

## 5. 滑动窗口

- 两道类似的题目没有做



## 6. 循环矩阵

- 类似题的代码不能一遍过，需要debug



# 链表

## 技巧

- 链表题，使用**虚拟头结点**会方便很多，可以省去不必要的麻烦

## 7.链表相交

https://leetcode.cn/problems/intersection-of-two-linked-lists-lcci/

<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205110838261.png" alt="image-20220511083831128" style="zoom: 50%;" />

1. 思路
	- 求出两条链表的长度
	- 根据长度，将长的链表与短的对齐，具体来说，将链表`B`的头结点变更为`b2`
	- 两条链表同时遍历，不停的指向各自链表中下一个节点。如果两个节点地址相同，则说明该节点是链表相交的第一个节点



## 8.环形链表II

https://leetcode.cn/problems/linked-list-cycle-ii/

<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205110909604.png" alt="image-20220511090951506" style="zoom:50%;" />

1. 思路：
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205110913360.jpg" alt="扫描全能王 2022-05-11 09.10" style="zoom: 33%;" />
	- 简单来说，如果链表存在环，那么快慢指针第一次相交的点`11`与环的入口`4`的距离d~1~等于链表起点`1`与环的入口`4`的距离d~2~



# 哈希表

## 9. 三数之和

<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205120946232.png" alt="image-20220512094608121" style="zoom:50%;" />

1. 思路：
	- 双指针法
	- 先对原数组进行排序
	- 排序后，令$i\in \set{0,...,n-1}, left = i + 1,right = n-1$，记`a = nums[i], b = nums[left], c = nums[right]`
	- $\forall a $，如果`a + b + c == 0`，则为一组答案；如果`a + b + c > 0`，则`b`过大，`right`减小`1`；否则`left`增加`1`
	- 由于元素可能重复，所以在`i`、`left`、`right`变化时需要跳过重复的元素
	- 总时间复杂度为$O(n^2)$
	- :eight_spoked_asterisk:这道题如果使用哈希表，在去重时很麻烦



## 10. 四数之和

1. 思路
	- 和[三数之和](9. 三数之和)一样，都是排序 + 双指针，只不过多了一层外循环



# 字符串

## 5. 左旋转字符串

<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205121308553.png" alt="image-20220512130809411" style="zoom: 50%;" />

1. 思路
	- 先反转前`k`个字符，得到`ba|cdefg`
	- 再反转后`n - k`个字符，得到`ba|gfedc`
	- 最后整体反转，得`cdefg|ab`
	- 时间复杂度为`O(n)`，空间复杂度为`O(1)`
	- :bulb:局部反转 + 整体反转 ，这两个组合起来用，是一种技巧。我掌握得并不好



## 6. KMP算法

1. 例子（记住这两个例子，方便推导和验证）

	- | 编号 | 原串`s`       | 子串`t`   | LPS                     |
		| ---- | ------------- | --------- | ----------------------- |
		| 1    | `aabaabaaf`   | `aabaaf`  | `[0, 1, 0, 1, 2, 0]`    |
		| 2    | `aabaaabaaac` | `aabaaac` | `[0, 1, 0, 1, 2, 2, 0]` |

2. 求出子串`t`的LPS——最长相等前后缀数组

	- 使用双指针`i`和`j`，`i`指向当前前缀数组最后一个字符，`j`指向当前最长前后缀长度的索引——太难表达了:fu:
	- :one:如果`t[i] != t[j]`，令`j = lps[j - 1]`，不断重复:one:，直至`j == 0`或`t[i] == t[j]`
	- :two:判断`t[i]` 与`t[j]`是否相等，如果相等`j++`
	- :three:令`lps[i] = j`
	- `i`从`1`开始不断增大，并不断重复上述步骤。`i = 0`时，`lps[i] = 0`，这需要单独写成一句话

3. 使用LPS参与字符串匹配

	- 使用双指针`i`和`j`，`i`指向`s`，`j`指向`t`
	- 不断重复以下过程，直至`i`走到`s`末尾（匹配失败:x:）或`j`走到`t`末尾（匹配成功:o:）
		- 如果`s[i] == t[j]`，则`i`与`j`都递增
		- 如果两者不相等
			- 如果`j != 0`，可以利用`lps`的前缀信息，令`j = lps[j - 1]`（`i`不需要增加）
			- 否则，两字符串需要从头开始匹配，这时，`i`需要递增`1`



## 7. 重复的子字符串

- 想复杂了，原因在于对于KMP算法中的LPS理解不到位



# 栈与队列

## 3. 用队列实现栈

1. 思路：
	- 每一次执行`poll`，等效于将队列中前`n - 1`个元素取出、再放入队列，这样原先最晚加入的元素处于能够操作的位置，弹出即可
	- 时间复杂度为`O(n)`，不能更快了

## 7. 滑动窗口最大值

<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205141349572.png" alt="image-20220514134937452" style="zoom:50%;" />

1. 思路：
	- 设计如下的单调队列：（单调递减）
		- `push(val)`：试图向单调队列中添加元素
			- 如果`val`比队尾元素大，则弹出队尾元素。不断重复此过程，然后加入`val`
		- `pop(val)`：试图从单调队列中弹出元素
			- 如果队首元素等于`val`，则弹出队首元素；否则无事发生
		- `max()`：返回队列中最大的元素，由于队列是单调递减的，返回队首元素即可
	- 使用该单调队列，每次滑动窗口移动，对变化的元素调用`push`和`pop`方法，并将`max()`的值存入`ans`



# 二叉树

## 3. 二叉树的迭代遍历

1. 前序遍历

	- ```java
		public List<Integer> preorderTraversal(TreeNode root) {
		    List<Integer> ans = new ArrayList<Integer>();
		    Stack<TreeNode> stk = new Stack<>();
		    stk.push(root);
		    TreeNode ptr;
		    while(!stk.empty()){
		        ptr = stk.pop();
		        if(ptr == null) continue;
		        ans.add(ptr.val);
		        stk.push(ptr.right);//栈是后进后出，所以先存入右子节点
		        stk.push(ptr.left);
		    }
		    return ans;
		}
		```



2. 中序遍历

	- 由于当前节点晚于其左子树被遍历，要把所有左子节点存入栈中

	- ```java
		public List<Integer> inorderTraversal(TreeNode root) {
		    List<Integer> ans = new ArrayList<Integer>();
		    if (root == null) return ans;
		
		    Stack<TreeNode> stk = new Stack<>();
		    //从根节点开始的所有左子节点存入栈中
		    while (root != null) {
		        stk.push(root);
		        root = root.left;
		    }
		
		    while (!stk.empty()) {
		        TreeNode ptr = stk.pop();//当前节点的左子树已经被遍历完毕
		        ans.add(ptr.val);
		        ptr = ptr.right;
		        //将右子树的所有左子节点存入栈中
		        while (ptr != null) {
		            stk.push(ptr);
		            ptr = ptr.left;
		        }
		    }
		    return ans;
		}
		```



3. 后序遍历

	- 没有办法直接使用迭代实现后序遍历，使用以下方法：

	- 前序遍历的顺序是：**中左右**；代码稍加修改，就成了：**中右左**。将存放结果的列表翻转，即**左右中**，正好是后序遍历的结果

	- ```java
		public List<Integer> postorderTraversal(TreeNode root) {
		    List<Integer> ans = new ArrayList<>();
		    Stack<TreeNode> stk = new Stack<>();
		    stk.push(root);
		
		    while (!stk.empty()){
		        root = stk.pop();
		        if(root == null) continue;
		        //中、右、左
		        ans.add(root.val);
		        stk.push(root.left);
		        stk.push(root.right);
		    }
		    Collections.reverse(ans);//反转结果集
		
		    return ans;
		}
		```



## 6. 翻转二叉树

- 对二叉树进行镜像翻转
- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205161102232.png" alt="image-20220516110219113" style="zoom:50%;" />

1. 思路：
	- 使用前序遍历
	- 每次递归，交换当前节点的左右子节点，再对左右子节点调用该函数
	- 递归结束的条件是当前节点为`null`



## 11. 完全二叉树的节点个数

- 题目：给一棵完全二叉树的根节点，求其中有多少个节点
- https://leetcode.cn/problems/count-complete-tree-nodes/

1. 不考虑完全二叉树的性质，直接写代码：

	- ```java
		public int countNodes(TreeNode root){
		    return root == null ? 0 :　1 + countNodes(root.left) + countNodes(root.right);
		}
		```

	- 时间复杂度为`O(n)`



2. 考虑完全二叉树：
	- 完全二叉树的性质如下：
		- 其左右子树也是完全二叉树
		- 完全二叉树要么是一棵完美二叉树；要么除了最后一层的所有节点靠左连续以外，是一棵完美二叉树
	- 因此，完全二叉树的以某些节点为根节点的子树是完美二叉树：
		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205161925956.png" alt="image-20220516192507794" style="zoom:50%;" />
	- 利用该性质，代码思路如下：
		- 设当前节点为`root`，令`cur = root`，不断执行`cur = cur.left`直到`cur`为`null`，求出通向最左的路径长度，即为左子树的高度；同理可以求出通向最右的路径长度（这个长度不一定是右子树的高度）。
		- 如果两者相等，说明以`root`为根节点的树为完美二叉树。根据公式，假设这棵树高度为`h`，则其节点数量为$\sum_{i = 0}^{h - 1}{2^i} = 2^h-1$。直接返回该结果即可
		- 如果两者不等，使用`1 + countNodes(root.left) + countNodes(root.right)`，递归地调用该函数
	- 时间复杂度：
		- 在每轮递归中，求出左右路径的长度，花费$O(log(n))$
		- 对于不是完美二叉树的子树来说，每轮递归，其左子树一定是完美二叉树。因而每棵子树都有一半的节点可以通过公式直接算出来。故递归深度为$O(log(n))$
		- 总的时间复杂度为$O(log^2(n))$



## 19. 从后序和中序遍历构造二叉树

1. 题目
	- https://leetcode.cn/problems/construct-binary-tree-from-inorder-and-postorder-traversal/
	- 给你两个数组，`inOrder`和`postOrder`，返回由这两个遍历顺序确定的二叉树的根节点

2. 思路：

	- 以这棵树为例：

		- ```
					1
				  /    \
				 2	    3
			    / \     / \
			   4   5   6   7
			```

		- `inOrder = [4, 2, 5, 1, 6, 3, 7]`

		- `postOrder = [4, 5, 2, 6, 7, 3, 1]`

	- 由于后序遍历是左右中，**从后往前**遍历`postOrder`，每个子树的根节点的父节点一定已经出现过

	- 对于节点`1`，它在`inOrder`中的位置将`inOrder`分为了两部分，左边是它的左子树，右边是它的右子树

	- 对于节点`3`，它位于`inorder`中`1`的右边，故是`1`的右子节点

	- 对于节点`6`，它位于`inorder`中`3`的左边，故是`3`的左子节点

	- 同理可构造出树的剩余部分



3. 代码：
	- 令全局变量`pos`代表当前元素在`postOrder`中的索引，故`pos`不断减小
	- 定义递归函数`TreeNode recur(int left, int right)`，其中`[left, right]`代表`postOrder[pos]`——即当前节点在`inOrder`中应该出现的位置
	- 如果实际的位置（记为`i`）不在`[left, right]`中，说明当前子树已经构造完毕，`postOrder[pos]`代表另一棵子树的根节点。停止递归。
	- 如果实际的位置在`[left, right]`中，则创建该节点`node`，同时`pos--`
	- 递归地调用该函数，即：
		- `node.right = recur(i + 1, right)`
		- `node.left = recur(left, i - 1)`
	- 最后返回`node`即可
	- 注意，先创建`node.right`是因为后序遍历为左右中，**中**之前是**右**，而不是**左**
	- 快速查找`postOrder[pos]`在`inOrder`中的位置可以使用哈希表



4. 另一道题
	- 从前序遍历和中序遍历构造二叉树
	- https://leetcode.cn/problems/construct-binary-tree-from-preorder-and-inorder-traversal/
	- 思路和本题相同，只不过`pos`不断递增，且先创建`node.left`
	- 中序遍历在这里的作用是分割二叉树的左右子树，它对于构建二叉树是必须的。如果使用前序和后序来构造二叉树，则结果不唯一



## 27. 最近公共祖先

1. 题目
	- https://leetcode.cn/problems/lowest-common-ancestor-of-a-binary-tree/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205180804372.png" alt="image-20220518080438193" style="zoom: 50%;" />



2. 思路：
	- 采用自底向上的递归方式——后序遍历
	- :one:如果当前节点为`null`，或者等于`p`或`q`，则返回当前节点
	- :two:对当前节点的子节点调用该函数，结果记为`leftAns`、`rightAns`
	- :three:如果任意结果为空，则返回另一个结果 
	- :four:如果`(leftAns == p && rightAns == q) || (leftAns == q && rightAns == p)`，则返回当前节点
	- :five:否则返回`null`
	- :eight_pointed_black_star:一些解释：
		- :three:的情况为`p`和`q`的最近公共祖先为它们其中的一个，即一个节点是另一节点的祖先。也考虑到当前子树不存在`p`和`q`的情况
		- :four:的情况为当前节点是`p`和`q`的最近公共祖先。对于该节点的父节点来说，其另一个子节点调用递归函数的结果一定是`null`，故会一直返回当前节点



# 回溯算法

## 1. 理论基础

1. 什么是回溯法？
	- 回溯搜索法，是一种搜索方式
	- 它的本质是穷举所有可能性，来解决一些困难的问题。
	- 因为是brute force，就算可以使用剪枝技巧来优化，仍然很消耗时间



2. 理解回溯算法
	- 使用回溯法解决的问题都可以**抽象**为树结构
	- ![image-20220518111406731](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205181114876.png)
	- 原问题的大小决定树的宽度；递归的深度即是树的高度



3. 回溯法模板

	- ```c++
		void backtracking(参数) {
		    if (终止条件) {
		        存放结果;
		        return;
		    }
		
		    for (选择：本层集合中元素（树中节点孩子的数量就是集合的大小）) {
		        处理节点;
		        backtracking(路径，选择列表); // 递归
		        回溯，撤销处理结果
		    }
		}
		```

	- 其中，for循环是操作同层元素，而递归是进入下一层



## 8. 组合总和 II	

1. 题目
	- https://leetcode.cn/problems/combination-sum-ii/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205190925506.png" alt="image-20220519092534373" style="zoom: 50%;" />



2. 思路：
	- 这题的难点在于去重：结果集中的每一个集合中的元素可以有重复，但集合之间不能重复
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205190935989.png" alt="image-20220519093527787" style="zoom:50%;" />
	- 在同一层循环中跳过重复的元素，但在层与层之间不跳过
	- 本质是让重复的元素只出现在`startIndex`的位置上，从而在层与层之间只会被遍历一次，不会造成重复



## 9. 分割回文串

1. 题目
	- https://leetcode.cn/problems/palindrome-partitioning/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205191043840.png" alt="image-20220519104342688" style="zoom: 50%;" />



2. 思路：
	- 本质是个组合问题，只不过使用隔板法。横向遍历的是新的板子的位置
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205191045021.png" alt="image-20220519104557802" style="zoom:50%;" />



## 15. 求全排列

1. 还是按照回溯的模板写代码
2. 由于排列要求每一层在剩余的元素中不断选取，且每层各子问题的大小是相等的，所以使用`boolean[] used`数组来判断元素是否被使用较为方便
3. <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205191528581.png" alt="image-20220519152845389" style="zoom:50%;" />





# 贪心

## 1. 理论基础

- 贪心**没有固定的模板**，如果不会使用严谨的数学推导，那就用:one:感觉（尝试） + :two:能否举反例的方式来**尝试**用贪心解题，无法通过再换别的方法
- 贪心的基本步骤为求出子问题的最优解，从而达到全局最优解



## 3. 摆动序列

1. 题目
	- https://leetcode.cn/problems/wiggle-subsequence/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205201128772.png" alt="image-20220520112824664" style="zoom:50%;" />



2. 思路
	- 摆动序列，直观来说，数组的值要不断地相对变大和变小，从而在画图时呈现出**峰谷不断交替**（峰谷之间不能有中间节点）的情形
	- **摆动序列的长度即为峰谷数量之和**。
	- 而**最长**摆动子序列的长度就等于**原数组中峰谷数量之和**，因为不可能有更多的峰或谷了。故只要数原数组中的峰谷数量即可
3. 例子
	- 以`[1,17,5,10,13,15,10,5,16,8]`为例
	- ![image-20220520114010086](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205201140169.png)
	- 原数组峰谷的总数为`7`，最长子序列的长度也为`7`



## 12. 分发糖果

1. 题目
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205211251912.png" alt="image-20220521125105792" style="zoom:50%;" />
	- https://leetcode.cn/problems/candy/



2. 思路
	- 每次只考虑元素的单边是否大于的情况（局部最优），这样两次遍历就能求出答案
	- 先给每个孩子`1`个糖果，即$\forall i \in n$，`sweets[i] = 1`
	- 从左向右遍历，如果`ratings[i] > ratings[i - 1]`，则`sweets[i] = sweets[i - 1] + 1`
	- 再从右向左遍历，如果`ratings[i] > ratings[i + 1]`，则`sweets[i]`的可能值为`sweets[i]`，或者`sweets[i + 1] + 1`，取最大值即可



## 14. 按照身高重建队列

1. 题目
	- https://leetcode.cn/problems/queue-reconstruction-by-height/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205211717745.png" alt="image-20220521171720651" style="zoom:50%;" />
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205211718044.png" alt="image-20220521171811935" style="zoom:50%;" />



2. 思路
	- 题目有两个维度，应**每次解决一个维度**。尝试两个维度一起解决只会顾此失彼、得不偿失
	- 先对`people`按身高`h`从大到小排序，如果相同，则按`k`从小到大排序
	- 排序后，位于`i`的人前面有`i - 1`个身高比他高的人（即**全都比他高**），且$h_i \le i - 1$
	- 对`people`使用插入排序的方法，将第`i`个人插入索引$h_i$处——根据定义，这个人的前面应该有$h_i$个人
	- 由于先插入的是`h`较大的元素，插入完毕后，对于其后元素来说，前面的元素依旧比它大。故这么做是正确的



## 22. 单调递增的数字

1. 题目
	- https://leetcode.cn/problems/monotone-increasing-digits/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205231100769.png" alt="image-20220523110009622" style="zoom:50%;" />



2. 思路：
	- 从后往前遍历数字`n`的每一位，
	- 如果$w_{i - 1} > w_{i }$，则$w_{i -1}$不满足要求，将$w_{i -1}$减去`1`，并将`n[i : ]`全部置为`9`
	- 由于这样的$i$可能**不止一个**，只需要记录最小的$i$，并在遍历完后将`n[i : ]`置为`9`即可



## 23. 买卖股票的最佳时机（含手续费）

1. 题目
	- https://leetcode.cn/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205231337319.png" alt="image-20220523133754187" style="zoom:50%;" />

2. 思路
	- 和[买卖股票的最佳时机 II](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock-ii/)的基本思路一样，从前往后遍历
	- 使用`min`记录股票买入的价格
	- 如果`prices[i] < min`，则`min = prices[i]`
	- 又如果`prices[i] - fee < min`，不需要卖出——因为是亏的
	- 否则，`ans += prices[i] - fee - min`，同时`min = prices[i] - fee`——如果以后才真正卖出股票，相当于提前支付了`fee`



3. 代码

	- ```java
		class Solution {
		    public int maxProfit(int[] prices, int fee) {
		        int n = prices.length;
		        int min = prices[0], ans = 0;
		
		        for (int i = 1; i < n; ++i) {
		            if (prices[i] < min){
		                min = prices[i];
		            } else if (prices[i] - fee < min) {
						//无事发生
		            } else {
		                ans += prices[i] - min - fee;
		                min = prices[i] - fee;
		            }
		        }
		        return ans;
		    }
		}
		```





# 动态规划

## 1.理论基础

1. 动规的五部曲：
	1. 确定`dp`数组以及下标的含义——定义子问题
	2. 确定递推公式
	3. `dp`数组如何初始化——初始条件
	4. 确定遍历顺序——拓扑顺序
	5. 举例推导`dp`数组——检验是否正确



## 8. 整数拆分

1. 题目
	- https://leetcode.cn/problems/integer-break/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205240958584.png" alt="image-20220524095852444" style="zoom:50%;" />



2. 思路
	- 令`dp[i]`为正整数`i`拆分后乘积的最大值
	- $\forall i \in [n]$，有如下等式：
		- $\forall j \in \set{1,2,...,i - 1}, dp[i] = max\set{j \times (i - j),j \times dp[i - j],dp[i]}$（`dp[i]`初始值为`0`）
		- 对于$\forall i$，我们至少要把它拆分成两个整数，即`j`和`i - j`，如果`j * (i - j)`大，我们选择该结果。否则，继续拆分`i - j`。按照遍历顺序，我们已经得出了`dp[i - j]`，即`i - j`拆分后乘积的最大值，直接使用该结果即可
		- 由于不知道具体怎么拆分，需要依次遍历所有小于`i`的值
	- 初始条件，照理说应该为`dp[2] = 1`，因为按照题意，`n`至少要拆分为两个正整数。但令`dp[1] = 1`也无妨，满足递归式即可
	- 时间复杂度为$O(n^2)$



## 9. 不同的BST

1. 题目
	- https://leetcode.cn/problems/unique-binary-search-trees/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205241542837.png" alt="image-20220524154209720" style="zoom:50%;" />



2. 思路
	- 上图的示例1可以提示解题思路
	- 定义子问题为：$\forall i \in [n]$，`dp[i]`为有`i`个节点的BST的种数
	- 如果一棵树有`n`个节点，则可以依次选择$1,2,...,n$作为BST的根节点
	- 假设根节点为$k,k\in[n]$，则其左子树有`k - 1`个节点，右子树有`n - k`个节点——BST的性质。这棵以`k`为根节点的BST的种数为`dp[k - 1] * dp[n - k]`，即左子树的种数与右子树的种数相乘——简单的排列组合
	- 故，$dp[i] = \sum_{k = 1}^{i} (dp[k -1] \times dp[i-k])$
	- `i`从小到大遍历即可



## 12. 01背包 滚动数组

1. 使用二维数组实现01背包
	- 子问题：从前`i`个物品中选取，背包的容量为`j`，`dp[i][j]`为此时最大的容量
	
	- 递归式如下：
	
	- $dp[i][j] = \begin{cases}dp[i - 1][j], w[i] >j　\\ max\set{dp[i - 1][j],dp[i - 1][j - w[i]]+v[i]} ,w[i] \le j \end{cases} $
	
	- 初始条件为`dp[i][0] = 0`，即背包容量为`0`时价值为`0`；且$\forall j \ge w[0], dp[0][j] = v[0]$，即只选取索引为`0`的物品时，仅当背包容量大于等于该物品的重量才能放下。初始化第一行是为了满足递归式中的`i - 1`
	
	- 遍历顺序有两种
	
		1. ```java
			for (int i = 1; i < w.length; i++) {
			    for (int j = 1; j <= capacity; j++) {
			        递归式
			    }
			}
			```
	
		2. ```java
			for (int j = 1; j < capacity; j++) {
				for (int i = 1; i < w.length; i++) {
			        递归式
			    }
			}
			```



2. 使用一维数组（滚动数组）实现01背包

	- 假设$j >= w[i]$，则递归式可以写成$dp[i][j] = max\set{dp[i - 1][j],dp[i - 1][j - w[i]]+v[i]}$:eight_spoked_asterisk:

	- 我们采用上述第一种遍历顺序:eight_pointed_black_star: 。由于`i`从小到大遍历，在遍历完内层循环的`j`后，`dp[i - 1]`记录了前一层的信息。注意到递归式只使用到了`i - 1`，可以将`dp[i]`记录在同一个数组上

	- 即$dp[i][j] = max\set{dp[i][j],dp[i][j - w[i]]+v[i]}$——该递归式的前提是`i`不断变大。没有这个前提，这个递归式是错误的。

	- 省略递归式中的`dp`的行索引`i`，得$dp[j] = max\set{dp[j],dp[j - w[i]]+v[i]}$

	- 此时需要将遍历顺序改为：

		- ```java
			for (int i = 1; i < w.length; i++) {
			    for (int j = capacity; j >= 1; j--) {
			        dp[j] = Math.max(dp[j], dp[j - w[i]] + v[i]);
			    }
			}
			```

	- 如果`j`依旧从小到大遍历，则`dp[j - w[i]]`使用的实际是`dp[i][j - w[i]]`，而非`dp[i - 1][j - w[i]]`。故这么做是错误的

	- :eight_pointed_black_star:也不能采取二维数组时的第二种遍历方式，即外`j`内`i`。因为$\forall j$，`i`遍历一遍，容量为`j`的背包最多只放入了一个物品
	
	- :eight_spoked_asterisk:$dp[i][j] = dp[i - 1][j],j <w[i] $的情况比假设的情况简单，为了表述方便，不特别表述





## 13. 分割等和子集

1. 题目
	- https://leetcode.cn/problems/partition-equal-subset-sum/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205251026911.png" alt="image-20220525102615783" style="zoom:50%;" />



2. 思路
	- 题目的另一种表述：令$sum = \sum_i nums[i]$，则`nums`中是否存在这样一些元素，其和等于`sum / 2`



3. 我自己的思路：
	- 子问题：`dp[i][j]`为在$nums[0],nums[1],..,nums[i]$中选择一些元素，这些元素的和能否为`j`，故`dp[i][j]`的类型为`boolean`
	- 递推式：
		- 如果`dp[i - 1][j] == true`，则`dp[i][j] = true`，即不选择`nums[i]`，且`dp[i][j + nums[i]] = true`，即选择`nums[i]`
		- 另外，`dp[i][nums[i]] = true`
	- 拓扑顺序：从小到大遍历`i`和`j`，`i`是外循环
	- 结果：$OR \set{dp[0][sum/2],dp[1][sum/2],...,dp[n][sum/2]}$

4. 应用01背包的思路：
	- 原问题转化：一共有`nums.length`个物品，第`i`个物品的重量为`nums[i]`，其价值为`nums[i]`
	- 子问题：`dp[i][j]`为从前`i`个物品中选择，背包容量为`j`时，该背包中物品的最大价值
	- 递归式：$dp[i][j] = max\set{dp[i - 1][j],dp[i - 1][j - nums[i]]+nums[i]}$
	- 由于物品的价值等于其重量，故背包中物品的总价值小于等于背包的容量，即$dp[i][j] \le j$。如果$\exist i, dp[i][sum/2] = sum/2$，则该问题有解
	- :bulb:这题的关键是物品的重量等于其价值



## 14. 最后一块石头的重量

1. 题目
	- https://leetcode.cn/problems/last-stone-weight-ii/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205251856895.png" alt="image-20220525185608767" style="zoom:50%;" />



2. 思路
	- 将这一堆石头分为重量尽可能相近的两堆石头，则最小可能重量等于这两堆石头重量的差值
	- 按照[13. 分割等和子集](#13. 分割等和子集)01背包的思路，其中一堆石头的重量为`dp[n][sum / 2]`，另一堆重量为`sum - dp[n][sum / 2]`，两者的差值即为结果



## 16. 目标和

1. 题目
	- https://leetcode.cn/problems/target-sum/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205260750653.png" alt="image-20220526075048473" style="zoom:50%;" />
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205260751691.png" alt="image-20220526075105571" style="zoom:50%;" />



2. 我自己的思路：
	- 子问题：`dp[i][j]`为在`nums[0 : i]`的每个整数前进行`+`、`-`号的排列，结果为`j`的不同的表达式的数目
	- 递归式：`dp[i][j] = dp[i - 1][j + nums[i]] + dp[i - 1][j - nums[i]]`（不考虑下标越界）
	- 理解递归式是直观的：假如已知`dp[i][j]`，那么对于`nums[i + 1]`，到达`dp[i + 1][j + nums[i]]`和`dp[i + 1][j - nums[i]]`有`dp[i][j]`种方法



3. 应用01背包
	- 假设我们在`nums`中选出这样一些整数，其和为$x$，则另一部分的和为$sum - x$
	- 则$x - (sum - x) = target \Rightarrow x = \frac{target +sum}{2}$:eight_spoked_asterisk:
	- 我们要求出有多少种加减号的排列，使得结果等于`x`
	- 子问题还是：`dp[i][j]`为在`nums[0 : i]`的每个整数前进行`+`、`-`号的排列，结果为`j`的不同的表达式的数目
	- 由于组成`x`的整数前面都是`+`号（:eight_spoked_asterisk:），递归式为：
	- $dp[i][j] = \begin{cases} dp[i - 1][j] , j < nums[j] \\ dp[i - 1][j] + dp[i - 1][j - nums[i]], j \ge nums[j] \end{cases}$





## 18. 完全背包理论

1. 完全背包与01背包
	- 01背包是每个物品最多选一次，完全背包是每个物品选任意次
	- 两者都是求物品总重量不超过背包容量时，背包中物品的总价值最大



2. 递归式：
	- $dp[i][j] = \begin{cases}dp[i - 1][j], w[i] >j　\\ max\set{dp[i - 1][j],dp[i][j - w[i]]+v[i]} ,w[i] \le j \end{cases} $
	- 核心在于$dp[i][j - w[i]]+v[i]$，即复用同一层（`i`相同）的结果，相当于允许多次放入第`i`个物品



3. 滚动数组的代码（完全背包**使用一维数组**，而非二维数组）：

	- ```java
		for (int i = 0; i < weights.length; ++i) {
		    for (int j = weights[i]; j <= capacity; ++j) {//顺序遍历以多次使用第i个物品
		        dp[j] = Math.max(dp[j], dp[j - weights[i]] + values[i]);
		    }
		}
		```



## 19. 零钱兑换II

1. 题目
	- https://leetcode.cn/problems/coin-change-2/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205261359700.png" alt="image-20220526135950560" style="zoom:50%;" />
2. 思路
	- 定义子问题：`dp[j]`为总金额为`j`时硬币组合数
	- 递归式：$dp[j] = \sum \limits_{i } dp[j - coins[i]]$
	- 初始条件：`dp[0] = 1`，即总金额为`0`时硬币只有一种组合：不使用硬币；$\forall i \in[amount], dp[i] = 1$
	- 拓扑顺序：外层遍历`i`，内层遍历`j`，**以形成组合数；否则是排列**



3. 核心代码

	- ```java
		for (int i = 0; i < coins.length; ++i) {
		    for (int j = coins[i]; j <= amount; ++j) {
		        dp[j] += dp[j - coins[i]];
		    }
		}
		```

	- 如果把`i`和`j`循环顺序颠倒，则为求组合数



## 23. 零钱兑换I

1. 题目
	- https://leetcode.cn/problems/coin-change/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205271012400.png" alt="image-20220527101242306" style="zoom:50%;" />

2. 思路
	- 子问题：`dp[j]`为凑足`j`所需要的最少硬币数
	- 递归式：$dp[j] = \min\limits_i dp[j - coins[i]] + 1 = \min\limits_i (dp[j - coins[i]] + 1)$；加不加括号在数学上没有区别，但在写代码上区别很大
	- 初始条件：$dp[0] = 1$，$\forall i \in [amount], dp[i] = \text{Integer.MAX\_VALUE}$
	- 拓扑顺序：先遍历硬币，还是先遍历金额没有区别



3. 核心代码

	- ```java
		for (int i = 0; i < coins.length; ++i) {
		    for (int j = coins[i]; j <= amount; ++j) {
		        if (dp[j - coins[i]] == Integer.MAX_VALUE) //无法凑出j - coins[i]
		            continue;
		        dp[j] = Math.min(dp[j], dp[j - coins[i]] + 1);
		    }
		}
		
		return dp[amount] == Integer.MAX_VALUE ? -1 : dp[amount];
		```





## 	30. 打家劫舍II

1. 题目
	- https://leetcode.cn/problems/house-robber-ii/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205280641169.png" alt="image-20220528064143071" style="zoom:50%;" />



2. 思路
	- 这道题在[打家劫舍I](https://leetcode.cn/problems/house-robber/)的基础上增加了首位房屋相邻的条件
	- 如果准备抢第一个房屋（不一定会抢），就不能抢最后一个。反之亦然。
	- 令求解[打家劫舍I](https://leetcode.cn/problems/house-robber/)的方法为`int solve(int[] nums)`
	- 则本题的答案为`Math.max(solve(nums[0 : n - 2], solve(nums[1 : n - 1])))`



## 35.买卖股票的最佳时机III

1. 题目
	- https://leetcode.cn/problems/best-time-to-buy-and-sell-stock-iii/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205281110661.png" alt="image-20220528111013461" style="zoom: 50%;" />



2. 我自己的思路：
	- 定义子问题：
		- `dp1[i]`为在`prices[0 : i]`中买卖1次股票取得的最大利润
		- `dp2[i]`为在`prices[i : n - 1]`中买卖1次股票取得的最大利润
	- 原问题的答案为$\max\limits_i (dp1[i] + dp2[i])$
	- 时间复杂度：`dp1`和`dp2`都能在$O(n)$时间内求出——两者的解法相似
	- :pencil:注意：这么做的条件是最多完成**两笔**交易。假如交易次数更多，无法在$O(n)$时间内完成



3. 更为正确的思路：
	- 定义子问题`dp[i][j]`：在`prices[0 : i]`中状态为`j`时的最大利润
		- 其中，`j`有以下值：`0`：无操作；`1`：第一次买入股票；`2`:第一次卖出股票；`3`：第二次买入股票；`4`：第二次卖出股票
	- 递归式：
		- $dp[i][0] = dp[i - 1][0]$ 
		- $dp[i][1] = max\set{dp[i-1][1],-prices[i]+dp[i - 1][0]}$
		- $dp[i][2] = max\set{dp[i-1][2],prices[i] + dp[i - 1][1]}$
		- $dp[i][3] = max\set{dp[i-1][3],-prices[i]+dp[i - 1][2]}$——第二次买入要以第一次卖出的股票价格为基准
		- $dp[i][4] = max\set{dp[i-1][4],prices[i] + dp[i - 1][2]}$
	- 初始条件：
	  - `dp[0][0] = 0`
	  - `dp[0][1] = -prices[0]`
	  - `dp[0][2] = 0`
	  - `dp[0][3] = -prices[0]`
	  - `dp[0][4] = 0`
	- 拓扑顺序：从小到大遍历`i`
	- 答案：`dp[n - 1][4]`
	- :pencil:这种写法可以保证如果最多有`k`笔交易，时间复杂度为$O(nk)$——即下一道题的做法[买卖股票的最佳时机 IV](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock-iv/)]



## 34. 买卖股票的最佳时机II

- 注：这里与[第35题](35.买卖股票的最佳时机III)的顺序颠倒并不是写错，只是我在写[第37题](#37. 最佳买卖股票时机含冷冻期)时意识到了这题解法的重要性

1. 题目
	- https://leetcode.cn/problems/best-time-to-buy-and-sell-stock-ii/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205281721375.png" alt="image-20220528172157270" style="zoom:50%;" />



2. 思路
	- 定义子问题：
		- `dp[i][0]`：第`i`天**持有**股票所拥有的最多资金
		- `dp[i][1]`：第`i`天**不持有**股票所拥有的最多资金
	- 递归式：
		- $dp[i][0] = \max\set{dp[i - 1][0],dp[i - 1][1] -price[i]}$
		- $dp[i][1] = \max\set{dp[i - 1][1],dp[i - 1][0] +price[i]}$
	- 初始条件：
		- `dp[0][0] = -price[0]`，`dp[0][1] = 0`



## 37. 最佳买卖股票时机含冷冻期

1. 题目
	- https://leetcode.cn/problems/best-time-to-buy-and-sell-stock-with-cooldown/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205281836038.png" alt="image-20220528183618918" style="zoom:50%;" />



2. 思路
	- 定义子问题：
		- `dp[i][0]`：第`i`天**持有**股票所拥有的最多资金
		- `dp[i][1]`：第`i`天**不持有**股票所拥有的最多资金
	- 递归式：
		- $dp[i][0] = \max\set{dp[i - 1][0],dp[i - 2][1] -price[i]}$——不能使用昨天卖出的价格，因为昨天卖出的话，今天为冷冻期。故使用前天卖出的价格
		- $dp[i][1] = \max\set{dp[i - 1][1],dp[i - 1][0] +price[i]}$
	- 初始条件：
		- `dp[0][0] = -price[0]`
		- `dp[1][0] = Math.max(-price[0], price[1])`
		- `dp[1][1] = Math.max(0, price[1] - price[0])`





## 41. 最长递增子序列

1. 题目
	- https://leetcode.cn/problems/longest-increasing-subsequence/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205300641743.png" alt="image-20220530064127584" style="zoom:50%;" />
	- 这道题其实在MIT 6.006 DP章节讲过



2. 思路
	- 定义子问题：`dp[i]`为以`nums[i]`结尾的最长递增子序列的长度
	- 递归式：$dp[i] = \max\limits_{0\le j<i,nums[j] < nums[i]} dp[j] + 1$，即`i`之前的所有可能（加上`nums[i]`仍旧是递增子序列）的递增子序列中最长的长度加1
	- 理解递归式：由于子序列（subsequence）**不一定是连续的**，所以`dp[i]`要和之前的**所有可能**的子序列进行比较。如果是子数组（subarray），则只要和`dp[i - 1]`比较
	- 初始条件`dp[0] = 1`
	- 答案：$\max\limits_i dp[i]$



## 44. 最长公共子序列

1. 题目
	- https://leetcode.cn/problems/longest-common-subsequence/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205300944501.png" alt="image-20220530094444316" style="zoom:50%;" />

2. 思路：
	- 定义子问题：`dp[i][j]`为`text1[0 : i]`和`text2[0 : j]`的最长公共子序列长度
	- 递归式：
		- $dp[i][j] = \begin{cases}1 + dp[i -1 ][j - 1],text1[i]=text2[j] \\ \max\set{dp[i-1][j],dp[i][j -1]}, text1[i]\neq  text2[j]\end{cases}$
	- 初始条件：（很重要:exclamation: ）
		- 如果`text1[0] = text2[j]`，则`dp[0][j] = 1`，且$\forall k \ge j,dp[0][k] = 1$
		- 即，如果出现一次相等，`dp[0][j]`之后的元素都为`1`
		- 对于`dp[i][0]`同理



## 45. 不相交的线

1. 题目
	- https://leetcode.cn/problems/uncrossed-lines/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205301022811.png" alt="image-20220530102226697" style="zoom:50%;" />
	- 一个例子：
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205301024975.png" alt="image-20220530102401901" style="zoom:50%;" />



2. 思路：
	- 从两个数组中各选出一些元素，使对应元素的连线不能重合。不能重合意味着：选出的元素的**相对位置是固定**的。而子序列的定义是：子序列元素的相对位置与原数组中这些元素的相对位置一致
	- 画出最多的连线即选出最多符合题意的对应元素
	- 分析时，**关注点**应该**在被选出的元素**上，而不是在线上。由此，不难得出以下结论：
	- 这道题是[44. 最长公共子序列](#44. 最长公共子序列)的应用，两者的代码基本没区别





## 48. 不同的子序列

1. 题目
	- https://leetcode.cn/problems/distinct-subsequences/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205301539411.png" alt="image-20220530153952310" style="zoom: 50%;" />
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205301540373.png" alt="image-20220530154011266" style="zoom:45%;" />



2. 我做题时的“思路”

	- 定义子问题：`dp[i][j]`为`s[0 : i]`的子序列中`t[0 : j]`出现的个数

	- 然后就没思路了，按照子问题的定义画出上面两个案例的`dp`数组

		1. `s = "babgbag", t = "bag"`

			- ```pseudocode
				  b a g
				b 1 0 0
				a 1 1 0
				b 2 1 0 
				g 2 1 1
				b 3 1 1
				a 3 4 1
				g 3 4 5
				```

		2. `s = "rabbbit", t = "rabbit"`

			- ```pseudocode
				  r a b b i t
				r 1 0 0 0 0 0
				a 1 1 0 0 0 0
				b 1 1 1 0 0 0
				b 1 1 2 1 0 0
				b 1 1 3 3 0 0
				i 1 1 3 3 3 0
				t 1 1 3 3 3 3
				```

	- 随后观察得到了规律，写出了代码。实际上并没有懂



3. 正确的思路

	- 子问题同样是：`dp[i][j]`为`s[0 : i]`的子序列中`t[0 : j]`出现的个数

	- 递归式：

		- $dp[i][j] = \begin{cases} dp[i - 1][j], s[i] \neq t[j] \\ dp[i - 1][j] + dp[i-1][j - 1],s[i] = t[j] \end{cases}$

	- 理解递归式：

		- 假如`s[i] == t[j]`，以`babgbag`和`bag`中的最后的`g`相匹配为例，
			- 我们可以使用`babgbag`去匹配`bag`，即使用`s[0 : i]`去匹配`t[0 : j]`。由于`s[i] == t[j]`，结果为`dp[i - 1][j - 1]`
			- 我们也可以不使用最后一个`g`，使用`babgba`去匹配`bag`，即使用`s[0 : i - 1]`去匹配`t[0 : j]`，结果为`dp[i - 1][j]`
			- 最终的结果为两者相加——排列组合的知识
		- 如果两者不等，则`s[i]`对于匹配是无用的，结果为`dp[i - 1][j]`

	- 初始条件：

		- 按照子问题的定义填满`dp[i][0]`和`dp[0][j]`即可

		- 使用数学关系式描述较为复杂，这里直接给出代码：

		- ```java
			if (s.charAt(0) == t.charAt(0)) {
			    dp[0][0] = 1;
			}
			
			//求出s[0 : i]中有多少个t[0]
			for (int i = 1; i < m; ++i) {
			    dp[i][0] = dp[i - 1][0];
			    if (s.charAt(i) == t.charAt(0)) {
			        dp[i][0]++;
			    }
			}
			
			//对于j >= 1, dp[0][j] = 0,但由于Java默认初始化为0，不用写
			```





## 50. 编辑距离

1. 题目
	- https://leetcode.cn/problems/edit-distance/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202205310916733.png" alt="image-20220531091648568" style="zoom: 50%;" />



2. 思路：
	- 定义子问题：`dp[i][j]`为将`word1[0 : i]`转换成`word2[0 : j]`所使用的最少操作数
	- 递归式：
		- $dp[i][j] = \begin{cases} dp[i - 1][j - 1], word1[i] = word[j] \\ \min\set{dp[i-1][j - 1],dp[i-1][j],dp[i][j-1]} + 1， word1[i] \neq word2[j] \end{cases}$
	- 对于递归式的理解
		- 如果`word1[i] == word2[j]`，则当前不需要操作
		- 如果使用替换，则将`word1[i]`变为`words2[j]`即可，此时操作数为`dp[i - 1][j - 1] + 1`
		- 如果使用插入，向`word1[i]`之后插入一个等于`words2[j]`的字符，此时操作数为`dp[i][j - 1] + 1`
		- 如果使用插入，将`word1[i]`删除，此时操作数为`dp[i - 1][j] + 1`
		- 以上三者在`word1[i] != word2[j]`情况下取最小即可
		- :bulb:**插入和删除本质上是一样**的，对于`words1[i]`的插入等效于`words2[j]`的删除。对比[两个字符串的删除操作](https://leetcode.cn/problems/delete-operation-for-two-strings/)的递归式即可理解这一点
	- 初始条件
		- 虽然使用原有的子问题分析较为方便，但边界条件的初始化极为复杂，我们将子问题的定义改为**左闭右开**区间：`dp[i][j]`为将`word1[0 : i)`转换成`word2[0 : j)`所使用的最少操作数
		- 原有的**递归式**只要将**改为**`word1[i] == word2[j]` 改为`word1[i - 1] == word2[j - 1]`即可
		- 而初始条件为`dp[i][0] = i`，`dp[0][j] = j`





# 单调栈

## 1. 每日温度

1. 题目
	- https://leetcode.cn/problems/daily-temperatures/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202206011125539.png" alt="image-20220601112505350" style="zoom: 50%;" />



2. 思路
	- 使用单调递减栈来记录比第`i`天温度高的下标
	- 从后往前遍历`temperatures`
		- :one:如果`temperatrues[i]`小于栈顶元素对应的温度，执行:three:
		- :two:否则，不断弹出栈顶元素，直到满足:one:，或者栈为空
		- :three:栈不为空时，使用栈顶元素与`i`的差值更新`ans[i]`
		- :four:将`i`加入栈





## 3. 下一个更大元素II

1. 题目
	- https://leetcode.cn/problems/next-greater-element-ii/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202206011317992.png" alt="image-20220601131741863" style="zoom:50%;" />



2. 思路：
	- 使用单调栈的方式与[每日温度](#1. 每日温度)一样
	- 要先从后往前遍历一遍`nums`，将符合条件的元素存入单调栈中
	- 第二次从后往前遍历时，才开始处理`ans`



## 4. 接雨水

1. 题目
	- https://leetcode.cn/problems/trapping-rain-water/
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202206030653700.png" alt="image-20220603065346495" style="zoom:50%;" />



2. 思路（动态规划）
	- 定义子问题：`dp1[i]`为索引`i`左侧（包括`i`）最高的高度
	- 递归式：$dp1[i] = \max\set{height[i],dp1[i - 1]}$
	- 同理可求出`dp2[i]`——索引`i`右侧（包括`i`）最高的高度
	- 则本题的答案为$\sum\limits_i (\min\set{dp1[i],dp2[i]} - height[i])$——对于每一列应该有的雨水求和
	- 时间复杂度为$O(n)$，空间复杂度也为$O(n)$






# EOF

