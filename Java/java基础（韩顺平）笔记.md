[最后一页](#EOF，文件末尾)（按住`Ctrl`并点击）



# Version 1.0时间： 2022年4月12日

- 课程全部学完

# Version 1.1 时间：2022年4月28日

- 一些校对

# 序言

- 所用教程：[【零基础 快速学Java】韩顺平 零基础30天学会Java](https://www.bilibili.com/video/BV1fh411y7R8)
- 这是我在会用C/C++编程后（工程方面只了解了泛型编程，但没用代码实现过。主要还是用STL做算法题）、在学校上完算法与数据结构这门课后，学习java的笔记。故重复的或是基本的章节和内容将省略。
- 同时，笔记记录的表达方法是完全主观的，主要是方便我自己看。即使表达不优美、不地道（因为我已经很久不看文学书了，看得都是些翻译的专业书——计算机、经济学、西方哲学等），笔记的所有语句在**逻辑上**肯定是无误的
- 中英混用对我来说基本**没区别**，一些专业术语肯定要用英文来写 ，或者用英文额外标注。
- 项目代码在[这里](https://github.com/el-nino2020/java-hanshunping)

# 目录

[toc]



# 第0章：Java背景知识

## Java技术体系平台

- Java SE (Java Standard Edition) 标准版
	- 支持面向桌面级应用（如windows应用），提供完整Java核心的API（Application Programming Interface，应用程序接口）
- Java EE (Java Enterprise Edition) 企业版
	- 为开发企业环境下的应用程序提供解决方案，主要针对Web应用开发
- Java ME (Java Micro Edition) 小型版
	- 支持Java程序在移动端运行

## Java特点

- OOP
- 语言健壮性：强类型机制、异常处理等
- 跨平台性（编译好的class文件可以在多个操作系统上运行——依靠JVM运行）
	- JVM——Java Virtual Machine虚拟机，包含在JDK中
- 解释型：编译后的文件需要通过解释器运行；不同于编译型（C/C++)，编译后的文件可以直接被机器执行

## 相关软件

- 编辑器：sublime、IDEA、eclipse
- JDK （Java Development Kit，java开发工具包）。其中包括JRE和java开发工具（如java，javac）
- JRE (Java Runtime Environment, java运行环境)。其中包括JVM和java核心类库

## 第一个程序

```java
public class Hello{
	public static void main(String[] args){
		System.out.println("hello,world\n你好,世界\n");
	}
}
```



运行过程：

1. 在同目录下打开cmd，输入`javac Hello.java`以编译；若成功，产生`Hello.class`文件(该文件属于字节码文件)
2. 在cmd中输入`java Hello`，运行`Hello.class`（本质是将.class文件装载到JVM中）；若成功，则输出`println()`中的内容

注意事项：

1. 为了显示中文，应该在sublime中将编码类型改为GBK——与cmd中的编码形式一致
2. 一个源文件中只能有一个public类，其余类个数不限
3. 如果源文件中包含public类，则源文件应该以该类的名字命名
4. 编译有多个类的源文件，会产生多个.class文件，对应各个类名。只需要单独运行某class文件就能实现该类的main()方法

## 转义字符

| `\t`           | 制表符                     |
| -------------- | -------------------------- |
| `\n`           | 换行符                     |
| `\\或 \"或 \'` | 输出`\ 或 " 或 '`          |
| `\r`           | 回车符，将光标退回初始位置 |

## 注释

1. 单行注释、多行注释和C一样（多行注释不能嵌套）
2. 文档注释（javadoc）[菜鸟教程参考](https://www.runoob.com/java/java-documentation.html)

类和方法的注释使用文档注释；而非javadoc注释是对代码的说明，提供给代码的维护者

基本格式：

```java
/**
*@author Morgan
* a test file
*@version 1.0
*/
```

在cmd中生成文档注释的命令：`javadoc test.java`，会生成多个html文件，打开`index.html`即可看该文档

## DOS命令

1. DOS （Disk Operating System，磁盘操作系统）。其交互方式：用户在cmd中输入dos命令，dos系统接收命令并解析，并对文件系统进行相关操作

2. 相对路径：从当前目录（文件夹）开始定位，形成的路径

	绝对路径：从顶级目录（如D盘）开始定位，形成的定位

3. 路径代码

	- `..\` 进入上一级目录；
	- `abc\`进入当前目录下的abc目录

	举例：相对路径： `..\..\x\y`

	​			绝对路径：`D:\x\y`

4. dos命令

	1. 查看某目录有什么内容
		- `dir `查看当前目录
		- `dir D:\x\y`查看指定目录
	2. 切换到其他目录 change directory
		- 切换至其他根目录`cd /D C:\tmp`
		- 切换至当前盘的其他目录`cd D:\x`（相对路径亦可）
		- 切换到上一级`cd ..`
		- 切换到当前根目录`cd \`
	3. 生成指定目录的目录树`tree D:\x`
	4. 清屏`cls`
	5. 退出DOS `exit`



# 第1章：变量

## 变量的概念（省略）

## 变量类型

1. 整型

| 类型            | 占用空间 | 数据大小上限 |
| --------------- | -------- | ------------ |
| byte            | 1byte    | $2^7-1$      |
| short           | 2byte    | $2^{15}-1$   |
| int（常量默认） | 4byte    | $2^{31}-1$   |
| long            | 8byte    | $2^{63}-1$   |

- 各个数据类型占用空间不受操作系统影响
- 声明long常量：`123L`或`123l`



2. 浮点型

	| 类型               | 占用空间 |
	| ------------------ | -------- |
	| float              | 4byte    |
	| double（常量默认） | 8byte    |

	- 浮点数在机器中的存放形式：浮点数=符号位+指数位+小数位
	- 声明float常量：`123.45f`或`123.45F`
	- 其他声明浮点常量方法：`.123`或5.12e或`5.12E-2`
	- 对于浮点数计算结果，如`double x=8.1/3`，x的数学值为2.7，但由于精度问题，`x != 2.7` 。故，若要比较两浮点值是否相等，应该采用其绝对值之和小于一个极小的正值来判断，即`Math.abs(x-y)<1e-6`；C++同样存在此问题

	

3. 字符类型

- char，占两个字节，用Unicode编码（char的本质是整数），故可以给char变量赋值中文字符。举例：`char a='華';`
- 常用编码：
	- ASCII：一个字节，表示英文字符
	- Unicode：所有字符都使用两个字节；Unicode兼容ASCII
	- UTF-8：互联网上使用最广泛的、一种Unicode的实现方式。UTF-8是一种大小变化的编码方式，使用1-6个字节表示符号：字母占一个字节，汉字占三个字节



4. 布尔类型

- `boolean`占一个字节。例如：`boolean x=true;`
- 在Java中，不可以用0替换false，用非0替换true

## 类型转换

1. 自动类型转换

	- 低精度数据类型转换为高精度，称为自动类型转换
	- 转换规则：
		1. `char` $\rightarrow$ `int` $\rightarrow$` long` $\rightarrow$ `float` $\rightarrow$  `double`
		2. `byte` $\rightarrow$ `short` $\rightarrow$` int` $\rightarrow$ `long` $\rightarrow$ `float` $\rightarrow$  `double`
	- 不同数据类型进行运算时，将低精度转换为当前式子中最高的精度（不一定是`double`）
	- 将高精度值赋给低精度变量，编译会报错（C++只会warning)
	- `byte`或`short`不会和`char`自动转换
	- `byte`、`short`、`char`参与运算时会转换为`int`
	- `boolean`不参与类型转换

	

2. 强制类型转换

	- 高精度数据类型转换为低精度，需要使用强制转换符，如`int x=(int)2.5;`
	- 强制转换会造成精度损失或数据溢出

	

3. 基本数据类型和String类型的互相转换

	1. 基本数据类型 $\rightarrow$ `String`

		语法：`基本数据类型 + ""`

		举例：

		```java
		int x = 13;
		String s = x + "";
		```

	2. `String` $\rightarrow$ 基本数据类型

	  语法：除`char`外，通过基本数据类型的包装类调用`parseXX`方法；转换为`char`则调用`String`类的`charAt`方法

	  举例：

	```java
	String s = "123.34";
	double d = Double.parseDouble(s);//123.34
	char c = s.charAt(1);//'2'
	```

	- 如果转换的数据类型不匹配，将抛出异常，如`int x = Integer.parseInt("hello");`

  

# 第2章：运算符

## 算数运算符

- 和C++一样：加`+` 、减`-` 、乘`*`、除 `/` 、 自增`++`、 自减`--` （包括变量前后的自增和自减）、取模`%`

- 取模的运算逻辑为 `a%b == a - a/b*b;` a和b可以取正数和负数

	例如: `10 % -3`的值为1

## 关系运算符

- 关系运算符返回`boolean`值

- 和C++一样：等于`==` 、不等于`!=`、小于`<=`、大于`>=`、小于等于`<=`、大于等于`>=`

- 新的运算符`instanceof` ：检查是否为类的对象

	举例：`"hello" instanceof String` 返回`true`



## 逻辑运算符

- 短路与 `&&` 、短路或` ||` 、取反`!`

- 逻辑与 `&` 、逻辑或 `| `、逻辑异或`^`

- 以上两组运算符结果均与C++一致

- 短路与`&&`：如果第一个条件为false，输出false，之后的条件不判断；

	逻辑与`&`：判断所有条件

- 短路或`||`：如果第一个条件为true，则输出true，之后的条件不判断

	逻辑或`|`：判断所有条件



## 赋值运算符

- 和C++一样：`=`、`+=`、`-=`、`*=`、`/=`、`%=`

- `+=`系列运算符和`++`、`--`运算时会进行自动类型转换

	举例：

	```java
	byte b = 3;
	b += 2;//allowed
	//b=b+2, not allowed
	b++;//allowed
	```

	`b+=2;` 的本质是`b=(byte)(b+2);`



## 三元运算符

- 和C++一样：条件表达式 ? 表达式1 ：表达式2



## 运算符优先级

| 运算符                                              | 运算方向         |
| --------------------------------------------------- | ---------------- |
| `.  ()  {}   ;   `                                  | L$\rightarrow$ R |
| `++    --    ~   !  (int) `                         | R$\rightarrow$ L |
| `*   /   %`                                         | L$\rightarrow$ R |
| `<<    >>    >>>`    位移                           | L$\rightarrow$ R |
| `<  >   <=   >=  instanceof`                        | L$\rightarrow$ R |
| `==     !=`                                         | L$\rightarrow$ R |
| `&`                                                 | L$\rightarrow$ R |
| `^`                                                 | L$\rightarrow$ R |
| `|`                                                 | L$\rightarrow$ R |
| `&&`                                                | L$\rightarrow$ R |
| `||`                                                | L$\rightarrow$ R |
| `?   :`  三元运算符                                 | L$\rightarrow$ R |
| `=  *=  /=   %=  +=  -=  <<=   >>=  >>>= ^= &=  |=` | R$\rightarrow$ L |
|                                                     |                  |

## 标识符

- 标识符指变量、类或方法的命名
- 命名规则
	- 由英文字母大小写、阿拉伯数字、**_或$**组成
	- **只有数字不可以**作为标识符开头
	- 不能使用关键字和保留字
- 命名规范
	- 包名：多单词组成时，所有字母小写：`aaa.ccc`
	- 类名、接口名：多单词组成时，所有单词首字母大写（大驼峰）：`TankShotGame`
	- 变量、方法名：多单词组成时，第一个单词首字母小写，其余单词首字母大写（小驼峰）：`tankShotGame`
	- 常量名：所有字母大写，单词之间用下划线连接：`TAX_RATE`
- 关键字
- 保留字：现有Java版本尚未使用，以后可能作为关键字使用



## 键盘输入

```java
import java.util.Scanner;//导入所需要的包java.util

class test{
	public static void main(String[] args){

		Scanner input = new Scanner(System.in);//input为Scanner类的对象，同时调用Scanner()的一个构造器

		System.out.println("What's your name?");
		String name = input.next();

		System.out.println("What's your age?");
		int age = input.nextInt();

		System.out.println("What's your salary?");
		double salary = input.nextDouble();

		System.out.println("Name\tAge\tSalary\n" + name + "\t" + age + "\t" + salary);

	}

}
```

## 四种进制

1. 介绍

	- 二进制bin：以`0b`或`0B`开头，如`int a=0b1010;//10`
	- 十进制dec
	- 八进制oct：以`0`开头，如`int b=01010;//`520
	- 十六进制hex：以`0x`或`0X`开头，`A-F`不区分大小写，如`int c=0x1010;//4112`

	

2. 其他进制转十进制（规律省略，只举例）

	1. bin $\rightarrow$ dec，$0b1011=1*2^0+1*2^1+0*2^2+1*2^3$
	2. oct $\rightarrow$ dec, $0234=4*8^0+3*8^1+2*8^2$
	3. hex $\rightarrow$ dec，$0x23A=10*16^0+3*16^1+2*16^2$



3. 十进制转其他进制

	- 规律：将数字不断除以x，直至商为0，再将每一步的余数反过来（从下往上）排序，得到相应的x进制

	1. dec $\rightarrow$ bin，十进制数为34

		$34 \div 2 =17 \cdots 0 \\ 17 \div 2 = 8 \cdots 1\\8 \div 2 = 4 \cdots 0 \\4\div2=2\cdots0\\2\div2=1\cdots0\\1\div2=0\cdots1$

		故`34=0b100010` 

	2. dec $\rightarrow$ oct，十进制数为131

	  $131\div8=16\cdots3\\16\div8=2\cdots0\\2\div8=0\cdots2$

	  故`131=0203` 

	3. dec $\rightarrow$ hex，十进制数为237

	  $237\div16=14\cdots13\\14\div16=0\cdots14$

	  故`237=0xED`



4. 二进制转其他进制

	1. bin $\rightarrow$ oct，从低位开始，每**三**位一组转成对应的**八**进制，高位不足**三**位补零

		举例：$0b11010101=0b\,011|010|101=0325$

	2. bin $\rightarrow$ hex，从低位开始，每**四**位一组转成对应的**十六**进制，高位不足**四位**补零

		举例：$0b11010101=0b\,1101|0101=\text{0xD5} $



5. 其他进制转二进制

	1. oct $\rightarrow$ bin，将**八**进制的每一位转换成对应的长为**三**位的二进制数

		举例：$0237=0b\,010|011|111=0b010011111$

	2. hex $\rightarrow$ bin，将**十六**进制的每一位转换成对应的长为**四**位的二进制数

		举例：$0x23B=0b\,0010|0011|1011=0b001000111011$



## 位运算，原码、反码、补码——2's complement

1. 原码、反码、补码的规则
	- 二进制最高位是符号位：0表示正数，1表示负数
	- 正数和0的原码、反码、补码一样
	- 负数的反码 = 原码符号位不变，其他位按位取反
	- 负数的补码 = 负数的反码 + 1
	- java没有无符号数
	- 计算机中，**以补码形式进行存储和运算**，即2's complement法则
	- 计算机展示运算结果是用原码



2. 位运算

	- 按位与`&`、按位或`|`、按位异或`^`、按位取反`~` ：运算规则和C++一致

		举例：求`~2`

		```
		2的补码等于原码：00000000 00000000 00000000 00000010
		对于补码执行按位取反操作，得到结果的补码形式：
					  11111111 11111111 11111111 11111101
		该数的反码是：	  11111111 11111111 11111111 11111100
		继而，原码是：	  10000000 00000000 00000000 00000011
		即为-3 故 ~2的结果为-3
		```

	- 算术右移`>>`：低位溢出，符号位不变，并用符号位补溢出的高位

	​     算数左移`<<`：符号位不变，低位补0

	​     逻辑右移（无符号右移）`>>>`：低位溢出，高位补0

	- **注意**，负数的补码和原码不一致，运算时不要忘记转换



3. 注记（Ver 1.1）
	- 上了计算机体系结构的课后，这一节的知识应该是常识





# 第3章：控制结构

## 顺序结构



## 分支结构

- 一些关键字：
- `if --- else if ---if`
- `switch --- case --- default`
- 分支结构的使用方法和C++一样



## 循环结构

1. 以下关键字使用方法和c++一样：
	- `for `
	- `while`
	- `do --- while`



2. `break`

	- 常用方法：

		- ```
			for (...)
			{
				if (...)
					break;
			}
			```

	- 多重嵌套，设置标签来跳转

		- ```java
			public class MyClass {
			    public static void main(String args[]) {
			        abc1: for (int i = 0; i < 3; ++i) {
			            int x;
			            label2:
			            // int j=0 ; 不允许，标签的下一条语句必须是循环
			            for (int j = 0; j < 10; ++j) {
			                if (j == 3)
			                    break abc1;
			                	//break label2;
			                	//break
			                System.out.println("i= " + i + "; j = " + j);
			            }
			        }
			        // abc3: 不允许有空标签
			    }
			}
			```

		- 标签的名字可以任意设置（在满足标识符命名规则的前提下）

		- `break abc1`表示跳出最外层的循环

		- 只写`break;`相当于`break label2`，即跳出最近的循环

		- 标签后一条语句必须是循环体，参考`label2`后面不能声明变量`j`

		- 实际开发一般不使用标签



3. `continue`
	- `continue`和`break`一样，也可以使用标签，用法一致	



# 第4章：数组



## 数组入门

1. 动态初始化

	```java
	int a[] = new int[5];
	double[] b = new double[8];//[]写在数据类型的后面（而非变量名的后面）的用法更常见
	
	double ele=b[6];//引用b中第7个元素
	
	int lb=b.length;//length是数组的成员，表示长度
	```

2. 动态初始化——先声明，后创建数组

	```java
	int[] a;
	a = new int[7];
	```

3. 静态初始化

	```java
	int[] a = {1,2,3};//[]里不能写数字
	```

4. 数组创建后，如果没有赋值，则赋默认值——广义0——`int`等为`0`，`string`为`null`，`boolean`为`false`

	```java
	int[] a = new int[3];//a[0]、a[1]、a[2]都为0
	```

5. 数组越界在编译时不会出错，但会在运行时抛出异常

6. 数组是引用类型，本质为对象

7. 数组名的赋值是引用赋值

	```java
	int[] arr1 = {1,2,3};
	int[] arr2 = arr1;
	//两者指向同一个数组，本质是地址传递
	```



## 二维数组

1. 动态初始化——列数相同

	```java
	int[][] a;//这个更常用
	int b[][];
	int[] c[];
	a = new int[2][3];
	```

2. 动态初始化——列数不同

	```java
	int[][] a = new int[3][];
	int a[0] = new int[4];
	int a[i] = new int[6];
	```

3. 静态初始化

	```java
	int[][] a={{1,2},{3,4,5}};
	```



# 第5章：面向对象（初级）



## 概念的定义

- 类是自定义的数据类型
- 对象是类的实例化
- 举例：`int`是类；`int a = 1;`，`a`是对象



## 属性/成员变量

1. ```java
	class Cat{
	    string name;
	    int age;
	    string color;
	}//没有分号
	```

2. 属性/成员变量/字段（field）定义规则：

	`访问修饰符 数据类型 属性名`





## 对象

1. ```java
	Cat c1 = new Cat();
	
	Cat c2;//先声明
	c2 = new Cat();//后创建
	```

2. `c1`（对象名/对象引用）指向一个堆中的地址。该地址（真正的对象存在）包括3个数据，即`name`、`age`、`color`的值。由于`name`的类型为`string`——一个引用类型——`name`又指向方法区的常量池的一个地址，该地址中才是`name`的内容

	| JVM内存分区    | 变量     | 值              |
	| -------------- | -------- | --------------- |
	| 栈             | c1       | 0x10001（假设） |
	| 堆             | c1.name  | 0x20001（假设） |
	|                | c1.age   | 2               |
	|                | c1.color | 0x20010（假设） |
	| 方法区——常量池 | 0x20001  | “李东风”        |
	|                | 0x20010  | “银灰色”        |
	| 方法区——类信息 |          |                 |

​	另一个例子的图解：

<img src="https://raw.githubusercontent.com/el-nino2020/ImageBed/main/image-20220204133746076.png" alt="另一个例子" style="zoom: 33%;" />





3. java创建对象流程：

- 在方法区中加载`Cat`类信息（只有首次创建才会加载）
- 在堆中分配一个`Cat`对象的空间，成员变量初始化
- 把该空间的地址赋给`c1`





## 方法

1. ```java
	class Cat{
	    string name;
	    int age;
	    string color;
	    public void sleep(){
	        System.out.println("^ - _ - ^");
	    }
	    public void miao(int n){
	        for (int i=0;i<n;++i)
	            System.out.println("Miao~~~");
	    }
	    public boolean response(int a,int b){
	        if(a + b > 50)
	        	return true;
	        return false;
	    }
	}//没有分号
	```

2. ```java
	Cat c1 = new Cat();
	c1.sleep();//使用方法
	c1.miao(5);
	boolean responsed=c1.response(10,60);
	```

3. 方法调用机制，以下列步骤为例：

	```java
	Cat c1 = new Cat();
	boolean responsed=c1.response(10,60);
	```

	- 在栈内为`main`函数分配空间（不妨称作`main`栈）
	- 在堆中生成一个`Cat`对象
	- 在`main`栈中生成`c1`，指向上述`Cat`对象
	- 在栈内为`response`函数分配空间（不妨称作`response`栈）
	- 在`response`栈中执行该函数内容，返回布尔值，释放该栈的内存
	- 释放`main`栈内存，程序结束

4. 方法（函数）定义规则

	- ```a
		访问修饰符 返回类型 方法名(参数){
			函数体
		}
		```

5. 同一个类中的方法可以直接调用，但调用别的类的方法则需要先创建对象

	- ```java
		class Abc{
		    public void A(){
		        
		    }
		    public void B()
		    {
		        A();//permitted
		        Cat c=new Cat();
		        c.sleep();
		    }
		}
		```

6. 基本数据类型的传参机制为按值传递

  e.g. 对于以下定义的`swap`函数，并不能执行交换值的功能：

```java
public void swap(int a, int b){
    int temp=a;
    a=b;
    b=temp;
}
```

7. 引用数据类型的传参机制为地址传递，形参和实参访问的是同一内存空间

  e.g.数组、对象作为方法的参数

```java
class Test(){
    public static void main(String args[]) {
        int[] a={1,2,3};
        change(a,0,100);//有效地将a[0]变为100
    }
    public void change(int[] arr, int pos, int val){
        arr[pos]=val;
    }
}
```

  

## 方法重载（overload）

- 重载：有多个**相同的方法名**，但每个方法的参数列表不同
- 参数列表不同：**形参类型、顺序或数量不同**
- 方法**返回类型无要求**





## 可变参数

- 基本格式

	```
	访问修饰符 返回类型 方法名(数据类型... 形参名){
	}
	```

- 例子

	```java
	//求所有参数之和
	public int sum(int... nums){
	    int ans = 0;
	    for (int i=0; i<nums.length; ++i)
	        ans += nums[i];
	   	return ans;
	}
	```

- 可变参数`nums`本质是数组，即`int[]`，因此可以使用数组相关操作

- 由于可视为数组，可变参数的个数可以为0,1,2,……

- 故实参可以是数组

	```java
	int[] arr={1, 2, 3};
	sum(arr);//allowed
	```

- 可变参数可以与普通形参一起使用，但可变参数需要放在参数列表最后。因此只能有一个可变参数

	```java
	public void f1(double d, char c, int... nums){
	}
	```



## 变量作用域

- 全局变量：类的属性，其作用域为整个类

- 局部变量：一般指方法中定义的变量，其作用域为该方法

- **局部变量必须在赋值后才能使用**；而属性不用（因为会被自动初始化为广义零）

	```java
	int num;
	System.out.print(num);//会报错，因为num没有初始化
	```

- 属性和局部变量可以重名，访问时采用就近原则

	```java
	class Cat{
	    String name = "李东风";
	    
	    void call(){
	        String name = "李小p";
	        System.out.print(name);//会输出李小p
	    }
	}
	```

- 同一作用域中的两变量不能重名



## 构造器

- 构造器的作用是对新对象初始化

- 基本语法：

	```
	[修饰符] 方法名(参数列表){
		方法体
	}
	```

- 构造器的修饰符可以默认，也可以写上

- 构造器可以重载

- 一个例子：

	```java
	class Cat{
	    String name;
	    int age = 1;
	    
	    //constructor
	    public Cat(String s, int i){
	        name = s;
	        age = i;
		}
	    
	    //constructor overload
	    public Cat(String s){
	        name = s;
	    }
	}
	```

- 若在类中没有定义构造器，则系统会自动生成一个默认的无参构造器。在上述例子中即为`Cat(){}`。该构造器的存在可以使用`javap`命令查看

- 若在类中已经定义了构造器（不管是不是无参的），则系统不会生成默认构造器。若要使用该构造器，需要人为地定义。

- `Cat`对象初始化过程：

	分析：`Cat c1 = new Cat("李东风",2);`

	1. 默认初始化：属性赋默认值，`name`为`null`，`age`为`0`
	2. 显式初始化：`age`为`1`
	3. 构造器初始化：`name`为`李东风`，`age`为`2`



## `this` 关键字

- JVM给每个对象分配`this`，代表当前对象

- `this`用于访问当前类的属性和方法

- `this`可以访问构造器，语法是`this(参数列表)`。此时，该语句必须出现是构造器的第一句

- 一个例子：

	```java
	Class Cat{
	    String name;
	    int age;
	    
	    public Cat(){
	        this("李东风", 2);//该语句必须是Cat()的第一句
	        System.out.println("calling default constructor");
	    }
	    
	    public Cat(String name, int age){
	        this.name = name;
	        this.age = age;
	    }
	    
	    public void f1(){
	        System.out.println("calling f1");
	        
	        String name = "臭卷宝";
	        
	        //以下两句不等价，从而可以看出this调用属性时的作用
	        System.out.println(name);
	        System.out.println(this.name);
	        
	    }
	    
	    public void f2(){
	        System.out.println("calling f2");
	        
	        //以下两句等价
	        this.f1();
	        f1();
	    }
	}
	```

- `this`将在继承中展现自己更多的用途







## 课后练习

1. 设计函数`max`，找到`double`数组的最大值，并返回

```java
public class MyClass {
    public static void main(String args[]) {
        double[] arr = { 1, 2.3, -1.2 };
        A a = new A();
        Double result = a.max(arr);
        if (result == null)
            System.out.println("Invalid input");
        else
            System.out.println("The maximum value is " + result);
    }
}

class A {
    public Double max(double[] arr) {
        // 利用对象引用值可以为null的特性和Double作为包装类来判断输入是否不合理
        if (arr == null || arr.length == 0)
            return null;

        double ans = arr[0];
        int n = arr.length;
        for (int i = 1; i < n; ++i) {
            if (arr[i] > ans)
                ans = arr[i];
        }
        return ans;
    }
}

```





# 第6章：面向对象（中级）



## IntelliJ IDEA使用相关

1. 快捷键设置`Settings` - `Keymap`，然后搜索

- `Delete Line`，删除当前行：`ctrl + d `

- `Dulicapate Line or Selection`，复制当前行：`Shift + Ctrl + 向下箭头`

- `Reformat Code`，格式化代码：`Shift + Ctrl + f`

- `Run`，快速运行程序：`F5`

	

2. `Settings` - `Editor` - `General` - `Auto Import`，自动导入包



3.`Settings` - `Editor` - `General` - `Code Completion`，将`Match case`关闭，使智能提示不区分大小写



4. 已有快捷键

- 补全代码：`Alt + /`
- 将当前段落变为注释或取消注释，`Ctrl + /`
- 生成构造器：`Alt + Ins`
- 查看类的层级关系：`Ctrl + H`
- 定位方法：`Ctrl + B`
- 自动分配变量名：`.var`
	- 例如输入：`new Cat().var`
- 查找：`Ctrl + F`
- 查找并替换：`Ctrl + R`



5. 模板和模板的自定义：`Settings` - `Editor` - `Live templates`

	e.g. `sout`为`System.out.println();`的模板



6. 导出当前设置：`File` - `Manage IDE Settings` - `Export Settings`



7. 查看源代码：光标放在方法名上，按`Ctrl + B` ，或右键：`Go To` - `Declaraction or Usages`
	- 如果没有成功，则需要事先配置源文件，方法如下：
	- 在`File` - `Project Structure` - `SDKs` - ‘Sourcepath’中添加jdk安装目录下的`src.zip`和`javafx-src.zip`文件
8. 调试——debug
	- 相关快捷键：
		- Step Over，逐行执行代码：`F8`
		- Step Into，进入方法体：`F7`
		- Force Step Into，强制进入（用于进入源码等场合）
		- Step out，跳出方法体：`Shift + F8`
		- Resume Program，运行到下一个断点：`F9`
		- Run to Cursor，运行到光标处：`Alt + F9`





## 包（package）

1. 包的作用
	- 区分相同名字的类
	- 当类有很多时，方便管理类
	- 控制访问范围



2. 基本语法：
	- `package aaa.bbb`；其中，`package`为关键字，`aaa.bbb`表示包名；
	- 使用该语法以声明当前类所在的包；
	- 该语句需要放在类的第一句，故一个类文件中只能出现一次



3. 包的本质：包含类文件的**文件夹**



4. 例子：

	- 建立以下文件目录：

		<img src="https://raw.githubusercontent.com/el-nino2020/ImageBed/main/image-20220204133439274.png" alt="image-20220204133439274" style="zoom: 33%;" />

		```
		src（顶级目录）
		---owner
			---jack
				---Dog.java
			---rose
		    	---Dog.java
			---use
				---Test.java
		```

	- 各文件内容：

		```java
		//Dog.java in file folder jack
		package owner.jack;
		
		public class Dog {
		}
		```

		

		```java
		//Dog.java in file folder rose
		package owner.rose;
		
		public class Dog {
		}
		```

		```java
		//Test.java
		package owner.use;
		
		import owner.jack.Dog;
		
		public class Test {
		    public static void main(String[] args) {
		        //由于import owner.jack.Dog，现在使用Dog即代表前者
		        Dog dog = new Dog();
		        System.out.println(dog);//打印dog的hashCode
		        
		        //由于不能重复引用同一个类名，声明dog1时需使用完整包名
		        owner.rose.Dog dog1 = new owner.rose.Dog();
		        System.out.println(dog1);
		
		    }
		}
		
		```



5. 包的命名
	- 命名规则：只能包含数字、字母、下划线、句点，不能以数字开头，不能使用关键字和保留字
	- 命名规范：使用小写字母和小圆点：`com.公司名.项目名.业务模块名`；
	- e.g. `com.sina.crm.user`



6. java中常用的包
	- `java.lang.*`：基本包，默认引入
	- `java.util.*`：工具包
	- `java.net.*`：网络包，网络开发
	- `java.awt.*`：界面开发，GUI



7. `import`：导入包
	- `import java.util.Scanner`：只导入`Scanner`类
	- `import java.util.*`：导入`java.util`中所有类
	- 应使用第一种导入方式
	- `import`写在类定义之前，且没有顺序要求





## 访问修饰符

1. 四种访问修饰符

	| 访问级别  | 同类         | 同包         | 子类         | 不同包       |
	| --------- | ------------ | ------------ | ------------ | ------------ |
	| public    | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ |
	| protected | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\times$     |
	| 默认      | $\checkmark$ | $\checkmark$ | $\times$     | $\times$     |
	| private   | $\checkmark$ | $\times$     | $\times$     | $\times$     |

2. 注意事项

- 表格的解读方法为：假定`A`类中定义了属性`protected String name;`，则修饰符`protected`表示从别处（包括`A`类自身）访问`name`的权限：即同类、同包中的类和子类可以访问`name`，而不同包中的类不能访问该变量
- 修饰符可以修饰属性、方法和类
- 修饰类时只能使用默认和`public`





## 封装（encapsulation）

1. OOP三大特征：**封装、继承和多态**



2. 封装的定义：隐藏对象的属性和方法的实现细节，仅对外公开接口，从而控制在程序中对于属性的读和修改的访问级别（即外部只能通过接口来间接修改属性）



3. 封装的好处：
	- 隐藏实现细节：用户使用时只要知道方法的作用——故输入参数即可使用——而无需关心实现细节
	- 保证数据（属性的值）安全合理



4. 封装实现步骤

	- 对于属性进行私有化，e.g. `private int age;`

	- 提供公共set方法，用于修改属性

		```java
		public void setAge(int age){
		    //判断age是否合理
		    this.age = age;
		}
		```

	- 提供公共get方法，用于获取属性的值

		```java
		public int getAge(){
		    //权限判断
		    return age;
		}
		```

	- 在IDEA中，可以使用`Alt` + `Ins`中的`Getter`、`Setter`快速设置以上方法



5. 在构造器中使用相关属性的set方法，以保护数据

	```java
	class Cat{
	    public String name;
	    private int age;
	    
	    public Cat(String name, int age){
	        setName(name);
	        setAge(age);
	    }
	    
	    public void setName(String name){
	        int l = name.length();
	        if(l > 0 and l <= 4)
	            this.name = name;
	    }
	    
	    public void setAge(int age){
	        if(age > 0 and age <= 20)
	            this.age = age;
	    }
	}
	```

	





## 继承（inheritance）

1. （不严谨的）定义：以某个类为基础，派生出其他类。派生时会保留父类的属性和方法，从而子类不需要重新定义。



2. 继承原理简图：
	- ![屏幕截图(231)](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202041621939.png)
	- 其中，A为父类，其所有属性和方法将被其派生类共有
	- B和C作为A的子类，可以再定义各自特有的属性和方法
	- D作为B的子类，将继承A和B的所有属性和方法。此外还可以定义其特有的属性和方法
	- 父类、基类、超类 $\Rightarrow$ 子类、派生类



3. 基本语法：

	- ```d
		class 类名 extends 类名{
		
		}
		```

	- `extends`为关键字，其后为父类名称

	

	

4. 一个例子：

	```java
	public class inheritance {
	    public static void main(String[] args) {
	        Cat cat = new Cat();
	        cat.setAge(2);
	        cat.setName("李东风");
	        cat.showInfo();
	        cat.makeNoise();
	        System.out.println("=================================");
	
	        Dog dog = new Dog();
	        dog.setAge(4);
	        dog.setName("旺财");
	        dog.showInfo();
	        dog.makeNoise();
	
	
	    }
	}
	
	class Animal {
	    public String name;
	    private int age;
	
	    public Animal() {
	    }
	
	    //刻意不继承构造器来设置属性，因为只是单纯演示
	    public void setName(String name) {
	        this.name = name;
	    }
	
	    public void setAge(int age) {
	        this.age = age;
	    }
	
	    public void showInfo() {
	        System.out.println(name + " is " + age + " years old");
	    }
	}
	
	class Cat extends Animal {
	    public void makeNoise() {
	        System.out.println("miao~~~ by " + name);
	    }
	}
	
	class Dog extends Animal {
	    public void makeNoise() {
	        System.out.println("wang~~~ by " + name);
	    }
	}
	
	
	```

	

5. 继承细节

	1. 子类继承所有的属性和方法，但不能直接访问父类的私有（`private`）属性和方法

	2. 子类**必须调用父类构造器**，以完成父类初始化

	3. 创建子类时，无论使用子类的哪一个构造器，都会默认调用父类的默认构造器；如果父类没有默认构造器，则应该用`super(参数列表)`来指定父类的相应构造器

		```java
		public class inheritance {
		    public static void main(String[] args) {
		        B1 b1 = new B1();
		        System.out.println("=================================");
		        B2 b2 = new B2();
		        System.out.println("=================================");
		        B2 b21 = new B2("Alice");
		
		    }
		}
		
		class A1 {
		    public A1() {
		        System.out.println("calling A1()");
		    }
		}
		
		class A2 {
		    public A2(String name) {
		        System.out.println("calling A2(String)");
		    }
		}
		
		class B1 extends A1 {
		    public B1() {
		        //A1存在默认构造器，所以super();可以省略
		        System.out.println("calling B1()");
		    }
		}
		
		class B2 extends A2 {
		    /**
		     * A2没有默认构造器，
		     * 故无论如何，B2都要显式调用A2中已有的构造器
		     * 而不能省略super(String)
		     */
		    public B2() {
		        super(" ");
		        System.out.println("calling B2()");
		    }
		
		    public B2(String name) {
		        super(name);
		        System.out.println("calling B2(String)");
		    }
		}
		```

	4. 想要指定调用父类的某个构造器，则显式地使用`super(参数列表)`

	5. `super()`必须放在，且只能放在构造器的第一句——因为需要先初始化父类、再初始化子类

	6. `super()`和`this()`在一个构造器中只能出现一次——因为子类的任何一个构造器都包含`super()`。如果同时使用`super()`和`this()`，会初始化父类两次——这是不可能的

	7. java中，`Object`类是所有类的基类

	8. 父类构造器的调用不限于直接父类，将一直上述至`Object`类——顶级父类

	9. java是**单继承机制**，即子类最多继承一个直接父类

	10. 不能滥用继承，子类和父类之间需要满足is-a的关系





6. 继承的本质（内存分析），以及**查找关系**的原则

	- 使用以下类：

		```java
		class Grandpa {
		    String name = "大头爷爷";
		    String hobby = "旅游";
		}
		
		class Father extends Grandpa {
		    String name = "大头爸爸";
		    int age = 39;
		}
		
		class Son extends Father {
		    String name = "大头儿子";
		}
		```

	- 在`main`中输入以下语句

		```java
		Son son = new Son();
		System.out.println(son.name);
		System.out.println(son.age);
		System.out.println(son.hobby);
		```

	- 内存分析：

		<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202050641086.png" alt="屏幕截图(233)" style="zoom: 50%;" />

		1. 由`Son`类的继承关系向上追溯至`Object`类，以自顶向下的顺序在方法区中加载类信息，即先`Object`，再`GrandPa`，再`Father`，最后`Son`。类信息包括属性信息和方法信息
		2. 在堆中分配空间，如图为0x11。首先为`Grandpa`类分配`name` 和`hobby`的空间（由于两者都是`String`，在常量池建立相应数据，即0x22和0x33）。再为`Father`类分配对应的`name`和`age`的空间。最后，给`Son`类分配它的`name`空间。在`main`中建立类变量`son`，将0x11赋值给它
		3. 接着，程序欲输出`son.name`。在继承中有以下**查找关系**：
			- 首先查找子类是否有`name`
			- 如果子类有该属性，且可以访问，则返回该属性。（*）
			- 如果子类没有该属性，则以其直接父类为基准，再查找，即重复（*）往下的过程。如果追溯到`Object`还没有，则报错
			- 在（*）中，如果子类有该属性，但不能访问，会直接报错，不论其父类是否有该属性。具体来说，假如只在`Son`中改变定义：`private String name;`（其父类定义不变），则会直接报错——报错信息为`name has private access`
			- 故`son.name`为`"大头儿子"`
		4. 按照3中的原则，`son.age`输出`39`，而`son.hobby`输出`"旅游"`







## `super`关键字

1. `super`代表父类对象的引用，以访问父类的属性、方法、构造器



2. 基本用法：
	- 访问父类属性（非`private`）：`super.属性名`
	- 访问父类方法（非`private`）：`super.方法名(参数列表)`
	- 访问父类构造器：`super(参数列表)`，且只能放在构造器第一句



3. 一些细节

	1. 好处：调用父类构造器使初始化分工明确——父类属性由父类构造器完成初始化，子类用自己的构造器完成其属性初始化

	2. 子类中有和父类重名的属性或方法时，使用`super`访问父类的属性或方法。

		- ```java
			public class inheritance {
			    public static void main(String[] args) {
			        B1 b1 = new B1();
			        B2 b2 = new B2();
			        b1.f2();
			        System.out.println("==========================");
			        b2.f2();
			    }
			}
			
			class A {
			    public int age = 10;
			
			    public void f1() {
			        System.out.println("call f1() in A");
			    }
			}
			
			class B1 extends A {
			    public void f2() {
			        System.out.println("call f2() in B1");
			        //以下三者等价
			        System.out.println(age);
			        System.out.println(this.age);
			        System.out.println(super.age);
			
			        //以下三者等价
			        f1();
			        this.f1();
			        super.f1();
			    }
			}
			
			class B2 extends A {
			
			    public int age = 17;
			
			    public void f1() {
			        System.out.println("call f1() in B2");
			    }
			
			    public void f2() {
			        System.out.println("call f2() in B2");
			
			        System.out.println(age);
			        System.out.println(this.age);
			        //以上两者等价
			        
			        System.out.println(super.age);
			
			        f1();
			        this.f1();
			        //以上两者等价
			
			        super.f1();
			    }
			}
			```

		- **查找关系**同样适用于方法

	3. 由**查找关系**可得，`super`不限于访问直接父类的属性和方法



## 方法重写/覆盖（override）

1. 简单定义：子类的一个方法与其父类的某个方法的**名称、返回类型、参数一样**，则该方法覆盖其父类的方法



2. 一个例子

	```java
	public class Test {
	    public static void main(String[] args) {
	        B b = new B();
	        b.f1();
	    }
	}
	
	class A {
	    public void f1() {
	        System.out.println("call f1() in A");
	    }
	}
	
	class B extends A {
	    public void f1() {
	        System.out.println("call f1() in B");
	    }
	}
	```



3. 重写规则：

	- 子类的方法的**形参和名称要与父类的完全相同**

	- 子类方法的**返回类型要与父类方法的返回类型相同**，或者是父类方法返回类型的子类。例如：

		|        | 父类返回类型 | 子类返回类型 |
		| ------ | ------------ | ------------ |
		| 情况一 | `String`     | `String`     |
		| 情况二 | `Object`     | `String`     |

	- **子类方法不能缩小父类方法的访问权限**。例如，父类的某方法定义为`void f1()` 。按照访问权限`public` > `protected` > 默认 > `private` ，子类的方法若要重写，则须定义为`public void f1()`或`protected void f1()`或`void f1()`



4. 重写和重载的比较

	|          | overload | override |
	| -------- | -------- | -------- |
	| 发生范围 | 本类     | 父子类   |
	| 方法名   | 相同     | 相同     |
	| 形参列表 | 不同     | 相同     |
	| 返回类型 | 无要求   | 有要求   |
	| 修饰符   | 无要求   | 有要求   |



## 多态（polymorphism）



1. 简单解释：方法或对象具有多种形态



2. 方法多态：**重写和重载**体现多态



3. 对象多态（核心）

	1. - 一个对象的编译类型和运行类型可以不一致。

		- 编译类型是在定义对象名时确定的，不能改变。

		- 运行类型可以随着赋给对象名的值（地址）的不同而改变。

		- 编译类型看定义时等号左边，运行类型看等号右边。

		- 一个例子，如下：

		- ```java
			public class poly {
			    public static void main(String[] args) {
			        //obj的编译类型为A，运行类型为B
			        A obj = new B();
			        //obj只是变量引用——即一个地址，
			        //它的本质还得看堆中的对象属于哪个类
			        obj.f1();
			
			        System.out.println("==========================");
			
			        //obj的编译类型还是A，运行类型改为A
			        obj = new A();
			        //同时使用了方法的覆盖，这是方法多态的体现
			        obj.f1();
			    }
			}
			
			class A {
			    public void f1() {
			        System.out.println("call f1() in A");
			    }
			}
			
			class B extends A {
			    public void f1() {
			        System.out.println("call f1() in B");
			    }
			}
			```

		- 该性质将极大地方便方法定义时参数的传递。例如，定义方法`feed`：主人给动物喂食物，实现如下：

			```java
			public void feed(Animal animal,Food food){
			    System.out.println("主人喂"+food.getName()+"给"+animal.getName()+"吃");
			}
			```

			由于`Animal`类可以派生出`Cat`、`Dog`等类，`Food`类可以派生出`Fish`、`Meat`等类。若不存在多态，则需要使用重载来定义大量的`feed`方法，代码复用性低

	2. 向上转型：

	- 本质：父类的引用指向子类的对象

	- 语法：`父类类型 引用名 = new 子类类型(参数列表);`

	- 编译类型看等号左边，运行类型看右边

	- :eight_pointed_black_star: 该引用名可以调用所有访问权限允许的父类成员（属性和方法）

	- :eight_spoked_asterisk: 该引用名**不能**调用子类的**特有**成员。

	- 以上两点由编译类型决定

	- 对于重写的方法，运行时以运行类型为基准，使用**查找关系**。由于重名的属性不是重写，对于属性的访问依旧看编译类型——一切都是由名字相同导致的:angry::angry::angry:

	- 代码如下：

	- ```java
		public class poly {
		    public static void main(String[] args) {
		        A a = new B();
		        //以下语句报错，提示找不到f3()，因为该方法是B的特有成员。
		        //因为a的编译类型为A，而在编译时已经决定能够使用哪些成员
		        //a.f3();
		
		        //f1()的具体实现在运行时依据查找关系确定
		        a.f1();
		
		        a.f2();
		
		        //重名的属性不是重写，故age由编译类型决定
		        System.out.println(a.age);
		    }
		}
		
		class A {
		    public int age = 10;
		
		    public void f1() {
		        System.out.println("call f1() in A");
		    }
		
		    public void f2() {
		        System.out.println("call f2() in A");
		    }
		}
		
		class B extends A {
		    public int age = 20;
		
		    public void f1() {
		        System.out.println("call f1() in B");
		    }
		
		    public void f3() {
		        System.out.println("call f3() in B");
		    }
		}
		
		```

	

	3. 向下转型：

	- 语法：`子类类型 引用名 = (子类类型) 父类引用名;`

	- 只能强制转换父类的引用，不能强转父类的对象——任何对象在创建时已经存在，引用的改变不会改变对象本身

	- 在转换前，父类的引用名必须指向子类的对象

	- 向下转型后，可以调用子类中所有的成员——因为编译类型是子类

	- 代码如下：

	- ```java
		public class poly {
		    public static void main(String[] args) {
		        //a编译类型为A，运行类型为B1
		        A a = new B1();
		        a.f1();
		        a.f2();
		        //a.f3()不能用
		        System.out.println("============================");
		
		        //b1的编译类型为B1，运行类型为B1
		        B1 b1 = (B1) a;
		        b1.f1();
		        b1.f2();
		        b1.f3();
		
		        //以下两例可以看出，在转换前，父类的引用名必须指向子类的对象
		        
		        B2 b2 = new B2();
		        //故两个无继承关系的类无法强转,这里会直接无法编译
		        //B1 b11=(B1) b2;
		
		        A a1 = new A();
		        //同样，父类对象也无法使用子类引用
		        //使用以下语句会抛出异常：ClassCaseException
		        //B1 b12 = (B1) a1;
		    }
		}
		
		class A {
		    public void f1() {
		        System.out.println("call f1() in A");
		    }
		
		    public void f2() {
		        System.out.println("call f2() in A");
		    }
		}
		
		class B1 extends A {
		    public void f1() {
		        System.out.println("call f1() in B1");
		    }
		
		    public void f3() {
		        System.out.println("call f3() in B1");
		    }
		}
		
		class B2 extends A {
		}
		
		```

	





4. `instanceof`比较操作符

	- 判断对象的运行类型是否为xx类型或xx的子类

	- 代码如下：

	- ```java
		public class poly {
		    public static void main(String[] args) {
		        B b = new B();
		        System.out.println(b instanceof B);
		        System.out.println(b instanceof A);
		
		        System.out.println("=====================");
		        A a = new B();
		        //instanceof 判断的是运行类型
		        System.out.println(a instanceof B);
		        System.out.println(a instanceof A);
		        System.out.println(a instanceof Object);
		
		        System.out.println("=====================");
		        a = new A();
		        System.out.println(a instanceof B);
		
		        String s = "hell";
		        //注意，以下语句无法编译
		        //System.out.println(s instanceof A);
		        //报错提示：Inconvertible types; cannot cast 'java.lang.String' to 'A'
		    }
		}
		
		class A {
		}
		
		class B extends A {
		}
		```



5. **动态绑定机制**

	- 调用对象方法时，该方法会和该对象的内存地址（也就是运行类型）相绑定。即，对象调用方法时，以运行类型为基准，进行**查找关系**

	- 属性无动态绑定机制

	- 代码如下：

	- ```java
		public class poly {
		    public static void main(String[] args) {
		        A a = new B();
		        //先进入A中sum()
		        //当前a的运行类型为B，由动态绑定机制，将调用B的getI()
		        //B的getI()返回B中的i，即23
		        //最终sum()将返回23+20=43
		        System.out.println(a.sum());
		
		        //知识点：向上转型 + 重写 + 查找关系
		        //B中有sum1()，故返回23+10=33
		        System.out.println(a.sum1());
		    }
		}
		
		class A {
		    public int i = 17;
		
		    public int getI() {
		        return i;
		    }
		
		    public int sum() {
		        //在这里写return this.getI() + 20;效果也是一样的
		        //this并不能改变动态绑定机制
		        return getI() + 20;
		    }
		
		    public int sum1() {
		        return i;
		    }
		}
		
		class B extends A {
		    public int i = 23;
		
		    public int sum1() {
		        return i + 10;
		    }
		
		    public int getI() {
		        return i;
		    }
		}
		```





6. 多态应用

	1. 多态数组
		- 数组定义为父类类型，里面存放的实际元素为子类类型
		- 调用重写的方法时，具体地实现要看子类类型
		- 要调用子类特有的方法时，可以先用`instanceof`判断，再用向下转型以使用该特有方法
	2. 多态参数

	- 形参为父类类型，实参可以为子类类型
	- 用法基本与多态数组一致







## Object类



1. Object类是所有类的基类，故所有类都可以使用Object类的成员



2. `equals`方法

	![屏幕截图(234)](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202061953289.png)

	1. 分析`equals`就要对比`==`和`equals`

		- `==`是运算符，可以判断基本类型和引用类型
		- `==`判断基本类型时，判断两者的值是否相等
		- `==`判断引用类型时，判断两者指向的地址是否相同
		- `equals`是object类中的方法，只能判断引用类型
		- 在Object类中，`equals`是判断地址是否相等。但其子类往往重写该方法，以判断内容是否想相等，如`String`类、`Integer`类

	2. 重写`equals`以判断内容是否相等

		- ```java
			public class Equals {
			    public static void main(String[] args) {
			        Cat cat1 = new Cat("李东风", 1.5);
			        Cat cat2 = new Cat("李东风", 1.5);
			        Cat cat3 = new Cat("臭卷宝", 2);//猜测应该是2岁。。。
			        //比较地址，不相等
			        System.out.println(cat1 == cat2);
			        //比较内容
			        System.out.println(cat1.equals(cat2));
			        System.out.println(cat1.equals(cat3));
			    }
			}
			
			class Cat {
			    private String name;
			    private double age;
			
			    public Cat(String name, double age) {
			        this.name = name;
			        this.age = age;
			    }
			
			    public boolean equals(Object obj) {
			        //obj是自己
			        if (obj == this)
			            return true;
			
			        if (obj instanceof Cat) {
			            Cat cat = (Cat) obj;
			            return this.name.equals(cat.name) && this.age == cat.age;
			        }
			        return false;
			    }
			}
			```





3. `hashCode()`方法

	![屏幕截图(235)](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202061956851.png)

	- 该方法能提高具有哈希结构的容器的效率——属于数据结构的范畴
	- 两个引用，如果指向同一个对象，则哈希值相同
	- 两个引用，如果指向不同对象，则哈希值不同
	- 哈希值由地址得来，但两者不同——其中一个原因是java程序在虚拟机上运行，对象的地址并不是计算机内存中的地址
	- 该方法可根据需求重写



4. `toString()`方法

	![屏幕截图(236)](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202062013232.png)

	- 该方法默认返回：全类名 + @ + 十六进制的哈希值。全类名为包名加上类名

	- 子类往往重写该方法，以返回属性信息

	- 打印对象或（作为字符串）拼接对象时，会自动调用对象的该方法

	- 代码如下：

	- ```java
		public class toString_ {
		    public static void main(String[] args) {
		        Cat cat1 = new Cat("李东风", 1.5);
		        Cat cat2 = new Cat("臭卷宝", 2.0);
		        Object o = new Object();
		
		        //原本的toString()
		        System.out.println(o.toString());
		        //经过重写的toString()
		        System.out.println(cat1.toString());
		        //打印对象时会自动调用对象的toString()方法
		        System.out.println(cat2);
		        //拼接对象时也会调用该方法
		        System.out.println("享受每一天吧~~~ " + cat2);
		    }
		}
		
		class Cat {
		    private String name;
		    private double age;
		
		    public Cat(String name, double age) {
		        this.name = name;
		        this.age = age;
		    }
		
		    @Override //alt + ins 自动生成
		    public String toString() {
		        return "Cat{" +
		                "name='" + name + '\'' +
		                ", age=" + age +
		                '}';
		    }
		}
		```



5. `finalize()`方法

	- 当对象被回收时（*），系统会自动调用该对象的该方法。子类可以重写`finalize`方法，以释放资源（如数据库连接、文件连接等），但一般不会重写该方法

	- （*）：何时回收对象：当某对象没有引用，JVM会判定该对象为垃圾对象。在某时刻（**）使用垃圾回收器来销毁对象，销毁对象前调用该对象的`finalize`方法——由此可见，`finalize`和析构器（destructor）类似

	- （**）：垃圾回收器的调用，由系统来决定。也可以使用`System.gc()`主动调用垃圾回收机制，但不一定立即触发该机制

	- 代码如下：

	- ```java
		public class test {
		    public static void main(String[] args) {
		        Person arthur = new Person("cockburnt");
		        //取消上述对象的引用，以使上述对象成为垃圾
		        arthur = null;
		
		        System.gc();
		        //输出时,下面这句和finalize中的语句谁先输出不确定
		        System.out.println("End of main()");
		    }
		}
		
		class Person {
		    private String name;
		
		    public Person(String name) {
		        this.name = name;
		    }
		
		    @Override
		    protected void finalize() throws Throwable {
		        System.out.println(name + "なくなった");
		    }
		}
		```





## 项目：零钱通（SmallChange）

1. 源代码：

	https://github.com/el-nino2020/java-hanshunping/tree/main/small_change

​	

2. 需求相关：

<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202090651460.png" alt="屏幕截图(237)" style="zoom: 33%;" />

<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202090652618.png" alt="屏幕截图(238)" style="zoom:33%;" />



3. 分析：

- 虽然这个**小**项目是在学完面向对象（中级）后学的，但知识点只覆盖继承之前，故写起来很轻松。
- 但在追求细节方面，由于掌握的知识点不够多，还是有不少缺点：
	- 不使用异常机制无法处理`nextDouble()`方法的非法输入问题；
	- `Date`和`SimpleDateFormat`类只是抄来用的，并没有学过
	- 没有文件I/O，所有操作都是在JVM上运行
	- `details`应该是动态数组，而非一个`String`，但前者也没有学



## 项目：房屋出租系统

1. 源代码：

https://github.com/el-nino2020/java-hanshunping/tree/main/house_rent

2. 需求相关：

<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202092006798.png" alt="屏幕截图(240)" style="zoom: 33%;" />

<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202092006258.png" alt="屏幕截图(241)" style="zoom: 33%;" />

<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202092006093.png" alt="屏幕截图(242)" style="zoom: 33%;" />

<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202092007172.png" style="zoom: 33%;" />

<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202092008764.png" alt="屏幕截图(244)" style="zoom: 33%;" />

<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202092008809.png" alt="屏幕截图(245)" style="zoom: 33%;" />

<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202110821478.png" alt="屏幕截图(250)" style="zoom: 33%;" />

<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202092009831.png" alt="屏幕截图(247)" style="zoom:50%;" />





3. 程序框架——分层模式

<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202100746012.png" alt="屏幕截图(248)" style="zoom: 33%;" />

- 程序框架图的目的：
	- 确定系统有哪些类
	- 明确类与类之间的调用关系
- 房屋出租系统的程序框架图如上图所示
- 工具类：实际开发中公司提供工具类和开发库，以提高开发效率。即，这个类是预先给定的。（在该项目中也是给定的）



4. 代码实现指导：

<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202110715919.png" alt="屏幕截图(249)" style="zoom: 33%;" />



5. 分析：
	- 这个项目的**重点**是分层模式，而代码实现比较次要。
		- `HouseView`作为界面层，负责全部的I/0，并将接受到的信息传给`HouseService`——业务层。
		- 业务层拥有基本的数据结构——array，负责存储`House`对象。并且，它通过`HouseView`中方法的参数传递，对数据作相应处理，然后将处理结果（`boolean`值，或者`House`对象）返还给`HouseView` 
		- `House`作为实体类，是一个数据单元。其用处更像是C++中的结构体，用来整合不同类型的数据。其方法多为对成员的直接操作，没有复杂的逻辑。
	- 说代码实现次要，有以下几点：
		- `Utility`类是现成的。如果自己写该工具类，代码编写难度将提高——要熟练运用现有I/0函数，还要有异常处理——虽然也没高到哪里去:sweat_smile:
		- 因为还没学异常处理，就没给`houses`设计扩容机制（我也不知道`new`会不会像C++中一样抛出异常），故它只是一个单纯的array
		- 如果不考虑`HouseService.find()`可以用二分查找优化这一点，`houses`的数据结构应该是链表，而非array







# 第7章：面向对象（高级）



## 类变量 / 静态变量

1. 快速入门：

	- 在类定义时，在某一属性前加上`static`，该属性就会被该类的所有对象共享

	- 注意区分：静态变量属于类，而不属于类的某一对象。前者是所有对象的抽象

	- 静态变量可以直接用`类名.静态变量名`访问

	- 代码实现：

	- ```java
		public class test {
		    public static void main(String[] args) {
		        Cat cat1 = new Cat("李东风");
		        Cat cat2 = new Cat("臭卷宝");
		
		        //以下三句访问的都是同一个变量
		        System.out.println(Cat.count);
		        System.out.println(cat1.count);
		        System.out.println(cat2.count);
		
		        cat1.count = 10;
		        System.out.println(cat2.count);
		    }
		}
		
		class Cat {
		    private String name;
		    public static int count = 0;
		
		    public Cat(String name) {
		        this.name = name;
		        ++Cat.count;
		    }
		}
		```



2. 类变量内存布局：
	- 静态变量被同一个类所有对象共享。即，在每一个对象中，静态变量实际都指向同一个地址，地址中才是静态变量的值
		- 在JDK8以前，静态变量存放在常量池的静态域中
		- JDK8以后，静态变量存放在堆中该类的原型类中
	- 静态变量在**类加载的时候被生成**。故没有对象被创建时也能够访问静态变量



3. 定义类变量

	```
	访问修饰符 static 数据类型 变量名;(推荐)
	static 访问修饰符 数据类型 变量名;
	```



4. 访问类变量
	- `类名.类变量名`或`对象名.类变量名`，一般使用前者
	- 类变量的访问权限和属性一致



5. 一些细节
	- 什么时候使用类变量？——当我们需要一个类的所有对象共享一个变量时
	- 变量名加上`static`称为类变量/静态变量，它被该类所有对象共享
	- 否则称为实例变量/普通变量/非静态变量——即属性，它被每个对象独享
	- 实例变量不能通过`类名.类变量名`来访问
	- 类变量的生命周期是随着类的加载开始，随着类的消亡而销毁



## 类方法 / 静态方法

1. 定义类方法：

	```
	访问修饰符 static 返回类型 方法名(参数列表){}(推荐)
	static 访问修饰符 返回类型 方法名(参数列表){}
	```



2. 调用类方法：

	```
	类名.类方法名(参数) (推荐)
	对象名.类方法名(参数)
	```

	- 调用类方法应遵从访问权限



3. 类方法使用场景
	- 当方法中不涉及与对象相关的成员，则可以将该方法设置为静态方法，以提高开发效率
	- 例如，`utils`工具类、`Math`类、`Arrays`类、`Collections`集合类
	- 在实际开发中，往往会将一些通用的方法设计为静态方法。例如，打印数组、排序等



4. 一些细节
	- 类方法不允许使用和对象有关的关键字，如`this`和`super`
	- **类方法只能访问静态成员**
	- 普通方法可以访问普通成员，也可以访问静态成员



## `main`方法

1. 解释`main`方法的形式：`public static void main(String[] args){}`

	- `main`方法由JVM调用

	- JVM需要调用类的`main`方法，因此访问权限必须是`public`

	- JVM在调用`main`方法时不必创建对象，因此需要加上`static`

	- `args`是执行`java`命令时传递给运行的类的`main`方法的参数

	- 代码如下：

	- ```java
		public class test {
		    public static void main(String[] args) {
		        for (int i = 0; i < args.length; i++) {
		            System.out.println(args[i]);
		        }
		        System.out.println("finished");
		    }
		}
		
		```

	- 在cmd中执行如下命令：`java 程序名 参数1 参数2`

	- 效果如下：

	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202140803032.png" alt="image-20220214080324955" style="zoom:33%;" />



2. 细节：

	- 由于`main`是静态方法，不能访问本类的非静态成员。需要访问时，要先创建本类的对象，再用对象名来访问

	- 代码如下：

	- ```java
		public class Test {
		    private String name = "lilith";
		
		    public static void main(String[] args) {
		        //下面这句话会报错，不符合static的使用规范
		        //System.out.println(name);
		
		        Test test = new Test();
		        //由本类访问自己的私有属性，合乎private的规则
		        System.out.println(test.name);
		    }
		}
		```



## 代码块

1. 定义相关：
	- 代码块，又称初始化块，属于类的成员
	- 代码块类似于方法：将逻辑语句封装在方法体中，用大括号{}包围起来
	- 但代码块没有方法名，没有返回类型，没有参数，只有方法体。且，代码块不通过类或对象显示调用，而是在加载类时，或创建对象时隐式调用



2. 基本语法：

	- ```
		[修饰符] {
			方法体
		};
		```

	- 修饰符要么不写，要么只能用`static`

	- 有`static`的代码块称为静态代码块，没有的称作普通代码块

	- 分号`;`可以写，也可以不写



3. 优点：

	- 代码块相当于另一种形式的构造器，是对构造器的补充，用于初始化操作

	- 使用场景：若多个构造器中有重复的语句，可以抽取到代码块中，提高代码复用性

	- 代码如下：

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        Screen screen = new Screen("佳能");
		        System.out.println("========================================");
		        Screen screen1 = new Screen("索尼", 1500);
		    }
		}
		
		class Screen {
		    //代码块总是先于构造器被调用
		    {
		        System.out.println("Loading: 0%");
		        System.out.println("Loading: 25%");
		        System.out.println("Loading: 75%");
		        System.out.println("Loading: 100%");
		    }
		
		    private String brand;
		    private double price;
		
		    public Screen(String brand, double price) {
		        this.brand = brand;
		        this.price = price;
		        System.out.println(this.brand + " " + this.price);
		    }
		
		    public Screen(String brand) {
		        this.brand = brand;
		        System.out.println(this.brand);
		    }
		}
		
		```



4. 细节：

	1. 静态代码块的作用，是**对类进行初始化**，它随着**类的加载**而执行，且只执行一次
	2. 类何时被加载？
		- 创建对象实例时
		- 创建子类对象实例时，父类也会被加载
		- 使用类的静态成员

	- 以上两条代码如下：

		```java
		public class Test {
		    public static void main(String[] args) {
		        //创建对象时类被加载
		        A a = new A();
		        //只会加载一次
		        A a1 = new A();
		        System.out.println("=========================");
		
		        //创建子类对象实例时，父类也会被加载
		        C c = new C();
		        System.out.println("=========================");
		
		        //调用静态成员时，类被加载
		        D.say();
		    }
		}
		
		class A {
		    static {
		        System.out.println("call static code block of A");
		    }
		}
		
		class B {
		    static {
		        System.out.println("call static code block of B");
		    }
		}
		
		class C extends B {
		    static {
		        System.out.println("call static code block of C");
		    }
		}
		
		
		class D {
		    static {
		        System.out.println("call static code block of D");
		    }
		
		    public static void say() {
		        System.out.println("call say() in D");
		    }
		}
		```

	3. 普通代码块，在创建对象时，会被隐式调用。且每被创建一次，就调用一次。如果使用静态成员，普通代码块不会被调用

	- 代码如下：

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        //创建对象时调用普通代码块
		        A a = new A();
		        //创建一次，调用一次
		        A a1 = new A();
		        System.out.println("=========================");
		        //使用静态成员不会调用普通代码块
		        System.out.println(a.n);
		    }
		}
		
		class A {
		    static {
		        System.out.println("call static code block of A");
		    }
		
		    {
		        System.out.println("call non-static code block of A");
		    }
		
		    public static int n = 10;
		}
		```

	4. 创建一个对象时，在**没有继承**时调用顺序如下：
		- 调用静态代码块和静态属性初始化。由于两者优先级相同，如果两者都存在，则按照定义顺序调用
		- 调用普通代码块和普通属性初始化。由于两者优先级相同，如果两者都存在，则按照定义顺序调用
		- 调用构造器

	- 代码如下：

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        A a = new A();
		    }
		}
		
		class A {
		    //构造器放在第一个并不影响最后被调用
		    public A() {
		        System.out.println("A的构造器");
		    }
		
		    static {
		        System.out.println("A的静态代码块");
		    }
		
		    private static int n1 = getN1();
		
		
		    private int nw = getN2();
		
		    {
		        System.out.println("A的普通代码块");
		    }
		
		    private static int getN1() {
		        System.out.println("call getN1()");
		        return 100;
		    }
		
		    private int getN2() {
		        System.out.println("call getN2()");
		        return 200;
		    }
		}
		
		```

	5. 代码块**继承相关**：
		- 构造器隐含了两句话：第一句是`super()`，第二句是调用普通代码块。
		- 而对于静态代码块和静态属性初始化，它们在类加载的时候就执行完成。因此先于构造器和普通代码块。

	- 代码如下：

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        B b = new B();
		    }
		}
		
		class A {
		    public A() {
		        System.out.println("A的构造器");
		    }
		
		    {
		        System.out.println("A的普通代码块");
		    }
		}
		
		class B extends A {
		    public B() {
		        //(1)super()
		        //(2)调用普通代码块
		        System.out.println("B的构造器");
		    }
		
		    {
		        System.out.println("B的普通代码块");
		    }
		}
		```

	6. 创建一个子类对象时，（**继承关系**），全部调用顺序如下：
		- 父类静态代码块和静态属性初始化（按定义顺序执行）
		- 子类静态代码块和静态属性初始化（按定义顺序执行）
		- 父类普通代码块和普通属性初始化（按定义顺序执行）
		- 父类构造器
		- 子类普通代码块和普通属性初始化（按定义顺序执行）
		- 子类构造器
		- 总结：以上就是结合了第4条和第5条的内容而成的
		- 代码这里省略，可以修改第4条的代码：新增`B`类继承`A`类，使用功能相同的属性初始化方法、代码块和构造器。然后创建`B`对象即可验证该规律的正确性。
	7. 静态代码块只能调用静态成员，普通代码块可以调用任意成员

	

## 单例设计模式

1. 什么是设计模式？
	- 设计模式是在大量的实践中总结和理论化之后**优选**的代码结构、编程风格和解决问题的思考方式



2. 什么是单例设计模式？
	- 单例，即单个实例。该模式是指采取一定方法，保证在**整个软件系统中**，某个类只能存在**一个**对象实例，并且该类提供一个取得实例的方法
	- 单例设计模式有两种方式：1）饿汉式；2）懒汉式
	- `java.lang.Runtime`是经典的单例模式



3. 单例设计模式一般步骤：
	- 构造器私有化
	- 类的内部创建对象
	- 向外暴露一个静态的公共方法——`getInstance`



4. 单例设计模式——饿汉式

	- ```java
		class A {
		    public A() {
		    }
		
		    private static A a = new A();
		
		    public static A getInstance() {
		        return a;
		    }
		}
		```

	- 饿汉是指：无论是否使用该对象，其都会被创建。具体地说，如果只使用该类的其他静态成员，该实例还是会被创建——这是一种浪费。



5. 单例设计模式——懒汉式

	- ```java
		class A {
		    public A() {
		    }
		
		    //默认为null
		    private static A a;
		
		    public static A getInstance() {
		        //第一次运行会创建对象，之后则直接返回该对象
		        if (a == null)
		            a = new A();
		        return a;
		    }
		}
		```

	- 懒汉：与饿汉相对，只有在使用对象时才会创建对象



6. 饿汉式与懒汉式
	- 最主要的区别在于创建对象的时机不同：饿汉式在类加载时就创建，懒汉式则在使用时创建
	- 懒汉式存在线程安全性问题——同时创建多个对象。而饿汉式不存在
	- 饿汉式存在资源浪费问题。懒汉式则不存在





## `final`关键字

1. 使用方式：
	- 当**不希望类被继承**时，可以用`final`修饰，例如`final Class Cat(){}`
	- 当**不希望**父类的某个方法被子类**重写**时，可以用`final`修饰，例如，`public final void f1(){}`——`f1()`是父类的方法
	- 当**不希望**类的某个属性**被修改**，可以用`final`修饰，例如：`public final double RATE = 0.04;`
	- 当不希望某个局部变量被修改，可以用`final`修饰，例如`final double TAX_RATE = 0.05;`
	- `final`类似于c++中的`const`，但更泛用



2. 细节相关

	1. `final`修饰的属性叫做常量，一般用AA_BBB_C的形式命名、

	2. `final`修饰的**属性必须在定义时赋值**，赋值可以在如下位置：

		- 定义时

		- 构造器中

		- 代码块中

		- 代码如下：

		- ```java
			class A {
			    //定义时
			    public final int N1 = 100;
			    public final int n2;
			    public final int n3;
			    //代码块中
			    {
			        n2 = 101;
			    }
			    //构造器中
			    public A() {
			        n3 = 102;
			    }
			}
			```

	3. 如果`final`修饰的属性时静态的，则初始化的位置只能是:one:定义时，:two:静态代码块中——不能在构造器中赋值的理由是明显的

	4. 如果类没有`final`修饰，但含有`final`方法。虽然该方法不能被重写，但该类可以被继承

		- 代码如下：

		- ```java
			public class Test {
			    public static void main(String[] args) {
			        new B().f1();
			    }
			}
			
			class A {
			    public final void f1() {
			        System.out.println("f1() in A");
			    }
			}
			
			class B extends A {
			}
			
			```

	5. 如果类已经被`final`修饰，则其方法没必要再用`final`修饰——没有继承，何来重写？

	6. `final`不能修饰构造器

	7. `final`和static 往往搭配使用，因为这样效率更高：**不会导致类加载**

		- 代码如下：

		- ```java
			public class Test {
			    public static void main(String[] args) {
			        System.out.println(A.n1);
			    }
			}
			
			class A {
			    //final 与 static 的顺序随意，但一般final在前
			    public final static int n1 = 100;
				//如果类加载，则下面代码块会被运行
			    //利用以上命题的逆否命题来验证
			    static {
			        System.out.println("A 静态代码块");
			    }
			}
			
			```

		- 这个应该接近c++中的`const`的全局变量

	8. 包装类（如`Integer`、`Boolean`）和`String`类是`final`类

	9. `final`可以**修饰形参**，例如：`public void f1(final int x, int y)`





## 抽象类

1. 快速入门

	- 当父类的某方法**不确定如何实现时**，可以用`abstract`来修饰。这样，该方法就是抽象方法。随后，需要用`abstract`修饰该类，使该类称为抽象类

	- 由上可得，只要类中有抽象方法，该类就是抽象类

	- 代码如下：

	- ```java
		//方法有abstract,类就必须有abstract,不然会报错
		abstract class Animal {
		    public String name;
		
		    //由于不知道动物喜欢吃什么，故该方法的实现没有意义
		    //故声明抽象类，待其子类来实现
		    public abstract void eat();
		
		    public Animal(String name) {
		        this.name = name;
		    }
		}
		
		```



2. 基本介绍

	- 用`abstract`修饰的类叫做抽象类，形式如下：

		- ```
			访问修饰符 abstract 类名{
			}
			```

	- 用`abstract`修饰的方法叫做抽象方法

	- 抽象类的价值更多在于设计，实现由子类完成

	- 抽象类在框架和设计模式中使用较多



3. 细节

	1. 抽象类**不能被实例化**

	2. 抽象类不一定要包含抽象方法

		- 以上两条，代码如下：

		- ```java
			public class Test {
			    public static void main(String[] args) {
			        //抽象类不允许实例化
			        //A a = new A();
			    }
			}
			
			//可以没有抽象方法
			abstract class A{
			    public int n1=10;
			}
			
			```

	3. 类一旦包含抽象方法，则该类必须有`abstract`修饰

	4. `abstract`**只修饰类和方法**，不修饰属性和其它的

	5. 抽象类作为类，可以有任意成员：非抽象方法、静态方法等

	6. 抽象方法不能有方法体`{}`

	7. 如果一个类继承抽象类，要么它实现**所有**抽象方法，要么它也是抽象类

		- 代码如下：

		- ```java
			public class Test {
			    public static void main(String[] args) {
			        //不允许实例化
			        //B1 b1 = new B1();
			
			        B2 b2 = new B2();
			        b2.f1();
			        b2.f2();
			    }
			}
			
			abstract class A {
			    public abstract void f1();
			
			    public abstract void f2();
			}
			
			//B1没有重写A的所有抽象方法，故还是抽象类
			abstract class B1 extends A {
			    @Override
			    public void f1() {
			        System.out.println("f1() in B1");
			    }
			}
			
			class B2 extends A {
			    @Override
			    public void f1() {
			        System.out.println("f1() in B2");
			
			    }
			
			    @Override
			    public void f2() {
			        System.out.println("f2() in B2");
			
			    }
			}
			```

	8. 抽象方法不能用`private`、`final`和`static`来修饰——因为它们矛盾



4. 抽象类用途——模板设计模式

	- 要求：

		- 有多个类，各自有`job()`方法，
		- 要求能够得到各自完成`job()`的时间

	- 实现方法：

		- 设计抽象类`Template`：
			- 实现方法`calculateTime()`，计算代码完成时间
			- 定义抽象方法`job()`
		- 设计子类`Sub`，继承`Template`，并实现`job()`方法

	- 代码如下：

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        new Sub().calculateTime("某个无穷级数近似估计");
		    }
		}
		
		abstract class Template {
		    public void calculateTime(String taskName) {
		        //该方法返回现在的毫秒数，以1970.1.1为开始时间
		        long start = System.currentTimeMillis();
		
		        //由于动态绑定机制，将调用子类的job方法
		        job();
		
		        long finish = System.currentTimeMillis();
		        System.out.println(taskName + " 执行的时间是： "
		                + (finish - start));
		    }
		
		    public abstract void job();
		}
		
		class Sub extends Template {
		    @Override
		    public void job() {
		        int sign = 1;
		        double ans = 0;
		        for (int i = 1; i < 1000000; i += 2) {
		            ans += sign / (double) i;
		            sign = -sign;
		        }
		    }
		}
		```

	- 编写不同的子类以实现不同的`job`，再调用`calculateTime`，即可求出相应的运行时间

	- 这里利用动态绑定机制，巧妙地回避了要将方法作为参数传递给`calculateTime`类的问题





## 接口（interface)

1. 基本介绍

	- 接口就是给出一些没有实现的方法，封装到一起。再根据具体情况，把这些方法写出来。

	- 语法如下：

	- ```
		interface 接口名{
			属性;
			方法;
		}
		class 类名 implements 接口名{
			类属性;
			类方法;
			必须实现的接口的抽象方法;
		}
		```

	- JDK 7.0及以前，接口的所有方法都是抽象方法

	- JDK 8.0及以后，接口可以有`static`方法和`default`方法，即可以有具体实现

	- 代码如下：

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        A a = new A();
		        a.f1();
		    }
		}
		
		interface InterA {
		    public int n1 = 10;
		
		    //抽象方法，这里加不加abstract都可以
		    public void f1();
		
		    //默认方法
		    default public void f2() {
		        System.out.println("f2() in InterA");
		    }
		
		    //静态方法
		    public static void f3() {
		        System.out.println("f3() in InterA");
		    }
		}
		
		class A implements InterA {
		    public int n2 = 9;
		
		    public void f4() {
		    }
		
		    @Override
		    public void f1() {
		        System.out.println("f1() in A");
		    }
		}
		```





2. 应用场景：

	- 在开发软件时，项目经理可以定义接口，然后由程序员具体实现。

	- 举例来说，2个程序员，编写2个类，实现对mysql和Oracle数据库的`connect`方法和`close`方法

	- 代码如下：

	- ```java
		
		public class Test {
		    public static void main(String[] args) {
		        Mysql mysql = new Mysql();
		        callInterface(mysql);
		        System.out.println("======================");
		        Oracle oracle = new Oracle();
		        callInterface(oracle);
		    }
		
		    public static void callInterface(InterA interA) {
		        interA.connect();
		        interA.close();
		    }
		}
		
		interface InterA {
		    public void connect();
		
		    public void close();
		}
		
		class Mysql implements InterA {
		    @Override
		    public void connect() {
		        System.out.println("连接Mysql数据库");
		    }
		
		    @Override
		    public void close() {
		        System.out.println("关闭Mysql数据库");
		    }
		}
		
		class Oracle implements InterA {
		    @Override
		    public void connect() {
		        System.out.println("连接Oracle数据库");
		    }
		
		    @Override
		    public void close() {
		        System.out.println("关闭Oracle数据库");
		    }
		}
		```

	- 由于接口的性质，程序员必须实现指定的方法。这样可以统一调用



3. 细节

	1. 接口不能被实例化

	2. 接口中，**所有方法**都是`public`方法（故写不写`public`都一样）。抽象方法可以不用`abstract`修饰

	3. 一个普通类实现接口，必须实现该接口的所有方法

	4. 抽象类实现接口，可以不用实现其方法

	5. 一个类可以实现多个接口

		- 代码如下：

		- ```java
			interface A {
			}
			
			interface B {
			}
			
			class CC implements A, B {
			}
			```

	6. 接口中的属性**默认**是`public static final`，故定义时可以只写`int n = 10;`这种形式

	7. 由6可得，接口属性的访问形式：`接口名.属性名`

	8. 接口不能继承类，但可以继承多个接口

		- 代码如下：

		- ```java
			interface A {
			}
			
			interface B {
			}
			
			interface C extends A, B {
			}
			```

	9. 接口的修饰符只能是`public`和默认，这和类一样

	- java居然在接口中实现了多继承:exclamation::exclamation::exclamation:



4. 接口 vs 继承

	- 两者解决的问题不同：

		- 继承的价值：解决代码的复用性和可维护性
		- 接口的价值：设计规范（方法），以待其他类去实现

	- 接口比继承更灵活：继承需要满足is - a 关系，接口只需要满足like - a关系

	- 接口在一定程度上实现代码解耦——即：接口规范性和动态绑定机制

	- 看以下的例子：

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        Students li_hua = new Students("Li Hua");
		        li_hua.eat();
		        li_hua.study();
		        li_hua.programming();
		        li_hua.training();
		    }
		}
		
		class Human {
		    public String name;
		
		    public Human(String name) {
		        this.name = name;
		    }
		
		    public void eat() {
		        System.out.println(name + "is eating food");
		    }
		}
		
		interface Programmers {
		    void programming();
		}
		
		interface Athletes {
		    void training();
		}
		
		
		//在报错的一行使用Alt + Enter,可以直接生成相应方法
		class Students extends Human implements Programmers, Athletes {
		
		    public Students(String name) {
		        super(name);
		    }
		
		    public void study() {
		        System.out.println(name + "is studying");
		    }
		
		    @Override
		    public void programming() {
		        System.out.println(name + "is programming like a programmer");
		    }
		
		    @Override
		    public void training() {
		        System.out.println(name + "is training like an athlete");
		
		    }
		}
		```

	- 当子类想要**拓展功能**时，可以通过实现接口的方式拓展

	- 接口可以理解为对单继承机制的一种补充



5. 接口的多态特性

	1. 向上转型：

		- 接口引用可以指向实现了接口的类的对象

		- 代码如下：

		- ```java
			public class Test {
			    public static void main(String[] args) {
			        InA inA = new B1();
			        inA = new B2();
			    }
			}
			
			interface InA {
			}
			
			class B1 implements InA {
			}
			
			class B2 implements InA {
			}
			
			```

	2. 向下转型：

		- 代码如下：

		- ```java
			public class Test {
			    public static void main(String[] args) {
			        Usb[] usbs = new Usb[2];
			
			        usbs[0] = new Phone();//向上转型
			        usbs[1] = new Camera();
			
			        for (int i = 0; i < usbs.length; i++) {
			            usbs[i].work();//动态绑定
			            
			            if (usbs[i] instanceof Phone)
			                ((Phone) usbs[i]).call();//向下转型
			            else if (usbs[i] instanceof Camera)
			                ((Camera) usbs[i]).takePhoto();
			        }
			    }
			}
			
			interface Usb {
			    void work();
			}
			
			class Phone implements Usb {
			    @Override
			    public void work() {
			        System.out.println("A phone is working");
			    }
			
			    public void call() {
			        System.out.println("A phone is calling");
			    }
			}
			
			class Camera implements Usb {
			    @Override
			    public void work() {
			        System.out.println("A Camera is working");
			    }
			
			    public void takePhoto() {
			        System.out.println("A Camera is taking photo");
			    }
			}
			```

	3. 接口的多态传递

		- 代码如下：

		- ```java
			public class Test {
			    public static void main(String[] args) {
			        //接口A的引用也能指向C,即使不是直接实现
			        A a = new C();
			        B b = new C();
			    }
			}
			
			interface A {
			    void f();
			}
			
			interface B extends A {
			}
			
			class C implements B {
			    //C也必须实现接口A中的方法
			    @Override
			    public void f() {
			    }
			}
			```







## 内部类

1. 基本介绍：

	- 一个类的内部又完整地嵌套了另一个类。被嵌套的类称为内部类（inner class），嵌套其他类的类称作外部类（outer class）。内部类是类的第五大成员——另外四个：属性、方法、构造器、代码块

	- 基本语法：

	- ```java
		class Outer{//外部类
			class Inner{//内部类
			
			}
		}
		class Other{//外部其他类
		}
		```

	- 内部类分类：

		- 定义在外部类局部位置（方法内）：
			- :one:局部内部类（有类名）
			- :two:匿名内部类（无类名）
		- 定义在外部类成员位置：
			- :three:成员内部类（无`static`）
			- :four:静态内部类（有`static`）



2. 局部内部类

	- 局部内部类时定义在外部类的局部位置，比如方法中，且有类名

	- 它可以**直接访问外部类的私有成员**

	- 前面不能添加访问修饰符，但可以用`final`修饰——这是它作为局部变量而言

	- 作用域：仅在定义它的方法或代码块中

	- 外部类访问局部内部类的成员：先创建对象，再访问

	- 代码如下：

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        A a = new A();
		        a.f2();
		    }
		}
		
		class A {
		    private int n = 10;
		
		    public void f1() {
		        System.out.println("f1() in A");
		    }
		
		    public void f2() {
		        class B {
		            public void f3() {
		                //可以直接访问外部类所有成员
		                f1();
		                System.out.println("n = " + n);
		            }
		
		            private int n2 = 7;
		        }
		        
		        //先创建对象，再使用
		        B b = new B();
		        b.f3();
		        System.out.println("n2 = " + b.n2);
		    }
		}
		```

	- 外部其他类不能访问局部内部类，因为后者只是一个局部变量

	- 如果外部类和局部内部类成员重名时，遵从就近原则。如果想访问外部类成员，可以用`外部类名.this.成员`——`外部类名.this`代表外部类的对象

	- 代码如下：

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        A a = new A();
		        a.f2();
		    }
		}
		
		class A {
		    private int n = 10;
		
		    public void f2() {
		        class B {
		            public void f3() {
		                System.out.println("B: n = " + n);
		                System.out.println("A: n = " + A.this.n);
		            }
		
		            private int n = 7;
		        }
		        B b = new B();
		        b.f3();
		    }
		}
		```





3. 匿名内部类

	1. 基本介绍与其本质：

		- 基本语法：

		- ```
			new 类名或接口名(参数列表){
				类体
			};
			```

		- 代码（基于接口）：

		- ```java
			public class Test {
			    public static void main(String[] args) {
			        B b = new B();
			        b.f1();
			    }
			}
			
			interface IA {
			    void cry();
			}
			
			class B {
			    void f1() {
			
			        IA cat = new IA() {
			            @Override
			            public void cry() {
			                System.out.println("miao~~~");
			            }
			        };
			        cat.cry();
			        //匿名内部类的名字是外部类名字+$1
			        System.out.println("该匿名内部类的名字是： " + cat.getClass());
			    }
			}
			```

		- 当需求为：使用接口`IA`，并创建对象时。同时，该类只会使用一次，以后不再使用。那么，与其定义一个类来实现该接口，不如使用匿名内部类来简化开发

		- 代码中，`cat`的编译类型是`IA`，运行类型是该匿名内部类——按照规则，应该叫做`B$1`

		- JDK在底层按如下方式定义匿名内部类，然后立即创建对象，把地址返回给`cat`：

			- ```java
				class B$1 implements A{
				    @Override
				    public void cry() {
				    	System.out.println("miao~~~");
				    }
				}
				```

		- 该匿名内部类只在此使用一次，此后就消失了（”匿名“的双重含义：该类没有名字；该类的定义是隐式进行的）。但`cat`对象在方法中一直存在

		- 代码实现（基于类）：

		- ```java
			public class Test {
			    public static void main(String[] args) {
			        B b = new B();
			        b.f1();
			    }
			}
			
			class Animal {
			    public Animal(String name) {
			        System.out.println("The Animal is called: " + name);
			    }
			
			    public void test() {
			        System.out.println("Animal中的test");
			    }
			}
			
			class B {
			    void f1() {
			        Animal cat1 = new Animal("臭卷宝") {
			            @Override
			            public void test() {
			                System.out.println("匿名内部类中的test()");
			            }
			        };
			        //匿名内部类的名字是外部类名字+$1
			        //如果出现第二个匿名内部类，则名字后面变成$2
			        System.out.println("该匿名内部类的名字是： " + cat1.getClass());
			        cat1.test();
			
			        System.out.println("==============================");
			        //注意两者有区别
			        Animal animal = new Animal("李东风");
			        System.out.println("该匿名内部类的名字是： " + animal.getClass());
			        animal.test();
			    }
			}
			```

		- `cat1`的运行类型的匿名内部类的定义是这样的：

			- ```java
				class B$1 extends Animal{
				    @Override
				    public void test() {
				    	System.out.println("匿名内部类中的test()");
				    }
				}
				```

			- 注意，在这里不需要定义构造器，而是直接调用`Animal`的有参构造器——这不是什么大问题，因为匿名内部类的使用大多为了方法的实现和重写

		- 由于本质是继承，类体为空亦可。但如果`Animal`是抽象类，该匿名内部类必须实现所有抽象方法

	2. 细节:

	- 匿名内部类的语法，既有定义类的特征，也有创建对象的特征。因此，也可以直接创建匿名对象，并使用其方法

		- 代码如下：

		- ```java
			public class Test {
			    public static void main(String[] args) {
			        B b = new B();
			        b.f1();
			    }
			}
			
			class Animal {
			    public void test() {
			        System.out.println("Animal中的test");
			    }
			}
			
			class B {
			    void f1() {
			        new Animal() {
			            @Override
			            public void test() {
			                System.out.println("匿名内部类中的test()");
			            }
			        }.test();
			    }
			}
			```

	- 匿名内部类可**以直接访问外部类的私有成员**

	- 它不能添加访问修饰符

	- 作用域：仅在定义它的方法或代码块中

	- 外部其他类不能访问匿名内部类

	- 若外部类和匿名内部类成员重名，匿名内部类访问遵从就近原则。访问外部类的成员，可以用`外部类名.this.成员名`



4. 使用场景：

	- 匿名内部类作为实参直接传递，简洁高效

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        Cellphone cellphone = new Cellphone();
		        //直接传递匿名内部类的对象
		        cellphone.clock(new Bell() {
		            @Override
		            public void ring() {
		                System.out.println("起床啦");
		            }
		        });
		        cellphone.clock(new Bell() {
		            @Override
		            public void ring() {
		                System.out.println("太阳烤屁股啦");
		            }
		        });
		    }
		}
		
		interface Bell {
		    void ring();
		}
		
		class Cellphone {
		    void clock(Bell bell) {
		        bell.ring();//动态绑定
		    }
		}
		```

	- 如果显式地定义了实现`Bell`的类，却只用一次，这样显得很死。不如在需要时创建匿名内部类对象，只不过这次是在参数位置创建的。

	- 每次创建匿名内部类时可以修改实现的方法，更灵活



4. 成员内部类

	- 它是指定义在成员位置上的类

	- 它可以直接访问外部类的私有成员

	- 可以添加任意访问修饰符——与成员相同

	- 它的作用域和外部类的其他成员一样，为整个类体——成员内部类可以访问外部类的私有成员

	- 外部类访问内部类成员：先创建对象，再访问

	- 代码如下：

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        A a = new A();
		        a.f1();
		    }
		}
		
		class A {
		    private int n = 10;
		
		    //成员内部类的定义
		    private class B {
		        public void g1() {
		            System.out.println("n = " + n);
		        }
		    }
		
		    public void f1() {
		        B b = new B();
		        b.g1();
		    }
		}
		```

	- 外部其他类访问成员内部类的两种方式：

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        //第一种方法：通过外部类直接创建
		        //注意这一语法：如同访问成员一样，访问内部类对象
		        A a = new A();
		        A.B b = a.new B();
		        //当然，也可以这样：
		        A.B b1 = new A().new B();
		
		        //第二种方法：通过方法返回成员内部类对象
		        A.B b2 = a.getBInstance();
		    }
		}
		
		class A {
		    //注意B的访问修饰符。若为private，则无法在Test类中新建对象
		    public class B {
		    }
		
		    public B getBInstance() {
		        return new B();
		    }
		}
		```

	- 外部类和内部类成员重名时，依旧遵从就近原则。访问外部类成员用`外部类名.this.成员名`





5. 静态内部类

	- 它是指定义在外部类的成员位置上，且有`static`修饰

	- 它可以**直接访问外部类私有的静态成员**，但不能直接访问非静态成员

	- 可以添加任意访问修饰符

	- 作用域为整个类体

	- 外部类访问静态内部类：创建对象，再访问

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        new A().f1();
		    }
		}
		
		class A {
		    public int a = 11;
		    private static int n = 19;
		
		    //能直接访问的只有A的静态成员
		    public static class B {
		        public void g1() {
		            System.out.println("n=" + n);
		        }
		    }
			//创建对象，再访问
		    public void f1() {
		        B b = new B();
		        b.g1();
		    }
		}
		```

	- 外部其他类访问静态内部类的几种方式：

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        //第一种：直接创建对象————静态成员可以直接用类名访问
		        A.B b = new A.B();
		        //第二种：利用方法返回。这里当然也可以使用非静态方法
		        A.B b2 = A.getB();
		    }
		}
		
		class A {
		    public static class B {
		    }
		
		    public static B getB() {
		        return new B();
		    }
		}
		```

	- 如果外部类和静态内部类成员重名，静态内部类访问时遵从就近原则。如果想访问外部类的成员，可以用`外部类名.成员名`访问





# 第8章：枚举和注解



## 枚举的引出与介绍（enumeration）

1. 需求：创建`Season`对象

	- 设计如下：

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        Season spring = new Season("春天", "樱花盛开的季节");
		    }
		}
		
		class Season {
		    private String name;
		    private String description;
		
		    public Season(String name, String description) {
		        this.name = name;
		        this.description = description;
		    }
		
		    public String getName() {return name;}
		    public void setName(String name) {this.name = name;}
		    public String getDescription() {return description;}
		    public void setDescription(String description) { this.description = description;}
		}
		```
		
	- 但是，`Season`的对象应该是四个常量——不能创建更多对象，也不能修改已有的对象
	
	- 这样的设计显然是不合理的。于是，引出枚举



2. 枚举的介绍
	- 枚举，enumeration，简称enum
	- 枚举是一组常量的集合
	- 也可以理解为：枚举是一种特殊的类，里面只包含一组有限的特定对象



3. 枚举的两种实现方法
	- :one:自定义类
	- :two:使用`enum`关键字





## 自定义枚举类

1. 基本方法：
	- 构造器私有化
	- 本类内部创建一组对象
	- 对外暴露对象：对枚举对象使用`public final static`修饰，实现底层优化
	- 不提供set方法，因为枚举对象通常为只读。但可以提供get方法
	- 枚举对象名通常全部大写——常量的命名规范
	- 枚举对象根据需要，可以有多个属性



2. 代码实现：

	```java
	public class Test {
	    public static void main(String[] args) {
	        System.out.println(Season.SPRING);
	        System.out.println(Season.WINTER);
	    }
	}
	
	class Season {
	    private String name;
	    private String description;
	
	    public final static Season SPRING = new Season("春天", "樱花盛开");
	    public final static Season SUMMER = new Season("夏天", "艳阳高照");
	    public final static Season AUTUMN = new Season("秋天", "红叶飘飘");
	    public final static Season WINTER = new Season("冬天", "万里雪飘");
	
	    private Season(String name, String description) {
	        this.name = name;
	        this.description = description;
	    }
	
	    public String getName() {
	        return name;
	    }
	
	    public String getDescription() {
	        return description;
	    }
	
	    //这个方法和枚举无关
	    @Override
	    public String toString() {
	        return name + description;
	    }
	}
	```

	

## `enum`关键字

1. 语法相关：

	- 使用`enum`关键字开发枚举类。这个类会默认继承`Eunm`类，且自动被`final`修饰——可以用`javap`命令查看
	- 枚举对象的定义用以下形式：`对象名(参数列表)`，参数列表对应相应的构造器
	- 如果使用无参构造器，对象名后面的`()`可以不加
	- 有多个枚举对象时，使用`,`间隔，最后一个对象后面才是`;`
	- 枚举对象必须放在枚举类最前面——即其他所有成员之前

2. 代码实现：

	```java
	public class Test {
	    public static void main(String[] args) {
	        System.out.println(Season.SPRING);
	        System.out.println(Season.WINTER);
	    }
	}
	
	//枚举类和一般类的定义方式还是很接近的
	enum Season {
	    SPRING("春天", "樱花盛开"),
	    SUMMER("夏天", "艳阳高照"),
	    AUTUMN("秋天", "红叶飘飘"),
	    WINTER("冬天", "万里雪飘");
	
	    private String name;
	    private String description;
	
	    //提示：Modifier 'private' is redundant for enum constructors
	    private Season(String name, String description) {
	        this.name = name;
	        this.description = description;
	    }
	
	    public String getName() {
	        return name;
	    }
	
	    public String getDescription() {
	        return description;
	    }
	
	    //这个方法和枚举无关
	    @Override
	    public String toString() {
	        return name + description;
	    }
	}
	```



3. `Enum`常用方法

	- `toString()`：`Enum`类重写过，返回该对象的名称（常量名）

		- ```java
			public class Test {
			    public static void main(String[] args) {
			        Gender gender = Gender.MALE;
			        System.out.println(gender);	}}
			enum Gender {MALE, FEMALE;}
			```

	- `name()`：返回常量名

	- `ordinal()`：返回当前对象在枚举序列中的序号（从0开始）

	- `values()`：静态方法，以数组形式返回枚举类中所有常量

	- `valueOf(String str)`：静态方法，将`str`转换成某枚举对象，并返回。该枚举对象的名称必须是`str`，否则抛出异常

	- `compareTo(Enum other)`：比较两个枚举常量的序号，并返回其差值。基本语法类似于`return this.ordinal() - other.ordinal()`

	- 代码如下（只给出`main`方法，省略`Season`枚举类的定义）：

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        Season season = Season.WINTER;
		        System.out.println(season.name());
		        System.out.println(season.ordinal());
		
		        System.out.println("===================");
		        Season[] values = Season.values();
		
		        //增强for循环，和c++类似，但不能用auto
		        for (Season itr : values) {
		            System.out.println(itr);
		        }
		
		        System.out.println("===================");
		        System.out.println(Season.valueOf("SPRING"));
		        System.out.println(season.compareTo(Season.SUMMER));
		    }
		}
		```



4. 细节
	- `enum`后不能再继承其他类，因为枚举类会隐式继承`Enum`类，而java是单继承
	- 枚举类和普通类一样，可以实现接口



5. 枚举和`switch`

	- 代码如下：（省略`Season`枚举类的定义）

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        Season season = Season.AUTUMN;
		        switch (season) {
		                //不需要写枚举类名，直接写常量名即可
		            case SPRING:
		                System.out.println("今は春だ");
		                break;
		            case SUMMER:
		                System.out.println("今は夏だ");
		                break;
		            case AUTUMN:
		                System.out.println("今は秋だ");
		                break;
		            case WINTER:
		                System.out.println("今は冬だ");
		        }
		    }
		}
		```









## 基本注解类型（Annotation）



1. 注解介绍
	- 注解（Annotation)，也称为元数据（Metadata），用于修饰解释包、类、方法、属性、构造器、局部变量等数据信息
	- 和注释一样，注解不影响程序逻辑。但注解可以被编译或运行，相当于在代码中嵌入补充信息
	- 在Java SE中，注解的使用比较简单。在Java EE中，注解占据更重要的角色。
2. 使用方法：
	- 使用注解时要在其前面添加`@`符号，并把该注解当成一个修饰符使用，用于修饰它支持的程序元素
	- 三个基本的注解：
		- :one:`@Override`：限定某个方法，它重写父类的方法
		- :two:`@Deprecated`：表示某个程序元素（类、方法等）已过时
		- :three:`@SuppressWarning`：抑制编译器警告



3. `@Override`注解：

	- 限定某个方法：它重写父类的方法。该注解只能用于方法：

	- ```java
		class A{
		    public void f1(){}
		}
		class B extends A{
		    @Override
		    public void f1() {
		        super.f1();
		    }
		}
		```

	- 如果子类确实重写了父类的方法，不使用`@Override`也无所谓

	- 但如果写上`@Override`，则表示指定重写父类方法，并且会从编译层面验证：编译器会检查是否真的重写了父类方法。是的话，编译通过，否则编译出错

	- `@Override`的定义如下：

		- ```java
			@Target(ElementType.METHOD)
			@Retention(RetentionPolicy.SOURCE)
			public @interface Override {
			}
			```

		- 在这里，`@interface`表示这是一个注解类，与接口无关。

		- `@Target`是修饰注解的注解，称作元注解

4. `@Deprecated`

	- 用于表示某个程序元素已经过时。注意，过时不代表不能使用，只是**不建议**用

	- 可以修饰方法、类、字段、包和参数等

	- 该注解的作用是：可以做到新旧版本的兼容和过渡

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        A a = new A();
		        //注意程序元素上的横线
		        System.out.println(a.message);
		        a.outputMessage();
		    }
		}
		
		class A {
		    @Deprecated
		    public String message;
		
		    @Deprecated
		    public void outputMessage() {
		    }
		}
		
		```





5. `@SuppressWarnings`

	- 当不希望看到某条警告时，可以用该注解不显示警告

	- 基本语法：`@SuppressWarnings({"AAA","BBB"})`

	- `AAA`可以是如下一些警告：

	- ![screencapture-cnblogs-fsjohnhuang-p-4040785-html-2022-02-19-15_25_00](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202191549865.png)

	- 代码演示：

	- ```java
		import java.util.ArrayList;
		
		public class Test {
		    @SuppressWarnings({"unused"})
		    public static void main(String[] args) {
		        //i没被使用过
		        int i = 1;
		    }
		}
		
		@SuppressWarnings({"all"})
		//A没被使用过
		class A {
		    public void f1() {
		        //这里没有指定类型
		        ArrayList arrayList = new ArrayList();
		    }
		}
		```

	- `@SuppressWarnings`放的位置很重要：放在类前面作用于整个类，放在方法前作用于整个方法



## 元注解

1. 基本介绍
	- JDK的元注解用于修饰其他注解
	- 元注解的种类：
		- :one:`Retention`
		- :two:`Target`
		- :three:`Documented`
		- :four:`Inherited`



2. `@Retention`

	- 用于指定注解可以保留多长时间

	- 该注解包含一个`RetentionPolicy`类型的成员变量，使用该注解时为其`value`成员变量指定值

	- 可以传入的值如下：

		- :one:`RetentionPolicy.SOURCE`：只存在于源码层面。编译器使用后，将丢弃该注解
		- :two:`RetentionPolicy.CLASS`：这是该注解的默认值。编译器会将该注解记录在`.class`文件中，但运行程序时，JVM不会保留注释
		- :three:`RetentionPolicy.RUNTIME`：与:two:不同，JVM会保留注释。
		- 可见，从:one:到:three:，注解的存在时间越来越长

	- 代码：

		- ```java
			@Target(ElementType.METHOD)
			@Retention(RetentionPolicy.SOURCE)
			public @interface Override {
			}
			```

		- `@Override`的作用是在编译时验证是否有重写，之后将不起作用

		



3. `@Target`

	- 用于指定被修饰的注解能够修饰那些程序元素。

	- 该元注解包含一个名为`value`的成员变量。后者的类型是`ElementType[]`

	- 代码：

		- ```java
			@Target({TYPE, FIELD, METHOD, PARAMETER, CONSTRUCTOR, LOCAL_VARIABLE})
			@Retention(RetentionPolicy.SOURCE)
			public @interface SuppressWarnings {
			    String[] value();
			}
			```

		- ```java
			@Documented
			@Retention(RetentionPolicy.RUNTIME)
			@Target(ElementType.ANNOTATION_TYPE)
			public @interface Target {
			    ElementType[] value();
			}
			```

		- ```java
			public enum ElementType {
			    /** Class, interface (including annotation type), or enum declaration */
			    TYPE,
			
			    /** Field declaration (includes enum constants) */
			    FIELD,
			
			    /** Method declaration */
			    METHOD,
			
			    /** Formal parameter declaration */
			    PARAMETER,
			
			    /** Constructor declaration */
			    CONSTRUCTOR,
			
			    /** Local variable declaration */
			    LOCAL_VARIABLE,
			
			    /** Annotation type declaration */
			    ANNOTATION_TYPE,
			
			    /** Package declaration */
			    PACKAGE,
			
			    /**
			     * Type parameter declaration
			     *
			     * @since 1.8
			     */
			    TYPE_PARAMETER,
			
			    /**
			     * Use of a type
			     *
			     * @since 1.8
			     */
			    TYPE_USE
			}
			```





4. `@Documented`

	- 用于指定某注解在`javadoc`生成文档时是否会被包括在内，即阅读文档时能否看到这一注解

	- 例如：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202191725599.png" alt="image-20220219172511511" style="zoom: 33%;" />

	- 代码：

		- ```java
			@Documented
			@Retention(RetentionPolicy.RUNTIME)
			@Target(value={CONSTRUCTOR, FIELD, LOCAL_VARIABLE, METHOD, PACKAGE, PARAMETER, TYPE})
			public @interface Deprecated {
			}
			```

	- 定义为`Documented`的注解必须设置`Rentention`的值为`RUNTIME`



5. `@inherited`
	- 被修饰的注解将具有继承性。如果某个类使用了`inherited`的注释，其子类将自动拥有该注释
	- 该元注解在实际应用中，使用较少



# 第9章：异常



## 异常的概念

1. 基本概念
	- 在Java中，将程序执行中发生的不正常情况称为异常
	- 而开发过程中的语法错误和逻辑错误不是异常



2. 执行过程中发生的异常事件可分为两大类：
	1. Error（错误）：JVM无法解决的严重问题。如StackOverflow（栈溢出）和OOM（out of memory）。这是严重错误，将会导致程序崩溃
	2. Exception：其它因编程错误或偶然的外在因素导致的一般性问题，可以使用针对性代码进行处理。如空指针访问或试图读取不存在的文件。Exception分为两类：
		- :one:：运行时异常
		- :two:：编译时异常（编译时编译器检测出的异常）





## 异常体系图

<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202201312085.png" alt="image-20220220131221925" style="zoom: 50%;" />

<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202201311700.png" alt="image-20220220131157539" style="zoom: 50%;" />

- 异常分为两大类：运行异常和编译异常
- 对于运行异常，编译器检测不出来。一般是指编程的逻辑错误，是程序员应该避免出现的异常。`java.lang.RuntimeException`类及其子类都是运行异常
- 运行异常非常普遍，故可以不作处理。如果全处理，会对程序可读性和运行效率产生影响
- 编译异常，是编译器指出的必须处理的异常
- 由图中可知，`Error`和`Exception`并列；`RuntimeException`和其它编译异常并列。而`Throwable`是所有异常类的父类



## 常见运行异常

1. `NullPointerException`空指针异常

	- 当程序试图在需要对象的地方使用`null`时，抛出该异常

	- ```java
		String s = null;
		System.out.println(s.length());
		```



2. `ArithmeticException`算术异常

	- ```java
		System.out.println(1 / 0);
		```



3. `ArrayIndexOutOfBoundException`数组下标越界异常

	- 当索引为负，或者大于等于数组长度时，该索引为非法索引，会抛出异常

	- ```java
		int[] arr = {1, 2};
		System.out.println(arr[2]);
		```



4. `ClassCastException`类型转换异常

	- 试图将对象强制转换为不是实例的子类时，抛出异常

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        A b = new B();
		        C c=(C) b;    }}
		class A{}
		class B extends A{}
		class C extends A{}
		```



5. `NumberFormatException`数字格式异常

	- 当程序试图将字符串转换成数值类型时，字符串的内容无法转换为该类型时，抛出异常

	- ```java
		String s = "hello";
		System.out.println(Integer.parseInt(s));
		```

	- 使用该异常，可以确保输入内容为数字







## 异常处理

1. 异常处理的方式：
	- :one:：`try-catch-finally`：程序员在代码中捕获发生的异常，并自行处理
	- :two:：`throws`：将发生的异常抛出给当前方法的调用者（别的方法），最顶级的调用者是JVM（它调用`main`方法）



2. `try-catch-finally`处理机制示意图：

	- 基本语法：

	- ```java
		try{
		 	代码1
		}catch (Exception e){
		    代码2
		}
		finally{
		    代码3
		}
		```

	- `try`中的代码1是可能会有异常的代码

	- 当发生异常时，系统将异常封装成`Exception`对象`e`，并传递给`catch`，执行代码2

	- 代码2中，程序员自己处理异常

	- 不管`try`中是否有异常发生，都会执行`finally`中的代码3。故一般在这里释放资源

	- 如果`try`中异常不发生，程序跳过`catch`，直接执行`finally`中的代码



3. `throws`处理机制示意图
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202201512862.png" alt="image-20220220151253504" style="zoom:50%;" />
	- 按照程序运行顺序，JVM调用`main`；`main`再调用`f1`方法；`f1`再调用`f2`方法
	- 如果`f2`出现异常，它可以使用`try`自行处理，也可以用`throws`将异常抛给`f1`
	- `f1`接收到异常。同样，它可以用`try`处理，或者使用`throws`继续将异常抛给自己的上级调用者`main`
	- 若`main`继续使用`throws`，将异常传递给JVM。JVM会输出异常信息，并退出程序。
	- 如果程序员没有显式地（用`try`）处理异常，该方法默认使用`throws`



4. `try-catch`细节

	- 如果异常发生，异常后面的代码不会执行，直接进入`catch`块

	- 如果异常没发生，则顺序执行`try`块的代码块，不会进入`catch`块

	- 不管是否发生异常，都执行`finally`块中的内容。当然，`finally`也可以没有

	- 代码：

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        //使用ctrl+alt+t可以将选中的代码块放入指定代码块中
		        try {
		            //分别使用以下两句来检验
		            //String s = "123";
		            String s = "hi";
		            int num = Integer.parseInt(s);
		            System.out.println("num = " + num);
		        } catch (NumberFormatException e) {
		            System.out.println("错误信息：" + e.getMessage());
		        } finally {
		            System.out.println("finally语句");
		        }
		        System.out.println("end of main");
		    }
		}
		```

	- 一个`try`可以有多个`catch`语句，以捕获不同的异常（从而进行不同的业务处理）。这时，子类异常在前，父类异常在后。如果发生异常，只会匹配一个`catch`

	- 代码：

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        try {
		            //分别使用以下两句来检验 NullPointerException
		            String s = null;
		            //String s = "hi";
		            System.out.println(s.length());
		
		            int n1 = 10;
		            //分别使用以下两句来检验ArithmeticException
		            int n2 = 3;
		            //int n2 = 0;
		            System.out.println(n1 / n2);
		        } catch (NullPointerException e) {
		            System.out.println("捕获空指针异常");
		        } catch (ArithmeticException e) {
		            System.out.println("捕获算术异常");
		        } catch (Exception e) {
		            System.out.println("捕获Exception——运行异常");
		        }
		        System.out.println("end of main");
		    }
		}
		```

	- 可以只使用`try-finally`，这种用法相当于没有捕获异常。程序在执行完`finally`中的代码后直接退出（或者说，崩溃）

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        try {
		            //分别使用以下两句来检验 
		            String s = null;
		            //String s = "hi";
		            System.out.println(s.length());
		        }finally {
		            System.out.println("Entering into finally");
		        }
		        System.out.println("end of main");
		    }
		}
		```



5. `try-catch`练习

	1. ```java
		public class Test {
		    public static void main(String[] args) {
		        System.out.println(f1());
		    }
		
		    public static int f1() {
		        String[] strings = new String[3];
		        int i = 1;
		        try {
		            System.out.println(strings[1].equals("AN94"));
		        } catch (NullPointerException e) {
		            return i;
		        } finally {
		            return 3;
		        }
		    }
		}
		```

		- 不论是否捕获异常，`finally`都**必须**被执行。在`catch`中，即使有`return`也不会直接返回，而是要先执行`finally`中的语句。

	2. ```java
		public class Test {
		    public static void main(String[] args) {
		        System.out.println(f1());
		    }
		    public static int f1() {
		        String[] strings = new String[3];
		        int i = 1;
		        try {
		            System.out.println(strings[1].equals("AK12"));
		        } catch (NullPointerException e) {
		            return ++i;
		        } finally {
		            return ++i;
		        }
		    }
		}
		```

		- 进入`catch`块后，先执行`++i`，然后遇到`return`，进入`finally`块

	3. ```java
		public class Test {
		    public static void main(String[] args) {
		        System.out.println(f1());
		    }
		    public static int f1() {
		        String[] strings = new String[3];
		        int i = 1;
		        try {
		            System.out.println(strings[1].equals("AN94"));
		        } catch (NullPointerException e) {
		            return ++i;
		        } finally {
		            ++i;
		            System.out.println("i = " + i);
		        }
		        return -1;
		    }
		}
		```

		- `catch`块中执行`++i`后`i`的值为`2`，系统生成临时变量`temp = 2`，之后遇到`return`进入`finally`。由于`finally`没有`return`，程序回到`catch`块中，返回`temp`的值，即`2`

	4. 接收用户输入的一个整数，如果不是整数，则再次接收，直至输入整数为止

	```java
	import java.util.Scanner;
	
	public class Test {
	    public static void main(String[] args) {
	        Scanner scanner = new Scanner(System.in);
	        int num = -2;
	        while (true) {
	            System.out.println("请输入一个整数：");
	            try {
	                num = Integer.parseInt(scanner.next());
	                break;
	            } catch (Exception e) {
	                System.out.print("输入有误。");
	            }
	        }
	        System.out.println("num = " + num);
	    }
	}
	```



6. `throws`异常处理——基本介绍

	- 如果一个方法可能产生某种异常，但不能确定如何处理异常，则此方法应显式地声明抛出异常，表明该方法不进行异常处理，而由该方法的调用者负责处理

	- 在方法声明中用`throws`可以声明抛出异常的列表，`throws`后面的异常类型可以是方法中产生的异常类型，或是这些异常的父类（如`Exception`类）

	- ```java
		public void f1() throws FileNotFoundException, ArithmeticException {
		        FileInputStream fileInputStream = new FileInputStream("D:\\temp.txt");
		        System.out.println(1 / 0);
		    }
		```



7. `throws`异常处理——细节

	- 对于编译异常，代码中必须处理：用`throws`显式抛出，或用`try-catch`处理，而**不能省略**

	- 对于运行异常，代码中如果没有处理，默认以`throws`方法处理

	- 子类**重写**父类的方法时，对抛出异常的规定是：子类方法抛出的异常**必须和父类的一致**，或是父类方法抛出**异常类型的子类**

	- `throws`是抛出异常，如果方法有`try-catch`，相当于处理异常，不必再`throws`了

	- ```java
		import java.io.FileInputStream;
		import java.io.FileNotFoundException;
		
		public class Test {
		    //3. main将编译异常抛给JVM，后者将使程序崩溃
		    public static void main(String[] args) throws FileNotFoundException {
		        f2();
		    }
		
		    //1. 编译异常必须处理
		    public static void f1() throws FileNotFoundException {
		        FileInputStream fileInputStream = new FileInputStream("D:\\temp.txt");
		    }
		
		    //2. f2要么处理异常，要么继续抛出
		    public static void f2() throws FileNotFoundException {
		        f1();
		    }
		
		    //对于运行异常(这里是ArithmeticException)系统默认使用throws方法处理
		    //不显示处理也可以
		    public static void f3() {
		        System.out.println(1 / 0);
		    }
		}
		
		class A {
		    public void f4() throws RuntimeException {
		    }
		}
		
		class B extends A {
		    //重写时的异常声明，f4只能抛出RuntimeException及其子类
		    @Override
		    public void f4() throws ArithmeticException {
		    }
		}
		```





## 自定义异常

1. 基本概念
	- 当程序中出现了某些“错误”，但该错误信息并没有在`Throwable`子类中描述处理。这时可以自己设计异常类，用于描述该错误信息



2. 自定义异常的步骤

	- 自定义异常类，继承`Exception`或`RuntimeException`类

	- 如果继承`Exception`，属于编译异常

	- 如果继承`RuntimeException`，属于运行异常

	- 一般来说，继承`RuntimeException`比较方便，因为不需要显式地处理异常

	- 代码：

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        int age = 10;
		        if (age >= 18 && age <= 120)
		            System.out.println("年龄输入正确");
		        else
		            throw new AgeException("年龄应该在18 - 120岁之间");
		    }
		}
		
		class AgeException extends RuntimeException {
		    public AgeException(String message) {
		        super(message);
		    }
		}
		```



## `throw`和`throws`的对比

|          | 意义                 | 出现位置   | 后面连接什么？ |
| -------- | -------------------- | ---------- | -------------- |
| `throws` | 异常处理的一种方式   | 方法声明处 | 异常类型       |
| `throw`  | 用于手动生成异常对象 | 方法体中   | 异常对象       |



## 课后作业

1. 1. 需求：

		- 编写程序：接收命令行的两个参数（整数），并输出它们相除的结果
		- 对数据格式不正确、命令行参数数量不正确和除以0进行异常处理

	2. 代码：

		- ```java
			public class Test {
			    public static void main(String[] args) {
			        try {
			            if (args.length != 2)
			                throw new ArrayIndexOutOfBoundsException("输入数量不正确");
			            int n1 = Integer.parseInt(args[0]);
			            int n2 = Integer.parseInt(args[1]);
			
			            System.out.println("整数除法的结果是：" + n1 / n2);
			        } catch (ArrayIndexOutOfBoundsException e) {
			            System.out.println(e.getMessage());
			        } catch (NumberFormatException e) {
			            System.out.println("应该输入整数");
			        } catch (ArithmeticException e) {
			            System.out.println("不能除以0");
			        }
			    }
			}
			```

	3. 分析：

		- 代码中可以用`throw`主动抛出异常，再用`try-catch`主动处理异常
		- 学习IDEA如何配置命令行参数



# 第10章：常用类



## 包装类

1. 包装类的分类

	- 包装类是针对八种基本数据类型设计的相应的类

	- 有了类的特点，就可以调用类中的方法

	- | 基本数据类型 | 包装类      | 直接父类 |
		| ------------ | ----------- | -------- |
		| `boolean`    | `Boolean`   | `Object` |
		| `char`       | `Character` | `Object` |
		| `byte`       | `Byte`      | `Number` |
		| `short`      | `Short`     | `Number` |
		| `int`        | `Integer`   | `Number` |
		| `long`       | `Long`      | `Number` |
		| `float`      | `Float`     | `Number` |
		| `double`     | `Double`    | `Number` |

	- 后六个包装类继承`Number`类，`Number`类再继承`Object`类。继承关系图如下：

	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202211436520.png" alt="image-20220221143628350" style="zoom: 50%;" />



2. 装箱和拆箱

	- 装箱：基本类型 $\rightarrow$ 包装类型。反之，为拆箱

	- JDK5 以前需要手动装箱和拆箱

	- JDK5及以后有自动装箱和拆箱

	- 自动装箱底层仍然调用`valueOf`方法。自动拆箱底层调用相应的`XXXValue`方法

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        int n1 = 10;
		        //手动装箱
		        Integer integer1 = new Integer(n1);
		        Integer integer2 = Integer.valueOf(n1);
		        //手动拆箱
		        int n2 = integer2.intValue();
		        int n3 = 7;
		        //自动装箱
		        Integer integer3 = n3;
		        //自动拆箱
		        int n4 = integer3;
		    }
		}
		```



3. 题目

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        Object obj1 = true ? new Integer(1) : new Double(2.0);
		        //debug可知，obj1的运行类型是Double
		        System.out.println(obj1);
		        Object obj2;
		
		        if (true)
		            obj2 = new Integer(1);
		        else
		            obj2 = new Double(2.0);
		        System.out.println(obj2);
		    }
		}
		```

	- 三元运算符是在一句话中比较。故在此处，`Integer`会提高精度至`Double`

	- `if-else`结构中则不会有影响



4. 包装类一些方法

	- 包装类和`String`相互转换

		- ```java
			public class Test {
			    public static void main(String[] args) {
			        Integer i1 = 7;
			        //包装类 --> String
			        String str1 = i1 + "";
			        String stt2 = i1.toString();
			        String str3 = String.valueOf(i1);
			
			        //String --> 包装类
			        String str4 = "234";
			        Integer i2 = Integer.parseInt(str4);
			        Integer i3 = new Integer(str4);
			    }}
			```

	- `Number`类子类具有的属性

		- ```java
			Integer.MIN_VALUE;  //最小值
			Integer.MAX_VALUE;//最大值
			```

	- `Character`类的方法

		- `isDigit(char)`：是否是数字
		- `isLetter(char)`：是否为字母
		- `isUpperCase(char)`：是否为大写字母
		- `toUpperCase(char)`：返回大写字母
		- `isWhitespace(char)`：是否为空格



5. `Integer`创建机制

	- 案例演示：

		- ```java
			public class Test {
			    public static void main(String[] args) {
			        Integer integer = new Integer(37);
			        Integer integer1 = new Integer(37);
			        System.out.println(integer1 == integer);
			
			        Integer integer2 = 1;
			        Integer integer3 = 1;
			        System.out.println(integer2 == integer3);
			
			        Integer integer4 = 128;
			        Integer integer5 = 128;
			        System.out.println(integer4 == integer5);
			
			        int i = 128;
			        System.out.println(integer5 == i);
			    }}
			```

		- 第一次比较 ，由于两者创建了各自的对象，地址肯定不同

		- 接下来两次比较，由于自动装箱调用`Integer`的`valueOf`方法，需要看源码：

		- ```java
			    /**
			     * Returns an {@code Integer} instance representing the specified
			     * {@code int} value.  If a new {@code Integer} instance is not
			     * required, this method should generally be used in preference to
			     * the constructor {@link #Integer(int)}, as this method is likely
			     * to yield significantly better space and time performance by
			     * caching frequently requested values.
			     *
			     * This method will always cache values in the range -128 to 127,
			     * inclusive, and may cache other values outside of this range.
			     */
			    public static Integer valueOf(int i) {
			        if (i >= IntegerCache.low && i <= IntegerCache.high)
			            return IntegerCache.cache[i + (-IntegerCache.low)];
			        return new Integer(i);
			    }
			```

		- `IntegerCache`作为`Integer`的私有静态类，在类加载时会创建`cache`数组，存放-128到127的`Integer`对象，以提高效率

		- 第二次比较，1在缓存的范围内，故它们指向同一对象 

		- 第三次比较，128超过了`high`，故两者分别创建对象，地址不同

		- 第四次比较，包装类与基本类型比较时看值是否相等





## `String`类

- 注意，string虽然有字符串的意思。但在编程中，字符串定义为字符数组，即`char[]`。不要将`String`类和字符串混淆。在java中，字符串是`String`类的一个属性



1. 结构剖析

	- `String`对象用于保存字符串——即字符序列

	- 字符串常量对象是用双引号`""`括起的字符序列，如`"你好，world"`

	- 字符串的字符是用Unicode编码，一个字符占两个字节

	- `String`的一些构造器如下：

	- ```
		String()
		String(String original)
		String(char[] a)
		String(char[] a, int startIndex, int count)
		String(byte[] b)//该参数与网络传输有关
		```

	- 继承关系：

		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202230918312.png" alt="image-20220223091815177" style="zoom:33%;" />
		- `Comparable`接口使`String`对象可以比较大小
		- `Serializable`接口使`String`对象可以串行化——即在网络中传输

	- 源代码：

		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202230920427.png" alt="image-20220223092037347" style="zoom:33%;" />

		- `String`不能被其他类继承

		- `String`的属性`value`，用来存储字符。注意在这里，`value`是作为`char[]`的引用被定义为`final`的，即`value`在初始化后不能指向其他字符串数组的引用。但该数组元素的值可以被修改

		- 代码如下：

		- ```java
			public class Test {
			    public static void main(String[] args) {
			        final char[] cs = {'1', '2', '3'};
			        cs[0] = 'H';//修改数组元素的值是允许的
			        char[] cs2 = {'1'};
			        //cs = cs2; 这句话不允许
			    }}
			```



2. 两种创建`String`对象的区别
	- :one:：直接复制`String s = "cat";`
		- 方式一：先从常量池查看是否有`"cat"`数据空间。如果有，直接指向；如果没有，先创建再指向。`s`最终指向常量池中的地址
	- :two:：调用构造器`String s2 = new String("cat");`
	- 方式二：在堆中给`String`对象分配空间，里面维护了`value`属性。如果常量池有`"cat"`数据空间，则`value`指向它；如果没有，则先创建再指向。`s2`指向了堆中的地址。
	- 如图：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202230941974.png" alt="image-20220223094147767" style="zoom: 33%;" />



3. `String`对象特性：`String`相加

	1. 字符串常量相加时，如`String s1 = "ab" + "cd";`。编译器自动优化，只在常量池创建`"abcd"`一个字符串，然后`s1`指向它

	2. 字符串变量相加时，如`String s2 = "ab", s3 = "cd"; String s4 = s2 + s3;`。`s2`、`s3`指向常量池中的字符串。在创建`s4`时，规则如下：

		- 先创建一个`StringBuilder`对象

		- 调用`StringBuilder`对象的`append(String)`方法，传入的参数为`"ab"`

		- 再次调用该方法，传入的参数为`"cd"`

		- 最后调用`StringBuilder`的`toString`方法：（源码如下）

		- ```java
			@Override
			    public String toString() {
			        // Create a copy, don't share the array
			        return new String(value, 0, count);
			    }
			```

		- 将堆中`String`对象的地址付给`s4`

	3. 故，常量相加，是在常量池中；变量相加，是在堆中



4. 常用方法

	- `equals(Object obj)`：判断内容是否相等

	- `equalsIgnoreCase(String s)`：判断内容是否相等，不区分大小写

	- `length()`：返回字符串长度

	- `indexOf(char c)`：判断**字符第一次**在字符串中出现的位置，没有则返回`-1`

	- `indexOf(String s)`：判断某**字符串第一次**在字符串中出现的位置，没有则返回`-1`

	- `lastIndexOf(char c)`：判断**字符最后一次**在字符串中出现的位置，没有则返回`-1`

	- `subString(int beginIndex)`：返回从某一位置开始截取，直到原字符串末尾的子字符串

	- `subString(int beginIndex, int endIndex)`：返回`[beginIndex, endIndex)`区间的子字符串

	- `trim()`：返回新字符串，但去掉前后空格

	- `charAt(int index)`：返回索引处的字符。注意，不能用`str[index]`的方式去索引。经常用于遍历字符串

	- `toUpperCase()`：返回新字符串，但全部大写

	- `concat(String s)`：返回新字符串，内容是原字符串加上`s`

	- `relpace(String target, String s)`：返回新字符串，内容是将原字符串中**每个**为`target`的子串替换为`s`

	- `split(String s)`：返回`String[]`，里面是以`s`为分割符分割的原字符串的各部分。注意，特殊字符需要转义。如：

		- ```java
			String dir = "D:\\game\\mirror";
			String s="\\\\";//第一个和第三个 '\' 是转义符
			String[] strings = dir.split(s);
			```

	- `toCharArray()`：返回`char[]`，将字符串的每一字符放入该数组

	- `compareTo(String s)`：以字典顺序与另一个字符串比较。相等返回`0`，大于`s`返回正数

		- 具体比较规则如下：
		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202251006284.png" alt="image-20220225100651147" style="zoom: 33%;" />

	- `format(String format, Object... args)`：静态方法，按格式返回字符串：

		- ```java
			public class Test {
			    public static void main(String[] args) {
			        String name = "李东风";
			        double weight = 4.87;
			
			        String s1 = String.format("The cat is called %s, which weighs %.1f kg.",
			                name, weight);
			        System.out.println(s1);
			        //也可以将格式保存为字符串
			        String formatStr = "The cat is called %s, which weighs %.1f kg.";
			        System.out.println(String.format(formatStr, "臭卷宝", 6.82));   }}
			```

		- 格式化类似于C中的`printf()`

		- `%s`、`%d`、`%c`等称作占位符

		- `%.1f`是保留一位小数，且会四舍五入

		- 注意到，该方法的可变参数的类型是`Object`，基本数据类型会自动装箱











## `StringBuffer`类

1. `StringBuffer`结构与介绍

	- `StringBuffer`代表可变的字符序列，可以对字符串内容进行增改

	- 其很多方法与`String`相同，但`StringBuffer`是可变长度的

	- `StringBuffer`是一个容器

	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202251459881.png" alt="image-20220225145937258" style="zoom:33%;" />

	- `StringBuffer`的直接父类是`AbstractStringBuilder`。后者源代码（一部分）如下：

	- ```java
		abstract class AbstractStringBuilder implements Appendable, CharSequence {
		    /**
		     * The value is used for character storage.
		     */
		    char[] value;
		```

	- 其中，属性`char[] value`存放字符串内容。且不像`String`声明为`final`，故该数组存放在堆中

	- `StringBuffer`保存的是字符串变量，里面的值可以修改。每次更新`StringBuffer`实际是更新`value`中的内容，而不用每次都创建一个新的数组，效率较高

	- `String`保存的是字符串常量（`private final char[] value`），每次`String`对象的更新实际是创建新的数组，效率较低



2. `StringBuffer`构造器
	1. `StringBuffer()`：构造一个空的字符串缓冲区，容量为16
	2. `StringBuffer(CharSequence seq)`：构造字符串缓存区，其内容与`seq`一致
	3. `StringBuffer(int capacity)`：构造空的字符串缓冲区，但自定义容量大小
	4. `StringBuffer(String str)`：构造字符串缓存区，其内容与`str`一致。其容量为`str.length() + 16`



3. `StringBuffer`与`String`相互转换：

	```java
	public class Test {
	    public static void main(String[] args) {
	        //string -> StringBuffer
	        String s1 = "lilith";
	        //第一种方式
	        StringBuffer stringBuffer = new StringBuffer(s1);
	        //第二种方式，其实和上一种差不多
	        StringBuffer stringBuffer1 = new StringBuffer();
	        stringBuffer.append(s1);
	
	        //StringBuffer -> String
	        StringBuffer stringBuffer2 = new StringBuffer("PassionLip");
	        //第一种方式
	        String s2 = stringBuffer2.toString();
	        //第二种方式
	        String s3 = new String(stringBuffer2);
	    }}
	```



4. 一些常用方法：
	- `append()`：尾部添加
	- `delete(int startIndex, int endIndex)`：删除`[startIndex, endIndex)`中的内容
	- `replce(int start, int end, String s)`：将`[start,end)`中的内容替换为`s`的内容。注意，两者的长度可以不等
	- `insert(int offset, String s)`：在`offset`索引处插入`s`
	- 其他和`String`用法一样的方法：`indexOf(String)`、`length()`



## `StringBuilder`类

1. `StringBuilder`结构
	- 一个可变的字符序列。此类提供一个与`StringBuffer`兼容的API，但不保证同步（`StringBuilder`不是线程安全的）。该类被设计用作`StringBuffer`的一个简易替换（即，用法基本相同），用在字符串缓冲区被单个线程使用的时候。如果可能，应该优先使用该类，因为大多数情况下，它比`StringBuffer`快
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202251723848.png" alt="image-20220225172313678" style="zoom:33%;" />



2. `String`、`StringBuffer`和`StringBuilder`比较
	- `StringBuffer`和`StringBuilder`非常类似，都代表可变的字符序列，且方法相同
	- `String`：不可变字符序列，效率低，但复用率高
	- `StringBuffer`：可变字符序列、效率较高、线程安全
	- `StringBuilder`：可变字符序列、效率最高、线程不安全
	- 对于`String`类，如果多次改变字符串的内容，会导致大量字符串对象副本留在内存中，降低效率。因此，如果要对字符串做大量修改，不要使用`String`



3. `String`、`StringBuffer`和`StringBuilder`的选择
	- 如果存在大量修改操作
		- 单线程时，使用`StringBuilder`
		- 多线程时，使用`StringBuffer`
	- 如果很少修改，且被多个对象引用，使用`String`





## `Math`类



常用静态方法如下：

- `abs(x)`：返回`x`的绝对值
- `pow(double a, double b)`：返回$a ^ b$
- `ceil(x)`：向上取整
- `floor(x)`：向下取整
- `round(x)`：四舍五入，相当于`floor(x + 0.5)`
- `sqrt(x)`：返回$\sqrt x$
- `random()`：返回`[0, 1)`之间的随机数。
	- 如果要返回`[a, b]`之间的整数，应使用这个式子：`(int)(a + Math.random() * (b - a + 1))` 
- `max(x, y)`：返回两数较大值





## `Date`日期类、`Calendar`日历类以及新的日期



1. 第一代日期类

	1. `Date`：精确到毫秒的日期类，代表特定时间

	2. `SimpleDateFormat`：用来格式化（日期  $\rightarrow$ 字符串 ）和解析（字符串 $\rightarrow$ 日期）日期的具体类

	3. 定义`SimpleDateFormat`的格式：

		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202261417401.png" alt="image-20220226141733178" style="zoom:33%;" />

	4. 代码如下：

		- ```java
			import java.text.ParseException;
			import java.text.SimpleDateFormat;
			import java.util.Date;
			
			public class Test {
			    public static void main(String[] args) throws ParseException {
			        Date date = new Date();//对象保存了当前时间的信息
			        //日期的输出格式是默认的
			        System.out.println(date);
			        //构造器：public SimpleDateFormat(String pattern)
			        SimpleDateFormat sdf = new SimpleDateFormat("HH:mm:ss yyyy年MM月dd日 E");
			        //format方法： String format(Date date) 返回一个格式化后的日期
			        String str = sdf.format(date);
			        System.out.println(str);
			
			        System.out.println("==================================================");
			        //解析日期:
			        String str2 = "12:01:43 2022年02月14日 星期一";
			        //parse方法： Date parse(String source) 
			        Date date1 = sdf.parse(str2);//调用parse要处理ParseException这一编译异常
			
			        System.out.println(date1);
			    }}
			```



2. 第二代日期类

	1. `Calander`类是抽象类，且它的构造器是`protected`，无法通过外部创建。但可以使用`getInstance()`方法得到`Calander`对象

		- 类声明：

			```java
			public abstract class Calendar implements Serializable, Cloneable, Comparable<Calendar> {
			```

		- 构造器声明（共两个）：

			```java
			protected Calendar(){}
			protected Calendar(TimeZone zone, Locale aLocale){}
			```

	2. 该类没有相应的格式化类，也没有重写`toString()`方法。但它提供大量字段，使程序员自己组合

		```java
		import java.util.Calendar;
		
		public class Test {
		    public static void main(String[] args) {
		        Calendar instance = Calendar.getInstance();
		
		        int year = instance.get(Calendar.YEAR);
		        //月份从0开始计
		        int month = instance.get(Calendar.MONTH) + 1;
		        int day = instance.get(Calendar.DAY_OF_MONTH);
		
		        int hour = instance.get(Calendar.HOUR_OF_DAY) ;
		        int minute = instance.get(Calendar.MINUTE);
		
		        System.out.println("现在的时间是：");
		        System.out.println(hour + ":" + minute + " " + year + "-" + month + "-" + day);
		    }}
		```

		

3. 第三代日期类

	1. 前两代日期类的不足：JDK 1.0中包含了一个`java.util.Date`类，但是它的大多数方法已经在JDK 1.1引入`Calendar`类之后被弃用了。在`Calendar`也存在的问题是：

		- 可变性：日期和时间类应该是不可变的
		- 偏移性：`Date`中的年份从`1900`年开始，月份是从`0`开始
		- 格式化：格式化只对`Date`有用，`Calendar`则不行
		- 此外，它们不是线程安全的，也不能处理闰秒

	2. 第三代日期类：

		- `LocalDate`：只包含日期（年月日），可以获取日期字段
		- `LocalTime`：只包含时间（时分秒），可以获取时间字段
		- `LocalDateTime`：包含日期和时间，可以获取相应字段

	3. 简单使用：

		- ```java
			import java.time.LocalDate;
			import java.time.LocalDateTime;
			
			public class Test {
			    public static void main(String[] args) {
			        //    public static LocalDateTime now()
			        LocalDateTime ldt = LocalDateTime.now();
			        System.out.println(ldt);
			        System.out.println(ldt.getYear() + "-"
			                + ldt.getMonthValue() + "-" + ldt.getDayOfMonth());
			        System.out.println(ldt.getMonth());
			
			        System.out.println("===============================");
			        LocalDate ld = LocalDate.now();
			        //LocalTime使用方法同理
			        System.out.println(ld);
			    }}
			```

	4. `DateTimeFormatter`格式日期类

		- 基本用法和`SimpleDateFormat`类似，但使用静态方法`ofPattern`来创建对象。

		- 日期输出格式参考JDK 8文档

		- 代码如下：

		- ```java
			import java.time.LocalDateTime;
			import java.time.format.DateTimeFormatter;
			
			public class Test {
			    public static void main(String[] args) {
			        //public static DateTimeFormatter ofPattern(String pattern)
			        DateTimeFormatter dateTimeFormatter =
			                DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm E");
			        LocalDateTime now = LocalDateTime.now();
			        System.out.println(dateTimeFormatter.format(now));
			    }}
			```

	5. `Instant`时间戳

		- 类似于`Date`的类，提供了和`Date`相互转换的方法

		- ```java
			import java.time.Instant;
			import java.util.Date;
			
			public class Test {
			    public static void main(String[] args) {
			        Instant ins1 = Instant.now();
			        System.out.println(ins1);
			
			        Date date = Date.from(ins1);
			        Instant ins2 = date.toInstant();
			    }}
			```

	6. 其他方法（举例）

		- `plusXXX`方法：增加时间的某个部分

		- `minusXXX`方法：减少时间的某个部分

		- ```java
			import java.time.LocalDateTime;
			import java.time.format.DateTimeFormatter;
			
			public class Test {
			    public static void main(String[] args) {
			        //可以在格式中加入日期，测试该日期类的性能是不是强大
			        DateTimeFormatter dateTimeFormatter =
			                DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm E");
			        LocalDateTime now = LocalDateTime.now();
			        System.out.println("now : " + dateTimeFormatter.format(now));
			
			        //public LocalDateTime plusDays(long days)
			        LocalDateTime future = now.plusDays(264);
			        System.out.println("264 days ahead is "+ dateTimeFormatter.format(future));
			
			        //public LocalDateTime minusWeeks(long weeks)
			        LocalDateTime past = now.minusWeeks(35);
			        System.out.println("35 weeks before is "+ dateTimeFormatter.format(past));
			    }}
			```





## `System`类

常用静态方法：

- `exit(int status)`：以`status`状态退出程序。主动退出时该参数一般为`0`
- `arraycopy(int[] src, int srcPos, int[] dest, int destPos, int length)`：复制数组元素，以如下规则：从`src`的`srcPos`开始，复制`length`个元素到`dest`的`destPos`处（依次向后复制）
- `currentTimeMillens()`：返回当前时间距离1970.1.1零时的毫秒数
- `gc()`：运行垃圾回收机制



## `Arrays`类

`Arrays`里面包含一系列静态方法，用于管理或操作数组（由于没有学泛型，出于方便，数组类型写成`int[]`）：

- `toString(int[] arr)`：将数组拼接成字符串，并返回。通常用于输出到屏幕以查看数组元素

- `sort(int[] arr)`：自然排序——使用系统默认的比较方式

- `sort(int[] arr, Comparator c)`：自定义排序，用实现`Comparator`接口的`compare(a, b)`来比较。类似c++中`sort(arr.begin(), arr.end(), Compare comp)`

- `binarySearch(int[] arr, int x)`：返回`x`在有序数组`arr`中的索引。不存在则返回一个负数

- `copyOf(int[] arr, int len)`:返回`arr`数组的复制，但复制前`len`个元素。如果`len > arr.length`，多余的会用默认值代替

- `fill(int[] arr, value)`：将`arr`中**所有元素替换**为`value`

- `equals(int[] arr1, int[] arr2)`：比较两个数组内容是否一致，返回`boolean`值

- 部分方法的代码：

- ```java
	import java.util.Arrays;
	import java.util.Comparator;
	
	public class Test {
	    public static void main(String[] args) {
	        int[] arr1 = {-9, 1, 5, -5, 100, 47};
	        System.out.println(Arrays.toString(arr1));
	
	        Arrays.sort(arr1);
	        System.out.println("after default sort:\n" + Arrays.toString(arr1));
	
	        System.out.println("===========================");
	        Integer[] arr2 = {-9, -5, 1, 5, 100, 47};
	        //定义匿名内部类来实现Comparator接口
	        Arrays.sort(arr2, new Comparator<Integer>() {
	            @Override
	            public int compare(Integer o1, Integer o2) {
	                return o2 - o1;
	            }
	        });
	        System.out.println("after custom sort:\n" + Arrays.toString(arr2)); }}
	```







## `BigInteger`和`BigDecimal`类

1. 基本介绍
	- `BigInteger`保存比较大的整型，可以远大于`long`的范围
	- `BigDecimal`保存精度更高的浮点型（小数），精度可以远远高于`double`的精度



2. `BigInteger`方法
	- `BigInteger(String val)`：构造器，使用字符串中保存的整数初始化
	- `BigInteger add(BigInteger val)`：将`this`与`add`相加，做成一个新对象，并返回
	- 其他的运算方法有`subtract(BigInteger)`、`multiply(BigInteger)`和`divide(BigInteger)`
	- 注意，运算符只能用在基本数据类型，不能用在类上



3. `BigDecimal`方法
	- 该类的构造器和运算方法与`BigInteger`的类似，需要特别注意以下方法：
	- `BigDecimal divide(BigDecimal val)`：由于是以高精度进行运算，如果除法产生无限不循环小数，将抛出异常。这时需要指定小数位数，使用下述方法：
	- `BigDecimal divide(BigDecimal val, int roundingMode)`，第二个参数可传入`BigDecimal.ROUND_CEILING`，使结果的小数位数与分子的一致



4. 代码：

	```java
	import java.math.BigDecimal;
	import java.math.BigInteger;
	
	public class Test {
	    public static void main(String[] args) {
	        BigInteger bigInteger = new BigInteger("74986641354684641654");
	        BigInteger bigInteger1 = new BigInteger("797464646354654646846165203");
	        System.out.println(bigInteger.add(bigInteger1));
	        System.out.println(bigInteger.multiply(bigInteger1));
	
	        System.out.println("=====================================================");
	        BigDecimal bigDecimal = new BigDecimal("478946316574941.131341354165464196846847897416351684");
	        BigDecimal bigDecimal1 = new BigDecimal("423.798465498616");
	        System.out.println(bigDecimal.subtract(bigDecimal1));
	        System.out.println(bigDecimal.divide(bigDecimal1, BigDecimal.ROUND_CEILING));
	    }
	}
	```

	

​	

## 课后作业

1. - 要求：

		- 编写方法`public static String reverse(String str, int start, int end)`：将字符串指定区间反转

	- 代码：

		- ```java
			    public static String reverse(String str, int start, int end) {
			        //判断错误的情况的代码，应为对正确情况取反————这样逻辑清晰，考虑周全
			        if (!(str != null && start >= 0 && end < str.length() && start < end)) {
			            throw new RuntimeException("wrong parameter input");
			        }
			        //toCharArray方法是关键
			        char[] chars = str.toCharArray();
			        char temp;
			        while (start < end) {
			            temp = chars[start];
			            chars[start] = chars[end];
			            chars[end] = temp;
			
			            ++start;
			            --end;
			        }
			        return new String(chars);
			    }
			```

		- 作为一道简单算法题倒是不难

​	

2. - 要求：

		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202271018030.png" alt="image-20220227101841751" style="zoom:25%;" />

	- 代码：

		- ```java
			import java.util.Scanner;
			
			public class Test {
			    private static Scanner scanner = new Scanner(System.in);
			
			    public static void main(String[] args) {
			        System.out.println("=========注册开始=============");
			        try {
			            String name = getName();
			            String password = getPassword();
			            String email = getEmail();
			
			            System.out.println("=========注册成功===============");
			            System.out.println("用户名： " + name);
			            System.out.println("密码： " + password);
			            System.out.println("邮箱： " + email);
			        } catch (Exception e) {
			            System.out.println(e.getMessage());
			            System.out.println("========注册失败，请重试===========");
			        }
			
			    }
			
			    public static String getName() {
			        System.out.print("输入用户名：");
			        String name = scanner.next();
			
			        if (!(2 <= name.length() && name.length() <= 4))
			            throw new RuntimeException("用户名长度在2-4之间");
			        return name;
			    }
			
			    public static String getPassword() {
			        System.out.print("输入密码：");
			        String password = scanner.next();
			        if (password.length() != 6) {
			            throw new RuntimeException("密码长度应为6");
			        }
			        //直接使用charAt方法遍历数组，检验每一个元素是否为数字即可
			        //因为这里parseInt方法的结果是无用的
			        //但当时一下子没有想到如何方便地遍历数组————我不想使用toCharArray方法，因为这会创建一个没用的数组
			        try {
			            Integer.parseInt(password);
			        } catch (Exception e) {
			            throw new RuntimeException("密码应为纯数字");
			        }
			        return password;
			
			    }
			
			    public static String getEmail() {
			        System.out.print("输入邮箱：");
			        String email = scanner.next();
			        int n = email.length();
			
			        int indexAt = email.indexOf("@");
			        int indexDot = email.indexOf(".");
			        if (indexAt < 0 || indexDot < 0) {
			            throw new RuntimeException("邮箱中需要包含@和.字符");
			        }
			        if (indexAt >= indexDot) {
			            throw new RuntimeException("邮箱名中@应在.前面");
			        }
			
			        return email;
			    }
			}
			```



3. - 要求：

		- ![image-20220227103330087](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202271033272.png)

	- 代码：

		- ```java
			public static void nameFormat(String name) {
			        String[] s = name.split(" ");
			        String outputFormat = "%s,%s.%c";
			        System.out.println(String.format(outputFormat,
			                s[2], s[0], Character.toUpperCase(s[1].charAt(0))));
			    }
			```

		- 代码没有进行检验

		- 使用`split`优于使用`indexOf(" ")`加循环的手动分割——看到题时我想使用后者

		- 格式化输出优于对字符串进行拼接——看到题时我想使用后者





# 第11章：集合

- 集合的引入：
	- 之前保存多个数据使用数组，但数组有如下缺点：
		- 长度是确定的，一旦创建，不能修改
		- 元素必须是同一类型
		- 使用数组删改元素比较麻烦——需要自定义方法
	- 而集合：
		- 可以动态保存任意多个对象
		- 提供一系列增删查改的方法
	- Java中的集合和C++ STL中的容器类似



## 集合体系图

1. Java中的集合分为单列集合(`Collection`的实现子类）和双列集合（`Map`的实现子类）
2. `Collection`体系图
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202271338009.png" alt="image-20220227133848703" style="zoom: 33%;" />
3. `Map`体系图
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202271341442.png" alt="image-20220227134134355" style="zoom:33%;" />





## `Collection`接口

1. `Collection`接口实现类的特点
	- 定义如下：`public interface Collection<E> extends Iterable<E>`
	- `Collection`实现子类可以存放多个元素。每个元素的类型可以是`Object`。故类中元素的运行类型可以完全不同
	- 有些`Collection`实现子类可以存放重复元素，有些则不行
	- 有些`Collection`实现子类是有序的（`List`），有些是无序的（`Set`）
	- `Collection`接口没有直接的实现子类，是通过它的子接口`Set`和`List`的实现子类来实现的



2. 常用方法：

	- `add(E e)`：添加单个元素

	- `addAll(Collection c)`：添加多个元素，参数为集合

	- `remove(E e)`：删除指定元素

	- `removeAll(Collection c)`：删除多个元素，参数为集合

	- `boolean contains(E e)`：查看某元素是否存在

	- `boolean containsAll(Collection c)`：查看多个元素是否存在，参数为集合

	- `int size()`：返回元素个数

	- `boolean isEmpty()`：集合是否为空

	- `clear()`：清空集合

	- 代码演示：

	- ```java
		import java.util.ArrayList;
		import java.util.Collection;
		
		public class Test {
		    public static void main(String[] args) {
		        Collection arrayList = new ArrayList();
		        arrayList.add("李东风");
		        arrayList.add('诚');
		        arrayList.add(23.4);
		        //ArrayList重写了toString()方法
		        System.out.println(arrayList);
		
		        Collection al2 = new ArrayList();
		        al2.add(43);
		        al2.add("臭卷宝");
		        arrayList.addAll(al2);
		        System.out.println(arrayList);
		
		        arrayList.remove(43);
		        System.out.println(arrayList);
		
		        System.out.println(arrayList.contains("臭卷宝"));
		        System.out.println(arrayList.containsAll(al2));
		
		        System.out.println("size = " + arrayList.size());
		        System.out.println("empty? " + arrayList.isEmpty());
		
		        arrayList.clear();
		        System.out.println(arrayList);    }}
		```





3. 迭代器遍历

	- `Iterator`对象称为迭代器，主要用于遍历`Collection`集合中的元素

	- 实现了`Collection`接口的集合类都有`iterator()`方法，返回一个实现了`Iterator`接口的对象——即，一个迭代器

	- `Iterator`仅用于遍历**集合**，它本身不存放对象

	- `Iterator`的两个重要方法：

		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202271439432.png" alt="image-20220227143905329" style="zoom:33%;" />

	- `Iterator`工作原理：

		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202202271439705.png" alt="image-20220227143957540" style="zoom:33%;" />
		- 每次调用`next()`方法，返回迭代过程中的下一个元素，并将游标往后移动一位
		- 如果下一条记录无效，将抛出`NoSuchElementException`异常。故，在每一次调用`next()`方法前，需要使用`hasNext()`方法来确认

	- 代码：

	- ```java
		import java.util.ArrayList;
		import java.util.Iterator;
		
		public class Test {
		    public static void main(String[] args) {
		        ArrayList al = new ArrayList();
		        al.add(123);
		        al.add(false);
		        al.add("いな");
		
		        /*输入 itit 以生成以下模板
		        while (iterator.hasNext()) {
		            Object next = iterator.next();
		        }
		        */
		        Iterator iterator = al.iterator();
		        while (iterator.hasNext()) {
		            Object next = iterator.next();
		            System.out.println(next);
		        }
		    }}
		
		```



4. 增强`for`循环遍历

	- 增强`for`循环，是`iterator`迭代器的简化版。两者本质一样。增强`for`循环只能用于遍历集合或数组

	- 代码如下：

	- ```java
		import java.util.ArrayList;
		
		public class Test {
		    public static void main(String[] args) {
		        ArrayList al = new ArrayList();
		        al.add(123);
		        al.add(false);
		        al.add("いな");
		
		        /*输入 I 生成以下模板，也可以使用iter快捷键
		        for (Object o :) {
		
		        }
		        */
		        for (Object o : al) {
		            System.out.println(o);
		        }
		    }}
		
		```





## `Collection`接口的子接口：`List`实现类

1. `List`接口介绍
	- `List`集合类中元素**有序，且可重复**
	- `List`集合类中，每个元素有相应的索引。该索引用整数标记。



2. `List`常用方法
	- `add(int index, Object o)`：在`index`处插入元素`o`
	- `addAll(int index, Collection c)`：在`index`处插入`c`中所有元素
	- `Object get(int index)`：返回指定索引处的元素。可用于该集合的遍历
	- `int indexOf(Object o)`：返回`o`在集合中首次出现的位置
	- `Object remove(int index)`：移除指定索引的元素，并返回该元素
	- `set(int index, Object o)`：修改指定索引处元素的值
	- `List subList(int start, int end)`：返回`[start, end)`构成的子集合



3. `List`的三种遍历方法
	- 使用`iterator`
	- 使用增强`for`
	- 使用普通`for`和`get(int index)`方法



4. `ArrayList`
	1. 基本介绍：
		- `ArrayList`的底层是由数组来实现数据存储的
		- `ArrayList`基本等同于`Vector`。但`ArrayList`是线程不安全的，因而执行效率较高
	2. 底层机制：
		- `ArrayList`中维护了一个`Object`类型的数组`elementData`
		- 当创建`ArrayList`对象时，如果使用无参构造器`ArrayList()`，`elementData`初始容量为0。第一次添加时，该数组长度扩容至10。之后每次扩容，长度都增加至原先的**1.5倍**
		- 如果使用指定大小的构造器`ArrayList(int)`，则`elementData`初始容量为该指定大小。之后每次扩容，长度都增加至原先的**1.5倍**
		- 具体步骤可以参考源码



5. `Vector`
	1. 基本介绍：
		- `Vector`的数据存储在一个对象数组中，即`Object[] elementData`
		- `Vector`是线程安全的
	2. 底层机制：
		- 如果调用无参构造器，则默认容量为10。容量满后，新的容量扩大至之前的**2倍**
		- 调用有参构造器，以指定容量大小。容量满后，新的容量扩大至之前的**2倍**



6. `LinkedList`
	1. 基本介绍：
		- `LinkedList`底层实现了双向链表和双端队列特点
		- 可以添加任意（可重复）的元素
		- 线程不安全
	2. 底层机制：
		- `LinkedList`底层维护了一个双向链表
		- `LinkedList`维护了两个属性：`first`和`last`，分别指向首节点和尾节点
		- 每个节点的类型是`Node`对象，里面维护了`prev`、`next`和`item`属性。`prev`指向前一个节点，`next`指向后一个节点，`item`存储数据
		- 故`LinkedList`的元素的增减，不是通过数组完成的，效率较高



7. `ArrayList`和`LinkedList`比较

	- |              | 底层结构 | 增删效率       | 查改效率 |
		| ------------ | -------- | -------------- | -------- |
		| `ArrayList`  | 数组     | 较低：数组扩容 | 较高     |
		| `LinkedList` | 双向链表 | 较高：追加节点 | 较低     |

	- 如果查改操作多，使用`ArrayList`

	- 如果增删操作多，选择`LinkedList`

	- 一般来说，程序中多为查询操作，选择使用`ArrayList`

	- 在实际项目中，要根据业务进行选择。可能一个模块是`ArrayList`，另一个是`LinkedList`



## `Collection`接口的子接口：`Set`实现类

1. `Set`基本介绍
	- 相对无序（添加和取出的顺序不一致），没有索引
	- 不允许（添加）重复元素
	- 由于没有索引，方法基本和`Collection`一致，不像`List`有更多方法



2. `Set`实现类迭代：
	- `iterator`迭代器对象循环
	- 增强`for`循环



3. `HashSet`
	
	1. 基本介绍
	
		- `HashSet`的底层实际是`HashMap`，见其构造器：
	
		- ```java
			public HashSet() { map = new HashMap<>(); }
			```
	
		- 其他性质已在`Set`中描述，不再赘述
	   
	2. 底层机制
		
		- 分析`HashSet`的底层就是分析`HashMap`，后者的底层是：数组＋链表＋红黑树
		- `HashSet`的`add`方法在底层是如何实现的——使用`hashCode`和`equals`方法：
		- 添加元素时，先得到`Hash`值，再由算法转为索引值
		- 在存储数据的表`table`中，查看该索引处是否已经存放元素
		- 如果没有，直接加入
		- 如果有，调用`equals`方法比较。如果相同，放弃添加。如果不相同，比较（该链表/红黑树中的）下一个元素。如果到最后都没有相同元素，才添加该元素
		- 在Java 8中，如果一条链表的元素个数达到`TREEIFY_THERSHOLD`(默认为8)，且`table`的长度大于等于`MIN_TERRIFY_CAPACITY`（默认为64），就会将该条链表树化
	
	
	3. 源码分析得到的一些结论：
	
		- `Hashset`的属性`map`是一个`HashMap`对象——双列集合。具体地，`map`将`add`方法传入的值作为key，而将该类的静态属性`PRESENT`作为value。`PRESENT`的类型是`Object`，在这里起占位的作用
	
		- `HashMap`的方法`hash`实现如下——这是个与`hashCode`不同的方法：
	
		- ```java
			static final int hash(Object key) {
			        int h;
			        return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);
			    }
			```
			
		- `HashMap`的方法`putVal`真正实现了添加元素
	
		- 当`map`中元素的数量（注意它和`table`的长度是不同的概念）达到一定值，就会调用`resize()`方法扩容`table`
	
	4. 扩容机制
		
		- `map`**第一次**添加时，`table`扩容到**16**，临界值`threshold`的值为`16 * loadFactor = 16 * 0.75 = 12`
		- 如果`map`中的**元素数量达到了临界值**，则**`table`扩大一倍**，临界值相应变化，即`32`和`32 * 0.75 = 24`。以此类推。
		- 如果**一条链表的元素个数**达到`TREEIFY_THERSHOLD`(默认为**8**)，且**`table`的长度大于等于**`MIN_TERRIFY_CAPACITY`（默认为**64**），就会将**该条链表树化**。否则，仍对`table`扩容，即：
	   - 数组的长度小于`MIN_TERRIFY_CAPACITY`，但一条链表的元素达到`TREEIFY_THERSHOLD`时，即使`map`中的元素数量没有达到临界值，`table`的长度仍将翻倍。
	   
	5. 课堂练习
		
		- 需求：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203020728418.png" alt="image-20220302072815211" style="zoom:33%;" />
		
		- ```java
		   import java.util.HashSet;
		   import java.util.Objects;
		   
		   public class Test {
		       public static void main(String[] args) {
		           HashSet hashSet = new HashSet();
		           hashSet.add(new Employee("jack", 23));
		           hashSet.add(new Employee("rose", 21));
		           hashSet.add(new Employee("jack", 23));
		           System.out.println(hashSet);
		       }
		   }
		   
		   class Employee {
		       private String name;
		       private int age;
		   
		       public Employee(String name, int age) {
		           this.name = name;
		           this.age = age;
		       }
		   
		       //直接使用快捷键alt + insert 选择equals() and hashCode()让系统自动重写
		       @Override
		       public boolean equals(Object o) {
		           if (this == o) return true;
		           if (o == null || getClass() != o.getClass()) return false;
		           Employee employee = (Employee) o;
		           return age == employee.age &&
		                   Objects.equals(name, employee.name);
		       }
		   
		       //如果属性相同，返回相同的hashCode
		       @Override
		       public int hashCode() {
		           return Objects.hash(name, age);
		       }
		   
		       @Override
		       public String toString() {
		           return "Employee{" +
		                   "name='" + name + '\'' +
		                   ", age=" + age +
		                   '}';
		       }
		   }
		   ```
		
		- 思考：为什么要同时重写`equals()`和`hashCode()`方法？
		
		- 目前得出的结论是：重写`hashCode`方法，以保证相同元素会落到`table`的同一个索引。再用`equals`方法检查该链表（或红黑树）是否存在相同元素
	


  	

4. `LinkedHashSet`
	1. 基本说明
		- `LinkedHashSet`是`HashSet`的子类
		- `LinkedHashSet`底层是一个`LinkedHashMap`。后者底层维护了一个数组 + 双向链表
		- `LinkedHashSet`根据元素的`hashCode`值来决定元素的存储位置，同时使用链表维护元素的——使元素在遍历时可以按照插入顺序输出
		
	2. 底层机制（源码分析）
		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203020756277.png" alt="image-20220302075648678" style="zoom: 33%;" />
		
		- 创建`LinkedHashSet`时，调用其父类`HashSet`的构造器，为（父类）属性`map`创建了一个`LinkedHashMap`对象
		
		- `LinkedHashMap`中，同样有一个数组`table`，但类型（指元素的运行类型，编译类型仍为`Node[]`）为`Entry[]`，见如下定义：
		
		- ```java
			static class Entry<K,V> extends HashMap.Node<K,V> {
			        Entry<K,V> before, after;
			        Entry(int hash, K key, V value, Node<K,V> next) {
			            super(hash, key, value, next);
			        }
			    }
			```
		
		- `before`、`after`用于连接双向链表。从`Node`继承来的属性在维护`table`方面起着和`HashMap`一样的作用
		
		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203020912807.png" alt="image-20220302091237682" style="zoom:33%;" />
		
		- 故，`LinkedHashMap`在维护`table`（`table`扩容，何时将链表转为红黑树，是否添加元素）方面和`HashMap`一样。只是多了连接双向链表的两个属性。在分析时不应该被双向链表这一概念所迷惑，其本质还是`HashMap`（也可能是视频过于强调双向链表了:grey_question:）



5. `TreeSet`

	1. 基本介绍：

		- `TreeSet`可以按照自定义的顺序存储元素，从而使遍历有序

		- **不能添加`null`**

		- 见代码：

		- ```java
			import java.util.Comparator;
			import java.util.TreeSet;
			
			public class Test {
			    public static void main(String[] args) {
			        TreeSet treeSet = new TreeSet(new Comparator() {
			            @Override
			            public int compare(Object o1, Object o2) {
			                //return ((String) o1).length() - ((String) o2).length();
			                return ((String) o1).compareTo((String) o2);
			            }
			        });
			
			        treeSet.add("123");
			        treeSet.add("abc");
			
			    }}
			
			```

	2. 底层机制（以分析以上代码为例）

		- `TreeSet`的底层是`TreeMap`。后者的底层是一棵有序树（属性名为`root`）
		- 树的排序规则由创建对象时传入的`Comparator`接口类确定
		- 加入`TreeSet`的对象是以键的形式存在`TreeMap`中的，而值仍是一个静态`Object`类属性`PRESENT`（起占位作用）
		- `TreeMap`使用`comparator`来判断传入的值是否重复。如果重复，就替换值。否则加入到`TreeMap`中
		- 因此，对于`TreeSet`，如果加入的两个元素按照`comparator`比较的结果是相等，则后加入的元素无法加入（改变以上代码中`compare`方法的实现即可证明），因为`TreeSet`中的元素是`TreeMap`中的键，而键在添加后是无法改变的
		- 如果创建对象时使用无参构造器，则添加元素时的比较规则为该元素类型的`compareTo()`方法



## `Map`接口

1. `Map`接口特点
	- `Map`用于保存具有映射关系的数据：`key -- value`（双列集合）
	- `key`和`value`可以是任何引用类型的数据（包括`null`），它们会被封装到`HashMap$Node`（`HashMap`的内部类`Node`）对象中
	- `key`不允许重复，而`value`可以重复



2. `Map`常用方法
	- `put(Object key, Object value)`：添加（修改）键值对
	- `remove(Object key)`：根据键删除键值对
	- `get(Object key)`：根据键返回值
	- `size()`：返回键值对数目
	- `isEmpty()`：判断键值对数目是否为零
	- `clear()`：删除所有键值对
	- `containsKey(Object key)`：查找键是否存在



3. `Map`遍历方式

	- 使用`keySet()`、`values()`和`entrySet()`方法分别返回包含键的`set`对象、包含值的`Collection`对象和包含键值对的`set`对象

	- 以上三个对象，都没有其特有的属性。也就是说，虽然叫“包含”，但它们都指向`Map`，而不是另外复制了一份`table`的内容。它们的作用，是为了方便程序员遍历`Map`

	- 然后再用`set`的遍历方式（增强`for`和迭代器）遍历即可

	- `keySet()`方法可以结合`get(Object key)`方法遍历相应的值

	- `values()`方法只能遍历值

	- `entrySet()`比较特殊，见该方法定义:

		- ```java
			public Set<Map.Entry<K,V>> entrySet() {
			        Set<Map.Entry<K,V>> es;
			        return (es = entrySet) == null ? (entrySet = new EntrySet()) : es;
			    }
			```

	- 而`Map.Entry`接口的方法和实现如下：

		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203021238525.png" alt="image-20220302123829403" style="zoom:33%;" />
		- `Node`即为`HashMap`的`table`中存放的数据类型

	- ```java
		import java.util.*;
		
		public class Test {
		    public static void main(String[] args) {
		        HashMap hashMap = new HashMap();
		        hashMap.put(1, "lilith");
		        hashMap.put("jack", true);
		        hashMap.put(null, "李东风");
		
		        Set key_set = hashMap.keySet();
		        for (Object o : key_set) {
		            System.out.println(o + " --- " + hashMap.get(o));
		        }
		        System.out.println("=======================");
		
		        Collection values = hashMap.values();
		        Iterator iterator = values.iterator();
		        while (iterator.hasNext()) {
		            System.out.println(iterator.next());
		        }
		        System.out.println("=======================");
		
		        Set entry_set = hashMap.entrySet();
		        //Object 没有提供getKey方法，需要向下转型
		        for (Object o : entry_set) {
		            Map.Entry entry = (Map.Entry) o;
		            System.out.println(entry.getKey() + "---" + entry.getValue());
		        }
		        
		    }}
		```

	



## `Map`接口实现类



1. `HashMap`
	1. 基本介绍
		- `HashMap`是`Map`接口**使用频率最高**的实现类
		- 它以键值对的形式存储数据（每个键值对的类型是`HashMap$Node`）
		- 如果添加相同的`key`，会覆盖原来的`value`。这相当于修改
		- 与`HashSet`一样，不能保证输出顺序与输入顺序相同
		- `HashMap`是**线程不安全**的
	2. 底层机制
		- `HashMap`的底层机制在分析`HashSet`时已经分析了。唯一需要强调的是，当要添加的键值对的`key`已经存在时，旧的值会被替换。而这一点在`HashSet`中是无关紧要的。



2. `Hashtable`
	1. 基本介绍
		- 该类存放键值对，即`key --- value`
		- **键和值都不能为`null`**
		- `Hashtable`使用方法基本和`HashMap`一样
		- `Hashtable`是**线程安全**的。而`HashMap`是线程不安全的
		- 因此，`HashMap`的效率比`Hashtable`高
	2. 底层机制
	
		  - 底层是数组（`table`）+ 单链表
	
		  - 当元素个数`count >= threshold`时（后者为`capacity * 0.75`），执行`rehash()`函数
	
		  - `rehash()`函数将`table`容量扩大至`2 * capacity + 1`，并对原先`table`中的**每一个**元素重新哈希，存放到新的`table`中
	
	
	
3. `Properties`
	1. 基本介绍
		- `Properties`继承`Hashtable`类并且实现`Map`接口，以键值对形式存放数据
		- 故使用方法和`Hashtable`类似
		- `Properties`可用于从`.properties`文件中加载数据到`Properties`对象，并进行读取和修改。这类文件通常作为配置文件使用



4. `TreeMap`

	- 基本原理已经在分析`TreeSet`时分析过了

	- **传入的键不能为`null`**

	- 需要再次强调添加键值对时的重复问题：

		- ```java
			import java.util.Comparator;
			import java.util.TreeMap;
			
			public class Test {
			    public static void main(String[] args) {
			        TreeMap tmp = new TreeMap(new Comparator() {
			            @Override
			            public int compare(Object o1, Object o2) {
			                return ((String) o1).length() - ((String) o2).length();
			            }
			        });
			        tmp.put("123", "李东风");
			        tmp.put("456", "臭卷宝");
			        System.out.println(tmp);
			    }}
			```

		- 只要按照`compare`方法，两个值相同，那么后加入的值**会**替换之前的值，但后加入的键**不会**替换之前的键



## `Collections`工具类

1. 基本介绍
	- `Collections`是一个操作`Set`、`List`和`Map`等集合的工具类
	- `Collections`中提供了一系列静态方法，对集合元素进行排序、查询、修改等操作



2. 常用静态方法：
	- `reverse(List)`：反转`List`元素顺序
	- `shuffle(List)`：对`List`元素进行随机排序
	- `sort(List)`：按照对`List`元素进行自然排序
	- `sort(List, Comparator)`：按照指定的`Comparator`对`List`元素进行排序
	- `swap(List, int, int)`：交换`List`中两个索引处的元素
	- `Object max(Collection)`：按照元素的自然排序，返回`Collection`中最大的元素
	- `Object max(Collection, Comparator)`：按照指定的排序规则，返回`Collection`中最大的元素
	- `int frequency(Collection, Object)`：返回`Collection`中指定元素出现的次数
	- `boolean replaceAll(List list, Object oldVal, Object newVal)`：将`List`中的所有`oldVal`替换为`newVal`



## 总结：开发中如何选择集合类

- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203040743056.png" alt="image-20220304074316320" style="zoom:50%;" />





## 课后作业

1. 分析`HashSet`和`TreeSet`分别如何去重的

	- `HashSet`去重机制：

		- 使用`hashCode()` + `equals()`方法：
		- 存入对象时，会调用其`hashCode()`方法，运算得到一个`hash`值，通过`hash`值运算得到对应的`table`的索引
		- 如果`table`索引所在的位置为`null`，则直接加入。
		- 如果该位置有元素，则对该位置的结构（链表 / 红黑树）中的元素遍历比较（使用`equals()`方法）。如果全都不相同，才添加。如果存在相同元素，则添加失败。
		- 这道题也回答了这一问题——为什么要同时重写`hashCode()`和`equals()`方法

	- `TreeSet`的去重机制：

		- 在创建`TreeSet`对象时，如果传入`Comparator`对象，就使用实现的`compare()`方法进行比较。如果该方法返回`0`，则认为两个元素相同，不添加

		- 如果使用无参构造器，在比较时使用传入对象实现`Compareable`接口的`compareTo()`方法。部分源代码如下：

			- ```java
				 @SuppressWarnings("unchecked")
				                Comparable<? super K> k = (Comparable<? super K>) key;
				            do {
				                parent = t;
				                cmp = k.compareTo(t.key);
				```

			- 注意到，如果传入的对象没有实现`Comparable`接口，程序运行时会抛出`ClassCastException`异常





# 第12章：泛型（generic）



## 泛型引入

1. 传统方法使用集合的问题

	- 遍历时，需要进行类型转换（从`Object`转到指定类）。如果集合中数据量较大，影响程序效率

	- 不能对加入集合中的数据类型进行约束，因而不安全
	- 例如，在遍历时，需要调用某方法，则应对元素向下转型，再调用方法。转型的类不匹配时，会抛出`ClassCastException`异常



2. 使用泛型的好处
	- **编译时**，会检查添加的元素的类型
	- 减少了类型转换的次数
	- 不再提示编译警告



## 泛型基本语法

1. 基本介绍

	- 泛型又称参数化类型，是JDK 5.0之后的新特性，以解决数据类型的安全性问题。

	- 泛型可以理解为数据类型的类型，其值代表某一具体的数据类型，如`String`、`Integer`

	- 使用泛型，只需在类实例化时指定需要的数据类型即可。

	- 泛型可以保证：如果程序在编译时没有发出警告，在运行时不会抛出`ClassCastException`异常

	- 泛型的作用：在类声明时通过标识符表示类中某属性的类型，或是某方法的返回值，或是参数类型

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        Person<String> lilith = new Person<String>("lilith");
		        System.out.println(lilith.getData());
		
		        Person<Integer> integerPerson = new Person<>(456);
		        System.out.println(integerPerson.getData());
		    }}
		class Person<E> {
		    //泛型属性
		    E data;
		
		    //泛型作为参数
		    public Person(E data) {
		        this.data = data;
		    }
		
		    //泛型作为返回值
		    public E getData() {
		        return data;
		    }}
		```

		- 创建对象时，只需要在`<>`中加入数据类型即可。编译器会使用该数据类型替换`E`进行编译



2. 泛型的声明

	- 基本语法：

		- ```java
			interface A<T>{}
			class B<K,V>{}
			```

	- 语法中，`T`、`K`和`V`表示类型
	- 可以使用任意字母表示泛型，但常用`T`表示——type的意思



3. 泛型应用场景：

	- ```java
		import java.util.HashMap;
		import java.util.Iterator;
		import java.util.Map;
		import java.util.Set;
		
		public class Test {
		    public static void main(String[] args) {
		        HashMap<Integer, Student> hm = new HashMap<>();
		        hm.put(23, new Student("Isaac", 23));
		        hm.put(17, new Student("Gabriel", 42));
		
		        Set<Map.Entry<Integer, Student>> entrySet = hm.entrySet();
		        Iterator<Map.Entry<Integer, Student>> iterator = entrySet.iterator();
		        
		        while (iterator.hasNext()) {
		            Map.Entry<Integer, Student> en = iterator.next();
		            System.out.println("Student ID: " + en.getKey() + "\t" + en.getValue());
		        }
		    }
		}
		
		class Student {
		    private String name;
		    private int age;
		
		    public Student(String name, int age) {
		        this.name = name;
		        this.age = age;
		    }
		
		    @Override
		    public String toString() {
		        return "name=" + name + ", age=" + age;
		    }
		}
		```



4. 使用细节

	- `<>`内只能传入引用类型，**不能传入基本数据类型**

	- 在指定泛型基本类型后，可以**传入该类型或其子类**

		- ```java
			public class Test {
			    public static void main(String[] args) {
			        A<B> ba = new A<>(new B());
			        A<B> ba1 = new A<>(new C());
			    }}
			class B{}
			class C extends B{}
			
			class A<E>{
			    E e;
			
			    public A(E e) {
			        this.e = e;
			    }
			}
			```

	- 两种泛型使用格式

		- ```java
			ArrayList<String> strings = new ArrayList<>();
			ArrayList<String> strings2 = new ArrayList<String>();
			```

		- 在开发中，往往使用第一种格式来简写。这时，编译器会进行类型推断。

	- 如果不指定泛型类型，如`ArrayList arrayList = new ArrayList();`，则泛型默认为`Object`



## 自定义泛型

1. 自定义泛型类

	- 基本语法：

		- ```
			class 类名<T, R>{
				成员
			}
			```

	- 泛型的值**不能是基本数据类型**

	- 普通成员可以使用泛型

	- **不能使用泛型的数组**——因为编译器不知道分配多大的空间。可以考虑使用`Object[]`，集合类的源码就是这么写的

	- 泛型类的类型，是在**创建对象时**确定的
	
	- 静态方法**不能**使用泛型——因为类加载在创建对象前



2. 自定义泛型接口

	- 基本语法：

		- ```
			interface 接口名<T, R>{}
			```

	- 接口中，静态成员也不能使用泛型

	- 泛型接口的类型，在**继承接口或实现接口时指定**

	- 没有指定类型，默认为`Object`

	- ```java
		interface I1<T, R> {
		    R get(T t);
		    //默认方法也能使用泛型
		    default T deFunc() {
		        return null;
		    }
		}
		interface I2 extends I1<String,Double>{}
		
		class C implements I1<Integer,Float>{
		    @Override
		    public Float get(Integer integer) {
		        return null;
		    }
		    @Override
		    public Integer deFunc() {
		        return null;
		    }
		}
		```





3. 自定义泛型方法

	- 基本语法：

		- ```
			修饰符 <K,V> 返回类型 方法名(参数列表){}
			```

	- 泛型方法可以定义在普通类中，也可定义在泛型类中

	- 当泛型方法被调用时，类型会自动确定（一般是由传入的参数类型确定）。也是在编译层面确定的

	- 对于泛型类中的方法，如`public void eat(E e)`，它不是泛型方法，只是使用了类的泛型

	- ```java
		import java.util.ArrayList;
		
		public class Test {
		    public static void main(String[] args) {
		        A a = new A();
		        //使用时自动进行类型推断，不需要人为地在<>中添加类型
		        a.f1("yu",new ArrayList<Double>());
		    }}
		
		class A{
		    //普通类中的泛型方法
		    public <K,R> void f1(K k,R r){}
		}
		
		class B<T,P>{
		    //泛型类中的普通方法
		    public void f1(T t){}
		    //泛型类中的泛型方法
		    //一般地，泛型方法的泛型标识符应和类的不一样
		    public <E> void f2(E e){}
		    //不同泛型的混合使用
		    public <K> void f3(K k,T t){}
		}
		```





## 泛型继承和通配符

1. **泛型不具备继承性**，以下语句是非法的：

	- ```java
		List<Object> list = new ArrayList<String>();
		```

2. `<?>`：支持任意类型

3. `<? extends A>`：支持`A`类及其子类，规定了泛型的上限

4. `<? super A>`：支持`A`类及其父类，规定了泛型的下限

5. ```java
	import java.util.ArrayList;
	import java.util.List;
	
	public class Test {
	    public static void main(String[] args) {
	        f1(new ArrayList<Object>());
	        f1(new ArrayList<String>());
	        f1(new ArrayList<A>());
	        f1(new ArrayList<B>());
	        f1(new ArrayList<C>());
	
	        //f2(new ArrayList<Object>()); //not allowed
	        //f2(new ArrayList<String>()); //not allowed
	        f2(new ArrayList<A>());
	        f2(new ArrayList<B>());
	        f2(new ArrayList<C>());
	
	        f3(new ArrayList<Object>());
	        //f3(new ArrayList<String>()); //not allowed
	        f3(new ArrayList<A>());
	        //f3(new ArrayList<B>()); //not allowed
	        //f3(new ArrayList<C>()); //not allowed
	
	    }
	
	    public static void f1(List<?> l) {}
	
	    public static void f2(List<? extends A> l) {}
	
	    public static void f3(List<? super A> l) {}
	}
	
	class A {}
	
	class B extends A {}
	
	class C extends B {}
	```







# 第13章：坦克大战（1）

## 原版游戏

网址：https://90kids.com/tank-1990/



## java绘图坐标体系

1.  基本介绍
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203061458347.png" alt="image-20220306145855206" style="zoom:33%;" />
	- 该图说明了Java坐标体系。坐标原点位于左上角，以像素为单位。每一个像素用数对`(x, y)`来表示
	- 何为像素？计算器屏幕显示的内容由屏幕上的一个个像素组成。如果显示器分辨率为800 *600，则表示该屏幕一行有800个点，共600行。故该屏幕共有480000个像素
	- 该坐标系中，y轴正方向朝下——这和二维数组/二维矩阵的行的编号一样

## java绘图技术

1. 快速入门

	- 相关说明以注释形式写在代码中

	- ```java
		import javax.swing.*;
		import java.awt.*;
		
		//JFrame类似于画框，需要将画板(JPanel)摆在上面
		public class Test extends JFrame {
		    private MyPanel mp;
		
		    public static void main(String[] args) {
		        new Test();
		    }
		
		    Test() {
		        mp = new MyPanel();
		        this.add(mp);//将画板放在画框上
		        this.setSize(400, 400);//程序执行后窗口的大小
		        this.setVisible(true);//使窗口可见
		        this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);//关闭窗口同时结束程序
		    }
		}
		
		//JPanel类似画板，在上面才能画图
		class MyPanel extends JPanel {
		    //Graphics 类似于画笔，需要在画板上画图。
		    //画什么形状取决于调用Graphics的哪个方法
		    @Override
		    public void paint(Graphics g) {
		        super.paint(g);//这句话必须保留
		
		        //画了个左上顶点为(20,20)，边长为100的正方形的内切圆
		        g.drawOval(20, 20, 100, 100);
		
		        g.drawString("臭卷宝", 60, 60);//插入文本框
		    }
		}
		```



2. 绘图原理
	1. `Component`类提供了两个和绘图相关的重要的方法：
		- :one:`paint(Graphics g)`：绘制组件外观
		- :two:`repaint()`：刷新组件外观
	2. 当组件第一次在屏幕上显示时，程序会自动调用`paint`方法来绘制组件。在以下情况，`paint`方法也会被调用：
		- 窗口最小化，再最大化
		- 窗口大小发生变化
		- `repaint`方法被调用



3. `Graphics`常用方法

	- `drawLine(int x1, int y1, int x2, int y2)`：给出两点，画一条线段

	- `drawRect(int x, int y, int width, int height)`：画一个空心矩形，给出其左上顶点位置和长款

	- `drawOval(int x, int y, int width, int height)`：画一个空心椭圆，是`drawRect(x,y,width,height)`画出的矩形的内切圆

	- `fillRect(int x, int y, int width, int height)`：画一个实心矩形

	- `fillOval(int x, int y, int width, int height)`：画一个实心椭圆

	- `setFont(Font font)`：设置画笔的字体

	- `setColor(Color c)`：设置画笔的颜色

	- `drawString(String str, int x,int y)`：类似于插入文本框（和文体），`(x, y)`是文本框的左下顶点

	- `drawImage(Image img, int x, int y, int width, int height, ImageObserver observer)`：画板上显示图片，图片的左上顶点为`(x, y)`

	- ```java
		public void paint(Graphics g) {
		
		        super.paint(g);
		        g.drawLine(60, 60, 230, 450);
		
		        g.setColor(Color.GREEN);
		
		        g.fillRect(20, 20, 400, 200);
		
		        g.setColor(Color.RED);
		        g.setFont(new Font("黑体", Font.ITALIC, 40));
		        g.drawString("臭卷宝", 60, 150);
		
		        //该图片的相对路径是/out/production/hello/9k=.jpg
		        //hello是包名
		        //注意，有些图片就是显示不出来，不知道为什么
		        Image image = Toolkit.getDefaultToolkit().getImage(MyPanel.class.getResource("/9k=.jpg"));
		        g.drawImage(image, 400, 20, 500, 300, this);
		    }
		```

	- 







## java事件处理机制

1. 小球移动案例

	- 目标：使屏幕上的小球受键盘控制

	- ```java
		import javax.swing.*;
		import java.awt.*;
		import java.awt.event.KeyEvent;
		import java.awt.event.KeyListener;
		
		public class Test extends JFrame {
		    private MyPanel mp = null;
		
		    public static void main(String[] args) {
		        new Test();
		    }
		
		    Test() {
		        mp = new MyPanel();
		        this.add(mp);
		        this.addKeyListener(mp); //使JFrame对象可以监听mp面板上发生的键盘事件
		        this.setSize(200, 200);
		        this.setVisible(true);
		        this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		    }
		}
		
		//KeyListener是监听器，用于监听键盘事件
		class MyPanel extends JPanel implements KeyListener {
		    private int x = 10;
		    private int y = 10;
		
		
		    @Override
		    public void paint(Graphics g) {
		        super.paint(g);
		        g.fillOval(x, y, 20, 20);
		    }
		
		    //字符输出时触发该方法
		    @Override
		    public void keyTyped(KeyEvent e) {
		
		    }
		
		    //按下按键时触发该方法
		    @Override
		    public void keyPressed(KeyEvent e) {
		        if (e.getKeyCode() == KeyEvent.VK_DOWN) {
		            //边界检查
		            if (y < 200 - 10)//面板的宽度
		                ++y;
		        } else if (e.getKeyCode() == KeyEvent.VK_UP) {
		            if (y > 0)
		                --y;
		        } else if (e.getKeyCode() == KeyEvent.VK_LEFT) {
		            if (x > 0)
		                --x;
		        } else if (e.getKeyCode() == KeyEvent.VK_RIGHT) {
		            if (x < 200 - 10)//面板的长度
		                ++x;
		        }
		        repaint();//用于再次执行paint()方法，更新球的位置
		
		    }
		
		    //松开按键时触发该方法
		    @Override
		    public void keyReleased(KeyEvent e) {
		
		    }
		}
		```



2. 基本说明
	- java事件处理采取“委派事件模型”（将事件发生与处理事件分开）。当事件发生时，产生事件对象，会把该**信息**传递给**事件监听者**处理。这里，信息指`java.awt.event`事件类库里某个类所创建的对象
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203100637589.png" alt="image-20220310063721325" style="zoom:33%;" />



3. 深入理解
	1. 事件源：一个产生事件的对象，比如按钮、窗口
	2. 事件：承载事件源状态改变时的对象，例如键盘事件、鼠标事件。此时，会生成一个事件对象，该对象保存了当前事件的很多信息。在`java.awt.event`包和`javax.swing.event`包中定义了各种事件
	3. 事件类型：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203100641597.png" alt="image-20220310064101398" style="zoom: 50%;" />
	4. 事件监听器**接口**：
		- 当事件源产生一个事件，可以传送给事件监听者处理
		- 事件监听者是一个类，它实现了某个事件监听器接口，从而对接收到的事件进行处理
		- 事件监听器接口有多种，不同事件监听器接口可以监听不同事件。一个类可以实现多个监听接口
		- 常用的接口：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203100645191.png" alt="image-20220310064521984" style="zoom:33%;" />







## 坦克大战（Ver 1.0）

1. 设计思路
	1. 设计`Tank`类，使我方坦克（`MyTank`）和敌方坦克继承该类
	2. 设计`MyPanel`类，继承`JPanel`，用于绘图
	3. 设计`TankGame01`类，继承`JFrame`
	3. 设计`EnemyTank`类，继承`Tank`。`MyPanel`对象存储`Vector<EnemyTank>`对象，因为以后要使用多线程操作敌方坦克



2. 编程过程
	1. 设置背景（`MyPanel.paint()`）和窗口（`TankGame01`）参数
	2. 画坦克：在`MyPanel`类定义一个`drawTank`方法，坦克的设计如图：
		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203080810946.png" alt="image-20220308081029783" style="zoom: 25%;" />
	3. 画出四个朝向的坦克
	3. 让坦克能够移动
	3. 画出3辆地方坦克（这一条属于本章作业）



3. 分析：
	- 程序设计仍然采用分层模式——使用`JFrame`和`JPanel`画图也确实需要这么做
	- 这一部分涉及到绘图技术和事件处理机制的知识点，但编程难度与讲解知识点时相近，可以说是按部就班





# 第14章：线程基础

## 线程介绍

1. 线程相关概念
	1. 程序（program）
		- 为完成特定任务、用某种语言编写的一组指令的集合。简而言之，程序就是代码
	2. 进程
		- 进程是指运行中的程序。当使用迅雷时，启动了一个进程，操作系统为迅雷分配新的内存空间
		- 进程是程序的一次执行过程，或是正在运行的一个程序。它是动态过程：有自身的产生、存在和消亡过程
	3. 线程
		- 线程由进程创建，是进程的一个实体
		- 一个进程可以拥有多个线程。例如，迅雷可以同时执行多个下载任务
	4. 单线程：同一个时刻，只允许执行一个线程
	5. 多线程：同一时刻，可以执行多个线程
	6. 并发：
	
		  - 同一时刻，多个任务交替执行。由于CPU在任务间的切换速度极快，造成一种“同时”的错觉。
		  - 简而言之，单核CPU执行的多任务就是并发
		  - <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203110743672.png" alt="image-20220311074335476" style="zoom: 33%;" />
	7. 并行：
	
		  - 同一时刻，多个任务同时执行
	
		  - 多核CPU可以实现并行
	
		  - <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203110744584.png" alt="image-20220311074431415" style="zoom:33%;" />



2. 查看当前电脑有几颗CPU：

	```java
	public class Test {
	    public static void main(String[] args) {
	        Runtime runtime = Runtime.getRuntime();
	        System.out.println(runtime.availableProcessors()); }}
	```

	



## 线程使用

1. java中使用线程的两种方法
	- :one:继承`Thread`类，重写`run()`方法
	- :two:实现`Runnable`接口，重写`run()`方法



2. 继承`Thread`类——基本介绍

	- 要求：

		- 编写程序，开启一个线程。该线程每隔1秒输出一句话
		- 当输出8此后，结束该线程

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        Cat cat = new Cat();
		        cat.start();//启动线程
		    }}
		
		class Cat extends Thread {
		    @Override
		    public void run() {
		        int time = 0;
		        while (time++ < 8) {
		            System.out.println("miao~~" + time);
		            try {//必须捕获异常，不然会报错
		                Thread.sleep(1000);//停顿1秒
		            } catch (InterruptedException e) {
		                e.printStackTrace();
		            }
		        }    }}
		```



3. 多线程机制

	- 分析以下代码，并使用`Jconsole`监控线程执行情况

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        Cat cat = new Cat();
		        cat.start();//启动线程
		        int time = 0;
		        while (time++ < 60) {
		            System.out.println("main方法" + time + "线程名：" + Thread.currentThread().getName());
		            try {
		                Thread.sleep(1000);//停顿1秒
		            } catch (InterruptedException e) {
		                e.printStackTrace();
		            }
		        }    }}
		
		class Cat extends Thread {
		    @Override
		    public void run() {
		        int time = 0;
		        while (time++ < 80) {
		            System.out.println("miao~~" + time + "线程名：" + Thread.currentThread().getName());
		            try {
		                Thread.sleep(1000);//停顿1秒
		            } catch (InterruptedException e) {
		                e.printStackTrace();
		            }
		        }    }}
		```

	- 程序执行分析

		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203110839913.png" alt="image-20220311083902741" style="zoom:50%;" />
		- 当执行程序时，打开了一个进程
		- 调用`main`方法时，开启了`main`线程
		- 在`main`线程中，又开启了`Thread-0`子线程（即`cat.start();`）
		- 两个线程同时执行，即`Thread-0`的执行并不会阻塞`main`的执行
		- 由于`main`方法中只循环60次，所以`main`线程先结束。此时，程序不会退出，`Thread-0`线程继续执行
		- 当`Thread-0`线程结束（循环了80次后）。当前进程中没有线程执行，进程关闭，程序结束。
		
	- 为什么使用`start()`方法，而不直接使用`run()`方法
	
	  - 直接使用`run()`方法，就不会创建`Thread-0`子线程。`main`线程在执行完`run()`方法后才会执行后面的内容——这时，不涉及多线程问题
	  - `start()`方法负责创建子线程。具体来说，该方法将调用`start0()`方法，定义如下：`private native void start0();`（`native`表示本地方法，由JVM调用），该方法负责创建线程，并调用`run()`方法
	  - <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203112006597.png" alt="image-20220311200622437" style="zoom: 50%;" />



4. 实现`Runnable`接口

	- 代码：

	- ```java
		public class Test {
		    public static void main(String[] args) {
		        Cat cat = new Cat();
		        Thread thread = new Thread(cat);
		        thread.start();
		    }}
		
		class Cat implements Runnable {
		    @Override
		    public void run() {
		        int time = 0;
		        while (time++ < 8) {
		            System.out.println("miao~~" + time + "线程名：" + Thread.currentThread().getName());
		            try {
		                Thread.sleep(1000);//停顿1秒
		            } catch (InterruptedException e) {
		                e.printStackTrace();
		            }
		        }    }}
		```

	- 使用`Runnable`接口时，使用了（静态）代理模式这一设计模式。即`Thread`的构造器接收`Runnable`对象，再由`Thread`的`start`方法调用该对象的`run`方法

	- 源码分析：

		- 用有参构造器创建`Thread`对象后，`cat`被赋给`target`属性（定义如下：`private Runnable target;`）

		- `thread.start();`调用`start0`本地方法，后者创建子线程并使用`thread`的`run`方法。定义如下：

		- ```java
			@Override
			    public void run() {
			        if (target != null) {
			            target.run();
			        }
			    }
			```

		- 由动态绑定机制，将会执行定义在`cat`中的`run`方法，从而实现代理



5. `Thread` vs `Runnable`

	1. 从java设计的角度看，两者创建线程在本质上没有区别

	2. 实现`Runnable`接口方式更适合多个线程共享一个资源的情况，而且避免了单线程的限制，例如：

		- ```java
			T t = new T(123);
			Thread thread1 = new Thread(t);
			Thread thread2 = new Thread(t);
			thread1.start();
			thread2.start();
			```

		- 如果继承`Thread`类，每次都会创建不同的对象，无法实现多线程访问一个资源



6. 线程终止

	- 当线程完成任务后，会自动退出

	- 还可以通过使用变量，控制`run()`方法的执行，来停止线程。即**通知方式**

	- ```java
		public class Test {
		    public static void main(String[] args) throws InterruptedException {
		        Cat cat = new Cat();
		        cat.start();
		        Thread.sleep(1000 * 3);
		        cat.setLoop(false);//终止循环
		    }}
		
		class Cat extends Thread {
		    private boolean loop = true;//loop用于控制循环进行
		
		    @Override
		    public void run() {
		        int time = 0;
		        while (loop) {
		            System.out.println("miao~~" + (++time));
		
		            try {
		                Thread.sleep(50);
		            } catch (InterruptedException e) {
		                e.printStackTrace();
		            }
		        }
		    }
		
		    public void setLoop(boolean loop) {
		        this.loop = loop;
		    }
		}
		```







## `Thread`方法

1. 常用方法第一组

	- `setName`：设置线程名称
	- `getName`：返回线程名称
	- `start`：使线程开始执行
	- `run`：调用线程的`run`方法
	- `setPriority`：更改线程优先级
	- `getPriority`：获取线程优先级
	- `sleep`：静态方法，让正在执行的线程休眠指定毫秒数
	- `interrupt`：中断线程

2. 注意事项

	- `start`底层会创建新的线程，调用`run`。`run`只是一个普通的方法，不会启动新的线程

	- 线程优先级范围：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203120943511.png" alt="image-20220312094307342" style="zoom: 25%;" />

	- `sleep`是`Thread`类静态方法，使当前线程休眠

	- `interrupt`方法中断线程，但没有真正结束线程。故，一般用于中断正在休眠的线程

	- ```java
		public class Test {
		    public static void main(String[] args) throws InterruptedException {
		        Cat cat = new Cat();
		        cat.setName("李东风");
		        cat.start();
		        Thread.sleep(1000 * 3);
		        System.out.println("打断" + cat.getName() + "休息");
		        cat.interrupt();
		    }}
		
		class Cat extends Thread {
		
		    @Override
		    public void run() {
		
		        while (true) {
		            for (int i = 1; i <= 5; i++) {
		                System.out.println(Thread.currentThread().getName() + "吃冻干" + i);
		            }
		            System.out.println("休息10秒继续吃\n");
		            try {
		                Thread.sleep((10 * 1000));
		            } catch (InterruptedException e) {//调用interrupt方法，就会被捕获
		                System.out.println("休息被打断了，继续吃\n");
		            }
		        }
		
		    }}
		```



3. 常用方法第二组

	- `yield`：静态方法，让出当前CPU，使其他线程执行（并行的情况）。但礼让的时间不确定，也不一定成功

	- `join`：线程的插队。某线程一旦插队成功，则会先执行完插队的线程的任务，再执行当前线程的任务

		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203121329202.png" alt="image-20220312132935008" style="zoom:33%;" />
		- 在`t1`线程插队时，`main`暂时停止执行任务，直到`t1`结束

	- ```java
		public class Test {
		    public static void main(String[] args) throws InterruptedException {
		        Cat cat = new Cat();
		        cat.start();
		        for (int i = 1; i <= 10; i++) {
		            System.out.println("臭卷宝" + "吃冻干" + i);
		            Thread.sleep(1000);
		            if(i==5){
		                System.out.println("============================");
		                cat.join();
		                //Thread.yield();//不一定成功
		                System.out.println("============================");
		            }
		        }
		    }}
		
		class Cat extends Thread {
		    @Override
		    public void run() {
		        for (int i = 1; i <= 10; i++) {
		            System.out.println("李东风" + "吃冻干" + i);
		            try {
		                Thread.sleep(1000);
		            } catch (InterruptedException e) {
		                e.printStackTrace();
		            }
		        }
		    }}
		```



4. 用户线程和守护线程

	- 用户线程：也叫工作线程。当线程任务执行完成后结束，或者以通知方式结束

	- 守护线程（daemon）：一般是为工作线程服务的。当所有用户线程结束，守护线程自动结束

	- 常见的守护线程：垃圾回收机制

	- ```java
		public class Test {
		    public static void main(String[] args) throws InterruptedException {
		        Cat cat = new Cat();
		        cat.setDaemon(true);//使该线程成为守护线程
		        cat.start();
		        for (int i = 1; i <= 10; i++) {
		            System.out.println("臭卷宝" + "吃冻干" + i);
		            Thread.sleep(1000);
		        }
		    }}
		
		class Cat extends Thread {
		    @Override
		    public void run() {
		        while(true){
		            System.out.println("猫猫的守护者在巡逻");
		            try {
		                Thread.sleep(1000);
		            } catch (InterruptedException e) {
		                e.printStackTrace();
		            }
		        }
		    }}
		```



## 线程生命周期

1. `Thread.State`枚举类表示了线程的几种状态;
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203121536519.png" alt="image-20220312153654273" style="zoom: 50%;" />



2. 线程状态转换图
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203121529972.png" alt="image-20220312152949757" style="zoom: 50%;" />
	- 其中，`Runnable`状态可细分为`Ready`和`Running`两个状态。这两个状态的转换是由CPU决定的



3. 代码：

	```java
	public class Test {
	    public static void main(String[] args) throws InterruptedException {
	        Cat cat = new Cat();
	        System.out.println(cat.getState());
	        cat.start();
	        System.out.println(cat.getState());
	        
	        while(cat.getState()!=Thread.State.TERMINATED){
	            System.out.println(cat.getState());
	            Thread.sleep(500);
	        }
	        System.out.println(cat.getState());
	    }}
	
	class Cat extends Thread {
	    @Override
	    public void run() {
	        try {
	            for (int i = 1; i <= 10; i++) {
	                System.out.println("臭卷宝" + "吃冻干" + i);
	                Thread.sleep(1000);
	            }
	        } catch (InterruptedException e) {
	            e.printStackTrace();
	        }
	    }}
	```

	





## `Synchronized`关键字

1. 线程同步机制
	- 在多线程编程中，一些敏感数据不允许被多个线程同时访问，此时就使用线程同步访问技术，保证数据（该内存地址）在任何时刻，最多有一个线程访问，以保证数据的完整性。
	- 当一个线程完成操作，另一个线程才能进行操作



2. 同步具体手段——`synchronized`

	1. 同步代码块

		- ```java
			synchronized(对象){//只有得到对象锁，才能操作同步代码
			}
			```

	2. 声明方法为同步方法

		- ```java
			public synchronized void m(){}
			```

	3. 代码（售票问题）

		- ```java
			public class Test {
			    public static void main(String[] args) throws InterruptedException {
			        TicketStation ticketStation = new TicketStation();
			        for (int i = 0; i < 3; i++) {
			            new Thread(ticketStation).start();
			        }
			    }}
			
			class TicketStation implements Runnable {
			    private int ticketNum = 300;
			    private boolean loop = true;
			
			    public synchronized void sell() {
			        if (ticketNum == 0) {
			            System.out.println(Thread.currentThread().getName() +"票已售罄");
			            loop = false;
			            return;
			        }
			
			        System.out.println(Thread.currentThread().getName()
			                + "卖出一张票，还剩" + (--ticketNum) + "张票");
			
			        try {
			            Thread.sleep(25);
			        } catch (InterruptedException e) {
			            e.printStackTrace();
			        }
			    }
			
			    @Override
			    public void run() {
			        while (loop) {//这里是个循环，因此不应该将run方法设置为同步方法
			            sell();
			        }
			    }}
			```

		- 如果不使用同步方法，最后显示的票数可能为负



3. 同步原理分析
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203121657295.png" alt="image-20220312165703001" style="zoom: 25%;" />
	- 执行同步方法时，三个线程同时来争夺对象锁。之所以叫对象锁，是因为该对象本身保存了锁打开还是关闭这一信息。故这把锁与方法无关
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203121706543.png" alt="image-20220312170605886" style="zoom: 25%;" />
	- 当一个线程获得锁后，执行该方法。之后锁关闭，三个线程再次争夺该锁





## 互斥锁

1. 基本介绍

	- Java中，引入了对象互斥锁的概念，以保证共享数据操作的完整性

	- 每个对象都对应于一个可称为互斥锁的标记。该标记用来保证在任一时刻，只有一个线程能访问该对象

	- `synchronized`关键字用来与对象的互斥锁联系。使用该关键字的对象，任一时刻只能由一个线程访问

	- 同步的局限性：会导致线程的执行效率要降低——此时，操作变为单线程，但任务总数没有变化（多个线程在这个关口被阻塞，只能一个一个地进入关口）

	- 非静态同步方法的锁可以是`this`，也可以是其他对象

	- 静态同步方法的锁为当前类本身（当前类的`Class`对象）

	- 代码演示;

	- ```java
		class A implements Runnable{
		    Object obj = new Object();
		    //锁在this对象上
		    public synchronized void f1(){}
		    //锁在this对象上
		    public void f2(){
		        synchronized (this){}
		    }
		    //锁在obj对象上
		    public void f3(){
		        synchronized (obj){}
		    }
		    //锁在A.class上
		    public synchronized static void f4(){}
		    //锁在A.class上
		    public static void f5(){
		        synchronized (A.class){}
		    }
		    @Override
		    public void run() {f1();}
		}
		
		```



2. 细节

	  - 非静态同步方法，默认锁对象为`this`

	  - 静态同步方法，默认锁对象为`类名.class`

	  - `synchronized`是一把非公平锁，即同一线程可能连续多次获取到这把锁


3. 互斥锁实现步骤：

	- 先分析上锁的代码

	- 选择同步代码块或同步方法

	- 多个线程的锁对象必须是同一个。参考以下不合格的代码：

		- ```java
			public class Test {
			    public static void main(String[] args) {
			        new A().start();
			        new A().start();
			    }}
			class A extends Thread{
			    @Override
			    public void run() {
			        synchronized (this){}
			    }}
			```

		- 这段代码并没有用到互斥锁，因为是不同的对象锁



## 死锁

1. 基本介绍

	- 每个线程都占用了对方的锁资源，互不相让，导致死锁，程序无法继续执行

2. 案例：

	- ```java
		public class Test {
		    public static void main(String[] args) throws InterruptedException {
		        Demo A = new Demo(true);
		        A.setName("A");
		        Demo B = new Demo(false);
		        B.setName("B");
		        A.start();
		        B.start();
		        
		        int time = 0;
		        while (true) {
		            Thread.sleep(1000);
		            System.out.println("counting: " + (++time));
		        }
		    }
		}
		
		class Demo extends Thread {
		    private static Object o1 = new Object();
		    private static Object o2 = new Object();
		    private boolean flag;
		
		    public Demo(boolean flag) {
		        this.flag = flag;
		    }
		
		    @Override
		    public void run() {
		        if (flag) {
		            synchronized (o1) {
		                System.out.println(Thread.currentThread().getName() + " 占用o1锁资源");
		                synchronized (o2) {
		                    System.out.println(Thread.currentThread().getName() + " 占用o2锁资源");
		                }
		            }
		        } else {
		            synchronized (o2) {
		                System.out.println(Thread.currentThread().getName() + " 占用o2锁资源");
		                synchronized (o1) {
		                    System.out.println(Thread.currentThread().getName() + " 占用o1锁资源");
		                }
		            }
		        }
		    }}
		```
		
	- 某一对象作为锁资源被占用后，使用该对象作为互斥锁的其他地方也无法被访问：在代码中，`B`线程先占用`o2`锁资源，导致`A`线程无法占用。对于`o1`锁资源来说也是如此。`synchronized (o2)`能够在代码多处被使用，而不是只能使用一次



3. 以下操作**会**释放锁（参考线程状态转换图）
	- 当前线程的同步方法（代码块）执行结束
	- 当前线程在同步方法（代码块）中遇到`break`、`return`
	- 当前线程在同步方法（代码块）中出现未处理的`Error`或`Exception`，导致异常结束
	- 当前线程在同步方法（代码块）中执行了线程对象的`wait()`方法。当前线程暂停，并释放锁
4. 以下操作**不会**释放锁
	- 当前线程在同步方法（代码块）中，执行`Thread.sleep()`、`Thread.yield()`方法，会暂停当前线程的执行，但不会释放锁
	- 当前线程执行同步代码块时，其他线程调用该线程的`suspend()`方法，该线程被挂起，但不会释放锁
		- `suspend()`、`resume()`方法已过时，不推荐使用



## 课后作业

1. - 要求：

		- 在`main`方法中启动两个线程

		- 第一个线程循环打印100以内的随机正整数

		- 直到第二个线程从键盘读取了`q`命令

	- 代码：

		- ```java
			import java.util.Scanner;
			
			public class Test {
			    public static void main(String[] args)  {
			        Printer printer = new Printer();
			        printer.start();
			        new Watcher(printer).start();
			    }
			}
			
			class Printer extends Thread {
			    private boolean loop = true;
			
			    @Override
			    public void run() {
			        while (loop) {
			            System.out.println((int) (100 * (Math.random())) + 1);
			            try {
			                Thread.sleep(1000);
			            } catch (InterruptedException e) {
			                e.printStackTrace();
			            }
			        }
			        System.out.println("printer ends");
			    }
			
			    public void setLoop(boolean loop) {
			        this.loop = loop;
			    }
			}
			
			class Watcher extends Thread {
			    private Printer printer;
			
			    public Watcher(Printer printer) {
			        this.printer = printer;
			    }
			
			    @Override
			    public void run() {
			        Scanner scanner = new Scanner(System.in);
			        while (true) {
			            char c = scanner.next().charAt(0);
			            if (Character.toUpperCase(c) == 'Q') {
			                printer.setLoop(false);
			                break;
			            }
			        }
			        System.out.println("watcher ends");
			    }
			}
			```

		- 本来想用`Watcher`类实现`KeyListener`接口，但没有成功——我不会写这个功能

		- 使用`Scanner`对象，在接收输入之前，该线程会一直停在某处，效果和使用`KeyListener`一样。且停止`printer`线程后不会再次运行，没必要实现`KeyListener`接口





# 第15章：坦克大战（2）

## 坦克大战(Ver 2.0)

1. 设计思路
	- 设计`Bullet`类，实现`Runnable`接口，重写`run()`方法以不断改变子弹位置
	- `Mytank`拥有`Bullet`属性。在键盘按下`J`，调用`shot`方法后，`Bullet`对象不断移动（相当于启动一个线程）
	- `Mypanel`需要不断重绘子弹，因此也需要实现`Runnable`接口
	- `EnemyTank`类拥有`Vector<Bullet>`属性
	- 定义`Bomb`类，用于爆炸效果
	- `EnemyTank`实现`Runnable`接口，用于实现坦克自由移动



2. 编程过程
	- 完成`Bullet`类设计，使屏幕上的子弹能移动
	- 使敌方坦克也能发射子弹
	- 我方坦克击中敌方坦克时，敌方坦克消失
	- 坦克消失时产生爆炸效果
	- 敌方坦克可以随机移动
	- 控制坦克的移动范围——不能超出边界
	- 己方坦克发射多颗子弹，以及多颗子弹同时存在的限制
	- 敌方坦克能自动发射子弹
	- 我方坦克被击中后爆炸



3. 总结：
	- 这一部分（也可以说是整个游戏）的重点是多线程，但我掌握得并不特别好
	- 在多线程的实际应用中，应明确：
		- `start()`方法创建线程，线程调用**一次**`run()`方法。至于实现不断重绘子弹、敌方坦克能够自由移动等功能，是依靠`run()`方法中的`while(true){}`，而与多线程问题无关
		- 主线程能够用`start()`创建线程。而线程一旦创建，就**不受主线程的控制**，直至自己消亡。故，重写的`run()`方法应保证能够结束
		- 多个线程只是在时间上并发，每个线程能够使用的数据（即对象）都是定义在主线程中、存储在同一块内存中。因此，`Bullet`对象的`run()`方法只负责改变子弹的位置，而`MyPanel`对象的`run()`方法专门调用`repaint()`方法不断画图
	- 实现不同的功能并不需要新的知识点，但对业务逻辑能力有一定需求——不能写bug
	- 使用封装、继承以精简代码，提高代码复用性
	- 一些功能的实现，比如判断坦克是否被击中，只依靠单纯的循环，效率较低。若是使用特定的算法或数据结构，能提高效率——虽然我没有想过如何优化
	- 整个游戏在功能上还有很多需要完善的地方







# 第16章：IO流



## 文件

1. 什么是文件？
	- 保存数据的地方



2. 文件流
	- 文件在程序中是以流的形式来操作的
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203151700423.png" alt="image-20220315170050068" style="zoom: 33%;" />
	- 流：数据在数据源（文件）和程序（内存）之间的路径（也可以说是途径）
	- 输入流、输出流的主语都是内存



3. 创建`File`对象和创建文件

	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203151740631.png" alt="image-20220315174032446" style="zoom: 50%;" />

	- 构造器：

		- `File(String pathname)`：根据路径创建对象
		- `File(File parent, String child)`：根据父目录对象和子路径创建对象
		- `File(String parent, String child)`：根据父目录和子路径创建对象

	- 使用`createNewFile()`方法创建新文件

	- ```java
		import java.io.File;
		import java.io.IOException;
		
		public class Test {
		    public static void main(String[] args) throws IOException {
		        f1();
		        f2();
		        f3();
		        System.out.println("文件创建成功");
		    }
		
		    public static void f1() throws IOException {
		        File file = new File("D:\\temp\\newFile1");//只是在内存中创建了File对象
		        file.createNewFile();//在磁盘中创建文件
		    }
		
		    public static void f2() throws IOException {
		        File parent = new File("D:/temp/");//两种路径的写法都可以
		        File newFile2 = new File(parent, "newFile2");
		        newFile2.createNewFile();
		    }
		
		    public static void f3() throws IOException {
		        String parent = "D:\\temp\\";
		        String child = "newFile3";
		        new File(parent, child).createNewFile();
		    }
		}
		```



4. 获取文件信息——一些方法

	- ```java
		import java.io.File;
		
		public class Test {
		    public static void main(String[] args) {
		        File file = new File("D:\\GAME\\Doki Doki Literature Club Plus");
		        File file1 = new File("D:\\GAME\\美少女万華鏡_罪と罰の少女\\Lisence.txt");
		        showInfo(file);
		        showInfo(file1);
		    }
		
		    public static void showInfo(File file) {
		        System.out.println("文件名： " + file.getName());
		        System.out.println("绝对路径： " + file.getAbsolutePath());
		        System.out.println("父目录： " + file.getParent());
		        System.out.println("文件大小(字节)： " + file.length());
		        System.out.println("是否存在： " + file.exists());
		        System.out.println("是否为文件： " + file.isFile());
		        System.out.println("是否为文件夹： " + file.isDirectory());
		        System.out.println("====================================");
		    }
		}
		```





5. 目录生成与删除文件相关方法

	- `mkdir()`：创建一级目录。如果路径上有多个目录未创建，则创建失败

	- `mkdirs()`：创建多级目录

	- `delete()`：删除空目录或文件

	- ```java
		import java.io.File;
		
		public class Test {
		    public static void main(String[] args) {
		        //本来，在D:\temp目录下只有file1文件
		        File file = new File("D:\\temp\\a\\b");
		        File file1 = new File("D:\\temp\\file1");
		        System.out.println(file.mkdir());//false
		        System.out.println(file.mkdirs());//true
		        System.out.println(file1.delete());//true
		        System.out.println(new File("D:\\temp").delete());//false
		    }}
		```
		
	- 
	
	





## IO流原理及流的分类

1. I/O流原理
	- I/O是Input/Output的缩写。该技术用于处理数据传输，如读写文件、网络通讯等
	- Java程序中，数据的输入/输出操作以流（stream）的方式进行
	- `java.io`包下提供了各种“流”类和接口，用以获取不同种类的数据，并通过方法输入或输出数据
	- 输入：读取外部数据（磁盘、光盘、网络、数据库等）到程序（内存）中
	- 输入：将程序（内存）数据输出到外部
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203160837167.png" alt="image-20220316083752917" style="zoom: 50%;" />



2. 流的分类

	1. 按操作数据单位不同分为：

		- 字节流（1 byte），适合处理二进制文件（如音视频文件）
		- 字符流（字符大小视编码而定），适合处理文本文件

	2. 按数据流流向分为：

		- 输入流
		- 输出流

	3. 按流的角色不同分为：

		- 节点流
		- 处理流（也叫包装流）

	4. | 抽象基类 | 字节流         | 字符流   |
		| -------- | -------------- | -------- |
		| 输入流   | `InputStream`  | `Reader` |
		| 输出流   | `OutputStream` | `Writer` |

		- Java的IO流涉及40多个类，都是从上述4个抽象基类派生出来的
		- 其子类名称都以父类名作为后缀

	5. I/O体系图：

		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203160844368.png" alt="image-20220316084433182" style="zoom: 70%;" />





## `FileInputStream`和`FileOutputStream`

1. `FileInputStream`继承关系
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203160904430.png" alt="image-20220316090447229" style="zoom:33%;" />



2. `FileInputStream`快速入门

	- ```java
		import java.io.File;
		import java.io.FileInputStream;
		import java.io.IOException;
		
		public class Test {
		    public static void main(String[] args) throws IOException {
		//        f1();
		        f2();
		
		    }
		
		    public static void f1() throws IOException {
		        String filePath = "C:\\Users\\Morgan\\Desktop\\temp\\text.txt";
		        FileInputStream fileInputStream = new FileInputStream(filePath);
		        int readData;
		        //read()方法读取输入流中的下一个字符，以int形式返回。
		        // 如果读到文件末尾，则返回-1
		        while ((readData = fileInputStream.read()) != -1) {
		            //需要将int 转为char
		            System.out.print((char) readData);
		        }
		
		        fileInputStream.close();//一定要关闭，以释放资源
		    }
		
		    public static void f2() {
		        File file = new File("C:\\Users\\Morgan\\Desktop\\temp\\text.txt");
		        FileInputStream fileInputStream = null;
		        try {
		            fileInputStream = new FileInputStream(file);
		            byte[] buffer = new byte[8];
		            int readLen;
		            //read(byte[] b)方法读取最多b.length个字符进入b数组
		            //返回读入的字符数，如果到达文件末尾则返回-1
		            //使用该方法能提高读取效率
		            while ((readLen = fileInputStream.read(buffer)) != -1) {
		                System.out.print(new String(buffer, 0, readLen));
		            }
		        } catch (IOException e) {
		            e.printStackTrace();
		        } finally {
		            try {
		                fileInputStream.close();
		            } catch (IOException e) {
		                e.printStackTrace();
		            }
		        }
		    }
		}
		```



3. `FileOutputStream`继承关系
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203160955990.png" alt="image-20220316095543877" style="zoom:33%;" />

4. `FileOutputStream`快速入门

	- ```java
		import java.io.FileOutputStream;
		import java.io.IOException;
		
		
		public class Test {
		    public static void main(String[] args) {
		
		        String filePath = "C:\\Users\\Morgan\\Desktop\\temp\\a.txt";
		
		        FileOutputStream fileOutputStream = null;
		
		        try {
		            //如果该文件不存在，则创建该文件
		            //第二个参数为true则采用append模式，不然覆盖原文件
		            fileOutputStream = new FileOutputStream(filePath, false);
		            fileOutputStream.write('a');//写入一个字符，char自动转为int
		            fileOutputStream.write('\n');
		            //写入byte[] 数组
		            fileOutputStream.write(new String("i like apple\n").getBytes());
		
		        } catch (IOException e) {
		            e.printStackTrace();
		        } finally {
		            try {
		                fileOutputStream.close();
		            } catch (IOException e) {
		                e.printStackTrace();
		            }
		        }
		    }
		}
		```



5. 练习：拷贝文件

	- ```java
		import java.io.FileInputStream;
		import java.io.FileOutputStream;
		import java.io.IOException;
		
		public class Test {
		    public static void main(String[] args) {
		        FileInputStream fileInputStream = null;
		        FileOutputStream fileOutputStream = null;
		
		        String srcFilePath = "C:\\Users\\Morgan\\Desktop\\temp\\屏幕截图(22).png";
		        String destFilePath = "C:\\Users\\Morgan\\Desktop\\temp\\屏幕截图(22)_copy.png";
		
		        try {
		            fileInputStream = new FileInputStream(srcFilePath);
		            fileOutputStream = new FileOutputStream(destFilePath);
		            byte[] buffer = new byte[1024];
		            int readLen;
		            while ((readLen = fileInputStream.read(buffer)) != -1) {
		                fileOutputStream.write(buffer, 0, readLen);
		            }
		            System.out.println("copy success~!");
		        } catch (IOException e) {
		            e.printStackTrace();
		        } finally {
		            try {
		                if (fileInputStream != null) {
		                    fileInputStream.close();
		                }
		                if (fileOutputStream != null) {
		                    fileOutputStream.close();
		                }
		            } catch (IOException e) {
		                e.printStackTrace();
		            }
		        }
		    }
		}
		```



## `FileReader`和`FileWriter`

1. `FileReader`介绍
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203161757520.png" alt="image-20220316175717337" style="zoom:33%;" />
	- 相关方法：
	- `FileReader(File/String)`：构造器
	- `read()`：读取返回的字符，读取到文件末尾返回-1
	- `int read(char[])`：读取多个字符到数组，返回读取到的字符数，读取到文件末尾返回-1



2. `FileWriter`
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203161805636.png" alt="image-20220316180554392" style="zoom:33%;" />
	- 常用方法：
	- `FileWriter(File/String, boolean)`：构造器，第二个参数为`true`则为append，不然为覆盖
	- `write(int)`：写入单个字符
	- `write(char[])`：写入数组
	- `write(char[], int offset, int len)`：写入数组的指定部分
	- 注意，`FileWriter`使用后**，必须使用`close()`或`flush()`，**否则无法写入——内存中的流对象在程序结束后会被销毁



3. `FileReader`快速使用

	```java
	import java.io.FileReader;
	import java.io.IOException;
	
	public class Test {
	    public static void main(String[] args) {
	        String filePath = "C:\\Users\\Morgan\\Desktop\\temp\\a.txt";
	        FileReader fileReader = null;
	        try {
	            fileReader = new FileReader(filePath);
	            char[] buffer = new char[8];
	            int readLen;
	            while ((readLen = fileReader.read(buffer)) != -1) {
	                System.out.print(new String(buffer, 0, readLen));
	            }
	        } catch (IOException e) {
	            e.printStackTrace();
	        } finally {
	            try {
	                fileReader.close();
	            } catch (IOException e) {
	                e.printStackTrace();
	            }
	        }
	    }
	}
	```



4. `FileWriter`快速使用

	- ```java
		import java.io.FileWriter;
		import java.io.IOException;
		
		public class Test {
		    public static void main(String[] args) {
		        String filePath = "C:\\Users\\Morgan\\Desktop\\temp\\a.txt";
		        FileWriter fileWriter = null;
		        try {
		            fileWriter = new FileWriter(filePath, true);
		            fileWriter.write('\n');
		            fileWriter.write("美少女が");
		            fileWriter.write("好きではないか", 0, 2);//写入从索引0开始的2个字符，即"好き"
		        } catch (IOException e) {
		            e.printStackTrace();
		        } finally {
		            try {
		                //不调用该方法，无法写入文件
		                fileWriter.close();
		            } catch (IOException e) {
		                e.printStackTrace();
		            }
		        }
		    }
		}
		```

	- 





## 节点流和处理流

1. 节点流
	- 节点流可以从一个特定的数据源读写数据，如`FileReader`
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203181708657.png" alt="image-20220318170813947" style="zoom:33%;" />
	- 该数据源可以是文件、数组



2. 处理流（包装流）

	- 处理流（也叫包装流），是连接在**已存在**的流之上，为程序提供更为强大的读写功能，也更加灵活，如`BufferedReader`

	- 以`BufferedReader`部分源码为例：

		- ```java
			public class BufferedReader extends Reader {
			    private Reader in;
			```

		- 该类拥有`Reader`属性，即封装了一个继承`Reader`抽象类的节点流/处理流对象。从而“连接在已存在的流之上”



3. 一览图
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203181711134.png" alt="image-20220318171116793" style="zoom:50%;" />



4. 节点流和处理流的区别和联系
	- 节点流是底层流，直接跟数据源相连
	- 处理流包装节点流，既可以消除不同节点流的实现差异，也可以提供更方便的方法完成输入输出
	- 处理流对节点流进行包装，使用修饰器设计模式，不会直接与数据源相连
	- 处理流的功能体现在以下两方面：
		- 性能的提高：主要以增加缓冲的方式来提供输入输出效率
		- 操作的便捷：提供方法一次输入输出大量数据等





## `BufferedInputStream`和`BufferedOutputStream`

1. 基本介绍
	- 两者都是字节处理流
	- 继承关系如下：
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203190743689.png" alt="屏幕截图(25)" style="zoom:40%;" />
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203190745999.png" alt="屏幕截图(26)" style="zoom:40%;" />
	- 如上图，这两个类本身没有包装的流对象的属性，而是在它们的父类中有该属性



2. 使用这两个类拷贝二进制文件

	- ```java
		import java.io.*;
		
		public class Test {
		    public static void main(String[] args) throws IOException {
		        String srcFilePath = "C:\\Users\\Morgan\\Desktop\\temp\\Lesson1.mp3";
		        String destFilePath = "C:\\Users\\Morgan\\Desktop\\temp\\Lesson1_copy.mp3";
		        BufferedInputStream bis = new BufferedInputStream(new FileInputStream(srcFilePath));
		        BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream(destFilePath));
		
		        byte[] buffer = new byte[1024];
		        int readLen;
		
		        while ((readLen = bis.read(buffer)) != -1) {
		            bos.write(buffer, 0, readLen);
		        }
		
		        bis.close();
		        bos.close();
		
		    }}
		```







## `BufferedReader`和`BufferedWriter`

1. `BufferedReader`快速使用

	- ```java
		import java.io.BufferedReader;
		import java.io.FileReader;
		import java.io.IOException;
		
		public class Test {
		    public static void main(String[] args) throws IOException {
		        String filePath = "C:\\Users\\Morgan\\Desktop\\temp\\a.txt";
		        BufferedReader bufferedReader = new BufferedReader(new FileReader(filePath));
		
		        String s;
		        //readLine()方法，一次读取一行文本(不包括换行符)。读到文件最后返回null
		        //该方法体现了处理流功能的拓展性
		        while ((s = bufferedReader.readLine()) != null) {
		            System.out.println(s);
		        }
		        //该方法将调用包装的节点流的close()方法
		        bufferedReader.close();
		    }
		}
		```



2. `BufferedWriter`快速使用

	- ```java
		import java.io.*;
		
		public class Test {
		    public static void main(String[] args) throws IOException {
		        String filePath = "C:\\Users\\Morgan\\Desktop\\temp\\b.txt";
		        //BufferWriter本身并不提供构造器来决定文件写入方式是append还是覆盖
		        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(filePath, false));
		        bufferedWriter.write("homestay la");
		        bufferedWriter.newLine();//插入一个和系统相关的换行符——不一定是'\n'，视操作系统而定
		        bufferedWriter.write("graceが好き");
		
		        bufferedWriter.close();
		    }
		}
		```



3. 使用这两个类完成文本文件的拷贝

	- ```java
		import java.io.*;
		
		public class Test {
		    public static void main(String[] args) throws IOException {
		        String srcFilePath = "C:\\Users\\Morgan\\Desktop\\temp\\b.txt";
		        String destFilePath = "C:\\Users\\Morgan\\Desktop\\temp\\b2.txt";
		
		        BufferedReader bufferedReader = new BufferedReader(new FileReader(srcFilePath));
		        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(destFilePath));
		        String line;
		        
		        while ((line = bufferedReader.readLine()) != null) {
		            bufferedWriter.write(line);
		            bufferedWriter.newLine();
		        }
		
		        bufferedReader.close();
		        bufferedWriter.close();
		    }
		}
		```



## 对象流：`ObjectInputStream`和`ObjectOutputStream`

1. 对象处理流引入
	- 需求：将一个自定义对象保存到文件中，且能从文件中恢复。例如`Dog dog = new Dog("大黄", 3);`
	- 实现该需求，不仅需要保存类的属性的值，还需要保存类属性的**数据类型和类信息**
	- 该需求，就是将基本数据类型或对象进行序列化和反序列化操作



2. 序列化和反序列化
	- 序列化是在保存数据时，保存数据的**值和数据类型**
	- 反序列化是在恢复数据时，恢复数据的值和数据类型
	- 若需要让某个对象支持序列化机制，则必须让其类是可序列化的。该类必须实现下面两个接口之一：
		- :one:`Serializable`：这是一个标记接口（没有方法需要实现），通常使用这个
		- :two:`Externalizable`：该接口中有方法需要实现



3. `ObjectInputStream`
	- 继承关系：
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203190841558.png" alt="image-20220319084127401" style="zoom:33%;" />
	- 该类提供反序列化功能



4. `ObjectOutputStream`
	- 继承关系：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203190842646.png" alt="image-20220319084246494" style="zoom:33%;" />
	- 该类提供序列化功能



5. 使用`ObjectOutputStream`完成序列化

	- ```java
		import java.io.*;
		
		public class Test {
		    public static void main(String[] args) throws IOException {
		        //.dat后缀也可以改为.txt。但数据是以特定方式存储的，并不是纯文本形式，所以后缀名是无所谓的
		        String filePath = "C:\\Users\\Morgan\\Desktop\\temp\\a.dat";
		        ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream(filePath));
		
		        oos.writeInt(13);
		        oos.writeBoolean(true);
		        oos.writeDouble(3.1415);//Double包装类继承Number类，后者实现Serializable
		        oos.writeUTF("rairai");//写入字符串
		
		        oos.writeObject(new Cat("李东风", 2));
		
		        oos.close();
		    }
		}
		
		class Cat implements Serializable {
		    private String name;
		    private int age;
		
		    public Cat(String name, int age) {
		        this.name = name;
		        this.age = age;
		    }
		    public String getName() {        return name;    }
		    public void setName(String name) {        this.name = name;    }
		    public int getAge() {        return age;    }
		    public void setAge(int age) {       this.age = age;    }
		}
		```



6. 使用`ObjectInputStream`完成反序列化

	- ```java
		import java.io.*;
		
		public class Test {
		    public static void main(String[] args) throws IOException, ClassNotFoundException {
		        String filePath = "C:\\Users\\Morgan\\Desktop\\temp\\a.dat";
		
		        ObjectInputStream ois = new ObjectInputStream(new FileInputStream(filePath));
		
		        //反序列化的顺序必须和序列化的顺序一致
		        //因为读写都是顺序执行的
		
		        System.out.println(ois.readInt());
		        System.out.println(ois.readBoolean());
		        System.out.println(ois.readDouble());
		        System.out.println(ois.readUTF());//读取字符串
		
		        //1.可能抛出ClassNotFoundException，因此反序列化时必须能引用到该类
		        //2.由于序列化会保存类信息，类成员只要变动(比如添加一个方法)，就需要重新序列化
		        //不然在反序列化时会报错
		        Object o = ois.readObject();
		        Cat cat = (Cat) o;
		        System.out.println("A cat named " + cat.getName() + " ages " + cat.getAge());
		
		        ois.close();
		    }
		}
		
		class Cat implements Serializable {
		    private String name;
		    private int age;
		
		    public Cat(String name, int age) {
		        this.name = name;
		        this.age = age;
		    }
		    public String getName() {        return name;    }
		    public void setName(String name) {        this.name = name;    }
		    public int getAge() {        return age;    }
		    public void setAge(int age) {        this.age = age;    }
		}
		```



7. 注意事项
	- 读写顺序要一致
	- 要求序列化的对象，需要实现`Serializable`接口
	- 序列化类中可以添加`private static final long serialVersionUID`属性，作为序列化的版本号，提高兼容性。拥有该属性的类，如果添加其他成员，序列化时系统会将修改的类作为一个新版本，而不是一个全新的类。（后者会抛出异常，无法序列化）
	- 序列化时，**默认会将所有属性序列化**，但被`static`或`transient`（该关键字专门用来修饰不想被序列化的属性）修饰的属性是例外
	- 序列化时，类的属性也必须能够序列化
	- 序列化具备继承性，例如`Integer`继承`Number`，而`Number`实现`Serializable`接口，因此`Integer`可以序列化



## 标准输入、输出流

|          |              | 编译类型      | 运行类型              | 默认设备 |
| -------- | ------------ | ------------- | --------------------- | -------- |
| 标准输入 | `System.in`  | `InputStream` | `BufferedInputStream` | 键盘     |
| 标准输出 | `System.out` | `PrintStream` | `PrintStream`         | 显示器   |



## 转换流：`InputStreamReader`和`OutputStreamReader`

1. 转换流引入

	- 使用字节输入流打印文本文件（文本中有中文字符），会输出乱码

	- 输出乱码的原因，是没有指定文件的编码

	- 用以下代码读取包含中文的文本文件，并将该文件编码从UTF-8改为ANSI（中文系统中，ANSI等于GBK），观察输出的效果：

	- ```java
		import java.io.*;
		/*
		a.txt 中不妨存入以下内容：
		I like 苹果
		我喜欢 apple
		*/
		public class Test {
		    public static void main(String[] args) throws IOException {
		        String filePath = "C:\\Users\\Morgan\\Desktop\\temp\\a.txt";
		
		        //默认情况下，按照UTF-8读取文件
		        BufferedReader br = new BufferedReader(new FileReader(filePath));
		        String line;
		
		        while ((line = br.readLine()) != null) {
		            System.out.println(line);
		        }
		        br.close();
		    }}
		```
	
	
	
	



2. 基本介绍

	- `InputStreamReader`：`Reader`的子类，可以将`InputStream`字节流包装成`Reader`字符流
	- `OutputStreamWriter`：`Writer`的子类，可以将`OutputStream`字节流包装成`Writer`字符流
		- <img src="C:\Users\Morgan\AppData\Roaming\Typora\typora-user-images\image-20220319172715983.png" alt="image-20220319172715983" style="zoom:33%;" />
		- 从类继承图可以看出，`InputStreamReader`只包装`InputStream`(字节流)对象。`OutputStreamWriter`同理
	- 处理纯文本数据时，使用字符流效率较高，并且可以解决中文编码问题，故建议将字节流转换为字符流
	- 可以在使用时指定编码格式

	

3. `InputStreamReader`使用
	

	- 还是使用上一份代码中相同的文件，代码如下：
	
	- ```java
	  import java.io.*;
	  
	  public class Test {
	      public static void main(String[] args) throws IOException {
	          String filePath = "C:\\Users\\Morgan\\Desktop\\temp\\a.txt";
	  		//BufferedReader只是起到方便打印的作用，与这里的问题无关
	          BufferedReader br = new BufferedReader(new InputStreamReader(
	                  new FileInputStream(filePath), "gbk"));
	  
	          String line;
	          while ((line = br.readLine()) != null) {
	              System.out.println(line);
	          }
	          br.close();
	      }}
	  ```



4. `OutputStreamWriter`使用

	- 可以按照指定编码写入文件

	- ```java
		import java.io.*;
		
		public class Test {
		    public static void main(String[] args) throws IOException {
		        String filePath = "C:\\Users\\Morgan\\Desktop\\temp\\a.txt";
		
		        String charSet = "utf-16";
		        //String charSet = "ascii";//用这个会有乱码
		        OutputStreamWriter osw = new OutputStreamWriter(
		                new FileOutputStream(filePath), charSet);
		
		        osw.write("ライコネン~~rairai\n");
		        osw.write("棉花糖");
		        osw.close();
		    }
		}
		```



## 打印流：`PrintStream`和`PrintWriter`

- 打印流只有输出流、没有输入流

1. 类继承关系：
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203191933975.png" alt="image-20220319193346507" style="zoom:33%;" />
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203191934533.png" alt="image-20220319193435387" style="zoom:33%;" />



2. `PrintStream`使用

	- ```java
		import java.io.*;
		
		public class Test {
		    public static void main(String[] args) throws IOException {
		        String filePath = "C:\\Users\\Morgan\\Desktop\\temp\\a.txt";
		
		        //System.out是一个标准打印流,默认输出到显示器
		        PrintStream out = System.out;
		        out.println("莲华");
		        out.write("桃乐丝".getBytes());
		        out.close();
		
		        //改变输出位置
		        System.setOut(new PrintStream(filePath));
		        out = System.out;
		        out.println("雾枝");
		        out.println("优莉");
		        out.close();
		    }
		}
		```



3. `PrintWriter`使用

	- ```java
		import java.io.*;
		
		public class Test {
		    public static void main(String[] args) throws IOException {
		        String filePath = "C:\\Users\\Morgan\\Desktop\\temp\\a.txt";
		
		        PrintWriter pw = new PrintWriter(System.out);
		        pw.write("24r");
		        pw.close();//不使用close()方法，控制台没有输出
		
		        pw = new PrintWriter(filePath);
		        pw.println(32525);
		        pw.println("lovelive");
		        pw.close();
		    }}
		```

	- 



## `Properties`类

1. 引入

	- 需求：对于以下`a.properties`文件，获取各个键对应的值（对`Properties`类的介绍，参考[`Map`接口实现类](# `Map`接口实现类)第3条）

		- ```properties
			ip=192.168.1.1
			user=root
			password=111111
			```

	- 如果使用输入流读取，则要对读入的字符串进行判断，看是否与某个键（例如`ip`）相一致



2. 基本介绍

	- 是`Hashtable`的子类

	- 专门用于读写配置文件（即`.properties`文件）的集合类

	- 配置文件的格式如下：

		- ```properties
			键=值
			键=值
			```

	- 键值对之间不需要有空格；值不需要用引号括起来；默认类型是`String`



3. 常用方法
	- `load`：加载输入流（包含配置文件的键值对信息）到`Properties`对象中
	- `list`：将数据打印到指定位置（通过打印流）
	- `getProperty`：根据键获取值
	- `setProperties`：设置键值对
	- `store`：将类中的键值对信息写入到配置文件中。



4. 案例：

	1. 从配置文件中读取信息：

		- ```java
			import java.io.*;
			import java.util.Properties;
			
			public class Test {
			    public static void main(String[] args) throws IOException {
			        String filePath = "src\\a.properties";
			
			        Properties properties = new Properties();
			        properties.load(new FileReader(filePath));
			
			        properties.list(System.out);
			        System.out.println(properties.getProperty("ip"));
			
			    }}
			```

	2. 创建配置文件

		- ```java
			import java.io.FileWriter;
			import java.io.IOException;
			import java.util.Properties;
			
			public class Test {
			    public static void main(String[] args) throws IOException {
			        String filePath = "src\\b.properties";
			
			        Properties properties = new Properties();
			        //对于没有的键，会创建新的键值对
			        //对于已有的键，其值会被替换为新的
			        properties.setProperty("name", "鈴仙");
			        properties.setProperty("age", "1000+");
			
			        //分别使用以下两句看看comment的效果
			//        properties.store(new FileWriter(filePath), null);
			        properties.store(new FileWriter(filePath),"hello");
			    }}
			```



# 第17章：坦克大战（3）

1. 设计思路：
	- 防止坦克重叠运动
		- ![屏幕截图(28)](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203201247895.png)
		- 根据当前坦克（黄色）的两个顶点（红色）是否落在其他坦克（蓝色）的区域中来判断，一共8种
	- 记录玩家总成绩——总击毁坦克数，并存入文件
	- 记录游戏退出时敌人坦克的坐标和方向（写入文件）
	- 打开程序时，选择新开游戏还是继续上局游戏







2. 编程过程
	- 防止坦克重叠运动，需要在每个敌方坦克的线程中不断循环`enemyTanks`。由于`MyPanel`的`paint`方法会删除`enemyTanks`中消亡的坦克。如果在循环时使用迭代器或增强for，会抛出`ConcurrentModificationException`异常，具体的原理看[这里](https://www.cnblogs.com/dolphin0520/p/3933551.html)。我的解决方式是，使用普通for循环
	- 设计`Recorder`类，记录玩家总成绩，同时写入文件
	- 玩家选择新开游戏，或是继续上局游戏，通过在控制台输入来决定。
	- 增加获胜提示



3. 总结
	- 这一部分继续完善坦克大战的执行逻辑，并增添了文件IO，记录游戏信息。总体来说难度不大
	- 程序本身还是有问题的：如果生成大量敌方坦克，击毁几辆后，仍然会抛出`ConcurrentModificationException`异常。这超出了我现有的关于多线程的知识。所谓解决，也只是将迭代器循环改为普通for循环（并且越改越有问题）。等日后学习了并发的知识再来解决吧。好在普通的游玩（一次生成几辆坦克）并不会触发该异常。





# 第18章：网络编程



## 网络基础

1. 网络通信
	- 概念：两台设备之间通过网络实现数据传输
	- `java.net`包下提供了一些列的类或接口，供程序员完成网络通信
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203241117812.png" alt="image-20220324111725532" style="zoom:33%;" />



2. 网络
	- 概念：多态设备通过一定物理设备连接起来，构成网络
	- 根据网络的覆盖范围不同，对网络进行分类：
		- 局域网：覆盖范围最小，最多覆盖一个公司或一个学校
		- 城域网：覆盖范围较大，可以覆盖一个城市
		- 广域网：覆盖范围最大，可以覆盖国家，甚至全球。万维网是广域网的代表。
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203241121154.png" alt="image-20220324112148932" style="zoom: 50%;" />



3. IP地址
	- 概念：用于唯一标识网络中的每台计算机的地址
	- 查看IP地址：在命令行中输入`ipconfig`
	- IP地址表示形式：点分十进制，`aa.bbb.cc.d`；每个十进制的范围为`0 - 255`，占一个字节。故共占4个字节
	- IP地址的组成：网络地址 + 主机地址
	- IPv4最大的问题在于网络地址资源有限，制约了互联网的应用和发展。IPv6的使用，不仅解决了网络地址资源数量问题，也解决了多种设备连入互联网的障碍。
	- IPv6使用128位（16个字节）表示地址，是IPv4的四倍
	- IPv4地址分类
		- <img src="C:\Users\Morgan\AppData\Roaming\Typora\typora-user-images\image-20220324190046513.png" alt="image-20220324190046513" style="zoom:33%;" />
		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203241901552.png" style="zoom:33%;" />
		- A、B、C类比较常见



4. 域名

	- 概念：域名能够被映射为IP地址（依靠HTTP协议）

	- 举例：www.baidu.com
	- 好处：相比记忆IP地址，记忆域名更容易



5. 端口
	- 概念：用于标识计算机上某个特定的网络程序（也叫服务）。单机程序不是服务
	- 表示形式：用2个字节的整数表示，端口范围`0 - 65535`
	- `0 - 1024`已经被占用，如ssh: 22、ftp : 21、http: 80。不应在编程中使用。
	- 其他常见的网络程序端口号：tomcat: 8080、MySQL: 3306
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203241938789.png" alt="image-20220324193857484" style="zoom:33%;" />
		- 如图，百度主机上运行着不同的服务，这些服务监听着不同的端口。电脑通过IP + 端口，可以访问百度主机上的不同服务。
		- 故，不同服务不能监听同一个端口。



6. 网络通信协议
	- 协议，简而言之，就是数据的组织形式。使用协议，能保证数据传输的完整性
	- TCP/IP协议
		- Transmission Control Protocol / Internet Protocol，	传输控制协议 / 因特网互联协议，又叫网络通信协议。该协议是最基本的网络协议，也是国际互联网的基础
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203242014583.png" alt="image-20220324201400400" style="zoom: 50%;" />
	- <img src="C:\Users\Morgan\AppData\Roaming\Typora\typora-user-images\image-20220324202615219.png" alt="image-20220324202615219" style="zoom:50%;" />
		- OSI模型为理论模型，现实中并不会分为7层
		- 现实中，使用TCP/IP模型，一共有4层。每层都有许多协议可供使用。



7. TCP协议：传输控制协议
	- 使用TCP协议前，必须先建立TCP连接，形成传输数据通道
	- 传输前，采用“三次握手”方式，故可靠
	- TCP协议进行通信时有两个应用进程：客户端、服务端
	- 在连接中可进行大数据量的传输
	- 传输完毕，需释放已建立的连接，故效率低



8. UDP协议：用户数据协议
	- 将数据、源、目的封装成数据包，不需要建立连接，故相对不可靠
	- 每个数据包大小限制在64KB以内，不适合传输大量数据
	- 发送数据结束时无需释放资源（因为没有连接），故速度快



## InetAddress

1. `InetAddress`类快速使用

	- ```java
		import java.net.InetAddress;
		import java.net.UnknownHostException;
		
		public class Test {
		    public static void main(String[] args) throws UnknownHostException {
		        //本机的InetAddress对象
		        InetAddress localHost = InetAddress.getLocalHost();
		        System.out.println(localHost);
		
		        //通过主机名/域名获取对象
		        InetAddress host1 = InetAddress.getByName("LAPTOP-GGH5PC7C");//我这台电脑的主机名
		        InetAddress host2 = InetAddress.getByName("www.bilibili.com");//b站的域名
		
		        System.out.println(host1);
		        System.out.println(host2);
		
		        //当前对象的IP地址
		        System.out.println(host2.getHostAddress());
		        //当前对象的主机名/域名
		        System.out.println(host2.getHostName());
		    }
		}
		```





## Socket

1. 基本介绍
	- 英语中的本意：(电源)插座
	- 套接字（Socket）开发网络应用程序被广泛采用，以至于成为事实上的标准
	- 通信的两端都有Socket，是两台及其间通信的端点
	- 网络通信其实就是Socket间的通信
	- Socket允许程序把网络连接当成一个流，数据在两个Socket间通过IO传输
	- 一般，主动发起通信的应用程序为客户端，等待通信请求的为服务端
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203251631916.png" alt="image-20220325163113898" style="zoom:33%;" />



## TCP编程

1. 基本介绍
	- 即基于客户端——服务端的网络通信
	- 底层使用TCP/IP协议
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203251643475.png" alt="image-20220325164303199" style="zoom: 50%;" />



2. 应用案例1：
	- 编写服务端和客户端
	
	- 服务端在9999端口监听
	
	- 客户端连接到服务器端，发送一条消息，然后退出
	
	- 服务器接收到客服端发送的信息，输入，并退出
	
	- ![image-20220325170759219](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203251708027.png)
	
	- ```java
		import java.io.IOException;
		import java.io.InputStream;
		import java.net.ServerSocket;
		import java.net.Socket;
		
		/**
		 * 服务端
		 */
		public class Test {
		    public static void main(String[] args) throws IOException {
		        //在本机的9999端口进行监听，等待连接
		        //要求本机的9999端口未被占用
		        ServerSocket serverSocket = new ServerSocket(9999);
		        System.out.println(System.currentTimeMillis() + " 等待客户端连接");
		
		        //当没有客户端连接9999端口时，程序会阻塞，等待连接
		        //如果有客户端连接，则返回Socket对象，程序继续
		        Socket socket = serverSocket.accept();
		        System.out.println(System.currentTimeMillis() + " 服务端与客户端连接成功");
		
		        InputStream inputStream = socket.getInputStream();
		        byte[] buffer = new byte[1024];
		        int readLen;
		        while ((readLen = inputStream.read(buffer)) != -1) {
		            System.out.println(new String(buffer, 0, readLen));
		        }
		
		        System.out.println(System.currentTimeMillis()+ "服务端打印完毕");
		
		        //释放资源
		        inputStream.close();
		        socket.close();
		        //serverSocket用以创建Socket对象，当前Socket对象关闭后,
		        // serverSocket可以继续创建其他Socket对象。故不需要创建对象时，
		        // 应主动释放资源，不再监听该端口
		        serverSocket.close();
		
		        System.out.println(System.currentTimeMillis() + "服务端关闭");
		    }}
		```
	
	- ```java
		import java.io.IOException;
		import java.io.OutputStream;
		import java.net.InetAddress;
		import java.net.Socket;
		
		/**
		 * 客户端
		 */
		public class Test2 {
		    public static void main(String[] args) throws IOException {
		        //连接服务器(IP + 端口)。只不过在这里，一台电脑同时是服务端和客户端
		        //这句话尝试连接本机的9999端口，如果连接成功，返回Socket对象
		        Socket socket = new Socket(InetAddress.getLocalHost(), 9999);
		        System.out.println(System.currentTimeMillis() + "客户端连接服务端成功 ");
		
		        //与socket相关联的输出流对象
		        OutputStream outputStream = socket.getOutputStream();
		        outputStream.write("hello, world".getBytes());
		
		        System.out.println(System.currentTimeMillis() + "客户端写入数据完毕");
		
		        //释放资源，这一步很重要
		        outputStream.close();
		        socket.close();
		
		        System.out.println(System.currentTimeMillis() + "客户端关闭");
		    }}
		```





3. 应用案例2

	- 在案例1的基础上，服务端在接收客户端发送的消息后，回发一条消息给客户端

	- ```java
		import java.io.IOException;
		import java.io.InputStream;
		import java.io.OutputStream;
		import java.net.ServerSocket;
		import java.net.Socket;
		
		/**
		 * 服务端
		 */
		public class Test {
		    public static void main(String[] args) throws IOException {
		        System.out.println("这里是服务端：");
		
		        ServerSocket serverSocket = new ServerSocket(9999);
		
		        Socket socket = serverSocket.accept();
		        System.out.println("与客户端连接成功");
		
		        InputStream inputStream = socket.getInputStream();
		        byte[] buffer = new byte[1024];
		        int readLen;
		        while ((readLen = inputStream.read(buffer)) != -1) {
		            System.out.println(new String(buffer, 0, readLen));
		        }
		
		        OutputStream outputStream = socket.getOutputStream();
		        outputStream.write("hello, client!".getBytes());
		        socket.shutdownOutput();
		
		        outputStream.close();
		        inputStream.close();
		        socket.close();
		        serverSocket.close();
		        System.out.println("服务端关闭");
		    }
		}
		```

	- ```java
		import java.io.IOException;
		import java.io.InputStream;
		import java.io.OutputStream;
		import java.net.InetAddress;
		import java.net.Socket;
		
		/**
		 * 客户端
		 */
		public class Test2 {
		    public static void main(String[] args) throws IOException {
		        System.out.println("这里是客户端：");
		
		        Socket socket = new Socket(InetAddress.getLocalHost(), 9999);
		        System.out.println("与服务端连接成功");
		
		        OutputStream outputStream = socket.getOutputStream();
		        outputStream.write("hello, server".getBytes());
		        //一个结束输出的标记
		        //如果没有该语句，服务端会一直等待接收，没法发送消息
		        socket.shutdownOutput();
		
		        InputStream inputStream = socket.getInputStream();
		        byte[] buffer = new byte[1024];
		        int readLen;
		        while ((readLen = inputStream.read(buffer)) != -1) {
		            System.out.println(new String(buffer, 0, readLen));
		        }
		
		        inputStream.close();
		        outputStream.close();
		        socket.close();
		
		        System.out.println( "客户端关闭");
		    }
		}
		```



4. 应用案例3

	- 需求与案例2一致，但使用字符流

	- ```java
		import java.io.*;
		import java.net.ServerSocket;
		import java.net.Socket;
		
		/**
		 * 服务端
		 */
		public class Test {
		    public static void main(String[] args) throws IOException {
		        System.out.println("这里是服务端：");
		
		        ServerSocket serverSocket = new ServerSocket(9999);
		
		        Socket socket = serverSocket.accept();
		        System.out.println("与客户端连接成功");
		
		        InputStream inputStream = socket.getInputStream();
		        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(inputStream));
		
		        System.out.println(bufferedReader.readLine());
		
		
		        OutputStream outputStream = socket.getOutputStream();
		        BufferedWriter bufferedWriter = new BufferedWriter(new OutputStreamWriter(outputStream));
		        bufferedWriter.write("hello, client!");
		        bufferedWriter.newLine();
		        bufferedWriter.flush();
		
		        bufferedWriter.close();
		        bufferedReader.close();
		        socket.close();
		        serverSocket.close();
		        System.out.println("服务端关闭");
		    }
		}
		```

	- ```java
		import java.io.*;
		import java.net.InetAddress;
		import java.net.Socket;
		
		/**
		 * 客户端
		 */
		public class Test2 {
		    public static void main(String[] args) throws IOException {
		        System.out.println("这里是客户端：");
		
		        Socket socket = new Socket(InetAddress.getLocalHost(), 9999);
		        System.out.println("与服务端连接成功");
		
		        OutputStream outputStream = socket.getOutputStream();
		        BufferedWriter bufferedWriter = new BufferedWriter(new OutputStreamWriter(outputStream));
		        bufferedWriter.write("hello, server!");
		        bufferedWriter.newLine();//newLine()方法也可以作为传输结束的标记，但对方需要用readLine()来接收
		        bufferedWriter.flush();//不使用flush()的话，实际上没有写入
		
		        InputStream inputStream = socket.getInputStream();
		        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(inputStream));
		
		        System.out.println(bufferedReader.readLine());
		
		        bufferedReader.close();
		        bufferedWriter.close();
		        socket.close();
		
		        System.out.println("客户端关闭");
		    }
		}
		```



5. 应用案例4

	- 客户端连接到服务端，发送一张本地图片

	- 服务端接收到客户端的图片后，保存到本地。再发送“收到图片”消息给客户端，随后退出

	- 客户端接收到服务端的消息后，退出

	- ![image-20220326103600399](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203261036962.png)

	- 传送本地文件时，客户端和服务端都需要在Socket --- 内存 ---磁盘之间建立流对象，以传输数据

	- 在这里，设计一个工具类，以简化代码：

	- ```java
		//Utils.java
		
		import java.io.*;
		
		public class Utils {
		    private Utils() {
		    }
		
		    public static byte[] inputStreamToByteArray(InputStream is) throws IOException {
		        byte[] buffer = new byte[1024];
		        int readLen;
		        ByteArrayOutputStream baos = new ByteArrayOutputStream();
		
		        while ((readLen = is.read(buffer)) != -1) {
		            baos.write(buffer, 0, readLen);
		        }
		        byte[] ans = baos.toByteArray();
		        baos.close();//不要忘了关闭流对象
		
		        return ans;
		    }
		
		    public static String inputStreamToString(InputStream is) throws IOException {
		        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(is));
		        StringBuilder sb = new StringBuilder();
		        String line;
		        while ((line = bufferedReader.readLine()) != null) {
		            sb.append(line + "\n");
		        }
		        return sb.toString();
		    }
		}
		```
		
	- ```java
		//服务端
		
		import java.io.*;
		import java.net.ServerSocket;
		import java.net.Socket;
		
		public class Test {
		    public static void main(String[] args) throws IOException {
		        System.out.println("这里是服务端：");
		
		        ServerSocket serverSocket = new ServerSocket(9999);
		
		        Socket socket = serverSocket.accept();
		
		        System.out.println("与客户端连接成功");
		
		        InputStream inputStream = socket.getInputStream();
		        byte[] bytes = Utils.inputStreamToByteArray(inputStream);
		
		        String destFilePath = "src\\cooked.jpg";
		        FileOutputStream fos = new FileOutputStream(destFilePath);
		        fos.write(bytes);
		        fos.close();
		
		        System.out.println("图片读取成功");
		
		        OutputStream outputStream = socket.getOutputStream();
		        BufferedWriter bufferedWriter = new BufferedWriter(new OutputStreamWriter(outputStream));
		        bufferedWriter.write("收到图片~~~:hot:");
		        bufferedWriter.flush();
		        socket.shutdownOutput();
		
		        inputStream.close();
		        bufferedWriter.close();
		        socket.close();
		        serverSocket.close();
		    }}
		```
	
	- ```java
		//客户端
		
		import java.io.FileInputStream;
		import java.io.IOException;
		import java.io.InputStream;
		import java.io.OutputStream;
		import java.net.InetAddress;
		import java.net.Socket;
		
		public class Test2 {
		    public static void main(String[] args) throws IOException {
		        System.out.println("这里是客户端：");
		
		        Socket socket = new Socket(
		                InetAddress.getLocalHost(), 9999);
		        System.out.println("与服务端连接成功");
		
		        String srcFilePath = "C:\\Users\\Morgan\\Desktop\\raw.jpg";
		
		        FileInputStream fis = new FileInputStream(srcFilePath);
		
		        byte[] bytes = Utils.inputStreamToByteArray(fis);
		
		        OutputStream outputStream = socket.getOutputStream();
		        outputStream.write(bytes);
		        socket.shutdownOutput();
		
		        System.out.println("图片发送成功");
		
		        InputStream inputStream = socket.getInputStream();
		        String s = Utils.inputStreamToString(inputStream);
		        System.out.println("来自服务端的消息：" + s);
		
		        inputStream.close();
		        outputStream.close();
		        fis.close();
		        socket.close();
		    }}
		
		```



6. `netstat`指令：DOS指令
	- `netstat -an`：查看当前主机网络情况，包括端口监听情况和网络连接情况
	- `netstat -anb`：在`-an`的基础上，显示监听端口的程序名
	- `netstat -an | more`：分页显示内容
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203261301569.png" alt="image-20220326130119379" style="zoom:33%;" />
	- 状态：LISTENGING表示正在监听，而ESTABLISHED表示建立了网络连接



7. 一个知识点
	- 当客户端连接到服务端后，客户端也是通过一个端口和服务端进行通讯的。这个端口由TCP/IP分配的，因此是随机的





## UDP编程

1. 基本介绍
	- `DatagramSocket`和`DatagramPacket`（数据包 / 数据报）类实现了基于UDP协议的网络程序
	- UDP数据报通过`DatagramSocket`发送和接收，系统不保证UDP数据报安全送到目的地，也不确定何时可以抵达。
	- `DatagramPacket`对象封装了UDP数据报。后者包含了发送端的IP地址和端口号，以及接收端的IP地址和端口号
	- 因为每个UDP数据报都给出了完整的地址信息，因此无需建立发送方和接收方的连接



2. 原理示意图
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203261336589.png" alt="image-20220326133610310" style="zoom:33%;" />
	- UDP中，没有明确的服务端和客户端，只有数据的发送端和接收端
	- 发送数据时，将数据封装到`DatagramPacket`对象——装包
	- 接收数据时，需要对`DatagramPacket`对象进行拆包，以取出数据
	- `DatagramSocket`可以指定在哪个端口接收数据



3. 基本流程
	- 核心的两个类：`DatagramSocket`和`DatagramPacket`
	- 建立发送端和输出端
	- 发送数据前，建立数据报（`DatagramPacket`对象）
	- 调用`DatagramSocket`的发送、接收方法
	- 关闭`DatagramSocket`



4. 应用案例

	- 有接收端A和发送端B

	- B给A发送一条消息，然后退出

	- A收到消息后退出

	- ```java
		//接收端A
		
		import java.io.IOException;
		import java.net.DatagramPacket;
		import java.net.DatagramSocket;
		
		public class Test {
		    public static void main(String[] args) throws IOException {
		        System.out.println("这里是A：");
		        //监听9999端口，等待接收数据
		        DatagramSocket socket = new DatagramSocket(9999);
		
		        DatagramPacket packet = new DatagramPacket(new byte[1024], 1024);
		
		        //将来自网络传输的DatagramSocket对象填充到packet中
		        //如果没有接收到，程序将会阻塞在此
		        socket.receive(packet);
		
		        int length = packet.getLength();
		        byte[] data = packet.getData();
		        System.out.println("收到来自B的消息：" + new String(data, 0, length));
		
		        socket.close();
		        System.out.println("A退出");
		    }}
		```

	- ```java
		//发送端B
		
		import java.io.IOException;
		import java.net.*;
		
		public class Test2 {
		    public static void main(String[] args) throws IOException {
		        System.out.println("这里是B：");
		        //监听9998端口
		        DatagramSocket socket = new DatagramSocket(9998);
		
		        byte[] bytes = "你好，这里是B。".getBytes();
		
		        DatagramPacket packet = new DatagramPacket(bytes,
		                bytes.length, InetAddress.getLocalHost(), 9999);
		
		        socket.send(packet);
		
		        socket.close();
		        System.out.println("B退出");
		    }}
		```



## 课后作业

1. 需求：TCP/IP下载文件
	- 编写客户端和服务端程序
	- 客户端输入文件名，服务端收到文件名后，给客户端返回这个文件。如果没有该文件，返回一个默认文件即可
	- 客户端收到文件后，保存到本地
	
2. 代码：
	- ```java
		//Utils.java
		
		import java.io.*;
		
		public class Utils {
		    private Utils() {
		    }
		
		    public static byte[] inputStreamToByteArray(InputStream is) throws IOException {
		        byte[] buffer = new byte[1024];
		        int readLen;
		        ByteArrayOutputStream baos = new ByteArrayOutputStream();
		
		        while ((readLen = is.read(buffer)) != -1) {
		            baos.write(buffer, 0, readLen);
		        }
		        byte[] ans = baos.toByteArray();
		        baos.close();//不要忘了关闭流对象
		
		        return ans;
		    }
		}
		```
	
	- ```java
		//服务端
		
		import java.io.*;
		import java.net.ServerSocket;
		import java.net.Socket;
		
		public class Test {
		    public static void main(String[] args) throws IOException {
		        System.out.println("这里是服务端：");
		
		        ServerSocket serverSocket = new ServerSocket(9999);
		        Socket socket = serverSocket.accept();
		
		        InputStream inputStream = socket.getInputStream();
		        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(inputStream));
		        //客户端请求下载的文件名
		        String fileName = bufferedReader.readLine();
		
		        String filePath = "C:\\Users\\Morgan\\Desktop\\data\\";
		        File file = new File(filePath + fileName);
		        FileInputStream fis = null;
		        String reply = null;
		
		        if (file.exists()) {
		            System.out.println(reply = ("检索成功：客户端请求的" + fileName + "存在"));
		            fis = new FileInputStream(file);
		        } else {//该文件不存在时，返回默认文件
		            System.out.println(reply = ("检索失败：客户端请求的" + fileName + "不存在，返回default.png"));
		            fis = new FileInputStream(filePath + "default.png");
		        }
		
		        byte[] bytes = Utils.inputStreamToByteArray(fis);
		
		        OutputStream outputStream = socket.getOutputStream();
		        outputStream.write(bytes);
		        outputStream.flush();//一定要flush，不然文件传输会有损失
		        socket.shutdownOutput();
		
		        System.out.println("传输成功");
		
		        fis.close();
		        outputStream.close();
		        bufferedReader.close();
		        socket.close();
		        serverSocket.close();
		
		        System.out.println("服务端退出");
		    }
		}
		```
	
	- ```java
		// 客户端
		
		import java.io.*;
		import java.net.InetAddress;
		import java.net.Socket;
		import java.util.Scanner;
		
		public class Test2 {
		    public static void main(String[] args) throws IOException {
		        System.out.println("这里是客户端：");
		
		        Socket socket = new Socket(InetAddress.getLocalHost(), 9999);
		
		        Scanner scanner = new Scanner(System.in);
		        System.out.println("输入你要下载的图片名称：");
		        String request = scanner.next();
		
		
		        //请求下载一张图片
		        OutputStream outputStream = socket.getOutputStream();
		        BufferedWriter bufferedWriter = new BufferedWriter(new OutputStreamWriter(outputStream));
		        bufferedWriter.write(request);
		        bufferedWriter.flush();
		        socket.shutdownOutput();
		
		        InputStream inputStream = socket.getInputStream();
		
		        byte[] bytes = Utils.inputStreamToByteArray(inputStream);
		
		        String destFilePath = "C:\\Users\\Morgan\\Desktop\\temp\\";
		        FileOutputStream fos = new FileOutputStream(destFilePath + request);
		        fos.write(bytes);
		        System.out.println("下载成功");
		
		        fos.close();
		        inputStream.close();
		        bufferedWriter.close();
		        socket.close();
		        System.out.println("客户端退出");
		    }
		}
		```
	
	- 客户端确实接收了数据，但是没有接收图片名称。这是这段代码的缺点



# 第19章：多用户即时通讯系统



## 设计相关

1. 项目开发流程
	- ![image-20220327145849314](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203271458905.png)



2. 需求分析
	- 用户登录
	- 拉取在线用户列表
	- 无异常退出（客户端、服务端）
	- 私聊
	- 群聊
	- 发文件
	- 服务器推送新闻



3. 界面设计
	- 用户登录
		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203271511635.png" alt="image-20220327151103520" style="zoom: 50%;" />
	- 拉取在线用户列表
		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203271512034.png" alt="image-20220327151201907" style="zoom: 50%;" />
	- 私聊
		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203271512415.png" alt="image-20220327151246103" style="zoom:33%;" />
	- 群聊
		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203271513827.png" alt="image-20220327151314373" style="zoom:33%;" />
	- 发文件
		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203271514154.png" alt="image-20220327151414687" style="zoom:33%;" />
	- 文件服务器推送新闻
		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203271515557.png" alt="image-20220327151501079" style="zoom:33%;" />



4. 项目思路分析
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203271531422.png" alt="image-20220327153132740" style="zoom: 50%;" />
	- 客户端与服务端间使用对象流进行数据传输 
	- 由于网络通信可以说是Socket间的IO，对于服务端，每当有一个客户端与它连接，都需要创建一个`Socket`对象。
	- 又因为多台客户端对服务端的通信是同时进行的，需要使用线程。在这里，我们让线程持有`Socket`对象
	- 为了更好地管理线程，我们把线程放到集合中
	- 一个客户端可能同时有多个`Socket`对象（即创建多个线程）与服务端连接，故也需要集合来管理线程



## 功能实现

1. 用户登录（同时搭建程序主架构）
	- 设计`User`和`Message`类，这两个类被客户端和服务端共享
	- 设计`TELEView`类，显示菜单（主菜单和二级菜单）。这里使用到了房屋出租系统项目中的`Utility`工具类
	- 判断用户是否登录成功：设计`UserClientService`类，其中一个方法用于返回登录是否成功。方法的实现为：向服务端发送`User`对象，服务端验证后，回发`Message`对象。客户端根据`MessageType`来判断。
	- 如果登录成功，需要启动线程，该线程持有`Socket`对象，用于接收来自服务端的消息。故设计`ClientConnectServerThread`类
	- 为了管理客户端的多个线程，设计`ManageCCST`类，其中有`HashMap`对象，用于存放线程。
	- 设计`TELEServer`类，不断监听端口，接收客户端发来的`User`对象。如果登录成功，创建相应线程，并使用`HashMap`存储线程
	- 在`TELEServer`类中使用`HashMap`模拟数据库



2. 显示在线用户列表
	- 客户端向服务端发送请求，服务端直接返回即可



3. 无异常退出
	- 客户端要退出时，给服务端发送消息，然后使用`System.exit(0)`，以关闭进程（这样做，就关闭了两个线程）
	- 服务端收到消息后，释放线程的`Socket`对象，并退出线程



4. 私聊功能
	- 假设客户端A给客户端B发送私聊消息
	- A把消息发给服务端，服务端找到对应的与B通行的`Socket`对象，并转发消息
	- 在这里，设计`MessageClientService`类，处理客户端发送消息的功能



5. 群发功能
	- 思路基本和私聊一致 



6. 发文件
	- 思路基本和私聊一致，但要拓展`Message`类的属性
	- 设计`FileClientService`类，用来实现发文件的功能



7. 服务器推送新闻
	- 本质还是群发
	- 需要在服务端另外启动一条线程，接收控制台的输入。



## 总结

1. 程序架构

	- 网络通讯分为服务端和客户端。客户端的行为都需要服务端处理。如，客户端要发送私聊消息，该消息得由服务端中转

	- 每有一个客户端与服务端连接，就需要创建一对`Socket`对象。为了多个客户端的同步运行，需要把`Socket`对象放入线程

2. 多线程

	- 这个项目能够加深对于多线程和面向对象的理解
	- 客户端发送请求，由对应的`XxxxClientService`类完成，随后`ServerConnectClientThread`线程对象接收请求，并把消息回发给`ClientConnectServerThread`线程对象，由该对象输出信息。尤其是私聊消息时，`ServerConnectClientThread`要区分消息发送者和接受者对应的`Socket`对象。
	- 故每增加一个新功能，增添代码的顺序往往是`TeleView` $\rightarrow$ `XxxClientService` $\rightarrow$  `ServerConnectClientThread` $\rightarrow$ `ClientConnectServerThread`
	- 对于客户端，主线程和`ClientConnectServerThread`线程共享控制台，分别打印菜单和消息
	- 而对于服务端，主线程和所有`ServerConnectClientThread`线程共享控制台，分别打印用户登录情况和用户发送消息。之后实现的服务器群发新闻，又新建了一个线程，接收来自控制台输入的内容。

3. IO知识

	- 传输中使用对象流能提高大大效率
	- 使用对象，传输的内容的拓展性也大大加强——当然，这属于面向对象的知识





# 第20章：反射（reflection）

## 反射入门

1. 需求

	- 根据配置文件`re.properties`信息，创建对象并调用方法

	- ```properties
		#re.properties
		classFullPath=com.Cat
		method=hi
		```



2. 代码：

	- ```java
		package com;
		
		public class Cat {
		    private String name = "李东风";
		
		    public void hi() {
		        System.out.println(name + "打招呼");
		    }
		
		    public void eat() {
		        System.out.println(name + "吃冻干");
		    }
		}
		```

	- ```java
		import java.io.FileInputStream;
		import java.lang.reflect.Method;
		import java.util.Properties;
		
		public class Test {
		    public static void main(String[] args) throws Exception {
		        FileInputStream fis = new FileInputStream("src\\re.properties");
		        Properties properties = new Properties();
		        properties.load(fis);
		        String className = properties.getProperty("classFullPath");
		        String methodName = properties.getProperty("method");
		
		        fis.close();
		
		        //使用反射机制
		        //得到Class类型的对象
		        Class<?> cls = Class.forName(className);
		
		        //获得className对应的类的对象
		        Object o = cls.newInstance();
		        System.out.println(o.getClass());
		
		        //Method对象
		        Method method = cls.getMethod(methodName);
		        //调用该方法
		        method.invoke(o);
		    }
		}
		```

	- 如果需要调用`Cat`的`eat()`方法，只需要修改`re.properties`配置文件，而不是修改`Test`的代码



3. 这样的需求在学习框架时特别多，即通过外部文件配置，在不修改源码的情况下，控制程序。这也符合设计模式的OCP原则（开闭原则：扩容功能但不修改源码）



## 反射机制

1. 基本介绍
	- 反射机制允许程序在执行期间借助于reflection API取得任何类的内部信息（成员、构造器等），并能操作对象的属性及方法。反射机制在设计模式和框架底层都会用到
	- 加载完类后，堆中就产生一个`Class`对象，该对象包含了类的完整结构信息。通过这个对象，能够得到类的结构。该对象就像一面镜子，能够透过该镜子看到类的结构，故称之为反射



2. 反射原理图
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203300715107.png" alt="image-20220330071518844" style="zoom:50%;" />
	- 在编译阶段，`.java`源码文件被编译成`.class`字节码文件，后者包含全部类信息
	- 在类加载阶段（运行阶段第一次创建`Cat`对象之前），类加载器`ClassLoader`将`.class`文件的信息加载到堆中，形成`Cat`类对应的`Class`对象。`Cat`的成员信息也被创建为对象，存放在该`Class`对象中。如`Cat`的属性成为`Field`对象，保存在`Field[]`中。换言之，将成员信息本身也抽象为对象，以进行管理
	- 运行阶段，根据堆中的`Class`对象创建`Cat`对象。该`Cat`对象知道其属于哪个`Class`对象，即可以根据`Cat`获取`Class`对象。得到`Class`对象后，可以创建相应对象，调用方法，并操作属性。（类加载阶段不受程序员控制，而运行阶段可以控制）



3. 反射机制可以：
	- 在运行阶段：
		- 判断任意对象所属的类
		- 构造任意类的对象
		- 得到任意类所具有的成员
		- 调用任意对象的成员
	- 生成动态代理



## 反射相关类

1. 相关类介绍
	- `java.lang.Class`：代表一个类，其对象是类加载后生成在堆中的
	- `java.lang.reflect.Method`：代表类的方法，其对象表示某个类的某方法
	- `java.lang.reflect.Field`：代表类的属性，其对象表示某个类的某属性
	- `java.lang.reflect.Constructor`：代表类的构造器，其对象表示某个类的某构造器



2. 快速使用

	- ```java
		package com;
		
		public class Cat {
		    private String name = "李东风";
		    public int age = 2;
		
		    public Cat() {
		    }
		
		    public Cat(String name) {
		        this.name = name;
		    }
		
		    public void hi() {
		        System.out.println(name + "打招呼");
		    }
		
		    public void eat() {
		        System.out.println(name + "吃冻干");
		    }
		}
		```

	- ```java
		import java.io.FileInputStream;
		import java.lang.reflect.Constructor;
		import java.lang.reflect.Field;
		import java.lang.reflect.Method;
		import java.util.Properties;
		
		public class Test {
		    public static void main(String[] args) throws Exception {
		        FileInputStream fis = new FileInputStream("src\\re.properties");
		        Properties properties = new Properties();
		        properties.load(fis);
		        String className = properties.getProperty("classFullPath");
		        String methodName = properties.getProperty("method");
		
		        fis.close();
		
		        Class<?> cls = Class.forName(className);
		        Object o = cls.newInstance();
		        System.out.println(o.getClass());
		
		        //Method对象
		        Method method = cls.getMethod(methodName);
		        method.invoke(o);//调用该方法
		
		        Field field = cls.getField("age");//不能获取私有属性
		        System.out.println(field.get(o));//获取该字段的值
		
		        Constructor<?> constructor = cls.getConstructor(String.class);//有参构造器对象
		        System.out.println(constructor);
		        constructor = cls.getConstructor();//无参构造器对象
		        System.out.println(constructor);
		    }
		}
		```

	- 



## 反射调用性能优化

1. 反射的优缺点：
	- 优点：可以动态创建和使用对象，使用灵活。没有反射机制，框架技术就失去底层支撑
	- 缺点：使用发射基本是解释执行，对执行速度有影响



2. 反射调用优化
	- `Method`、`Field`和`Constructor`类都继承了`AccessibleObject`对象。后者有`setAccessible(boolean)`方法
	- 该方法的作用是启动或禁用访问安全检查
	- 参数设置为`true`，则反射对象在使用时取消访问检查，可以部分提高反射效率（提高后效率还是远不如直接使用对象调用方法）



## `Class`类



1. 基本介绍：
	- `Class`类继承图
		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203300918514.png" alt="image-20220330091813361" style="zoom:33%;" />
	- `Class`对象不是`new`出来的，而是在类加载阶段由`ClassLoader`类的`loadClass`方法创建的
	- 一个类的`Class`对象，在内存中只有一份，因为类只加载一次
	- 每个类对象都知道自己是由哪个`Class`对象生成的
	- 通过`Class`对象可以完整地得到一个类的完整结构
	- 在类加载时，不仅在堆中创建相应`Class`对象，还在方法区保存该类的字节码二进制数据（也叫类的元数据），两者有一定联系



2. 常用方法

	- ```java
		package com;
		
		public class Cat {
		    private String name = "李东风";
		    public int age = 2;
		    public String type = "美短";
		
		    public Cat() {
		    }
		
		    public Cat(String name) {
		        this.name = name;
		    }
		
		    public void hi() {
		        System.out.println(name + "打招呼");
		    }
		
		    public void eat() {
		        System.out.println(name + "吃冻干");
		    }
		
		    @Override
		    public String toString() {
		        return "Cat{" +
		                "name='" + name + '\'' +
		                ", age=" + age +
		                ", type='" + type + '\'' +
		                '}';
		    }
		}
		```

	- ```java
		import java.lang.reflect.Field;
		
		public class Test {
		    public static void main(String[] args) throws Exception {
		        String classFullPath = "com.Cat";
		
		        Class<?> cls = Class.forName(classFullPath);
		
		        System.out.println(cls);//Class对象所指向的类，即Cat
		        System.out.println(cls.getClass());//运行类型
		        System.out.println(cls.getPackage().getName());//包名
		        System.out.println(cls.getName());//类的全路径
		        System.out.println("=============================================");
		
		        Object o = cls.newInstance();//创建Cat对象
		        Field age = cls.getField("age");
		        System.out.println(age.get(o));//哪个对象的age属性的值
		        age.set(o, 1);
		        System.out.println(o);//修改该对象属性的值
		        System.out.println("=============================================");
		
		        Field[] fields = cls.getFields();
		        for (Field f : fields) {
		            System.out.println(f.getName());
		        }
		    }}
		```



3. 获取`Class`类对象的6种方式
	1. 已知一个类的全类名，可通过`Class`的静态方法`forName`获取
	
		- 例如：`Class cls = Class.forName("com.cat");`
		- 应用场景：多用于从配置文件读取类全路径
	
	2. 已知具体的类，通过`类名.class`获取。该方式最为安全可靠，程序性能最高
	
		- 例如`Class cls = String.class;`
		- 多用于参数传递，例如通过反射得到对应构造器对象
	
	3. 已知某个类的实例，调用该实例的`getClass()`方法获取`Class`对象
	
		- 例如`Class cls = cat.getClass();`
	
	4. 通过类加载器
	
		- ```java
			ClassLoader cl = cat.getClass().getClassLoader();
			Class cls = cl.loadClass("com.Ct");
			```
	
	5. 基本数据类型通过`.class`得到`Class`类对象
	
		- 例如：`Class cls = int.class`
	
	6. 包装类通过`.TYPE`得到`Class`类对象
	
		- 例如：`Class cls = Integer.TYPE;`



4. 以下类型有`Class`对象
	- 外部类和4种内部类
	- 接口
	- 数组：`float[][].class`
	- 枚举类
	- 注解：`Deprecated.class`
	- 基本数据类型
	- `void`：`void.class`


​		

## 类加载

1. 两种类加载方式

	- 静态加载：编译时加载相关的类，如果没有该类则报错。依赖性强

	- 动态加载：运行时加载需要的类，如果该语句没有被执行，即使类不存在，也不报错。依赖性低

	- 反射机制是Java实现动态语言的关键，即通过反射实现类动态加载

	- 举例：

		- ```java
			import java.lang.reflect.Method;
			import java.util.Scanner;
			
			public class Test {
			
			    public static void main(String[] args) throws Exception {
			        Scanner scanner = new Scanner(System.in);
			        System.out.print("What's your choice? ");
			        String s = scanner.next();
			        switch (s) {
			            case "1":
			                Dog dog = new Dog();
			                dog.bark();
			                break;
			            case "2":
			                Class<?> cls = Class.forName("Person");
			                Method method = cls.getMethod("eat");
			                method.invoke(cls);
			                break;
			        }
			    }
			}
			
			class Dog {
			    public void bark() {
			        System.out.println("woooooooooooooo");
			    }
			}
			```

		- 如果不定义`Dog`类，则编译时就会出错

		- 如果不定义`Person`类，控制台输入`1`不会报错，只有输入`2`才会抛出`ClassNotFoundException`



2. 类加载时机
	- 使用`new`创建对象时
	- 子类被加载时，父类也加载
	- 调用类的静态成员时
	- 通过反射
	- :pencil2:前3种为静态加载，后一种为动态加载



3. 类加载过程图

	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203310725842.png" alt="image-20220331072523227" style="zoom: 33%;" />
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203310727857.png" alt="image-20220331072729967" style="zoom: 33%;" />

	

	

4. 类加载五阶段

	1. 加载阶段

		- JVM在该阶段的主要目的是：将字节码从不同的数据源（`.class`文件、`jar`包甚至网络）转化为二进制字节流加载到内存中（即方法区的元数据），并生成代表该类的`java.lang.Class`

	2. 连接阶段——验证

		- 目的：确保`.class`文件的字节流包含的信息符合当前JVM的要求，并且不会危害JVM自身的安全。
		- 这些信息包括：文件格式验证（`.class`文件是否以魔数`0xcafebabe`开头）、元数据验证、字节码验证和符号应用验证
		- 可以使用`-Xverify:none`参数来关闭大部分的类验证措施，缩短JVM加载时间

	3. 连接阶段——准备

		- JVM会在该阶段对静态变量分配内存并默认初始化（用广义0赋值）。这些变量使用的内存将在方法区中进行分配

		- ```java
			public int n1 = 10;
			public static int n2 = 20;
			public static final int n3 = 30;
			```

		- `n1`是普通属性，准备阶段不分配内存

		- `n2`是静态变量，准备阶段分配内存，并赋值为`0`

		- `n3`是常量，在准备阶段直接赋值为`30`

	4. 连接阶段——解析

		- JVM将常量池内的符号引用替换为直接引用
		- 举例：在源码中，A类中有指向B类的引用。在解析阶段，由于B类对应的`Class`对象已经生成，该引用就指向`Class`对象的内存地址

	5. 初始化阶段

		- 该阶段才开始执行类中定义的Java代码，此阶段是执行`<clinit>`方法（class initialization）的过程
		- `<clinit>`方法是由编译器按语句在源文件中出现的顺序，依次自动收集类中所有静态变量的赋值动作和静态代码块中的语句，并进行合并
		- JVM会保证一个类的`<clinit>`方法在多线程环境中被正确地加锁、同步。如果多个线程同时去初始化一个类，则只有一个线程执行`<clinit>`方法，其他线程都需要等待，直到活动线程执行完该方法





## 反射获取类的结构信息

1. `Class`类常用方法
	- `getName()`：获取全类名
	- `getSimpleName()`：获取简单类名
	- `getFields()`：获取所有`public`修饰的属性对象，包括本类和父类的
	- `getDeclaredFields`：获取本类所有属性
	- `getMethods()`、`getDeclaredMethods`、`getConstructors()`、`getDeclaredConstructors()`：用法类似，但`getConstructors`只返回本类的`public`构造器
	- `getPackage()`：返回包信息
	- `getSuperClass()`：返回父类`Class`对象
	- `getInterfaces`：返回本类所有接口
	- `getAnnotations`：返回注解信息



2. `Field`类常用方法
	- `getModifiers()`：以`int`形式返回修饰符：默认为`0`，`public`为`1`，`private`为`2`，`protected`为`4`，`static`为`8`，`final`为`16`。`public static`即为`1 + 8 = 9`
	- `getType()`：以`Class`对象返回类型
	- `getName()`：返回属性名



3. `Method`类常用方法：
	- `getModifiers()`：以`int`形式返回修饰符
	- `getReturnType`：以`Class`对象获取方法的返回类型
	- `getName()`：返回方法名
	- `getParameterTypes()`：以`Class[]`返回参数类型



4. `Constructor`类常用方法：
	- `getModifiers()`：以`int`形式返回修饰符
	- `getName()`：返回构造器名（全类名）
	- `getParameterTypes()`：以`Class[]`返回参数类型



5. 通过反射创建对象

	- ```java
		import java.lang.reflect.Constructor;
		
		public class Test {
		    public static void main(String[] args) throws Exception {
		        Class<?> cls = Class.forName("Cat");
		        //1.调用无参构造器
		        Object o1 = cls.newInstance();
		        System.out.println(o1);
		
		        //2.调用public有参构造器
		        Constructor<?> constructor = cls.getConstructor(String.class);//获取对应的Constructor对象
		        Object o2 = constructor.newInstance("臭卷宝");//传入实参
		        System.out.println(o2);
		
		        //3.调用private有参构造器
		        //该方法可以获取private的构造器对象
		        Constructor<?> constructor1 = cls.getDeclaredConstructor(String.class, int.class);
		        constructor1.setAccessible(true);//暴破(暴力破解)，已调用私有构造器
		        Object o3 = constructor1.newInstance("李小p", 2);
		        System.out.println(o3);
		    }
		}
		
		
		class Cat {
		    private String name = "李东风";
		    private int age = 1;
		
		    public Cat() {
		    }
		
		    public Cat(String name) {
		        this.name = name;
		    }
		
		
		    private Cat(String name, int age) {
		        this.name = name;
		        this.age = age;
		    }
		
		    @Override
		    public String toString() {
		        return "Cat{" +
		                "name='" + name + '\'' +
		                ", age=" + age +
		                '}';
		    }
		}
		```



6. 使用反射操作属性

	- ```java
		import java.lang.reflect.Field;
		
		public class Test {
		    public static void main(String[] args) throws Exception {
		        Class<?> cls = Class.forName("Cat");
		        Object o = cls.newInstance();
		        //1.操作私有属性
		        Field field1 = cls.getDeclaredField("age");
		        field1.setAccessible(true);//暴破
		        System.out.println(field1.get(o));
		        field1.set(o, 2);
		        System.out.println(field1.get(o));
		
		        //2. 操作静态属性
		        Field field2 = cls.getField("type");
		        field2.set(null, "美短");//只有静态属性可以填入null
		//        field2.set(o,"美短");//这两句话是等效的，因为对象也能访问静态属性
		
		        System.out.println(field2.get(null));
		        System.out.println(field2.get(o));//同理，这两句话也是等效的
		    }
		}
		
		class Cat {
		    private String name = "李东风";
		    private int age = 1;
		    public static String type;
		}
		```



7. 反射访问方法

	- ```java
		import java.lang.reflect.Method;
		
		public class Test {
		    public static void main(String[] args) throws Exception {
		        Class<?> cls = Class.forName("Cat");
		        Object o = cls.newInstance();
		        //1. 访问私有方法
		        Method method1 = cls.getDeclaredMethod("think", String.class);//方法名 + 形参列表
		        method1.setAccessible(true);//暴破
		        //传入对象 + 实参，返回Object对象
		        Object returnVal = method1.invoke(o, "你太狗了");
		        System.out.println(returnVal);
		
		        //2. 访问静态方法
		        Method method2 = cls.getMethod("eat", String.class);
		        method2.invoke(null, "冻干");//静态方法可以不使用对象
		    }
		}
		
		class Cat {
		    private static String name = "李东风";
		
		    private String think(String content) {
		        return name + "在想： " + content;
		    }
		
		    public static void eat(String food) {
		        System.out.println(name + "在吃" + food);
		    }
		}
		```







# 第21章：MySQL基础



## 基本配置

- MySQL安装和配置

1. 软件下载：

	https://dev.mysql.com/get/Downloads/MySQL-5.7/mysql-5.7.19-winx64.zip

2. 解压文件，路径不含中文和空格

3. 给`\bin`目录添加环境变量

4. 在目录下创建`my.ini`文件，内容如下：

	- ```ini
		[client]
		port=3306
		default-character-set=utf8
		[mysqld]
		#自己的sql安装目录
		basedir=D:\mysql5.7.19\
		#设置数据目录
		datadir=D:\mysql5.7.19\data\
		port=3306
		character_set_server=utf8
		#第一次进入要跳过安全检查
		skip-grant-tables
		```

5. 使用管理员打开cmd，切换到`\bin`目录下，执行`mysqld- install`命令。如果没问题，会显示`Service successfully installed.`

6. 输入命令：`mysqld --initialize-insecure --user=mysql`，以初始化数据库

7. 启动`mysql`服务：`net start mysql`

8. 进入MySQL管理终端：`mysql -u root -p`（用户名为`root`，密码为空）。在填密码时直接回车

9. 输入`use mysql;`（有分号）

10. 修改`root`用户密码：`update user set authentication_string=password('你的密码') where user='root' and Host='localhost';`

11. 刷新权限：`flush previleges;`

12. 退出：输入`quit`

13. 修改`my.ini`，将`skip-grant-tables`删除

14. 重启MySQL，先`net stop mysql`，再`net start mysql`

15. 再次登录，这次登录要输入密码：`mysql -u root -p`



- 使用命令行窗口连接MySQL数据库
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203311450307.png" alt="image-20220331145005671" style="zoom:50%;" />



- 安装Navicat for MySQL
	- 下载：我的百度网盘里
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203311607464.png" alt="image-20220331160700044" style="zoom:33%;" />
	- 这个连接的界面和命令行的无异




安装SQLyog

- 网址：https://www.filehorse.com/download-sqlyog-community-edition/50527/
- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203311651831.png" alt="image-20220331165145568" style="zoom:33%;" />
- 









## 基本知识

1. 基本介绍
	1. 数据库三层结构
		- 所谓安装MySQL数据库，就是在主机安装一个数据库管理系统（DBMS，即database manage system），该系统可以管理多个数据库
		- 一个数据库可以创建多个表，以保存数据
		- 三者关系如图：
		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203311710122.png" alt="image-20220331171027816" style="zoom:33%;" />
		- MySQL数据库中，普通表的本质仍然是文件。客户端通过3306端口与MySQL进行交互：客户端发送命令，MySQL查询本地数据，并返回信息
	2. 数据在数据库中的存储方式
		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203311714864.png" alt="image-20220331171458522" style="zoom:33%;" />
		- 表的一行称为一条记录。在java中，一条记录往往用对象表示



2. SQL语句分类
	- DDL：数据定义语句，如`create`
	- DML：数据操作语句，如`insert`（增加）、`update`（修改）、`delete`（删除）
	- DQL：数据查询语句，如`select`
	- DCL：数据控制语句，用于管理数据库，比如操作用户权限：`grant`和`revoke`



## 数据库

1. 创建数据库

	- 格式：

	- ```sql
		CREATE DATABASE [IF NOT EXISTS] db_name [create_specification...]
		
		create_specification:
		CHARACTER SET charset_name
		COLLATE collation_name
		```

	- `CHARACTER SET`：指定数据库采用的字符集，默认为utf8

	- `COLLATE`：指定数据库字符集的校对规则，常用的有：`utf8_bin`（区分大小写）、`utf8_general_ci`（不区分大小写；默认值）

	- 代码：

	- ```sql
		#IF NOT EXISTS参数的使用；分号可加可不加
		CREATE DATABASE IF NOT EXISTS db01;
		#删除数据库
		DROP DATABASE db01;
		#创建一个名称为db01的数据库
		CREATE DATABASE db01;
		#创建一个使用utf8字符集的db02数据库
		CREATE DATABASE db02 CHARACTER SET utf8;
		#创建一个使用utf8字符集，并带有校对规则的db03数据库
		CREATE DATABASE db03 CHARACTER SET utf8 COLLATE utf8_bin;
		###########################################################
		#可以使用反引号``包上数据库的名字，以防止关键字冲突。为了安全起见，理论上每个名字都应该有反引号
		#创建一个名为CREATE的数据库
		CREATE DATABASE `CREATE`
		```



2. 查看、删除数据库
	- 显示数据库：`SHOW DATABASES`
	- 显示数据库创建语句：`SHOW CREATE DATABASE db_name`
	- 删除数据库（慎用）：`DROP DATABASE [IF EXISTS] db_name`



3. 备份、恢复数据库
	- 备份：导出，恢复：导入
	- 备份（在DOS执行）：`mysqldump -u 用户名 -p[密码] -B 数据库1 [数据库2] [数据库n...] > 文件路径`
	- 恢复数据库（进入MySQL后执行）：`source 文件路径`
	- 备份数据库中的表：`mysqldump -u 用户名 -p[密码] 数据库 表1 [表n...] > 文件路径`
	- 恢复表：与恢复数据库相同。注意，这是恢复某个数据库中的某一张表。如果该数据库不存在，则恢复不成功





## 表

1. 创建表

	- ```sql
		CREATE TABLE table_name_(
			field1 datatype,
		    field2 datatype
		)character set 字符集 collate 校对规则 engine 引擎
		```

	- `field`：指定列名

	- `datatype`：指定列类型（字段类型）

	- `character set`：默认为数据库字符集

	- `collate`：默认为数据库校对规则

	- `engine`：引擎（这里先略过）

	- 举例：在`db01`数据库创建一张`user`表

	- ```sql
		CREATE TABLE `user`(
			id INT,
			`name` VARCHAR(255),
			`password` VARCHAR(255),
			birthday DATE
		) CHARACTER SET utf8 COLLATE utf8_bin
		```



2. 修改表

	- 添加列：`alter table 表名 add 列名 datatype [参数] `

	- 修改列：`alter table 表名 modify 列名 datatype [参数]`

	- 删除列：`alter table 表名 drop 列名`

	- 修改表名：`rename table 表名 to 新表名`

	- 修改字符集`alter table 表名 character set 字符集`

	- 例子：

	- ```mysql
		DROP TABLE IF EXISTS `user`
		DROP TABLE IF EXISTS `person`
		
		CREATE TABLE `user`(
			id INT,
			`name` VARCHAR(255),
			`password` VARCHAR(255),
			birthday DATE
		) CHARACTER SET utf8 COLLATE utf8_bin
		#增加字段
		ALTER TABLE `user` ADD `sex` CHAR(1) NOT NULL DEFAULT ' ' AFTER `name`;
		#修改字段
		ALTER TABLE `user` MODIFY `name` VARCHAR(60) NOT NULL DEFAULT ' ';
		#删除字段
		ALTER TABLE `user` DROP `sex`
		
		DESC `user`;
		SELECT * FROM `user`;
		#表改名
		RENAME TABLE `user` TO `person`
		ALTER TABLE `person` CHARACTER SET utf8 
		#改变列名称
		ALTER TABLE person CHANGE `password` `pwd` VARCHAR(100) NOT NULL DEFAULT ' ';
		
		DESC `person`;
		SELECT * FROM `person`;
		```







## MySQL数据类型

1. 基本介绍
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204010851904.png" alt="image-20220401085101427" style="zoom: 50%;" />
	- 常用的一些数据类型：`int`、`double`、`decimal`、`char`、`varchar`、`text`、`datetime`、`timestamp`
	- `BLOB`存储二进制数据，但文件一般存储在磁盘上，不需要存放在数据库里



2. 数值型（整型）

	- <img src="C:\Users\Morgan\AppData\Roaming\Typora\typora-user-images\image-20220401091602163.png" alt="image-20220401091602163" style="zoom: 50%;" />

	- 在满足需求的情况下，尽量选择占用空间小的类型

	- 举例：

	- ```mysql
		CREATE TABLE t1(id TINYINT);
		CREATE TABLE t2(score INT UNSIGNED);
		```



3. 数值型(`bit`)
	- 定义：`BIT(M)`：`M`指定位数，大小为`1 - 64`
	- 举例：`CREATE TABLE t1(num bit(8))`
	- `bit`字段显示时，按照二进制方式显示。但在查询时，仍可以用添加时的数值。
	- 实际使用的不多



4. 数值型（小数）
	- `FLOAT`、`DOUBLE`表示单精度和双精度小数 。也可以使用`UNSIGNED`
	- `DECIMAL[M, D] [UNSIGNED]`：表示精度更高的小数。
		- 假设往表中插入`xxx.yyyyy`，则M是`xxx.yyyyy`的总最大长度，D是`.yyyy`的最大长度
		- 如果D为0，则没有小数部分。M最大为65，D最大为30
		- 如果不写明`(M, D)`，则默认为`(10, 0)`



5. 字符串

	1. `CHAR(size)`

		- 固定长度字符串，`size`最大为255，表示能容纳255个**字符**

	2. `VARCHAR(size)`

		- 最大占用65535个**字节**，但其中有1到3**字节**用于记录字符串大小，故实际可以使用65532**字节**

		- 不同编码方式中，一个**字符**的大小不定。故使用`utf8`字符集，`size`的最大值为`65532 / 3 = 21844`**字符**；而使用`gbk`字符集，`size`的最大值为`65532 / 2 = 32766`**字符**

		- ```mysql
			CREATE TABLE t1(info VARCHAR(32766))CHARACTER SET gbk
			CREATE TABLE t2(info VARCHAR(21844))CHARACTER SET utf8
			```

	3. 使用细节

		- 对于`char(4)`和`varchar(4)`，无论是中文还是英文字母，都最多存放4个
		- `char(4)`是定长，即使只插入`'aa'`，也依旧分配4个字符的空间
		- `varchar(4)`是变长，如果插入`'aa'`，会按照实际占用空间来分配（按照编码的算出的字节数，加上1至3个字节存放字符串长度）
		- 何时使用`char`？数据是定长时，如MD5密码、邮编等；何时使用`varchar`？数据长度不定，如留言、文章等。但在查询速度方面，`char` > `varchar`
		- 存放文本时，也可以使用`TEXT`数据类型。该类型类似于`VARCHAR`，但没有默认值。存放更大的文本时，可以使用`MEDIUMTEXT`或`LONGTEXT`



5. 日期类型

	- 举例：

	- ```mysql
		CREATE TABLE `user`(
			t1 DATE,
			t2 DATETIME,
			t3 TIMESTAMP NOT NULL -- 非空
			DEFAULT CURRENT_TIMESTAMP -- 默认为当前时间戳
			ON UPDATE CURRENT_TIMESTAMP -- 更新时使用当前时间戳
		)
		INSERT INTO `user`(t1,t2) VALUES('2018-1-1','2017-2-3 23:10:9')
		```





## CRUD

1. `insert`语法

	- 格式：`insert into table_name [(列名...)] values (value...)`

	- 举例：

	- ```mysql
		INSERT INTO person (id,`name`,sex,pwd, birthday)
		VALUES (100,'jack','M', '123456','1991-12-25');
		```



2. `insert`细节
	- 插入的数据应与字段类型相同
	- 数据的长度应在列的规定范围内
	- 在`(value...)`中的数据顺序应与字段的顺序（即`(列名...)`）一致。即实参顺序应与形参顺序一致
	- 字符和日期型数据应包含在单引号中
	- 如果某字段允许为空，则该列可以插入空值，即`insert into table_name values(null)`
	- 可以同时添加多条记录：`insert into table_name (列...) values (value1...),(value2...),(valuen...)`
	- 如果是给表中所有字段添加数据，可以省略`(列名...)`
	- 关于默认值：如果不给某个字段值时，
		- 没有默认值则会填入`null`（前提是允许为空）
		- 有默认值则会填入默认值。定义方式为：`field datatype default 默认值`
		- 否则会报错



3. `update`语法

	- 格式：

	- ```mysql
		update 表名
			set field1=expr1 [, field2=expr2...]
			[where 条件语句]
		```

	- 举例：

	- ```mysql
		DROP TABLE IF EXISTS `user`;
		CREATE TABLE `user`(
			id INT,
			`name` VARCHAR(255),
			salary DOUBLE
		) ;
		INSERT INTO `user`
		VALUES (100, 'jack', 3000),(200,'mary',5000),(300,'lilith', 2600);
		UPDATE `user` SET salary=3050 WHERE `name`='jack'
		UPDATE `user` SET salary = salary + 400 ,`name` = 'marie' WHERE `id` = 200
		SELECT * FROM `user`;
		```



4. `update`使用细节：
	- 该指令可以用新值替换原有表行中的各列
	- `where`指定应更新哪些行。如果没有该指令，则更新所有行。因此要慎重





5. `delete`语句：
	- 格式：`delete from table_name [where 条件]`



6. `delete`细节
	- 如果不使用`where`，则删除表中所有记录
	- 该语句仅删除记录，不删除表本身



### `select`单表查询

7. `select`基本语法

	- ```mysql
		select [distinct] * | (列名...) from tablename
		```

	- `*`代表查询所有列

	- `from`指定查询哪张表

	- `distinct`：显示结果时，如果**所有**字段相同，则对记录去重

	- 例子：

	- ```mysql
		DROP TABLE IF EXISTS `user`;
		CREATE TABLE `user`(
			id INT,
			`name` VARCHAR(255),
			salary DOUBLE,
			kpi INT
		) ;
		INSERT INTO `user`
		VALUES (100, 'jack', 3000,54),
				(200,'mary',5000,67),
				(300,'lilith', 2600,68),
				(400,'eve',5000,67),
				(500,'adam',4000,98);
		SELECT * FROM `user`; #所有字段
		SELECT `name`, kpi FROM `user` ;#特定字段
		SELECT * FROM `user`;#记录去重
		SELECT DISTINCT salary, kpi FROM `user`;#一条记录的这些字段完全相同才去重
		```



8. `select`语法2

	- 使用表达式对查询的列进行运算：

	- ```mysql
		select * | (列名 | expr ...) from tableName
		```

	- 使用`as`创建别名

	- ```mysql
		select 列名 as 别名 from tableName
		```

	- 例子：

	- ```mysql
		DROP TABLE IF EXISTS `user`;
		CREATE TABLE `user`(
			id INT,
			`name` VARCHAR(255),
			salary DOUBLE,
			kpi INT
		) ;
		INSERT INTO `user`
		VALUES (100, 'jack', 3000,54),
				(200,'mary',5000,67),
				(300,'lilith', 2600,68),
				(400,'eve',5000,67),
				(500,'adam',4000,98);
		SELECT `name`, (salary * kpi /100) FROM `user`;#使用表达式
		SELECT `name`,(salary * kpi /100) AS '实际工资' FROM `user`;#取别名
		SELECT `name` AS '姓名',(salary * kpi /100) AS '实际工资' FROM `user`;#取别名
		
		```



9. `select`语法3：条件

	- 以下是`where`语句中常用的运算符

	- | 运算符                          | 意义                                                |
		| ------------------------------- | --------------------------------------------------- |
		| `>`、`<`、`>=`、`=`、`<>`或`!=` | 比较运算符（不等号有两种表示）                      |
		| `between A and B`               | 是否在区间`[A, B]`中                                |
		| `in(set)`                       | 是否在集合中                                        |
		| `like ''`、`not like ''`        | 模糊查询。规则为`%`表示0到多个字符，`_`表示单个字符 |
		| `is null`、`is not null`        | 是否为空。判断是否为空不能用`=`或`!=`               |
		| `and`、`or`、`not`              | 逻辑运算符                                          |

	- 例子：

	- ```mysql
		DROP TABLE IF EXISTS `user`;
		CREATE TABLE `user`(id INT,`name` VARCHAR(255),salary DOUBLE,kpi INT) ;
		INSERT INTO `user`
		VALUES (100, 'jack', 3000,54),(200,'mary',5000,67),(300,'lilith', 2600,68),
				(400,'eve',5000,67),(500,'adam',4000,98);
		SELECT * FROM `user` WHERE (kpi * salary/100) >3000;
		SELECT * FROM `user` WHERE kpi BETWEEN 67 AND 68;
		SELECT * FROM `user` WHERE id IN (200,400);
		#%表示通配符，可以匹配0到多个字符
		SELECT * FROM `user` WHERE `name` LIKE 'e%' AND kpi >60; #名字以e开头
		SELECT * FROM `user` WHERE `name` LIKE '_a%'; #名字的第二个字母为a
		```





10. `select`语法4：排序

	- 对查询结果进行排序

	- ```mysql
		select 列名 | expr ... from tableName order by 列名 | expr (asc|desc) ...
		```

	- 排序的列既可以是表中的列名，也可以是`as`指定的别名

	- `asc`表示升序（默认值），`desc`表示降序

	- `order by`应位于`select`语句结尾

	- 例子：

	- ```mysql
		DROP TABLE IF EXISTS `user`;
		CREATE TABLE `user`(id INT,`name` VARCHAR(255),salary DOUBLE,kpi INT) ;
		INSERT INTO `user`
		VALUES (100, 'jack', 3000,54),(200,'mary',5000,67),(300,'lilith', 2600,68),
				(400,'eve',5000,67),(500,'adam',4000,98),(600,'Messiah', 5000, 78);
		SELECT `name`, (salary * kpi /100) AS real_salary FROM `user` 
				ORDER BY real_salary DESC;#order by后面使用中文别名会有问题
		#多个排序规则，仅当前一个字段相等才比较下一个
		SELECT * FROM `user` ORDER BY salary DESC, kpi DESC;
		#when 和 order by 的组合使用
		SELECT * FROM `user` WHERE salary >= 4000 ORDER BY kpi DESC, id DESC;
		```



11. `select`语法5：分组

	- ```mysql
		select 列名... from 表名 group by 列名...
		```

	- `group by`用于对查询的结果进行分组统计。分组的意思是：将某字段相同的记录分为一组，进行操作

	- ```mysql
		select 列名... from 表名 group by 列名... having ...
		```

	- `having`用于对分组结果进行过滤

	- ```mysql
		DROP TABLE IF EXISTS person;
		CREATE TABLE person(id INT,`name` VARCHAR(255),salary DOUBLE,kpi INT, 
		jobID INT , departID INT);
		INSERT INTO person
		VALUES (100, 'jack', 3000,54,1,1),(200,'mary',5000,67,1,2),
				(300,'lilith', 2600,68,2,3),(400,'eve',5000,67,2,4),
				(500,'adam',4000,98,2,3),(600,'Messiah', 5000, 78,3,2),
				(700,'Solomon',4000,99,1,1),(800,'eve', 4500,80,2,3);
		SELECT * FROM person;
		#每个部分的平均工资和最高工资
		SELECT AVG(salary) ,MAX(salary),departID FROM person GROUP BY departID;
		#每个部门的每种岗位的平均工资和最低工资：要对两个字段进行分组
		SELECT AVG(salary) AS avg_sal, MIN(salary), departID, jobID 
			FROM person GROUP BY departID, jobID;
		#平均工资低于4000的部门号：使用having
		SELECT AVG(salary) AS avg_sal, departID FROM person 
			GROUP BY departID HAVING avg_sal < 4000;
		
		```



12. `select`语法6：分页查询

	- ```mysql
		select ... limit start_, rows
		```

	- 从查询到的第`start_ + 1`条记录开始，取出`rows`行。该子句应放在`select`语句的最后

	- 故，为了分页查询，可以使用以下公式：

	- ```mysql
		select * from 表名 limit rows * (第几页 - 1),rows
		```

	- `limit`子句不允许表达式，故应该在程序中算出`start_`的具体值，再使用MySQL语句

	- ```mysql
		DROP TABLE IF EXISTS `user`;
		CREATE TABLE `user`(id INT,`name` VARCHAR(255),salary DOUBLE,kpi INT) ;
		INSERT INTO `user`
		VALUES (100, 'jack', 3000,54),(200,'mary',5000,67),(300,'lilith', 2600,68),
				(400,'eve',5000,67),(500,'adam',4000,98);
		SELECT * FROM `user` ORDER BY id DESC LIMIT 0, 2;
		SELECT * FROM `user` ORDER BY id DESC LIMIT 2, 2;
		SELECT * FROM `user` ORDER BY id DESC LIMIT 4, 2;
		```





13. `select`单表总结

	- ```mysql
		select 列名 from 表名
				group by 列名
				having 条件
				order by 列名
				limit start_, rows
		```

	- 子句的顺序不能颠倒
	
	- 这种语法的查询也叫内连接，与[外连接](#外连接)相对





### `select`多表查询

14. MySQL多表查询

	- 多表查询是基于两个及以上的表查询。在实际应用中，查询单个表可能不满足需求，故需要使用多表

	- 多表查询学习中，使用的表如下：

	- ```mysql
		DROP TABLE IF EXISTS person;
		#mgr为这个人上级的id
		CREATE TABLE person(id INT,`name` VARCHAR(255),	salary DOUBLE,
				kpi INT, 	jobID INT , departID INT, mgr INT) ;
		INSERT INTO person
		VALUES (100, 'jack', 3000,54,1,1,800),(200,'mary',5000,67,1,2,NULL),
				(300,'lilith', 2600,68,2,3,100),(400,'eve',5000,67,2,4,NULL),
				(500,'adam',4000,98,2,3,200),(600,'Messiah', 5300, 78,3,2,NULL),
				(700,'Solomon',4000,99,1,1,600),(800,'Issac', 4500,80,2,3,600);
		
		DROP TABLE IF EXISTS depart;
		CREATE TABLE depart(departID INT, depart_name VARCHAR(255), 
				loc VARCHAR(255));
		INSERT INTO depart VALUES
				(1,'sales','London'),(3, 'HR', 'Osaka'),
				(2,'design','Hong Kong'),(4, 'engineering','Tokyo');
				
		DROP TABLE IF EXISTS sal_grade;
		CREATE TABLE sal_grade(#工资级别
				grade INT, low DOUBLE, high DOUBLE #[low, high]规定工资级别
		);
		INSERT INTO sal_grade VALUES(1, 2000,3000),(2,3001,4000),(3,4001,5000),(4,5001,9999);
				
		SELECT * FROM depart;
		SELECT * FROM person;
		SELECT * FROM sal_grade;
		```



15. 笛卡尔集

	- 对于两个表查询时，如果不加条件，即`selext * from person, depart;`，则会：

		- 从第一张表中取出每一行与第二章表的每一行进行组合，返回的记录包含两张表的所有列
		- 总记录数为两张表行数的乘积

	- 这种多表查询默认处理的结果，称为笛卡尔集。（对该概念的理解参考笛卡尔坐标系，以及 $ {[0, 1]}^3$和$[2, 3] \times [0,1]$这两个记号——数学分析课的知识）

	- 因此解决多表的关键是要写出正确的过滤条件

	- 多表查询的条件不能少于`表的个数 - 1`，否则会出现笛卡尔集

	- ```mysql
		#默认查询会返回笛卡尔集
		SELECT * FROM person,depart;
		
		#查询 人名，工资和部门的名字
		#使用 表.字段 是为了解决两张表字段重名的问题，不然可以直接使用字段名
		SELECT `name`, salary, depart_name FROM person, depart
				WHERE person.departID = depart.departID AND person.departID = 1;
				
		#显示员工的姓名，工资和工资级别，并按工资降序排列
		SELECT `name`, salary, grade FROM person, sal_grade 
					WHERE salary BETWEEN low AND high 
					ORDER BY salary DESC;
		```

	- 对于笛卡尔集产生与过滤可以这样理解：

		- ```c++
			vector<Record> ans;
			for(Record r1: table1){
			    for (Record r2 : table2){
			        if( 有where条件 ? true : where条件的结果 ){
			            ans.push_back(r1 + r2);
					}
			    }
			}
			```

		- 如果没有`where`条件，则为`if(true)`；有`where`条件，则使用该条件来判断





16. 自连接

	- 同一张表的连接查询——一张表当作两张表来用

	- 由于`select`语句中，表名需要唯一，因此给表名取别名以使用自连接：`表名 表别名`

	- ```mysql
		# 输出员工和他的上级的名字
		SELECT person.`name` AS '员工名', senior.`name` AS '上级名'
				FROM person, person senior#取别名为senior
				WHERE person.mgr = senior.id; #没有上级的人不算在内
		```



17. 子查询

	- 子查询是指嵌入在其他MySQL语句中的`select`语句，也叫嵌套查询

	- :one:单行子查询：只返回一行数据/记录的子查询语句

	- ```mysql
		#显示与Issac同一部门的员工：
		#思路分析：先查询到Issac的部门，结果为一条记录
		SELECT departID FROM person WHERE `name` = 'Issac';
		
		#再以该结果作为查询依据
		SELECT `name`, departID FROM person 
						WHERE departID = (
							SELECT departID FROM person WHERE `name` = 'Issac' );
		```

	- :two:多行子查询：返回多行数据数据的子查询，使用关键字`in`

	- ```mysql
		#查询和部门2员工工作相同的员工的名字、岗位、部门号，
		#但查询的结果不包括部门2的员工
		#返回多条记录，注意去重
		SELECT DISTINCT jobID FROM person WHERE departID = 2;
		
		SELECT `name`, jobID, departID FROM person WHERE jobID IN (
			SELECT DISTINCT jobID FROM person WHERE departID = 2);
		```

	- :eight_pointed_black_star:子查询当作临时表使用

	- ```mysql
		#需求：返回各个工作种类中工资最高的员工
		
		#先求得各个工作种类最高的工资
		SELECT jobID, MAX(salary) FROM person GROUP BY jobID;
		
		#将查询的结果作为一张表来使用，命名为temp
		SELECT *
				FROM person, 
					(SELECT jobID, MAX(salary) AS max_salary #这里需要给字段取别名
							FROM person GROUP BY jobID) temp
				WHERE temp.jobID = person.jobID AND max_salary = person.salary;
		```

	- :eight_pointed_black_star:关键字`all`和`any`，类似于任意$\forall  $和存在$\exists$ 

	- ```mysql
		#输出工资比3号部门所有员工高的人的信息
		SELECT * FROM person 
				WHERE salary > 
					ALL(SELECT salary FROM person WHERE departID = 3);
		#也可以用select max(salary)实现需求
		
		#输出工资比3号部门某员工高的人的信息
		SELECT * FROM person 
				WHERE salary > 
					ANY(SELECT salary FROM person WHERE departID = 3);
		#也可以用select min(salary)实现需求
		```

	- :three:多列子查询：返回多个列数据的子查询语句。（:one:和:two:都是单列子查询）
	
	- 语法：`where (字段...) = (select 字段... from 表名)`
	
	- ```mysql
		#需求:返回与adam同部门同工作的员工(不包括adam)
		#adam 的部门号和工作号
		SELECT jobID, departID FROM person WHERE `name` = 'adam';
		
		SELECT * FROM person 
			WHERE (jobID, departID) = 
			(SELECT jobID, departID FROM person WHERE `NAME` = 'adam')
			AND `name` != 'adam';
		```



18. 表复制

	1. 自我复制数据——蠕虫复制

		- 为了测试MySQL语句的效率，我们需要海量数据，可以用这种方法为表创建海量数据

		- ```mysql
			SELECT * FROM person;
			#1. 如何进行表复制?
			DROP TABLE IF EXISTS temp;
			CREATE TABLE temp(tId INT , salary INT);
			#使用插入语句
			INSERT INTO temp (tId, salary) 
				SELECT id, salary FROM person;
			SELECT * FROM temp;
			
			#2. 自我复制；每次使用，表中的记录会以指数级增长
			INSERT INTO temp SELECT * FROM temp;
			SELECT * FROM temp;
			```

	2. 一道题：如何删除一张表的重复记录

		- ```mysql
			DROP TABLE IF EXISTS temp2;
			CREATE TABLE temp2 LIKE person;#创建的表和person结构完全相同
			INSERT INTO temp2 SELECT * FROM person;#这句话多执行几遍以生成重复记录
			SELECT * FROM temp2;
			
			#开始去重
			/* 思路：
			   生成一张临时表，用distinct将temp2中的数据复制进去
			   然后(1)清空temp2，再将临时表的数据插入进去，并删除临时表
			 或者：(2)把temp2删除，将临时表改名为temp2
				这里使用第二种方法，因为效率更高
			*/
			DROP TABLE IF EXISTS tt2;
			CREATE TABLE tt2 LIKE temp2;
			
			INSERT INTO tt2 SELECT DISTINCT * FROM temp2;
			SELECT * FROM tt2;
			
			DROP TABLE temp2;
			RENAME TABLE tt2 TO temp2;
			SELECT * FROM temp2;
			```



19. 合并查询

	- 为了合并多个`select`语句的结果，可以使用集合操作符`union`和`union all`。前者合并时去重，后者则不会去重

	- ```mysql
		SELECT * FROM person WHERE salary >=4000;
		SELECT * FROM person WHERE kpi >=70;
		
		#1. union 去重,即数学中的并集符号
		SELECT * FROM person WHERE salary >=4000
		UNION 
		SELECT * FROM person WHERE kpi >=70;
		
		#1. union all不去重,只是把结果拼凑在一起
		SELECT * FROM person WHERE salary >=4000
		UNION ALL
		SELECT * FROM person WHERE kpi >=70;
		```





## 函数

1. 合计/统计函数：`count`

	- `select count(* | 列名) from 表名 [where 条件]`

	- 返回行的总数。如果参数中填入列名，则该字段为空的行不算入总数

	- ```mysql
		DROP TABLE IF EXISTS person;
		CREATE TABLE person(id INT,`name` VARCHAR(255),salary DOUBLE,kpi INT) ;
		INSERT INTO person
		VALUES (100, 'jack', 3000,54),(200,'mary',5000,67),(300,'lilith', 2600,68),
				(400,'eve',5000,67),(500,'adam',4000,98),(600,'Messiah', 5000, 78),
				(NULL,'Solomon',4000,99);
		SELECT COUNT(*) FROM person;
		SELECT COUNT(id) FROM person WHERE kpi >90; #不统计id字段为空的记录
		```



2. 合计函数：`sum`

	- 返回满足条件的行的某些字段的和，一般**使用在数值列**

	- ```mysql
		select sum(列名) {,sum(列名)...} from 表名 [where 条件]
		```

	- ```mysql
		DROP TABLE IF EXISTS person;
		CREATE TABLE person(id INT,`name` VARCHAR(255),salary DOUBLE,kpi INT) ;
		INSERT INTO person
		VALUES (100, 'jack', 3000,54),(200,'mary',5000,67),(300,'lilith', 2600,68),
				(400,'eve',5000,67),(500,'adam',4000,98),(600,'Messiah', 5000, 78),
				(700,'Solomon',4000,99);
		SELECT * FROM person;
		SELECT SUM(salary) FROM person;
		#一个比较笨的求平均值的方法；函数的值也可以命名
		SELECT SUM(salary) / COUNT(*) AS '平均工资' FROM person;
		#统计多个值
		SELECT SUM(salary) , SUM(kpi) FROM person;
		```



3. 合计函数：`avg`

	- 返回满足条件的一列的平均值

	- ```mysql
		select avg(列名|表达式) {,avg(列名)...} from 表名 [where 条件]
		```

	- ```mysql
		DROP TABLE IF EXISTS person;
		CREATE TABLE person(id INT,`name` VARCHAR(255),salary DOUBLE,kpi INT) ;
		INSERT INTO person
		VALUES (100, 'jack', 3000,54),(200,'mary',5000,67),(300,'lilith', 2600,68),
				(400,'eve',5000,67),(500,'adam',4000,98),(600,'Messiah', 5000, 78),
				(700,'Solomon',4000,99);
		SELECT * FROM person;
		SELECT AVG(salary) FROM person;
		SELECT AVG(salary) , AVG(kpi) FROM person;
		SELECT AVG(salary * kpi /100) AS '实际平均工资' FROM person;
		```





4. 合计函数：`max/min`

	- 返回满足条件的某列的最大值/最小值

	- ```mysql
		select min(列名) from 表名 [where 条件]
		```

	- ```mysql
		DROP TABLE IF EXISTS person;
		CREATE TABLE person(id INT,`name` VARCHAR(255),salary DOUBLE,kpi INT) ;
		INSERT INTO person
		VALUES (100, 'jack', 3000,54),(200,'mary',5000,67),(300,'lilith', 2600,68),
				(400,'eve',5000,67),(500,'adam',4000,98),(600,'Messiah', 5000, 78),
				(700,'Solomon',4000,99);
		SELECT * FROM person;
		SELECT MAX(salary) FROM person;
		SELECT MIN(salary * kpi /100) FROM person;
		```



5. 字符串函数

	- ```mysql
		DROP TABLE IF EXISTS person;
		CREATE TABLE person(id INT,`name` VARCHAR(255),salary DOUBLE,kpi INT, 
		jobID INT , departID INT) ;
		INSERT INTO person
		VALUES (100, 'jack', 3000,54,1,1),(200,'mary',5000,67,1,2),
				(300,'lilith', 2600,68,2,3),(400,'eve',5000,67,2,4),
				(500,'adam',4000,98,2,3),(600,'Messiah', 5000, 78,3,2),
				(700,'Solomon',4000,99,1,1),(800,'Issac', 4500,80,2,3);
		SELECT * FROM person;
		#1. charset(str)，返回字符串字符集
		SELECT CHARSET(`name`) FROM person;
		#2. concat(str1 [, str2 ...]) 拼接字符串，str可以是字符串常量
		SELECT CONCAT(`name`,'的工资是',salary) AS basic_info FROM person;
		#dual 亚元表 系统表，可以在测试时使用
		#3. instr(str, substr) 返回substr在str第一次出现的位置，没有则返回0，
		#类似于str.indexOf(substr) + 1
		SELECT INSTR('abcbbcsa', 'bcb') FROM DUAL;
		SELECT UCASE('AbcDE') FROM DUAL;#全部变成大写
		SELECT LCASE('AbcDE') FROM DUAL;#全部变成小写
		#4. left(str, len) 返回str前len个字符
		SELECT LEFT('AbcDE', 2) FROM DUAL;
		#5. right(str, len) 返回str后len个字符
		SELECT RIGHT('AbcDE', 2) FROM DUAL;
		#6. 返回字符串长度，单位是字节Byte
		SELECT LENGTH('ass你好') FROM DUAL;
		#7. replace(str, search_str, replace_str)：将str中的所有search_str替换为replace_str
		SELECT `name`, REPLACE(jobID, 1, '灵活就业') AS '就业情况' FROM person;
		#8. 字典序比较两个字符串
		SELECT STRCMP('abc', 'abb') FROM DUAL;
		#9. substring(str, pos [,len])返回pos开始长度为len的字符串，len不填则为pos开始直至末尾
		#pos从1开始
		SELECT SUBSTRING('let\'s go, 自由へ', 1,2) FROM DUAL;
		#10. 去除左/右/左右空格
		SELECT LTRIM('   abc    ') AS ans, LENGTH(LTRIM('   abc    ') ) AS len  FROM DUAL;
		SELECT RTRIM('   abc    ') AS ans, LENGTH(RTRIM('   abc    ') ) AS len FROM DUAL;
		SELECT TRIM('   abc    ') AS ans, LENGTH(TRIM('   abc    ') ) AS len FROM DUAL;
		
		#练习：以首字母大写的形式显示所有员工姓名
		SELECT CONCAT(UCASE(LEFT(`name`,1)),SUBSTRING(`name`,2)) 
			AS '姓名' FROM person; 
		```



6. 数学函数

	- ```mysql
		#绝对值
		SELECT ABS(10), ABS(-10) FROM DUAL;
		#向上/下取整
		SELECT CEILING(1.1), FLOOR(1.1) FROM DUAL;
		#十进制转为二进制/十六进制
		SELECT BIN(22), HEX(22) FROM DUAL;
		#conv(num, base1, base2) 将base1下的num转为base2进制
		SELECT CONV(10, 10 ,3) FROM DUAL;
		#保留小数位数，四舍五入
		SELECT FORMAT(10.3453434,2) FROM DUAL;
		#least(set) 即min{set}
		SELECT LEAST(-1,3,5,-9) FROM DUAL;
		#mod(a,b) 返回a%b
		SELECT MOD(7,3) FROM DUAL;
		#rand([seed]) 返回[0,1]的随机数；如果没有参数，则每次的随机数不同
		#如果有参数，则生成的随机数是固定的
		SELECT RAND(), RAND(1) FROM DUAL;
		```



7. 日期函数

	- ```mysql
		DROP TABLE IF EXISTS mes;
		CREATE TABLE mes(id INT, content VARCHAR(255), get_time DATETIME);
		#1. 当前日期：年月日
		SELECT CURRENT_DATE();
		
		#2. 当前时间：时分秒；括号可写可不写
		SELECT CURRENT_TIME;
		
		#3. 当前时间戳：日期 + 时间；两种写法
		SELECT CURRENT_TIMESTAMP();
		SELECT NOW();
		#可以这么使用：
		INSERT INTO mes VALUES(1,'文文新闻',CURRENT_TIMESTAMP);
		SELECT * FROM mes;
		
		#4.  YEAR| MONTH | DAY | DATE | HOUR | MINUTE | SECOND |TIME (datetime | time |date)
		#返回想要的一个特定信息
		SELECT DAY(CURRENT_TIMESTAMP());
		
		#5. DATE_ADD (date1, INTERVAL val d_type)：在date1基础上加上val ，单位是MINUTE等
		SELECT DATE_ADD(NOW(), INTERVAL 2 MINUTE);
		#查询一小时内发送的消息
		SELECT * FROM mes WHERE  DATE_SUB(NOW(),INTERVAL 1 HOUR) < get_time;
		
		#6. DATE_SUB()同理
		
		#7. 两个日期差，单位是天
		SELECT DATEDIFF(NOW(),'1991-12-25')/365 AS '距离解体过去了多少年？';
		
		#8. 时间差，单位是秒
		SELECT TIMEDIFF(TIME(NOW()),'12:00:00') AS 'p.m.';
		
		#9. 返回1970-1-1到现在的秒数
		SELECT UNIX_TIMESTAMP() /(365* 24 * 3600);
		
		#10.把一个unix_timestamp数转成指定格式的日期
		#因此，在开发中可以使用int来保存unix时间戳，然后使用该函数转换
		SELECT FROM_UNIXTIME(UNIX_TIMESTAMP(),'%y年%m月%d日%h时%i分%s秒');
		
		#11.日期类型可以直接比较大小
		SELECT NOW() > '1991-12-25';
		```



8. 加密和系统函数

	- ```mysql
		# 1. 返回登录到MySQL的用户 + 用户的地址
		SELECT USER();
		
		#2. 返回当前数据库名称
		SELECT DATABASE();
		
		# 3. 返回一个长度为32的MD5加密字符串
		#无论输入的字符串有多长，输出都是32位
		SELECT MD5('jack'), LENGTH(MD5('jack'));
		#加密算法满足单射关系，而从输出反推输入几乎不可能
		#故存放用户密码应该使用加密方式，而不是使用明文存储
		DROP TABLE IF EXISTS user_;
		CREATE TABLE user_( id INT, pwd CHAR(32));
		INSERT INTO user_ VALUES(1,MD5('MAGA'));
		INSERT INTO user_ VALUES(2,MD5('mina'));
		SELECT * FROM user_;
		#登录查询
		SELECT * FROM user_ WHERE id = 1 AND pwd = MD5('MAGA');
		
		#4. password(str)：另一种加密方式
		SELECT PASSWORD('jack');
		#该加密方式用在mysql数据库密码加密
		SELECT * FROM mysql.user;#数据库.表：可以在不切换数据库情况下，访问其它数据库
		```



9. 流程控制函数

	- ```mysql
		DROP TABLE IF EXISTS person;
		CREATE TABLE person(id INT,`name` VARCHAR(255),salary DOUBLE,kpi INT, 
		jobID INT , departID INT) ;
		INSERT INTO person
		VALUES (100, 'jack', 3000,54,1,1),(200,'mary',5000,67,1,2),
				(300,'lilith', 2600,68,2,3),(400,'eve',5000,67,2,4),
				(500,'adam',4000,98,2,3),(600,'Messiah', 5000, 78,3,2),
				(700,'Solomon',4000,99,1,1),(800,'eve', 4500,80,2,3);
		SELECT * FROM person;
		###############################################################################
		###############################################################################
		
		#1. if(expr1, expr2, expr3) : return expr1 == true ? expr2 :expr3
		SELECT IF(FALSE, 'yes', 0-1),IF(TRUE, 'yes', 0-1);
		
		#2. ifnull(expr1, expr2) : return expr1 IS NOT NULL ? expr1 :expr2 
		SELECT IFNULL(NULL, 'a'), IFNULL('b',1+3);
		
		#3. select case when expr1 then expr2 [when expr1 then expr2...] else expr3 end
		#如果expr1为真，返回expr2，依次查询，直至返回expr3
		SELECT `name`,CASE WHEN jobID=1 THEN '工程师'
					   WHEN jobID =2 THEN '运维'
					   ELSE jobID END AS '工作', jobID FROM person;
		```





## 外连接

1. 引入
	- 尝试用以上所学解决[这一道题](https://leetcode-cn.com/problems/combine-two-tables/)
	- 问题的**难点**在于将**没有匹配**上的人的地址显示成`null`。
	- 根据以上所学，利用`where`子句对多表形成的笛卡尔集进行筛选时，根据条件，匹配成功，该记录才显示。而**匹配失败的，则不显示**
	- 故这道题暂时解不出来，即使只是一道简单题:angry:



2. 外连接

	- :one:左外连接：左侧的表的记录全部显示，即使没有匹配上

	- 语法：`select 列名... from 左表 left join 右表 on 条件`

	- :two:右外连接：右侧的表的记录全部显示，即使没有匹配上

	- 语法：`select 列名... from 左表 right join 右表 on 条件`

	- 这两条语句其实等价（交换左右表的位置即可），因为“左”、“右”只是代表相对位置

	- ```mysql
		DROP TABLE IF EXISTS stu;
		DROP TABLE IF EXISTS exam;
		
		CREATE TABLE stu(id INT ,`name` VARCHAR(32) );
		INSERT INTO stu VALUES(1,'ririan'),(2,'sakuya')
			,(3,'reimu'),(4,'reisen');
		
		CREATE TABLE exam (id INT, score INT);
		INSERT INTO exam VALUES(1, 56),(2, 76),(11,8);
		
		SELECT * FROM stu;
		SELECT * FROM exam;
		
		# 1. 显示所有人的成绩，使用左外连接
		SELECT `name`, stu.id, score FROM
			stu LEFT JOIN exam 
			ON stu.id = exam.id;
			
		# 2. 显示所有成绩对应的人，使用右外连接
		SELECT  score ,`name`, stu.id FROM
			stu RIGHT JOIN exam 
			ON stu.id = exam.id;
		```



## 约束

1. 基本介绍
	- 约束用于确保数据库数据满足特定的商业规则
	- MySQL中，约束有五种：`not null`、`unique`、`primary key`、`foreign key`、`check`



2. 主键`primary key`

	- 用于唯一标识行的数据。当定义该主键约束后，列不能重复

	- 基本格式

		- :one:`字段名 类型 primary key`
		- :two:在表定义最后写：`primary key(列名...)`

	- 主键列不能重复且非空

	- 一张表最多有一个主键，但可以是复合主键

	- 实际开发中，每个表往往都会设计一个主键

	- ```mysql
		DROP TABLE IF EXISTS temp;
		#两种定义主键的方式
		CREATE TABLE temp (id INT PRIMARY KEY, salary DOUBLE);
		CREATE TABLE temp(id INT, salary DOUBLE, PRIMARY KEY(id));
		#复合主键。当且仅当主键中每一个字段都相等时，才算重复
		CREATE TABLE temp(id INT, salary DOUBLE, email VARCHAR(64),
				PRIMARY KEY(id,email));
		
		DESC temp;#可以看到字段的约束信息
		```



3. 非空：`not null`
	- 格式：`字段名 类型 not null`
	- 定义非空约束后，插入数据时必须为列提供数据



4. 唯一：`unique`
	- `字段名 类型 unique`
	- 定义唯一约束后，该列值不能重复
	- 如果没有指定`not null`，则`unique`字段可以有多个`null`值
	- 给字段加上`unique not null`的约束，效果等同于主键约束，但一张表可以有多个`unique`字段



5. 外键：`foreign key`

	- 用于定义主表和从表之间的关系。外键约束定义在从表字段上，而主表字段必须具有主键约束或唯一约束。

	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204041526198.png" alt="image-20220404152635646" style="zoom:33%;" />

	- 某字段被定义为外键后，要求该列数据必须在主表的主键列存在，或者数据的值为`null`

	- 语法：在表的最后定义：`foreign key (本表字段) references 主表名(主表字段)`

	- reference意为引用，可以按照c++中的引用来理解：从表中的外键字段必须引用主表字段中的一个值。`int& a = b`，b需要是一个存在的变量；而`int& a = 1`是非法的，正如从表外键列不能是主表列中不存在的值。
	
	- ```mysql
		DROP TABLE IF EXISTS class;
		DROP TABLE IF EXISTS stu;
		CREATE TABLE class(id INT PRIMARY KEY, `name` VARCHAR(25));
		CREATE TABLE stu(id INT, `name` VARCHAR(25), cls_id INT,
			FOREIGN KEY (cls_id) REFERENCES  class(id)) ;
		
		INSERT INTO class VALUES(1,'java'),(2,'Golang');
		INSERT INTO stu VALUE(1, 'jack',1);
		INSERT INTO stu VALUE(2, 'rose',3);#error，stu.id中不存在3
		```
		
	- 外键指向的表的字段，必须有主键或者唯一约束——主表如果有多个相同值，应该引用谁呢？
	
	- 只有引擎为`innodb`的表才支持外键
	
	- 外键字段的类型要和主键字段一致，但长度可以不一致
	
	- 一旦建立外键关系，主表中被引用的记录就不能随意删除，除非从表中不再有对它的引用。



6. `check`

	- 行数据必须满足`check`条件，否则会报错

	- 语法：`字段 类型 check(条件)`

	- MySQL 5.7不支持`check`，只做语法校验，但不生效

	- ```mysql
		DROP TABLE IF EXISTS employee;
		CREATE TABLE employee(
			id INT PRIMARY KEY , `name` VARCHAR(20),
			sex CHAR(1) CHECK (sex IN('M','F')),
			salary DOUBLE CHECK(salary BETWEEN 2000 AND 8000) 
		);
		#MySQL 5.7还不支持该check
		INSERT INTO employee VALUES (1, 'jack','男',10);
		```



7. 自增长

	- 使某一列在添加记录时自动加1

	- 语法：`字段 int (primary key | unique) auto_increment`

	- 通常，自增长配合主键使用。单独使用时，需要配合`unique`

	- 自增长修饰的字段类型为整型。虽然也可以修饰小数，但极少这样用

	- 自增长默认从1开始，也可以使用`alter table 表名 auto_increment = 新值;`来修改

	- 如果在添加数据时，给自增长字段指定值，则自增长的值会以本次的值为准。但一般不会刻意为自增长字段赋值。

	- ```mysql
		DROP TABLE IF EXISTS temp;
		CREATE TABLE temp(id INT PRIMARY KEY AUTO_INCREMENT, 
			`name` VARCHAR(25));
		#两种使用自增长的方式
		INSERT INTO temp VALUES(NULL,'jack');
		INSERT INTO temp (`name`) VALUES ('rose');
		SELECT * FROM temp;
		
		DROP TABLE IF EXISTS temp2;
		CREATE TABLE temp2 LIKE temp;
		#改变自增长的值
		ALTER TABLE temp2 AUTO_INCREMENT = 10;
		INSERT INTO temp2 VALUES(NULL, 'mary');
		INSERT INTO temp2 VALUES(NULL, 'nanami');
		#为自增长字段赋值，同样会改变自增长的值
		INSERT INTO temp2 VALUES(666, 'dick');
		INSERT INTO temp2 VALUES(NULL, 'raiha');
		SELECT * FROM temp2;
		```



## 索引

1. 基本介绍
	- 通过对表的一个字段建立索引，在查询时能**大大**提高速度



2. 基本原理
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204050830620.png" alt="image-20220405083014213" style="zoom:33%;" />
	- 为什么没有索引时查询会慢？每次查询都是对全表进行线性查询，效率为`O(N)`
	- 为什么使用索引查询会快 ？通过建立二叉树等结构，将效率提升为`O(log(N))`
	- 索引的代价：
		- 磁盘占用
		- 对于`update`、`delete`和`insert`语句有影响（参考AVL的原理）
	- 在项目中，`select`语句使用更多，故建立索引还是利大于弊的



3. 索引类型
	- :one:主键索引：主键约束**自动**的是主索引
	- :two:唯一索引`unique index`：唯一约束**自动**的是索引
	- :three:普通索引`index`
	- :four:全文索引：`fulltext`，适用于`MyISAM`引擎。但该索引效率较低，开发中一般不使用该索引，而是使用全文搜索框架Solr和ElasticSearch（ES）



4. 创建索引

	- 主键约束或唯一约束包含着以下信息：该字段是主键索引或唯一索引

	- ```mysql
		DROP TABLE IF EXISTS t1;
		
		#1. 创建唯一索引
		CREATE TABLE t1(id INT UNIQUE, `name` VARCHAR(25));
		
		CREATE TABLE t1(id INT, `name` VARCHAR(25));
		#2. 添加唯一索引，即是添加唯一约束。同时给索引取名为id_index1
		CREATE UNIQUE INDEX id_index1 ON t1(id);
		
		CREATE TABLE t1(id INT, `name` VARCHAR(25));
		#3. 添加普通索引方式1
		CREATE INDEX id_index2 ON t1(id);
		#4. 添加普通索引方式2
		ALTER TABLE t1 ADD INDEX id_index3(id);
		
		#5. 主键约束就是主键索引
		CREATE TABLE t1(id INT PRIMARY KEY, `name` VARCHAR(25));
		#6. 添加主键约束
		CREATE TABLE t1(id INT, `name` VARCHAR(25));
		ALTER TABLE t1 ADD PRIMARY KEY (id);
		
		
		#显示表的索引
		SHOW INDEX FROM t1;
		DESC t1;
		```



5. 删除索引

	- ```mysql
		DROP TABLE IF EXISTS t1;
		
		CREATE TABLE t1(id INT, `name` VARCHAR(25) PRIMARY KEY);
		CREATE INDEX id_index2 ON t1(id);
		#通过索引名删除索引
		DROP INDEX id_index2 ON t1;
		#去除主键约束
		ALTER TABLE t1 DROP PRIMARY KEY;
		
		SHOW INDEX FROM t1;
		```



6. 查询索引

	- ```mysql
		show index from 表名;
		show keys from 表名;
		desc 表名;
		```



7. 创建索引的一些规则
	- 频繁的作为查询条件的字段应该创建索引，如`select * from person where id = 1;`
	- 唯一性太差的字段不适合创建索引，即使频繁地被查询，如`select * from person where sex = '男';`
	- 更新频繁的字段不适合创建索引，因为涉及数据结构的频繁变动，比如记录登录次数的字段`login_count`
	- 不会出现在`where`条件中的字段不用创建索引，纯属浪费空间



## 事务

1. 引入：
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204050942824.png" alt="image-20220405094220084" style="zoom:33%;" />
	- 有如上需求：两个人之间转账，仅当一个人余额的减少等于另一个人余额的增加，转账才完成。不然，只有一方余额增加/减少，转账都算失败
	- 在MySQL中，需要将多个dml（data management language，即`update`、`delete`、`insert`）语句视作一个整体，要么全部成功，否则视为全部失败



2. 基本介绍
	- 事务用于保证数据的一致性，它由一组相关的dml语句组成，该组语句要么全部成功，否则全部失败
	- 当执行事务操作时，MySQL会在表上加锁，防止其他用户对表使用dml语句。



3. 控制事务的操作

	- `start transaction`：开始事务

	- `savepoint 保存点名`：设置保存点

	- `rollback to 保存点名`：回退至保存点

	- `rollback`：回退全部事务

	- `commit`：提交事务，使所有操作生效，不能回避

	- ```mysql
		DROP TABLE IF EXISTS t;
		CREATE TABLE t(id INT 
			,`name` VARCHAR(32));
		#先创建表，再开启事务，不然事务不起作用？
		START TRANSACTION;
		
		SAVEPOINT a;
		INSERT INTO t VALUES (1, 'jack');
		
		SAVEPOINT b;
		INSERT INTO t VALUES (2, 'rose');
		
		SELECT * FROM t;
		ROLLBACK TO b;
		```

	- 可以看出，事务的操作类似于Git的版本控制



4. 事务原理
	- :one:回退事务
		- :eight_pointed_black_star: 保存点：保存点是事务中的点，用于取消该点之后的dml语句
		- 当执行回退事务时，通过指定保存点回退到该点。回退后，原本该点之后的语句将全部失效，包括设置的保存点——即不可能跳向未来的保存点，这一点和Git不同
	- :two:提交事务
		- 使用`commit`语句来提交事务。事务提交后，会确认事务的变化、结束事务、删除保存点（意味着不能再回退）、释放锁，使数据正式生效。同时， 其他会话（其他用户的连接）可以看到事务变化后的新数据



5. 事务细节
	- 如果不开始事务，**默认情况下，dml操作时自动提交**的，回滚无效
	- 开启事务后，如果没有保存点，可以使用`rollback`回退到事务开始的状态
	- 保存点可以创建任意多个
	- `InnoDB`引擎支持事务机制，而`MyISAM`不支持
	- 也可以使用`set autocommit = off;`来开启事务



6. 事务隔离级别
	- 多个连接开启各自事务，操作数据库数据时，数据库要负责隔离操作，以保证各个连接在获取数据时的准确性。
	- 如果没有隔离，可能会引发如下问题：
		- :one:脏读（dirty read）：当一个事务读取另一个事务尚未提交的修改时，产生脏读
		- :two:不可重复读（nonrepeatable read）：同一查询在同一事务中多次执行，由于其它事务提交所做的**修改或删除**操作，每次查询返回的结果不同，产生不可重复读
		- :three:幻读（phantom read）：同一查询在同一事务中多次执行，由于其它事务提交所做的**插入**操作，每次查询返回的结果不同，产生幻读
		- 脏读是能够看见其他事务**提交前**的修改，而幻读和不可重复读是能够看见其他事务**提交后**的修改。后两者的区别仅在其他事务的操作不同



7. 4种隔离级别
	- MySQL隔离级别定义了事务与事务之间的隔离程度
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204051252543.png" alt="image-20220405125209189" style="zoom: 50%;" />
	- 加锁：如果有别的事务在操作数据，当前事务（级别为`serializable`）的查询行为会被挂起（等待），直到没有别的事务操作（其它事务全部提交），才能开始查询并返回结果。
	- 实操：
		- 使用两个控制台连接数据库
		- 一个负责修改表，另一个通过使用不同隔离级别，来查询表。两边都需要开启事务。



8. 隔离操作

	- 查看当前会话隔离级别：`select @@tx_isolation`

	- 查看系统当前隔离级别：`select @@global.tx_isolation`

	- 设置当前会话隔离级别：`set session transaction isolation level 隔离级别;`

	- 设置系统隔离级别：`set global transaction isolation level 隔离级别;`

	- MySQL默认的系统隔离级别为`repeatable read`，该级别能满足大部分项目需求，因此没必要改

	- 修改系统默认隔离级别：在`my.ini`文件最后加上：

		- ```ini
			[mysqld]
			transaction-isolation=READ-UNCOMMITTED
			```

		- 配置文件里的隔离级别写法为：`READ-UNCOMMITTED`、`READ-COMMITTED`、`REPEATABLE-READ`、`SERIALIZABLE`

		- 不写则默认为`REPEATABLE-READ`



9. 事务的ACID特性
	- :one:原子性（Atomicity）：事务是一个不可分割的工作单位。事务中的操作要么都发生，要么都不发生
	- :two:一致性（Consistency）：事务必须使数据库从一个一致性状态变换到另一个一致性状态。
		- 状态（state）由数据库中的数据定义。只要两份文件有1 bit不同，就代表不同的状态。
		- 由于事务有原子性，事务是否提交成功，数据库的状态只可能有两种，不可能有其他可能性
	- :three:隔离性（Isolation）：多个用户并发访问数据库时，数据库为每一个用户开启的事务，不能被其他事务的操作所干扰，多个并发事务之间要相互隔离
	- :four:持久性（Durability）:一个事务一旦被提交，它对数据库中数据的改变就是永久性的。即使数据库发生故障也不应该对其有影响





## 存储引擎

1. 基本介绍

	- MySQL的表类型由存储引擎（storage engines）决定，常用的有MyISAM、InnoDB、Memory等
	- 使用`show engines`可以查看




2. 引擎特点
	- <img src="C:\Users\Morgan\AppData\Roaming\Typora\typora-user-images\image-20220405162837324.png" alt="image-20220405162837324" style="zoom: 67%;" />
	- MyISAM不支持事务和外键，但访问速度快，对事务完整性没有要求
	- InnoDB提供了具有提交、回滚和崩溃恢复能力的事务安全。但相比MyISAM，InnoDB 写的效率较差，且会占用更多磁盘空间
	- MEMORY使用内存中的数据来创建表。每个MEMORY表只实际对应一个磁盘文件。MEMORY表访问非常快，因为数据放在内存中（不是文件IO），且默认使用HASH索引。但是，一旦MySQL服务关闭，表中的数据就会丢失，只有表的结构作为文件存在



3. 选择表的存储引擎
	- 如果不需要事务，只处理CRUD操作，则使用MyISAM，因为速度快
	- 如果需要支持事务，使用InnoDB
	- 使用MEMORY引擎的例子：记录用户在线状态。由于用户状态的改变极为频繁（QQ中可以有在线、离线等状态），每次改变都涉及文件IO的话效率低，故将用户id和状态做成一张MEMORY表，将数据记录在服务器内存中，以支持快速修改。







## 视图

1. 引入
	- 员工表有多列，其中一些字段包含个人隐私，如工资、奖金等。如果我们希望某个用户只能查询员工表的基本信息（如姓名、工号等），而不是隐私信息，应该如何实现？



2. 基本概念
	- 视图是一个虚拟表，其内容由查询定义。与表一样，视图包含列，但其数据来自对应的真实表（基表）
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204061048931.png" alt="image-20220406104809117" style="zoom: 50%;" />
	- 视图与基表之间存在映射关系。对视图的操作实际是对基表的操作。
	- 视图根据（多个）基表创建，但本身不包含数据——可以理解为一种对基表数据的引用



3. 基本使用

	- 创建视图：`create view 视图名 as (select语句);`

	- 修改视图：`alter view 视图名 as (select语句);`

	- 查看创建视图的指令：`show create view 视图名;`

	- 删除视图：`drop view 视图名;`

	- 这里使用[前面](#`select`多表查询)定义的`person`表做演示：

	- ```mysql
		SELECT * FROM person;
		#创建视图
		CREATE VIEW v1 AS (SELECT id, `name`, jobID FROM person);
		
		SELECT * FROM v1;
		#创建视图的语句
		SHOW CREATE VIEW v1;
		
		DROP VIEW v1;
		```



4. 细节
	- 创建视图后，数据库文件中只有对应的结构文件（`.frm`），没有数据文件
	- 视图的数据变化会影响到基表，反之亦然
	- 视图中可以再使用视图。这是把前者当作一张表来使用



5. 视图实践场景
	- :one:安全：一些数据表有重要的信息。有些字段是保密的，不能让用户看到。这时创建一个视图，只保留部分字段，供用户查询
	- :two:性能：关系数据库的数据常常会分表存储，并使用外键建立这些表的关系。查询时，通常会使用到`join`，效率较低。创建视图可以将相关的表和字段组合在一起，效率较高
	- :three:灵活：如果系统中有（多张）表，这些表由于设计问题，即将被废弃。但很多应用/项目都基于这些表，故不适宜修改。此时可以创建一个视图，作为一张新表供项目使用。这样做对数据改动较少，又达到了升级数据库的目的。




6. 练习

	- 使用[前面](#`select`多表查询)定义的三张表

	- ```mysql
		#使用这三张表：person depart sal_grade
		#员工编号、名字、部门名称 和薪水级别 创建视图
		SELECT * FROM person;
		SELECT * FROM depart;
		SELECT * FROM sal_grade;
		
		DROP VIEW IF EXISTS v1;
		CREATE VIEW v1 AS (
			SELECT id,`name`,depart_name, grade AS sal_grade
			FROM person, depart, sal_grade
			WHERE (person.departID = depart.departID)
				AND (person.salary BETWEEN low AND high)
			ORDER BY id
		);
		SELECT * FROM v1;
		```



## MySQL管理

1. MySQL用户
	- MySQL中的用户信息，都存放在数据库`mysql`的`user`表中
	- `host`字段：该用户允许登录的“位置”，`localhost`表示该用户只能在本机登录，也可以指定IP地址，如`192.168.1.100`
	- `user`字段：用户名
	- `authentication_string`字段：密码，但通过了`password()`函数加密



2. 用户管理

	- 项目开发时，可以根据不同的开发人员，赋予不同的MySQL操作权限。这样，不同的用户登录到DBMS后，根据权限不同，可以访问的数据库和数据对象（表、视图等）都不一样

	- 创建用户：`create user '用户名'@'登录位置' identified by '密码'`，如：

	- ```mysql
		create user 'morgan'@'localhost' identified by '123456';
		```

	- 删除用户：`drop user '用户名'@'登录位置' ;`

	- 修改自己密码：`set password = password('密码');`

	- 修改他人密码（需要有修改密码权限）：`set password for '用户名'@'登录位置' = password('密码');`



3. 权限管理
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204061406821.png" alt="image-20220406140642597" style="zoom: 67%;" />
	
	- :one:给用户授权：
		- 语法：`grant 权限列表 on 库名.对象名 to '用户名'@'登录位置' [identified by '密码'] ;`
		
		- 权限列表：（多个权限用逗号隔开）
		
			- ```mysql
				grant select on ...
				grant select, delete on ..
				grant all [privileges] on ...#授予所有权限
				```
		
		- `库.对象名`
		
			- `*.*`表示本系统所有数据库的所有对象（表、视图、存储过程等）
			- `库.*`表示某个数据库的所有对象
		
		- `identified by '密码'`如果写上
		
			- 如果用户存在，会修改用户密码
			- 如果用户不存在，会创建用户
		
	- :two:回收用户权限：
	
	  - 语法：`revoke 权限列表 on 库名.对象名 from '用户名'@'登录位置'; `
	
	- :three:权限生效指令
	
	  - 如果权限没有生效，可以使用`flush privileges;`



4. 细节
	- 在创建用户时，如果不指定`host`，其值为`%`，代表在所有IP连接都可以
	- 指定`host`时，也可以使用通配符，如`create user 'aaa'@'192.168.1.%';`
	- 删除用户时，如果`host`为`%`，可以直接用`drop user '用户名';`删除



# 第22章：JDBC和连接池



## JDBC概述

1. 基本介绍
	- Java Database Connectivity：Java数据库连接，简称JDBC
	- JDBC为访问不同的数据库提供了统一的接口，为使用者屏蔽细节问题。程序员只需要面向接口编程即可
	- 程序员使用JDBC，可以连接任何提供JDBC驱动程序的数据库系统，从而完成对数据库的操作



2. JDBC原理
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204071254628.png" alt="image-20220407125440984" style="zoom: 50%;" />
	- java制定程序连接数据库的规范，即要求各个数据库厂商实现java提供的接口
	- 各个数据库厂商实现接口，将代码封装到相应驱动中（即`.jar`文件），提供给java
	- 程序员只要调用接口，就能对各种数据库进行操作





3. JDBC好处
	- 如果java直接访问数据库，则不仅需要为不同数据库写不同代码，而且每当数据库更新，都需要修改代码——不合理
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204071258119.png" alt="image-20220407125825871" style="zoom: 50%;" />
	- 使用JDBC，数据库的更新只影响JDBC驱动更新，不会影响原有的代码和程序















## JDBC快速入门

1. 准备工作
	- 在[这里](https://dev.mysql.com/downloads/connector/j/)选择platform independent的压缩包下载，解压，得到驱动文件：`mysql-connector-java-8.0.28.jar`
	- 在项目目录下创建`libs`文件夹（名字随意），将驱动复制到这里，右键`Add as library`



2. 基本使用

	- 先建立一张表：

	- ```mysql
		CREATE TABLE t1(id INT PRIMARY KEY AUTO_INCREMENT,
				`name` VARCHAR(32),info VARCHAR(255) );
		SELECT * FROM t1;
		```

	- 代码：

	- ```java
		import com.mysql.cj.jdbc.Driver;
		
		import java.sql.Connection;
		import java.sql.SQLException;
		import java.sql.Statement;
		import java.util.Properties;
		
		public class Test {
		    public static void main(String[] args) throws SQLException {
		        //1. 注册驱动
		        Driver driver = new Driver();
		
		        //2.得到连接
		        //指定ip，端口和连接的数据库
		        String url = "jdbc:mysql://localhost:3306/db03";
		        //将用户名和密码放到Properties对象中
		        Properties properties = new Properties();
		        //这两个键是固定的
		        properties.setProperty("user", "root");
		        properties.setProperty("password", "123");
		        //建立与数据库的连接,类似于获得Socket对象
		        Connection connect = driver.connect(url, properties);
		
		        //3. 要执行的SQL语句
		        String query = "insert into t1 values(null ,'rose','a girl from a falling nobility family')";
		        //类似于获得一个IO流对象，即socket.getInputStream()
		        Statement statement = connect.createStatement();
		        //发送query给数据库，并接收结果
		        int i = statement.executeUpdate(query);//如果是dml语句，返回受影响的行数
		        System.out.println(i == 0 ? "失败" : "成功");
		
		        //4. 释放资源
		        statement.close();
		        connect.close();
		    }
		}
		```







## JDBC API

1. 基本介绍
	- JDBC API是一系列接口，它统一和规范了程序与数据库的连接、执行MySQL语句、得到结果等操作，相关类和接口在`java.sql`和`javax.sql`中



2. 获取数据库连接的5种方式

	- :one:：创建`Driver`对象

		- ```java
			Driver driver = new com.mysql.cj.jdbc.Driver();
			String url = "jdbc:mysql://localhost:3306/db03";
			Properties properties = new Properties();
			properties.setProperty("user", "root");
			properties.setProperty("password", "123");
			Connection connect = driver.connect(url, properties);
			```

	- :two:：使用反射，加载`Driver`类，灵活性比:one:高

		- ```java
			Class<?> cls = Class.forName("com.mysql.cj.jdbc.Driver");
			Driver driver = (Driver) cls.newInstance();
			String url = "jdbc:mysql://localhost:3306/db03";
			Properties properties = new Properties();
			properties.setProperty("user", "root");
			properties.setProperty("password", "123");
			Connection connect = driver.connect(url, properties);
			```

	- :three:：使用`DriverManager`

		- ```java
			Class<?> cls = Class.forName("com.mysql.cj.jdbc.Driver");
			Driver driver = (Driver) cls.newInstance();
			String url = "jdbc:mysql://localhost:3306/db03";
			String user = "root";
			String password = "123";
			
			DriverManager.registerDriver(driver);//注册驱动
			Connection connect = DriverManager.getConnection(url, user, password);
			```

	- :four:：利用`Driver`类加载时的自动注册，简化代码。更为常用。

		- ```java
			Class.forName("com.mysql.cj.jdbc.Driver");//加载类,自动注册
			String url = "jdbc:mysql://localhost:3306/db03";
			String user = "root";
			String password = "123";
			Connection connect = DriverManager.getConnection(url, user, password);
			```

		- `Driver`类的静态代码块：

		- ```java
			static {
			        try {
			            DriverManager.registerDriver(new Driver());
			        } catch (SQLException var1) {
			            throw new RuntimeException("Can't register driver!");
			        }
			    }
			```

		- 从JDK1.5以后使用了JDBC4，会自动调用驱动jar包下`META-INF\services\java.sql.Driver`文本中的类去注册，因此不显式调用`Class.forName()`方法也可以

	- :five:：基于:four:，但使用配置文件，更灵活

		- ```properties
			#re.properties
			driver=com.mysql.cj.jdbc.Driver
			user=root
			password=123
			url=jdbc:mysql://localhost:3306/db03
			```

		- ```java
			Properties properties = new Properties();
			properties.load(new FileInputStream("src//re.properties"));
			
			String url = properties.getProperty("url");
			String user = properties.getProperty("user");
			String password = properties.getProperty("password");
			Class.forName(properties.getProperty("driver"));
			        
			Connection connect = DriverManager.getConnection(url, user, password);
			```



3. `ResultSet`结果集

	- `ResultSet`对象由执行查询数据库的相关方法返回，里面存放了查询结果

	- `ResultSet`对象保持一个光标指向当前数据行。

	- `boolean next()`方法将光标移动到下一行。当没有更多行时，返回`false`

	- ```java
		import java.sql.*;
		
		public class Test {
		    public static void main(String[] args) throws SQLException {
		        //Driver类自动注册
		        String url = "jdbc:mysql://localhost:3306/db02";
		        Connection connect = DriverManager.getConnection(url, "root", "123");
		
		        //要执行的SQL查询语句
		        String query = "select * from person";//之前定义的一张雇员表
		        Statement statement = connect.createStatement();
		
		        //执行查询语句，并返回ResultSet对象
		        ResultSet resultSet = statement.executeQuery(query);
		
		        while (resultSet.next()) {
		            int id = resultSet.getInt(1);//第一列的数据，类型需要自己判断
		            String name = resultSet.getString(2);
		            int salary = resultSet.getInt(3);
		            //MySQL中的日期类型使用getDate()方法获取
		            System.out.println(id + "\t" + name + "\t" + salary);
		
		        }
		        //释放资源
		        resultSet.close();
		        statement.close();
		        connect.close();
		    }
		}
		```

	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204080614167.png" alt="image-20220408061405935" style="zoom: 50%;" />

	- 所有查询结果在`ResultSet`的`rowData`字段中，数据最终以`byte[]`的形式存在



4. `Statement`

	- :one:：`Statement`对象用于执行静态SQL语句并返回结果

	- :two:：在建立连接后，需要对数据库进行访问，执行SQL语句，可以通过以下接口访问：

		- `Statement`
		- `PreparedStatement`：预处理
		- `CallableStatement`：存储过程

	- :three:：`Statement`对象执行SQL语句时，存在SQL注入的风险

		- SQL注入：利用某些系统没有对用户输入的数据进行充分的检查，而在用户输入数据中注入非法的SQL语句或命令，恶意攻击数据库

		- ```mysql
			DROP TABLE IF EXISTS admin;
			CREATE TABLE admin(user_name VARCHAR(32),pwd VARCHAR(32));
			INSERT INTO admin VALUES('root','123');
			
			#通常查询
			SELECT * FROM admin 
				WHERE user_name = 'root' AND pwd = '123';
				
			#SQL注入
			#输入用户名为 1' or
			#输入密码为   or '1' = '1
			#如果只是单纯的文本替换，则查询语句如下
			SELECT * FROM admin 
				WHERE user_name = '1' OR' AND pwd = ' OR '1' = '1';
			#条件永远为真，安全校验没有意义
			```

		- 使用java程序来注入：

		- ```java
			import java.sql.*;
			import java.util.Scanner;
			
			public class Test {
			    public static void main(String[] args) throws SQLException {
			        //Driver类自动注册
			        String url = "jdbc:mysql://localhost:3306/db03";
			        Connection connect = DriverManager.getConnection(url, "root", "123");
			
			        Scanner scanner = new Scanner(System.in);
			        System.out.print("用户名：");
			        String userName = scanner.nextLine();
			        System.out.print("密码：");
			        String pwd = scanner.nextLine();
			
			        String query = "select * from admin where user_name = ' "
			                + userName + " ' AND pwd = ' " + pwd + "' ";
			        Statement statement = connect.createStatement();
			
			        ResultSet resultSet = statement.executeQuery(query);
			
			        System.out.println(resultSet.next() ? "登录成功" : "登录失败");
			
			
			        resultSet.close();
			        statement.close();
			        connect.close();
			    }
			}
			```

	- :four:：为了防范SQL注入，实际开发中不使用`Statement`，而是使用`PreparedStatement`



5. `PreparedStatement`

	- `PreparedStatement`是`Statement`的拓展，这种预处理的好处是：

		- 不再使用字符串相加的方式拼接SQL语句，减少语法错误
		- 有效的解决了SQL注入问题
		- 大大减少了编译次数，效率较高

	- :one:预处理查询：

	- ```java
		import java.sql.*;
		import java.util.Scanner;
		
		public class Test {
		    public static void main(String[] args) throws SQLException {
		        //Driver类自动注册
		        String url = "jdbc:mysql://localhost:3306/db03";
		        Connection connect = DriverManager.getConnection(url, "root", "123");
		
		        Scanner scanner = new Scanner(System.in);
		        System.out.print("用户名：");
		        String userName = scanner.nextLine();
		        System.out.print("密码：");
		        String pwd = scanner.nextLine();
		
		        // ? 相当于占位符
		        String query = "select * from admin where user_name = ?  AND pwd = ? ";
		        //将PreparedStatement对象与查询语句关联
		        PreparedStatement preparedStatement = connect.prepareStatement(query);
		        //给 ? 赋值
		        preparedStatement.setString(1, userName);//将第一个 ? 替换
		        preparedStatement.setString(2, pwd);
		
		        ResultSet resultSet = preparedStatement.executeQuery();
		        System.out.println(resultSet.next() ? "登录成功" : "登录失败");
		
		
		        resultSet.close();
		        preparedStatement.close();
		        connect.close();
		    }
		}
		```

	- :two:预处理DML

	- ```java
		import java.sql.*;
		import java.util.Scanner;
		
		public class Test {
		    public static void main(String[] args) throws SQLException {
		        //Driver类自动注册
		        String url = "jdbc:mysql://localhost:3306/db03";
		        Connection connect = DriverManager.getConnection(url, "root", "123");
		
		        System.out.println("添加记录");
		        Scanner scanner = new Scanner(System.in);
		        System.out.print("用户名：");
		        String userName = scanner.nextLine();
		        System.out.print("密码：");
		        String pwd = scanner.nextLine();
		
		
		        String query = "insert into admin values (?,?)";
		
		        PreparedStatement preparedStatement = connect.prepareStatement(query);
		        //给 ? 赋值
		        preparedStatement.setString(1, userName);
		        preparedStatement.setString(2, pwd);
		
		        int i = preparedStatement.executeUpdate();
		        System.out.println(i == 1 ? "插入成功" : "插入失败");
		
		        preparedStatement.close();
		        connect.close();
		    }
		}
		```





## 开发JDBCUtils

1. 说明
	- 在JDBC中，获取连接和释放资源是经常使用的，可以将其封装到相应的工具类中



2. 代码

	- ```java
		import java.io.FileInputStream;
		import java.io.IOException;
		import java.sql.*;
		import java.util.Properties;
		
		/**
		 * 自己开发的JDBC工具类
		 */
		public class JDBCUtils {
		    private static String driver;
		    private static String url;
		    private static String user;
		    private static String pwd;
		
		    private JDBCUtils() {
		    }
		
		    static {
		        try {
		            Properties properties = new Properties();
		            properties.load(new FileInputStream("src\\mysql.properties"));
		
		            driver = properties.getProperty("driver");
		            url = properties.getProperty("url");
		            user = properties.getProperty("user");
		            pwd = properties.getProperty("password");
		
		        } catch (IOException e) {
		            //将编译异常转化为运行异常，在开发中很常用
		            //程序员可以自主选择捕获与否(而编译异常必须被处理)
		            throw new RuntimeException(e);
		        }
		    }
		
		    /**
		     * 连接数据库
		     *
		     * @return
		     */
		    public static Connection getConnection() {
		        try {
		            return DriverManager.getConnection(url, user, pwd);
		        } catch (SQLException e) {
		            throw new RuntimeException(e);
		        }
		    }
		
		    /**
		     * 关闭JDBC相关资源.
		     * 如果不想关闭某个资源，传入null即可
		     *
		     * @param resultSet
		     * @param statement  Statement或PreparedStatement对象
		     * @param connection
		     */
		    public static void close(ResultSet resultSet, Statement statement, Connection connection) {
		
		        try {
		            if (resultSet != null) {
		                resultSet.close();
		            }
		
		            if (statement != null) {
		                statement.close();
		            }
		
		            if (connection != null) {
		                connection.close();
		            }
		        } catch (SQLException e) {
		            throw new RuntimeException(e);
		        }
		
		    }
		}
		```



## 事务

1. 基本介绍
	- JDBC程序中，当一个`Connection`对象创建时，**默认情况是自动提交事务的**。每执行一个SQL语句，如果执行成功，会自动提交，不能回滚
	- JDBC为了让多个SQL语句作为一个整体，使用事务
	- 调用`Connection`的`setAutoCommit(false)`方法以取消自动提交
	- 当所有SQL语句执行成功后，调用`commit()`提交事务；如果某个操作失败或出现异常，调用`rollback()`，回滚事务



2. 模拟转账

	- ```mysql
		DROP TABLE IF EXISTS `account`;
		CREATE TABLE `account`(id INT ,balance INT);
		INSERT INTO `account` VALUES(1,2000),(2,4500);
		
		SELECT * FROM `account`;
		```

	- ```java
		import java.sql.Connection;
		import java.sql.PreparedStatement;
		import java.sql.SQLException;
		
		public class Test {
		    public static void main(String[] args) {
		        String sql1 = "UPDATE `account` SET balance = balance - 100 WHERE id =1;";
		        String sql2 = "UPDATE `account` SET balance = balance + 100 WHERE id =2;";
		
		        Connection connection = null;
		        PreparedStatement preparedStatement = null;
		
		        try {
		            connection = JDBCUtils.getConnection();//使用之前写的工具类
		            connection.setAutoCommit(false);//相当于启动事务
		            
		            preparedStatement = connection.prepareStatement(sql1);
		            preparedStatement.executeUpdate();
		
		            int i = 1 / 0;//检验事务是否正常
		
		            preparedStatement = connection.prepareStatement(sql2);
		            preparedStatement.executeUpdate();
		
		            System.out.println("转账成功");
		            connection.commit();//提交事务
		            
		        } catch (Exception e) {
		            System.out.println("出现异常，转账失败");
		
		            try {
		                connection.rollback();//执行回退
		            } catch (SQLException throwables) {
		                throwables.printStackTrace();
		            }
		
		        } finally {
		            JDBCUtils.close(null, preparedStatement, connection);
		        }
		    }
		}
		```





## 批处理

1. 基本介绍
	- 当需要成批地插入或更新记录时，可以采用java的批量更新机制。该机制允许多条语句一次性提交给数据库批量处理，通常比单独提交处理更有效率
	- JDBC批处理包含以下方法
		- `addBatch()`：添加需要批量处理的SQL语句
		- `executeBatch()`：执行批量处理语句包
		- `clearBatch()`：清空批处理语句包
	- JDBC连接MySQL时，如果要使用批处理功能，需要在`url`最后添加参数`?rewriteBatchedStatements=true`
	- 批处理和`PreparedStatement`一起使用，既可以减少编译次数，又减少运行次数，从而大幅提高效率



2. 快速使用——对比传统方式

	- ```mysql
		DROP TABLE IF EXISTS admin;
		CREATE TABLE admin(user_name VARCHAR(32),pwd VARCHAR(32));
		SELECT COUNT(*) FROM admin;
		```

	- ```java
		import java.sql.Connection;
		import java.sql.PreparedStatement;
		
		public class Test {
		    public static void main(String[] args) throws Exception {
		        Connection connection = JDBCUtils.getConnection();//使用之前写的工具类
		        String sql = "insert into admin values(?,?)";
		        PreparedStatement preparedStatement = connection.prepareStatement(sql);
		        long start = System.currentTimeMillis();
		        
				//使用不同方式，先把表中已有的记录删除
		        if (false) {//传统方式：消耗毫秒数:3313
		            for (int i = 0; i < 5000; i++) {
		                preparedStatement.setString(1, "issac" + i);
		                preparedStatement.setString(2, "abc" + i);
		                preparedStatement.executeUpdate();
		            }
		
		        } else {//批处理(不要忘了给url后加上参数)：消耗毫秒数:118
		            for (int i = 0; i < 5000; i++) {
		                preparedStatement.setString(1, "issac" + i);
		                preparedStatement.setString(2, "abc" + i);
		                preparedStatement.addBatch();//将当前语句加入到批处理包中
		
		                if ((i + 1) % 1000 == 0) {//每有1000条SQL语句处理一次
		                    preparedStatement.executeBatch();
		                    preparedStatement.clearBatch();//清空已有的批处理包
		                }
		            }
		        }
		        long end = System.currentTimeMillis();
		        System.out.println("消耗毫秒数:" + (end - start));
		        JDBCUtils.close(null, preparedStatement, connection);
		    }
		}
		```



3. 底层原理
	- 每次执行`addBatch()`方法，都会将当前的SQL语句存入一个`ArrayList`中，以便在调用`executeBatch()`时一次性发送给MySQL



## 连接池

1. 引入

	- 编写程序，连接MySQL 5k次

	- ```java
		import java.sql.Connection;
		
		public class Test {
		    public static void main(String[] args) throws Exception {
		        for (int i = 0; i < 5000; i++) {
		            Connection connection = JDBCUtils.getConnection();
		        }
		    }
		}
		```

	- 抛出如下异常：`Exception in thread "main" java.lang.RuntimeException: java.sql.SQLNonTransientConnectionException: Data source rejected establishment of connection,  message from server: "Too many connections"`

	- 如果连接后就关闭了呢？

	- ```java
		import java.sql.Connection;
		
		public class Test {
		    public static void main(String[] args) throws Exception {
		        long start = System.currentTimeMillis();
		        for (int i = 0; i < 5000; i++) {
		            Connection connection = JDBCUtils.getConnection();
		            JDBCUtils.close(null, null, connection);
		        }
		        long end = System.currentTimeMillis();
		        System.out.println(end - start);
		    }
		}
		```

	- 耗时`13798`毫秒（14秒），时间太长



2. 传统连接问题分析
	- 传统的JDBC数据库连接使用`DriverManager`来获取，每次向数据库建立连接都要将`Connection`对象加载到内存中，再验证IP地址、用户名和密码**（0.05s - 1s）**。每当需要数据库连接，就向数据库申请，频繁地进行数据库连接操作将占用很很多的系统资源，容易造成服务器崩溃
	- 每一次建立数据库连接，使用完都得断开。如果未能断开，将导致数据库内存泄露，最终导致重启数据库
	- 传统连接的方式，不能控制创建的连接数量，如连接过多，也可能导致内存泄露，引发MySQL崩溃（想象一万人瞬间涌向地铁安检口要求通过）
	- 为了解决这个问题，可以采用数据库连接池技术（connection pool）



3. 数据库连接池基本介绍
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204081425248.png" alt="image-20220408142526986" style="zoom: 45%;" />
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204081426045.png" alt="image-20220408142600731" style="zoom: 37%;" />
	- 预先在缓冲池中放入一定数量的连接，当需要建立数据库连接时，只需从缓冲池中取出一个，使用完毕之后再放回去
	- 数据库连接池负责分配、管理和释放数据库连接。它允许程序重复使用一个现有的数据库连接，而不是重新建立一个
	- 当程序向连接池请求的连接数超过最大连接数量时，这些请求将被加入到等待队列中



4. 数据库连接池种类
	- JDBC数据库连接池使用`javax.sql.DataSource`接口，该接口通常由第三方提供实现（提供`.jar`包）
	- :one:C3P0：速度相对较慢，稳定性不错（被hibernate、string使用）
	- :two:DBCP：速度比C3P0块，但不稳定
	- :three:Proxool：有监控连接池状态的功能，稳定性比C390差一点
	- :four:BoneCP：速度快
	- :five:Druid（德鲁伊）：阿里提供的数据库连接池，集DBCP、C3P0、Proxool优点于一身
	- :eight_pointed_black_star:C3P0和Druid在开发中最为常用



5. C3P0

	- :zero:在[这里](https://mvnrepository.com/artifact/com.mchange/c3p0/0.9.5.5)下载`c3p0-0.9.5.5.jar`，在[这里](https://mvnrepository.com/artifact/com.mchange/mchange-commons-java/0.2.20)下载`mchange-commons-java-0.2.20.jar`，把这两个文件添加到项目中

	- :one:方式一：在程序中指定`user`、`url`等参数

	- ```java
		import com.mchange.v2.c3p0.ComboPooledDataSource;
		
		import java.io.FileInputStream;
		import java.sql.Connection;
		import java.util.Properties;
		
		public class Test {
		    public static void main(String[] args) throws Exception {
		        Properties properties = new Properties();
		        properties.load(new FileInputStream("src\\mysql.properties"));
		
		        String driver = properties.getProperty("driver");
		        String url = properties.getProperty("url");
		        String user = properties.getProperty("user");
		        String pwd = properties.getProperty("password");
		
		        //创建数据源对象
		        ComboPooledDataSource comboPooledDataSource = new ComboPooledDataSource();
		
		        //因为由连接池接管一切数据库连接请求，所以需要设置url、user等参数
		        comboPooledDataSource.setDriverClass(driver);
		        comboPooledDataSource.setJdbcUrl(url);
		        comboPooledDataSource.setUser(user);
		        comboPooledDataSource.setPassword(pwd);
		
		        //连接池中最初有几个连接
		        comboPooledDataSource.setInitialPoolSize(10);
		        //连接池中最多有几个连接，更多的连接请求会被放入等待队列
		        comboPooledDataSource.setMaxPoolSize(50);
		
		        //测试运行时间
		        long start = System.currentTimeMillis();
		        for (int i = 0; i < 5000; i++) {
		            Connection connection = comboPooledDataSource.getConnection();
		            connection.close();
		        }
		        long end = System.currentTimeMillis();
		        System.out.println(end - start);
		    }
		}
		```

	- 结果，`805`毫秒，比之前的`14`秒快了很多

	- :two:方式二：使用配置文件模板

	- 在`src`下创建配置文件`c3p0-config.xml`，内容如下：

	- ```xml
		<c3p0-config>
		    <!-- 数据源名称 -->
		    <named-config name="learnJDBC">
		
		        <!--  驱动类 -->
		        <property name="driverClass">com.mysql.cj.jdbc.Driver</property>
		        <!--  url -->
		        <property name="jdbcUrl">jdbc:mysql://localhost:3306/db03?rewriteBatchedStatements=true</property>
		        <!--  user -->
		        <property name="user">root</property>
		        <!--  pwd -->
		        <property name="password">123</property>
		
		        <!--连接数的增加幅度-->
		        <property name="acquireIncrement">5</property>
		        <!--初始化申请的连接数量-->
		        <property name="initialPoolSize">10</property>
		        <!--最大的连接数量-->
		        <property name="maxPoolSize">50</property>
		        <!--最小连接数(程序判断当前某些连接是多余时会释放这些连接，这时最小连接数起限制作用)-->
		        <property name="minPoolSize">5</property>
		        <!-- 可连接的最多的命令对象数-->
		        <property name="maxStatements">5</property>
		        <!-- 每个连接对象可连接的命令对象数-->
		        <property name="maxStatementsPerConnection">2</property>
		
		    </named-config>
		</c3p0-config>
		```

	- 程序代码：

	- ```java
		import com.mchange.v2.c3p0.ComboPooledDataSource;
		
		import java.sql.Connection;
		
		public class Test {
		    public static void main(String[] args) throws Exception {
		        //构造器参数为xml文件中写的数据源的名称
		        ComboPooledDataSource comboPooledDataSource = new ComboPooledDataSource("learnJDBC");
		        Connection connection = comboPooledDataSource.getConnection();
		        System.out.println(connection);
		        connection.close();
		    }
		}
		```



6. Druid连接池

	- :zero:在[这里](https://repo1.maven.org/maven2/com/alibaba/druid/1.2.8/)下载`druid-1.2.8.jar`，导入项目中

	- :one:在`src`下创建`druid.properties`文件，内容如下：

	- ```properties
		driverClassName=com.mysql.cj.jdbc.Driver
		url=jdbc:mysql://localhost:3306/db03?rewriteBatchedStatements=true
		username=root
		password=123
		#初始化连接的个数
		initialSize=10
		#最大连接池数量
		maxActive=50
		#获取连接时最大等待时间
		maxWait=3000
		#最少连接数
		minIdle=5
		```

	- :two:程序代码

	- ```java
		import com.alibaba.druid.pool.DruidDataSourceFactory;
		
		import javax.sql.DataSource;
		import java.io.FileReader;
		import java.sql.Connection;
		import java.util.Properties;
		
		public class Test {
		    public static void main(String[] args) throws Exception {
		        Properties properties = new Properties();
		        properties.load(new FileReader("src\\druid.properties"));
		
		        //获得Druid连接池对象
		        DataSource dataSource = DruidDataSourceFactory.createDataSource(properties);
		
		        long start = System.currentTimeMillis();
		        for (int i = 0; i < 5000; i++) {
		            Connection connection = dataSource.getConnection();
		            connection.close();
		        }
		        long end = System.currentTimeMillis();
		        System.out.println(end - start);
		    }
		}
		```

	- 耗时`872`毫秒，相比C3P0的`805`毫秒慢一点。我们将循环次数改为`500000`，C3P0运行`2743`毫秒，Druid运行`1230`毫秒。在连接数较大的情况下，Druid的性能更优。（在实际项目中，五十万次连接是一个很正常的数目 ）



7. 将`JDBCUtils`工具类改为由Druid实现

	- ```java
		import com.alibaba.druid.pool.DruidDataSourceFactory;
		
		import javax.sql.DataSource;
		import java.io.FileReader;
		import java.sql.Connection;
		import java.sql.ResultSet;
		import java.sql.SQLException;
		import java.sql.Statement;
		import java.util.Properties;
		
		/**
		 * 自己开发的JDBC工具类
		 */
		public class JDBCUtils {
		    private static DataSource dataSource;
		
		    private JDBCUtils() {
		    }
		
		    static {
		        try {
		            Properties properties = new Properties();
		            properties.load(new FileReader("src\\druid.properties"));
		            dataSource = DruidDataSourceFactory.createDataSource(properties);
		
		        } catch (Exception e) {
		            //将编译异常转化为运行异常，在开发中很常用
		            //程序员可以自主选择捕获与否(而编译异常必须被处理)
		            throw new RuntimeException(e);
		        }
		    }
		
		    /**
		     * 连接数据库
		     *
		     * @return
		     */
		    public static Connection getConnection() {
		        try {
		            return dataSource.getConnection();
		        } catch (SQLException e) {
		            throw new RuntimeException(e);
		        }
		    }
		
		    /**
		     * 关闭JDBC相关资源.
		     * 如果不想关闭某个资源，传入null即可
		     *
		     * @param resultSet
		     * @param statement  Statement或PreparedStatement对象
		     * @param connection
		     */
		    public static void close(ResultSet resultSet, Statement statement, Connection connection) {
		
		        try {
		            if (resultSet != null) {
		                resultSet.close();
		            }
		
		            if (statement != null) {
		                statement.close();
		            }
		
		            if (connection != null) {
		                connection.close();
		            }
		        } catch (SQLException e) {
		            throw new RuntimeException(e);
		        }
		    }
		}
		```



## Apache——DBUtils

1. 引入
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204090801196.png" alt="image-20220409080138867" style="zoom:33%;" />
	- 问题如下：
		- 关闭`Connection`对象后，`ResultSet`对象也被关闭——记录无法获取了
		- `ResultSet`对象不利于数据管理：如果作为函数返回值或参数，谁来负责关闭该对象是不确定的
	- 解决方法：
		- 设计Java类（如图中的`Actor`），将记录的信息封装到该类中（两者字段应相同）。这样的类被称作JavaBean、POJO（Plain Ordinary Java Object：普通Java对象）或Domain
		- 将所有`Actor`对象存放到`ArrayList`中。该集合就拥有了结果集的全部数据，而后者被关闭了也无所谓



2. Apache Commons DbUtils
	- Commons DbUtils是Apache组织提供的一个JDBC工具包。它是对JDBC的封装，使用其中的类能极大简化JDBC编码的工作量
	- DbUtils包中：
		- `QueryRunner`类：该类封装了SQL的执行，是线程安全的，可以实现crud和批处理。
		- `ResultSetHandler`接口：用于处理`java.sql.ResultSet`，将数据按要求转换为另一种形式。它的实现类有`ArrayHandler`、`BeanListHandler`、`KeyedHandler`、`MapListHandler`等
	- 在[这里](https://commons.apache.org/proper/commons-dbutils/download_dbutils.cgi)下载`commons-dbutils-1.7.jar`，导入项目



3. commons-dbutils查询1：多行记录

	- 使用[`select`多表查询](#`select`多表查询)中定义的`person`表

	- ```java
		import org.apache.commons.dbutils.QueryRunner;
		import org.apache.commons.dbutils.handlers.BeanListHandler;
		
		import java.sql.Connection;
		import java.util.List;
		
		public class Test {
		    public static void main(String[] args) throws Exception {
		        Connection connection = JDBCUtils.getConnection();
		
		        QueryRunner queryRunner = new QueryRunner();
		        String sql = "select  id,`name`,salary from person where kpi between ? and ?";
		
		        //该方法执行sql语句，得到ResultSet，再封装到List集合中
		        //第三个参数为ResultSetHandler对象，里面指定了JavaBean所用的类，在这里是Person.class
		        //底层使用反射生成Person对象
		        //最后为可变参数，对应sql语句的?占位符
		        List<Person> list = queryRunner.query(connection, sql,
		                new BeanListHandler<>(Person.class), 60, 90);
		
		        //sql语句只查询了id，name和salary字段，其他字段会被设置为null
		        for (Person person : list) {
		            System.out.println(person);
		            //使用person.getDepartID()比使用resultSet.getString(2)方便得多，
		            //代码意图更明显
		        }
		        //resultSet和statement对象由query()方法负责关闭，这里只要关闭JDBCUtils中创建的Connection对象
		        JDBCUtils.close(null, null, connection);
		    }
		}
		```

	- ```java
		/**
		 * 对应数据库中的person表
		 */
		public class Person {
		    private Integer id;
		    private String name;
		    private Double salary;
		    private Integer kpi;
		    private Integer jobID;
		    private Integer departID;
		    private Integer mgr;
		
		    //无参构造器用于反射
		    public Person() {
		    }
		
		    @Override
		    public String toString() {
		        return "Person{" +
		                "id=" + id +
		                ", name='" + name + '\'' +
		                ", salary=" + salary +
		                ", kpi=" + kpi +
		                ", jobID=" + jobID +
		                ", departID=" + departID +
		                ", mgr=" + mgr +
		                '}';
		    }
		    public Integer getId() {        return id;    }
		    public void setId(Integer id) {        this.id = id;    }
		    public String getName() {        return name;    }
		    public void setName(String name) {        this.name = name;    }
		    public Double getSalary() {        return salary;    }
		    public void setSalary(Double salary) {        this.salary = salary;    }
		    public Integer getKpi() {        return kpi;    }
		    public void setKpi(Integer kpi) {        this.kpi = kpi;    }
		    public Integer getJobID() {        return jobID;    }
		    public void setJobID(Integer jobID) {        this.jobID = jobID;    }
		    public Integer getDepartID() {        return departID;    }
		    public void setDepartID(Integer departID) {this.departID = departID;
		    }
		    public Integer getMgr() {return mgr;    }
		    public void setMgr(Integer mgr) {     this.mgr = mgr;    }
		}
		
		```

	- :warning:`Person`类和其无参构造器必须声明为`public`，不然`BeanListHandler`无法访问



4. commons-dbutils查询2：单行记录、单行单列

	- ```java
		import org.apache.commons.dbutils.QueryRunner;
		import org.apache.commons.dbutils.handlers.BeanHandler;
		import org.apache.commons.dbutils.handlers.ScalarHandler;
		
		import java.sql.Connection;
		
		public class Test {
		    public static void main(String[] args) throws Exception {
		        Connection connection = JDBCUtils.getConnection();
		        QueryRunner queryRunner = new QueryRunner();
		
		        //查询单行记录
		        String sql = "select  * from person where id = ?";
		        Person query = queryRunner.query(connection, sql,
		                new BeanHandler<>(Person.class), 200);
		        System.out.println(query);
		
		        //查询单行单列的数据
		        sql = "select  `name` from person where id = ?";
		        //scalar：标量；单一值
		        Object o = queryRunner.query(connection,
		                sql, new ScalarHandler<>(), 300);
		        System.out.println(o);
		
		
		        JDBCUtils.close(null, null, connection);
		    }
		}
		```



5. commons-dbutils执行DML语句

	- ```java
		import org.apache.commons.dbutils.QueryRunner;
		
		import java.sql.Connection;
		
		public class Test {
		    public static void main(String[] args) throws Exception {
		        Connection connection = JDBCUtils.getConnection();
		        QueryRunner queryRunner = new QueryRunner();
		
		        //update()方法中可以使用任何DML语句，不只是SQL中的update
		        String sql = "INSERT INTO person VALUES (?,?,?,?,?,?,?)";
		        //返回受影响的行数
		        int rows = queryRunner.update(connection, sql,
		                900, "john", 6000, 90, 4, 4, null);
		        System.out.println(rows);
		        //删除记录
		        String sql2 = "delete from person where id =?";
		        int rows2 = queryRunner.update(connection, sql2, 100);
		        System.out.println(rows2);
		
		
		        JDBCUtils.close(null, null, connection);
		    }
		}
		```



6. 细节
	- `QueryRunner`对象的`query()`方法，将查询的结果通过反射生成相应的javabean对象。这里**要求**：
		- javabean类被声明为`public`
		- javabean类有一个`public`的无参构造器，用于在反射时生成对象
		- javabean类的属性需要有set方法，用于在反射时赋值
	- javabean类属性的名称需要与查询到的结果集的列名相同，否则该属性值为`null`。例如：`select name from employee;`，而javabean类中没有名为`name`的字段，javabean对象中`name`的值永远为`null`
	- 在多表查询时，如果使用一个javabean类来接收结果集的所有列，需要在该类中定义这些属性——它们与各个表中需要的字段名相同。例如`employee`表中有`id`、`name`字段，`depart`表中有`departName`字段，查询语句为`select id, name, departName from employee, depart where 条件 ;`，那么javabean类中应定义这些字段——它们的名字为`id`、`name`和`departName`
	- 如果查询的两张表的某个字段名相同，如`employee`表中有`id`字段，`job`表中也有`id`字段，这两个字段都需要被存入一个javabean对象。此时，使用查询语句`select employee.id as id1, job.id as id2 from employee, job where 条件;`javabean类中定义名为`id1`和`id2`的字段即可





## DAO增删改查：BasicDao

1. 引入
	- 使用Druid和commons-dbutils简化了JDBC开发，但还有不足：
	- SQL语句是固定的（一句话只能执行一种功能），不能通过参数传入，需要进行改进
	- 查询语句的返回值应使用泛型，因为每张表的查询结果使用不同的POJO
	- 业务需求的复杂，不可能只靠一个Java类完成



2. DAO

	- ![image-20220409110132263](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204091101680.png)
	- DAO：data access object，数据访问对象
	- 使用一个DAO对一张表进行操作，例如`ActorDAO`对应`actor`表
	- 由于每个DAO在访问表之前，都需要连接数据库，因此可以把这个共同操作封装到`BasicDAO`中，让其他DAO继承该类
	- 同样，每一张表都需要设计一个与之对应的JavaBean类，将记录封装到对象中，如`actor`表对应`Actor`类



3. 简单设计
	- 创建`jdbc_dao`包：
		- `jdbc_dao.utils`：工具类
		- `jdbc_dao.domain`：javabean
		- `jdbc_dao.dao`：XxxDao和BasicDao
		- `jdbc_dao.test`：测试类



4. 代码
	- https://github.com/el-nino2020/java-hanshunping/tree/main/jdbc_dao





# 第23章：满汉楼

## 源代码

https://github.com/el-nino2020/java-hanshunping/tree/main/mhl



## 界面设计

1. 一个完整的项目长这样：
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204092000325.png" alt="image-20220409200030014" style="zoom:40%;" />
	- 但界面设计不是学习的重点，故使用控制台界面
	- 应完成项目的登录、订座、点餐和结账、查看账单等功能



2. 界面预览图：
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204092004950.png" alt="image-20220409200439640" style="zoom:45%;" />
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204092004693.png" alt="image-20220409200457463" style="zoom:45%;" />
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204092005208.png" alt="image-20220409200552092" style="zoom:60%;" />
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204092006926.png" alt="image-20220409200617611" style="zoom:45%;" />
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204092007778.png" alt="image-20220409200758346" style="zoom:45%;" />
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204092008609.png" alt="image-20220409200828273" style="zoom: 33%;" />
	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204092009861.png" alt="image-20220409200921433" style="zoom:33%;" />



## 项目设计

1. 分层模式
	- View层（界面层）调用service层（业务层）中的各个类，如`EmpService`、`GoodsService`等
	- service层中，每个类调用DAO层相应的类，如`EmpService`类调用`EmpDAO`类
	- DAO层，每个类对相应的表进行操作，如`EmpDAO`类对`emp`表进行操作
	- 每一张表对应一个javabean对象，后者存放在domain层
	- 此外还有工具类的开发，放在`utils`包中
	- 基本和[DAO增删改查：BasicDao](#DAO增删改查：BasicDao)中的框架图一致



## 实现过程

1. 建立相应包，创建工具类
2. 在`MHLView`类中实现显示主菜单、二级菜单和退出系统的功能
3. 实现登录功能：创建`employee`表、`Employee`类和`EmployeeService`类
4. 实现显示餐桌状态功能：创建`dining_table`表以及相应的javabean、DAO和service类
5. 实现餐桌预定功能
6. 实现显示菜品功能：创建`menu`表以及相应的javabean、DAO和service类
7. 实现点餐功能：
	- 点餐时需要检验餐桌号和菜品编号。点餐成功，需要修改餐桌状态
	- 点餐成功，因生成相应账单。设计账单表`bill`以及相应的javabean、DAO和service类
8. 实现查看账单功能
9. 实现结账功能：
	- 对餐桌号进行检验：该桌是否有“未结账”的账单
	- 修改`bill`表相应的记录，以及将`dining_table`相应的记录设置为初始状态
10. 增强查看账单功能：显示账单时显示菜品名：多表查询，设计`BillEnhanced`类作为javabean以及对应的DAO对象，还是使用`BillService`来返回所有记录



## 总结

1. 使用的技术为java、MySQL、JDBC（Druid + Apache-common-dbutils）
2. 在学习了数据库的基础上再次使用分层结构：自底向上，分别为数据层（数据库）+domain层 $\rightarrow$ DAO层 $\rightarrow$ Service层（业务层） $\rightarrow$ View层（界面层）。此外还用工具包`utils`。对分层模式的理解加深了:confetti_ball:
3. 在之前的学习中，完成了`JCBCUtils`和`BasicDAO`类，分别完成了对数据库连接和对数据库操作的封装。这大大简化了该项目。但因此，在写项目时没法对JDBC知识进行巩固和应用，感觉掌握得不是很扎实。（毕竟用的是两个第三方驱动）
4. 满汉楼项目对应的是餐饮行业，包括前台服务和后台订单、报表等。对餐饮行业不是很熟悉，部分影响了我对这个项目要实现哪些功能的理解。需求分析师还是很重要的，他必须熟悉某一行业经营的全部流程:thinking:
5. 各个service类都是用了`select`语句，不过都比较基本，是对于MySQL的简单应用
6. 总的来说，在第3条的基础上完成项目，难度不是很大。



# 第24章：正则表达式（regular expression）



## 快速入门

1. - 需求：找到文章中的所有英语单词

	- 现有方法：按字符逐一匹配，提取出各个完整的英文字母字符串

	- 使用正则表达式：

	- ```java
		import java.util.regex.Matcher;
		import java.util.regex.Pattern;
		
		public class Test {
		    public static void main(String[] args) {
		        //查找content中的所有英文单词
		        String content = "DriverManager：负责加载各种不同驱动程序（Driver），并根据不同的请求，向调用者返回相应的数据库连接（Connection）。Driver：驱动程序，会将自身加载到DriverManager中去，并处理相应的请求并返回相应的数据库连接（Connection）。Connection：数据库连接，负责与进行数据库间通讯，SQL执行以及事务处理都是在某个特定Connection环境中进行的。可以产生用以执行SQL的Statement。Statement：用以执行SQL查询和更新（针对静态SQL语句和单次执行）。PreparedStatement：用以执行包含动态参数的SQL查询和更新（在服务器端编译，允许重复执行以提高效率）。CallableStatement：用以调用数据库中的存储过程。SQLException：代表在数据库连接的建立和关闭和SQL语句的执行过程中发生了例外情况（即错误）。";//来自百度百科JDBC词条的一段文本
		
		        //创建一个Pattern对象，即模式对象
		        Pattern pattern = Pattern.compile("[a-zA-Z]+");
		
		        //创建一个匹配器对象，按照pattern匹配content中的内容
		        Matcher matcher = pattern.matcher(content);
		
		        //找到下一个匹配的内容，返回true，实现循环匹配
		        while (matcher.find()) {
		            System.out.println(matcher.group(0));
		        }
		    }
		}
		```



2. 其他需求
	- 找出文章中所有4个数字连在一起的子串，且满足`xyyx`的格式
	- 用户输入的电子邮箱，需要满足邮箱格式



3. 正则表达式
	- 为了解决上述需求，java提供了正则表达式技术，专门用于处理文本问题
	- 简而言之，正则表达式是对字符串执行模式匹配的技术



4. 基本介绍
	- 一个正则表达式，就是用某种模式去匹配字符串的一个公式。精通正则表达式，能够高效地处理文本工作
	- 大多数编程语言都支持正则表达式



5. 查询的底层原理

	- 以查询一段文字中连续4个数字的字符串为例，理解`Matcher`类的`find`和`group`方法

	- ```java
		import java.util.regex.Matcher;
		import java.util.regex.Pattern;
		
		public class Test {
		    public static void main(String[] args) {
		        //引用自百度百科达芬奇词条
		        String content = "列奥纳多·达·芬奇儒略历1452年4月15日（公历4月23日）~1519年5月2日］。" +
		                "达·芬奇生于托斯卡纳的芬奇镇附近。他在少年时已显露艺术天赋，15岁左右到佛罗" +
		                "伦萨拜师学艺，成长为具有科学素养的画家、雕刻家。并成为军事工程师和建筑师。" +
		                " [1]  1482年应聘到米兰后，在贵族宫廷中进行创作和研究活动，1513年起漂泊于罗" +
		                "马和佛罗伦萨等地。1516年侨居法国，1519年5月2日病逝。" ;
		        // \d表示一个数字
		        Pattern pattern = Pattern.compile("\\d\\d\\d\\d");
		
		        Matcher matcher = pattern.matcher(content);
		
		        while (matcher.find()) {
		            System.out.println(matcher.group(0));
		        }
		    }
		}
		```

	- `find()`方法：

		- `Matcher`对象中有属性`int[] groups`和`int oldLast`，初始值都为`-1`
		- 每次执行该方法，会将`group[0]`设置为目标字符串第一出现的位置，`group[1]`为目标字符串结束的位置+1（即超尾）。在例子中，第一次匹配的为`1452`，则`group[0] = 12`而`group[1] = 16`。
		- `oldLast`设置为`16`，是下一次查找的开始值——我自己写算法题也是这样做的
		- 不断执行`find()`方法，直到`content`匹配完毕

	- `group(int)`方法：

		- 先看其源码：

		- ```java
			    public String group(int group) {
			        if (first < 0)
			            throw new IllegalStateException("No match found");
			        if (group < 0 || group > groupCount())
			            throw new IndexOutOfBoundsException("No group " + group);
			        if ((groups[group*2] == -1) || (groups[group*2+1] == -1))
			            return null;
			        return getSubSequence(groups[group * 2], groups[group * 2 + 1]).toString();
			    }
			```

		- 将上述代码中，正则表达式改为`"(\\d\\d)(\\d\\d)"`

		- 每使用一组小括号，就代表分了一次组。这里分了两组

		- 执行`find()`方法，第一次匹配`1452`时，除了有`group[0] = 12`、`group[1] = 16`。还会记录分组的信息，第一组为`group[2] = 12`、`group[3] = 14`，即`14`出现在`content`的`[12, 14)`位置；而第二组为`group[4] = 14`、`group[4] = 16`，即`16`出现在`content`的`[14, 16)`位置

		- `group(int)`即是根据输入的整数，返回`content`中`group[]`对应位置的字符串，见源码的返回语句



## 基本语法

1. 基本介绍
	- 运用正则表达式，需要了解各种元字符（meta character）的功能，元字符从功能上大致分为：
		- 限定符
		- 选择匹配符
		- 分组、组合和反向引用符
		- 特殊字符
		- 字符匹配符
		- 定位符



2. 转义号`\\`
	- 使用正则表达式去检索某些特殊字符时，需要用转义符号`\\`。
	- 例如，匹配`"abc(sds("`中的`(`时，正则表达式为`\\(`



3. 字符匹配符

	- | 符号  | 含义             | 示例     | 解释                                           |
		| ----- | ---------------- | -------- | ---------------------------------------------- |
		| `[]`  | 可接受的字符列表 | `[efgh]` | 匹配这四个字符中的任意一个                     |
		| `[^]` | 不接收的字符列表 | `[^abc]` | 除这三个字符以外的任意字符，包括数字和特殊符号 |
		| `-`   | 连字符           | `[A-Z]`  | 任意单个大写字母                               |

	- | 符号 | 含义   | 示例 | 解释 | 匹配输入 |
	  | ---- | ------ | ---- | ---- | -------- |
	  | `.`  | 匹配除`\n`以外的任何字符 | `a..b` | 以`a`开头，`b`结尾，中间包括任意两个字符的字符串 | `a3eb`、`a#*b` |
	  | `\\d` | 匹配单个数字，相当于`[0-9]` | `\\d{3}(\\d)?` | 包含3个或4个数字的字符串 | `123`、`4652` |
	  | `\\D` | 匹配单个非数字字符，相当于`[^0-9]` | `\\D(\\d)*` | 单个非数字字符开头，后接任意个数字字符 | `a`、`A465` |
	  | `\\w` | 匹配单个数字、大小写字母和下划线字符，相当于`[0-9a-zA-Z_]` | `\\d{3}\\w{4}` | 以3个数字字符开头，长度为7的数字字母字符串 | `313ab8d` |
	  | `\\W` | `[^0-9a-zA-Z_]` | `\\W+\\d{2}` | 以至少1个非数字字母字符开头，2个数字字符结尾的字符串 | `#29`、`#?*34` |
	  | `\\s` | 匹配任何空白字符（空格、制表符） |  |  |  |
	  | `\\S` | 匹配任何非空白字符 |  |  |  |
	  



4. 字符匹配案例

	- 字符匹配符，表示该类匹配符只能匹配一个字符，而不是多个
	- 正则表达式默认区分大小写，使用以下方法不区分大小写：
		- `(?i)abc`：abc不区分大小写
		- `a(?i)bc`：bc不区分大小写
		- `a((?i)b)c`：只有b不区分大小写
		- `Pattern pattern = Pattern.compile(regex, Pattern.CASE_INSENSITIVE);`



5. 选择匹配符`|`
	- 可以匹配`|`之前或之后的表达式，如`ab|cd`，可以匹配ab或者cd
	- 也可以连续使用多个`|`，如`a|A|啊`，匹配这三个字符之中的任意一个



6. 限定符

	- 用于指定其前面的字符或组合连续出现多少次

	- | 符号    | 含义                   | 示例          | 说明                                         | 匹配输入         |
		| ------- | ---------------------- | ------------- | -------------------------------------------- | ---------------- |
		| `*`     | 字符出现0次或n次       | `(abc)*`      | 匹配包含任意个abc的字符串                    | `abc`、`abcabc`  |
		| `+`     | 字符出现1次或多次      | `m+a*`        | 以至少一个m开头，后接任意个a的字符串         | `m`、`maa`       |
		| `?`     | 字符出现0次或1次       | `m+abc?`      | 以至少一个m开头，后接ab或abc                 | `mmab`、`mabc`   |
		| `{n}`   | 连续n个字符            | `[abc]{3}`    | 在集合`{a, b, c}`中任意选3次组成的字符串     | `aaa`、`abc`     |
		| `{n,}`  | 至少连续出现n个字符    | `[abc]{3,}`   | 在集合`{a, b, c}`中任意选至少3次组成的字符串 | `abc`、`aabcabc` |
		| `{n,m}` | 连续出现`[n, m]`个字符 | `[abc]{3, 5}` | 在集合`{a, b, c}`中任意选3至5次组成的字符串  | `abc`、`aaabc`   |



7. 限定符案例
	- 使用`a{4}`匹配`"aaaaaa"`，只会有一次结果——`find()`方法会将`oldLast`设置为本次匹配到的字符串的超尾的索引
	- java中的限定符匹配是贪婪匹配——匹配尽可能多的字符。对于`aaaaaa`，`a{3,6}`会匹配一次，返回6个a，`a*`也会匹配一次，结果为6个a
	- 如果要使用非贪婪匹配——每次匹配尽可能少的字符，在限定符后面加上`?`即可。对于`aaaaaa`，`a+?`会匹配6次，每次匹配1个a



8. 定位符
	- 规定要匹配的字符串在`content`中出现的位置
	- :one:`^`：指定起始字符。如`^\\d+[a-z]*`，以至少1个数字开头（`content`的开头），后接任意个小写字母，能匹配`123`、`4dbbd`、不能匹配`bn 12ac`
	- :two:`$`：指定结束字符。如`\\d+$`，以至少1个数字结尾（`content`的结尾），能匹配`112`，不能匹配`11aa`、`112 11a`
	- :three:`\\b`：匹配位于边界的目标字符串。边界是指空格和字符串开头结尾，如`app\\b`，能够匹配`application app 2app`中的后两个`app`。`\\bhan`则能匹配前两个`app`
	- :four:`\\B`：匹配不位于边界的目标字符串。如`app\\B`，能够匹配`application app 2app`中第一个`app`。



9. 捕获匹配
	- :one:非命名捕获：`(pattern)`，匹配捕获的子字符串。编号为0的第一个捕获是由整个正则表达式匹配的文本，其它捕获结果则根据左括号的顺序从1开始自动编号。如匹配四个连续数字，`(\\d\\d)(\\d)\\d`，匹配到了`6789`，`group(0)`返回`6789`，`group(1)`返回`67`，`group(2)`返回`8`
	- :two:命名捕获：`(?<组名>pattern)`，可以使用`group(组名)`的形式获取某一组。组名不能包含任何标点符号，且不能以数字开头。还是匹配四个连续数字，`(?<n1>\\d\\d)(?<n2>\\d)\\d`，除了使用`group(int)`访问各组，可以用`group("n1")`访问第一组





10. 非捕获匹配
	- 非捕获：尽管语法中有括号`()`，但不捕获该组，即无法使用`group(1)`获取
	- 以`content = "寧々先生　寧々さん　寧々ちゃん"`为例
	- :one:`(?:pattern)`：经常与选择匹配符`|`搭配使用。如，`寧々(?:先生|さん)`等效于`寧々先生|寧々さん`，但前者更为经济
	- :two:`(?=pattern)`：`寧々(?=先生|さん)`将匹配`寧々先生`和`寧々さん`中的`寧々`
	- :three:`(?!pattern)`，用法与:two:相反，`寧々(?!先生|さん)`将不会匹配`寧々先生`和`寧々さん`中的`寧々`，而只匹配`寧々ちゃん`中的`寧々`



11. 应用
	1. 匹配汉字：`^[\u4e00-\u9fa5]+$`，即汉字的编码范围
	2. 检验邮政编码：以1-9开头的六位数：`^[1-9]\\d{5}$`
	3. 检验手机号码：以13、14、15、18开头的11位数：`^1[3458]\\d{9}$`
	4. 验证URL：以`https://www.bilibili.com/video/BV1fh411y7R8?p=894&spm_id_from=pageDriver`为例
		- 将URL分界为以下几部分：
		- 协议`https://`部分：`^((http|https)://)?`。有些URL没有这部分，例如GitHub，所以用`?`
		- `www.bilibili.com`部分：(数字字母组合 + `.`）为一组，有可能有多组，最后一部分只是数字字母组合：`([\\w-]+\\.)+\\w+`。有些URL中也会有`-`字符
		- `/video/BV1fh411`部分（可有可无）：`(/[\\w-?=/&.#]+)?`，这一部分会有一堆特殊字符
		- 故，验证URL的正则表达式为`^((http|https)://)?([\\w-]+\\.)+\\w+(/[\\w-?=/&.#]+)?$`





## 常用类

1. `Pattern`类
	- 该类没有公共构造方法，通过调用其静态方法`complie(String regex)`返回`Pattern`对象



2. `Pattern`类常用方法
	- `Matcher matcher(String content)`：返回一个`Matcher`对象
	- `boolean matches(String regex, String content)`：查看正则表达式是否**整体**匹配`content`，相当于`^表达式$`





3. `Matcher`类
	- 该类没有公共构造方法。通过使用`Pattern`对象的`matcher()`方法来获得一个`Matcher`对象——它是对输入字符串进行解释和匹配的引擎



4. `Matcher`类常用方法
	- `int start()`：返回匹配到的字符串的首位在`content`中的索引
	- `int end()`：返回匹配到的字符串的超尾在`content`中的索引
	- `boolean matches()`：正则表达式是否与`content`匹配
	- `String replaceAll(String s)`：将`content`中所有匹配到的字符串替换为`s`



5. `PatternSyntaxException`类
	- 一个运行异常类，表示正则表达式中的语法错误



## 分组、捕获、反向引用

1. 分组
	- 我们可以用圆括号组成一个比较复杂的匹配模式，一个圆括号部分可以看做是一个子表达式/一个分组



2. 捕获
	- 把正则表达式中分组匹配到的内容，保存到以数字编号命名或显式命名的组中，方便之后引用。从左向右，以分组的左括号为标志，第一个出现的分组租号为1，一次类推。0号代表整个匹配到的内容



3. 反向引用
	- 圆括号的内容被捕获后，可以在这个括号后被使用——这称为反向引用——从而写出一个比较实用的匹配模式。这种引用可以在正则表达式内部（`\\分组号`），也可以在外部（`$分组号`）



4. 反向引用案例
	- 匹配5个连续的相同数字：`(\\d)\\1{4}`
	- 匹配形如xyyx的数字：`(\\d)(\\d)\\2\\1`



5. 结巴去重

	- 把“我...我要...吃吃吃...饭”修改为“我要吃饭”

	- ```java
		import java.util.regex.Pattern;
		
		public class Test2 {
		    public static void main(String[] args) {
		        String content = "我...我要...吃吃吃...饭";
		        System.out.println(content);
		        Pattern pattern = Pattern.compile("\\.");
		        //将content中的.去除——替换为空字符串
		        content = pattern.matcher(content).replaceAll("");
		        System.out.println(content);
		
		        pattern = Pattern.compile("(.)\\1+");//字符至少重复一次
		        content = pattern.matcher(content).replaceAll("$1");//外部的反向引用
		        System.out.println(content);
		    }
		}
		```



6. `String`类方法使用正则表达式
	- [之前](#`String`类)学的`String`类部分方法其实都可以用正则表达式，这样就没必要专门创建`Pattern`和`Matcher`对象了。虽然这些方法的底层还是使用这两个类
	- ![image-20220412155157992](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204121551318.png)
	- ![image-20220412155313711](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204121553914.png)









# EOF，文件末尾

[返回顶部](#序言)
