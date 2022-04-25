[前往底部](#EOF)



# 序言

- 参考的教程是这个的Java 8 部分：https://www.bilibili.com/video/BV1Kb411W75N
- 学习开始时间为2022年4月23日
- 这部分是在学习完韩顺平的java基础（笔记在[这里](https://github.com/el-nino2020/note-of-learning/blob/main/java%E5%9F%BA%E7%A1%80%EF%BC%88%E9%9F%A9%E9%A1%BA%E5%B9%B3%EF%BC%89%E7%AC%94%E8%AE%B0.md)）后开始学习的，内容为Java 8的新特性，因而内容不会很长

# 目录

[toc]

# Lambda表达式

1. Lambda与匿名内部类相似：

	- ```java
		import java.util.Comparator;
		
		class Test {
		    public static void main(String[] args) {
		        //一个匿名内部类
		        Comparator<Integer> comp1 = new Comparator<Integer>() {
		            @Override
		            public int compare(Integer o1, Integer o2) {
		                return o1 - o2;
		            }
		        };
		
		        System.out.println(comp1.compare(1, 3));
				//Lambda表达式
		        Comparator<Integer> comp2 = (o1, o2) -> {
		            return o1 - o2;
		        };
		
		        System.out.println(comp2.compare(6, 1));
		        
		    }}
		```



2. 介绍
	- `->`：Lambda操作符，或箭头操作符
	- `->`左边：Lambda形参列表，即接口的抽象方法的形参列表
	- `->`右边：`Lambda`体，即接口的抽象方法的方法体
	- Lambda本质是一个[函数式接口](#函数式接口)的**对象**，就和匿名内部类的对象一样



3. 语法

	1. 无参，无返回值

		- ```java
			class Test {
			    public static void main(String[] args) {
			        Runnable r1 = new Runnable() {
			            @Override
			            public void run() {
			                System.out.println("hello");
			            }
			        };
			        r1.run();
			
			        Runnable r2 = () -> {
			            System.out.println("こんにちは");
			        };
			        r2.run();
			    }}
			```

	2. 一个参数，无返回值

		- ```java
			class Test {
			    public static void main(String[] args) {
			        A<String> a1 = new A<String>() {
			            @Override
			            public void say(String s) {
			                System.out.println(s);
			            }
			        };
			        a1.say("123");
			
			        A<String> a2 = (String s) -> {
			            System.out.println(s + "456");
			        };
			        a2.say("123");
			    }
			}
			
			interface A<T> {
			    void say(T t);
			}
			```

	3. 形参的类型可以省略，由编译器自动推断

		- ```java
			class Test {
			    public static void main(String[] args) {
			        A<String> a2 = (s) -> {
			            System.out.println(s + "456");
			        };
			        a2.say("123");
			        //自动类型推断和泛型无关，是编译器自动推断方法的参数类型
			        B b1 = (s) -> {
			            System.out.println(s + "123");
			        };
			        b1.say("nihao");
			    }
			}
			
			interface A<T> {
			    void say(T t);
			}
			
			interface B {
			    void say(String s);
			}
			```

	4. 如果只有一个形参，则`()`可以省略

		- ```java
			class Test {
			    public static void main(String[] args) {
			        A<String> a2 = s -> {
			            System.out.println(s + "456");
			        };
			        a2.say("123");
			    }}
			
			interface A<T> {
			    void say(T t);
			}
			```

	5. 有多个形参，方法体有多条语句，有返回值

		- ```java
			import sun.plugin.com.event.COMEventHandler;
			
			import java.util.Comparator;
			
			class Test {
			    public static void main(String[] args) {
			        //匿名内部类
			        Comparator<Integer> comp1 = new Comparator<Integer>() {
			            @Override
			            public int compare(Integer o1, Integer o2) {
			                return o1.compareTo(o2);
			            }
			        };
			        System.out.println(comp1.compare(1, 2));
			
			        //省略形参类型——自动推断
			        Comparator<Integer> comp2 = (o1, o2) -> {
			            System.out.println(o1);
			            System.out.println(o2);
			            return o1.compareTo(o2);
			        };
			        System.out.println(comp2.compare(3, 2));
			    }}
			```

	6. Lambda体中只有一条语句时，大括号`{}`和`return`（如果有）都可以省略

		- ```java
			import java.util.Comparator;
			
			class Test {
			    public static void main(String[] args) {
			        Comparator<Integer> comp2 = (o1, o2) -> o1.compareTo(o2);
			        System.out.println(comp2.compare(3, 2));
			    }}
			```



4. 总结
	- Lambda形参列表：可以省略形参类型。如果只有一个形参，可以省略`()`
	- Lambda体：应使用`{}`包裹。如果只有一条语句，可以省略`{}`和`return`（如果有）
	- 出于精简代码的目的，Lambda表达式应尽可能简洁（代码能省就省）
	- Lambda只能生成[函数式接口](#函数式接口)的实例，其他接口不行





# 一、函数式接口

1. 基本介绍

	- **只包含一个抽象方法的接口**，称为函数式接口

	- 可以在一个接口上使用`@FunctionalInterface`注解，已检验它是否为一个函数式接口

	- 自定义函数式接口：

	  - ```java
	    @FunctionalInterface
	    interface B {
	      void say(String s);
	    }
	    ```

	- 内置的一些函数式接口声明：

	  - ```java
	    @FunctionalInterface
	    public interface Runnable {
	    ```

	- 在`java.util.function`中定义了Java 7中丰富的函数式接口



2. Java内置函数式接口

	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204240921463.png" alt="image-20220424092124231" style="zoom:50%;" />

	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204240921824.png" alt="image-20220424092139550" style="zoom:50%;" />

	- 这些函数式接口定义了方法的参数类型和返回类型，实现由程序员自己决定。再次体现了通用API的好处

	- 例子：

	- ```java
		import java.util.ArrayList;
		import java.util.List;
		import java.util.function.Predicate;
		
		class Test {
		    public static void main(String[] args) {
		        ArrayList<String> list = new ArrayList<>();
		        list.add("apple");list.add("banana");
		        list.add("orange");list.add("melon");
		        List<String> ans = filter(list, s -> s.contains("o"));
		        System.out.println(ans);
		    }
		
		    public static List<String> filter(List<String> strings, Predicate<String> predicate) {
		        ArrayList<String> ans = new ArrayList<>();
		        for (String s : strings) {
		            if (predicate.test(s)) {
		                ans.add(s);
		            }
		        }
		
		        return ans;
		    }
		}
		```



# 二、方法引用与构造器引用



## 方法引用 method reference

1. 基本介绍
	- 当要传递给Lambda体的操作（即要实现的抽象方法）已经有实现的方法时，可以使用方法引用
	- 条件：现有的方法的**形参类型和返回类型**需要和抽象方法的形参类型和返回类型**一致**
	- 格式：`类名::方法名`或`对象名::方法名`
	- 方法引用有如下三种形式
		- `对象名::普通方法名`
		- `类名::静态方法名`
		- `类名::普通方法名`



2. `对象名::普通方法名`

	- ```java
		import java.io.PrintStream;
		import java.util.function.Consumer;
		
		class Test {
		    public static void main(String[] args) {
		        //不使用方法引用
		        Consumer<Object> con = o -> System.out.println(o);
		        con.accept("lilith");
		
		        /*
		        Consumer<T> void accept(T)，该抽象方法待实现
		        PrintStream void println(T)
		        两者的形参和返回类型相同
		        引用println这个已经实现的方法来实现accept方法
		        */
		        //取得PrintStream对象
		        PrintStream ps = System.out;
		        //对象名::普通方法名
		        Consumer<Object> consumer = ps::println;
		
		        consumer.accept(123.45);
		        consumer.accept("arthur");
		    }}
		```



3. `类名::静态方法名`

	- ```java
		import java.util.function.Function;
		
		class Test {
		    public static void main(String[] args) {
		        //不使用方法引用
		        Function<Double, Long> function = d -> Math.round(d);
		        System.out.println(function.apply(3.6));
		
		        /*
		        Function<T,R> R apply(T)，该抽象方法待实现
		        Math long round(double)
		        两者的形参和返回类型可以相同
		        引用Math.round这个已经实现的静态方法来实现apply方法
		        */
		
		        //类名::静态方法名
		        Function<Double, Long> func = Math::round;
		        System.out.println(func.apply(4.5));
		        System.out.println(func.apply(4.4));
		    }}
		```



4. `类名::普通方法名`

	- 这一种情况允许抽象方法与实现的方法的形参列表有略微不同

	- 格式：假如抽象方法为`T fun(R, S)`，类名为`A`，普通方法为`String f1(int)`，那么`fun<A, int, String> = A::f1`，即抽象方法的第一个形参用来接收`A`类的对象

	- ```java
		import java.awt.*;
		import java.util.function.BiFunction;
		import java.util.function.Function;
		
		class Test {
		    public static void main(String[] args) {
		       /*
		        Function<T,R> R apply(T)，该抽象方法待实现
		        Point         double getX()
		        */
		        //类名::普通方法名
		        Function<Point, Double> supplier = Point::getX;
		        Point point = new Point(1, 2);
		        System.out.println(supplier.apply(point));
		
		        /*
		        BiFunction<T,R,U>      U apply(T, R)，该抽象方法待实现
		        String           boolean equals(String)
		        */
		        //类名::普通方法名
		        BiFunction<String, String, Boolean> biFunction = String::equals;
		        System.out.println(biFunction.apply("abc", "abc"));
		        System.out.println(biFunction.apply("abc", "abd"));
		    }}
		```



## 构造器引用

1. 语法：
	- 构造器引用与方法引用类似，构造器引用的返回类型为本类，形参列表为构造器的形参列表
	- 格式：`类名::new`



2. 例子：

	- ```java
		import java.util.function.BiFunction;
		import java.util.function.Function;
		import java.util.function.Supplier;
		
		public class Test {
		
		    @org.junit.Test
		    public void test1() {
		        //无参构造器
		        //Lambda
		        Supplier<Cat> sup1 = () -> new Cat();
		        System.out.println(sup1.get());
		        //构造器引用
		        Supplier<Cat> sup2 = Cat::new;
		        System.out.println(sup2.get());
		
		    }
		
		    @org.junit.Test
		    public void test2() {
		        //一个参数的构造器
		        //Lambda
		        Function<String, Cat> sup1 = s -> new Cat(s);
		        System.out.println(sup1.apply("李东风"));
		        //构造器引用
		        Function<String, Cat> sup2 = Cat::new;
		        System.out.println(sup2.apply("臭卷宝"));
		    }
		
		    @org.junit.Test
		    public void test3() {
		        //两个参数的构造器
		        //Lambda
		        BiFunction<String, Double, Cat> sup1 = (s, d) -> new Cat(s, d);
		        System.out.println(sup1.apply("李东风", 2.0));
		        //构造器引用
		        BiFunction<String, Double, Cat> sup2 = Cat::new;
		        System.out.println(sup2.apply("臭卷宝", 3.5));
		    }
		}
		
		class Cat {
		    private String name;
		    private double age;
		
		    public Cat() {
		    }
		
		    public Cat(String name) {
		        this.name = name;
		    }
		
		    public Cat(String name, double age) {
		        this.name = name;
		        this.age = age;
		    }
		
		    @Override
		    public String toString() {
		        return "Cat{" + "name='" + name + '\'' + ", age=" + age + '}' + hashCode();
		    }
		}
		```



3. 数组引用

	- 数组引用与构造器引用类似

	- ```java
		import java.util.Arrays;
		import java.util.function.Function;
		
		public class Test {
		    public static void main(String[] args) {
		        //Lambda表达式,
		        Function<Integer, String[]> fun1 = length -> new String[length];
		        System.out.println(Arrays.toString(fun1.apply(2)));
		        //数组引用
		        Function<Integer, String[]> fun2 = String[]::new;
		        System.out.println(Arrays.toString(fun2.apply(3)));
		    }}
		```



# 三、Stream API

## 基本介绍

1. 引入
	- `java.util.stream`是Java 8中处理集合的API，可以对集合进行非常复杂的查找、过滤和映射数据的操作。使用Stream API对集合数据进行操作，类似于使用SQL执行数据库查询
	- 实际开发中，数据源多为MySQL、Oracle等数据库。Java使用JDBC向数据库获取满足一定条件（`[where 条件]`）的数据。而现在有了MongDB，radis等NoSQL的数据源，这些数据就需要Java进行处理，而不是由数据源自身处理
	- `Stream`和`Collection`的区别：
		- `Collection`是一种静态的内存数据结构，是面向内存的
		- `Stream`是有关计算的，是面向CPU的



2. `Stream`的三个步骤
	- ![image-20220424125200879](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204241252063.png)
	- :one:创建`Stream`：从一个数据源（如集合、数组中）获取一个流
	- :two:中间操作：一系列对数据源的数据进行的处理
	- :three:终止操作：执行终止操作，才会执行中间操作链，并产生结果。之后，该流不能再被使用

3. 注意事项
	- `Stream`自身不会存储元素
	- `Stream`不会改变源对象，而是会返回一个持有结果的新`Stream`
	- `Stream`操作是延迟执行的：只有执行了终止操作，一系列中间操作才会被执行



## 创建`Stream`

1. 通过集合创建`Stream`

	- 使用`Collection`接口的两个方法：

		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204241326156.png" alt="image-20220424132612588" style="zoom: 80%;" />

	- ```java
		ArrayList<String> list = new ArrayList<>();
		list.add("arthur");
		list.add("rose");
		list.add("mary");
		//一个顺序流
		Stream<String> stream = list.stream();
		//一个并行流
		Stream<String> parallelStream = list.parallelStream();
		```



2. 通过数组创建`Stream`

	- 使用`Arrays`的静态方法：

		- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204241331765.png" alt="image-20220424133110673" style="zoom:50%;" />

	- ```java
		String[] strings = {"arthur", "rose", "mary"};
		Stream<String> s1 = Arrays.stream(strings);
		
		int[] ints = {1, 3, 4, 5, 6};
		IntStream s2 = Arrays.stream(ints);	
		```



3. 使用`Stream`类的静态方法`of()`

	- ![image-20220424133623998](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204241336078.png)

	- ```java
		Stream<Integer> integerStream = Stream.of(1, 2, 3);
		Stream<String> stringStream = Stream.of("jack", "mary");
		```



4. 创建无限流

	- 无限流指数据量是无限的，除非人为地添加限制

	- ![image-20220424134306699](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204241346461.png)

	- ```java
		//Stream<T> iterate(final T seed, final UnaryOperator<T> f)
		//从seed开始不断迭代，这里是不断向流中加入一个正偶数
		Stream<Integer> s1 = Stream.iterate(0, t -> t + 2);
		
		//Stream<T> generate(Supplier<T> s)
		//不断向流中加入s.get()的值，这里是不断加入一个随机数
		Stream<Double> s2 = Stream.generate(Math::random);
		```



## `Stream`中间操作

1. 介绍
	- 多个中间操作可以连接起来形成一个流水线，除非流水线上出发终止操作，否则中间操作不会执行任何处理。在执行终止操作时一次性全部处理中间操作，这称为“惰性求值”



2. 删选与切片

	- ![image-20220424140055074](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204241400223.png)

	- ```java
		
		import java.util.Arrays;
		
		public class Test {
		    public static void main(String[] args) {
		        int[] arr = {4, 5, 6, 8, 10, 17, 20, 1, 1, 1};
		        //filter会保留Predicate方法结果为true的元素，这里是保留奇数
		        //forEach(System.out::println)属于终止操作，这里为了在屏幕上打印，先使用了该操作
		        Arrays.stream(arr).filter(i -> i % 2 != 0).forEach(System.out::println);
		        System.out.println("=================================");
		
		        //Stream在执行终止操作后被关闭，所以每次都需要重新创建Stream
		        //该方法用于去重
		        Arrays.stream(arr).distinct().forEach(System.out::println);
		        System.out.println("=================================");
		
		        //返回集合的前4个元素
		        Arrays.stream(arr).limit(4).forEach(System.out::println);
		        System.out.println("=================================");
		        //丢弃集合的前4个元素
		        Arrays.stream(arr).skip(4).forEach(System.out::println);
		        System.out.println("=================================");
		    }}
		```



3. 映射

	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204241427485.png" alt="image-20220424142720304" style="zoom:50%;" />

	- ```java
		import java.util.Arrays;
		import java.util.List;
		import java.util.stream.Stream;
		
		public class Test {
		    public static void main(String[] args) {
		        List<String> list = Arrays.asList("jack", "mary", "solomon", "eve");//这个方法挺好用的:)
		        //Stream<R> map(Function<? super T, ? extends R> mapper);
		        //将流中每一个元素映射为一个新的元素，两个元素的类型不必一致
		        list.stream().map(s -> s.length()).forEach(System.out::println);
		        System.out.println("=====================================");
		
		        //Stream<R> flatMap(Function<? super T, ? extends Stream<? extends R>> mapper);
		        //mapper的输入类型为? super T，即一个元素
		        // 而返回类型为? extends Stream<? extends R>，即一个流
		        //该方法的作用是将每个元素mapper后产生的多个流合并为一个流
		        Stream<Character> s2 = list.stream().flatMap(Test::S2CS);
		        //与map方法作对比：
		        //Stream<Stream<Character>> streamStream = list.stream().map(Test::S2CS);
		        s2.forEach(System.out::println);
		    }
		
		    public static Stream<Character> S2CS(String s) {
		        return Stream.of(Character.toUpperCase(s.charAt(0)));
		    }
		}
		```



4. 排序

	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204241449458.png" alt="image-20220424144905365" style="zoom:50%;" />

	- ```java
		import java.util.Arrays;
		import java.util.List;
		
		public class Test {
		    public static void main(String[] args) {
		        List<String> list1 = Arrays.asList("jack", "mary", "solomon", "eve");//这个方法挺好用的:)
		        List<Integer> list2 = Arrays.asList(4, 2, 5, -1, 3, 67, -90);
		        //自然排序
		        list2.stream().sorted().forEach(System.out::println);
		        System.out.println("==========================");
		        //定制排序
		        list1.stream().sorted((s1, s2) -> s1.length() - s2.length()).forEach(System.out::println);
		    }}
		```





## `Stream`终止操作

1. 匹配与查找

	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204250800033.png" alt="image-20220425080055895" style="zoom: 50%;" />

	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204250801139.png" alt="image-20220425080151996" style="zoom:50%;" />

	- ```java
		import java.util.Arrays;
		import java.util.List;
		import java.util.Optional;
		
		public class Test {
		    public static void main(String[] args) {
		        List<String> list = Arrays.asList("jack", "eve", "arthur", "lilith");
		
		        //所有元素都满足条件才返回true
		        boolean b1 = list.stream().allMatch(s -> s.length() < 10);
		        System.out.println(b1);
		        //存在元素满足条件就返回true
		        boolean b2 = list.stream().anyMatch(s -> s.startsWith("e"));
		        System.out.println(b2);
		        //所有元素都不满足条件才返回true
		        boolean b3 = list.stream().noneMatch(s -> Character.isUpperCase(s.charAt(0)));
		        System.out.println(b3);
		        //返回流的第一个元素，Optional之后再说
		        Optional<String> first = list.stream().findFirst();
		        System.out.println(first);
		        //元素数量
		        long size = list.stream().count();
		        System.out.println(size);
		        //按照制定规则，返回最大值
		        Optional<String> max = list.stream().max((s1, s2) -> s1.length() - s2.length());
		        System.out.println(max);
		    }}
		```



2. 归约

	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204250839637.png" alt="image-20220425083945489" style="zoom: 50%;" />

	- ```java
		List<Integer> list = Arrays.asList(1, 2, 3, 4, 5, 6);
		//对流中元素求和
		Integer res1 = list.stream().reduce(10, Integer::sum);
		System.out.println(res1);
		Optional<Integer> res2 = list.stream().reduce(Integer::sum);
		System.out.println(res2);
		```





3. 收集

	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204250849897.png" alt="image-20220425084951731" style="zoom:50%;" />

	- `Collector`接口的方法决定了如何对流中的数据进行收集（收集到`List`或`Set`中）

	- `Collectors`实用类提供了很多静态方法，以方便地创建`Collector`实例：

	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204250853560.png" alt="image-20220425085316305" style="zoom:50%;" />

	- ```java
		List<Integer> list = Arrays.asList(1, 2, 3, 4, 5, 6);
		Set<Integer> set = list.stream().map(i -> 4 * i).collect(Collectors.toSet());
		System.out.println(set);
		```



# 四、Optional 类

1. 基本介绍
	- `java.util`包中的`Optional<T>`是一个容器类，它可以保存一个`T`的值，也可以保存一个`null`。使用该类可以避免空指针异常，并且可以简化代码（不用处处判断对象是否为`null`）

2. `Optional`类的常用方法

	- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204250936767.png" alt="image-20220425093607464" style="zoom:50%;" />

	- `of`和`get`方法使用时，应保证对象为空

	- 如果不确定对象是否为空，应使用`ofNullable`和`orElse`方法

	- ```java
		import java.util.Optional;
		
		public class Test {
		    public static void main(String[] args) {
		        System.out.println(getAName2(new A("jack")));
		        System.out.println(getAName2(new A(null)));
		
		    }
		
		    //传统写法
		    public static String getAName1(A a) {
		        //如果A中的属性为另一个类的对象，我们想要访问后者中的属性，那么代码会更复杂
		        if (a != null) {
		            return a.getName();
		        }
		        return null;
		    }
		
		    public static String getAName2(A a) {
		        Optional<A> a1 = Optional.ofNullable(a);
		        A a2 = a1.orElse(new A("a default name"));//a2一定非空
		        return a2.getName();
		    }
		}
		
		class A {
		    private String name;
		
		    public A(String name) {this.name = name;}
		
		    public String getName() {return name; }
		
		    @Override
		    public String toString() { return "A{" + "name='" + name + '\'' + '}'; }
		}
		```



# #EOF

[返回顶部](#目录)

