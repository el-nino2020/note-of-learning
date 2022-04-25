# 基本快捷键

`Ctrl 1-6`  1-6级标题

`Ctrl B`  加粗

`Ctrl I`  斜体

`Ctrl U`下划线

`Ctrl K`超链接 [b站](www.bilibili.com) ；或者是本文件的标题：[无快捷键操作](#无快捷键操作)；使用`Ctrl + 点击`来操作

`Ctrl T`插入表格

|      |      |      |      |
| :--: | ---- | ---- | ---- |
|      |      |      |      |
|      |      |      |      |



# 无快捷键操作

`^abc^` 上标 ^abc^

`~abc~` 下标~abc~

`~~xx~~` 划去 ~~xx~~

`==abc==` 高亮==abc==

`> abc `引用

> 生活就像海洋，……
>
> This is an apple, ......

`shift ctrl i` 插入图片（路径可以是本地，也可以是网络）

![图片](https://img2.baidu.com/it/u=411374890,3609130831&fm=253&fmt=auto&app=138&f=JPEG?w=499&h=281)



`$ equation $` latex 公式：

+ $f(x)=\frac{x+1} {\pi}$
+ $f(x)=\begin{cases} x+1,x \gt 0 \\ 2x, 1\le x \lt 5 \\ x^e , x\gt 5\end{cases}$



代码块：(可标注语言)

```c++
#include <iostream>
#include <algorithm>
using namespace std;
int main()
{
    int a = 2, b = 1;
    cout << "a=" << a << "  b=" << b << endl;
    cout << "now swapping:" << endl;
    swap(a, b);
    cout << "a=" << a << "  b=" << b << endl;
    return 0;
}
```



无序列表`- space `

-  1
     - 2
          - 3
               - 4
     - 2b



有序列表 `1 . space`

1. a
2. b

任务列表

- [x] 吃饭
- [ ] 洗衣服



文献参考：

​		生活就像海洋[^1]，只有意志坚定的人才能到达对岸[^2]。

[^1]:This is an apple
[^2]:I like apples

`---`分割线

---

`:command` emoji 表情 :label: :laughing:



`[toc]`目录

[toc]

流程图（flow、sequence、mermaid)

```flow
start=>start: 开始
input=>inputoutput: 输入
operation=>operation: 操作
condition=>condition: 操作出错？
output=>inputoutput: 输出
error=>operation: 请重新输入
end=>end: 结束

start->input
input->operation
operation->condition
condition(no,bottom)->output
condition(yes)->error(top)->input
output->end
```

