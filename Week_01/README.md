
# 第一周学习笔记

## 一、训练准备和复杂度分析

### 1、训练环境设置、编码技巧和Code Style

#### 1）工具

- google 
- mac:iTerm2+zsh
- windows:microsoft new terminal
- VSCode；IntelliJ;
- LeetCode plugin(VSCode & InteLLiJ)


### 2）方法
* 自顶向下的编程模式、不纠结细节；

* 先解决主干逻辑；

### 2、时间复杂度和空间复杂度分析

#### 1）时间和空间复杂度

* 分析时间和空间复杂度；

* 用最简洁的时间和空间复杂度完成代码；

#### 2）常见时间复杂度表示(由低到高)

* O(1)：常数复杂度，例如一层循环for(int i=1;i<=n;i++){}
* O(log n)：对数复杂度
* O(n)：线性时间复杂度
* O(n^2)：平方，例如2层for循环
* O(n^3)：立方，例如3层for循环
* O(2^n)：指数，例如费波纳基数列
* o(n!)：阶乘
* 注：只看最高复杂度的运算


## 二、数组、链表、跳表

### 1、数组、链表、跳表的基本实现

* 数组、链表、跳表的原理和实现
* 三者的时间复杂度、空间复杂度
  * linkedList时间复杂度
    * prepend O(1)
    * append O(1)
    * <u>lookup O(n)</u>
    * insert O(1)   ？是否需要先查找
    * delete O(1)
  * Array的时间复杂度
    * prepend O(1)
    * append O(1)
    * <u>lookup O(1)</u>
    * <u>insert O(n)</u>
    * <u>delete O(n)</u>
  * 跳表，Skip 时间复杂度
	* prepend 	O(logn)
	* append 	O(logn)
	* loopup 	O(logn)
	* insert 	O(logn)
	* delete 	O(logn)
* 工程运用：LRU算法或redis算法
* 跳表：升维思想+空间换时间：
  * redis数据结构：有序集类型、字典
  * Redis跳表介绍：https://redisbook.readthedocs.io/en/latest/internal-datastruct/skiplist.html

## 三、栈、队列、优先队列、双端队列

### 1、栈和队列的实现与特性

* Stack 栈
  * 先入后出；添加、删除皆为O(1)，查询O(n)
  * 方法：peek、pop
  * 官方推荐用Deque
  * 源码分析
  * 扩展：实现类
* Queue 队列
  * 先入先出；添加、删除皆为O(1)，查询O(n)
  * 方法：add、remove、element抛异常；offer、poll、peek返回null；
  * 扩展：实现类
* Deque 双端队列(double ended queue)
  * 头和尾都可以出；插入、删除皆是O(1)，查询是O(n)
  * 方法：addFirst、addLast
  * 扩展：实现类
* Priority Queue 优先级队列
  * 插入操作O（1）；取出操作O(logN)按优先级取出
  * 底层数据结构多样，可以是heap、二叉树、Fibonacci堆、红黑树、treap
  * 优先级排序实现Comparator接口
* 作业
  
  * 用 add first 或 add last 这套新的 API 改写 Deque 的代码  
 ```
	Deque<String> deque = new LinkedList<>();
	deque.addFirst("a");
	deque.addFirst("b");
	deque.addFirst("c");

	String first = deque.getFirst();
	System.out.println(first);
	System.out.println(deque);

	while (deque.size() > 0) {
	    System.out.println(deque.removeFirst());
	}

	System.out.println(deque);
```
  
  * 分析 Queue 和 Priority Queue 的源码
  
``` java
    //Queue 接口
    //继承接口Collection：有集合操作方法如size、isEmpty、contains等
    //继承Iterable可以迭代iterator
    public interface Queue<E> extends Collection<E> {
        /**
         * 添加元素到队列
         */
        boolean add(E e);
    
        /**
         * 添加元素到队列，如果满抛异常
         */
        boolean offer(E e);
    
        /**
         * 移除元素
         */
        E remove();
    
        /**
         * 移除队头元素
         */
        E poll();
    
        /**
         * 查看头部元素，如果为空抛出异常
         */
        E element();
    
        /**
         * 查看头部元素，如果为空返回null
         */
        E peek();
    }

```

## 四、学习感想

```
通过7天的学习，不仅在算法上有了一定眼界，更重要的是在学习方法上得到了很大的启发，另外也需要加强自己的意志力，克服困难按老师方法练习、总结。
```

