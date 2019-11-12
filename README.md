# Android-Interview

----------

# Java

## 基础

1. [什么是面向对象（OOP）？](https://github.com/jeanboydev/Android-Interview/blob/master/Java.md#java_1)
2. [什么是多态？实现多态的机制是什么？](https://github.com/jeanboydev/Android-Interview/blob/master/Java.md#java_2)
3. [接口（Interface）与抽象类（Abstract Class）的区别？](https://github.com/jeanboydev/Android-Interview/blob/master/Java.md#java_3)
4. [重写（Override）与重载（Overload）的区别?]  
重写是子类对父类的允许访问的方法的实现过程进行重新编写, 返回值和形参都不能改变。即外壳不变，核心重写！  
重写的好处在于子类可以根据需要，定义特定于自己的行为。 也就是说子类能够根据需要实现父类的方法。  

重载(overloading) 是在一个类里面，方法名字相同，而参数不同。返回类型可以相同也可以不同。   
每个重载的方法（或者构造函数）都必须有一个独一无二的参数类型列表。  
只能重载构造函数  

5. 父类的静态方法能否被子类重写？
不能，无法使用@Override关键字，编译会报错。
但是子类可以重新定义父类的静态方法，并将父类的静态方法屏蔽掉。
   
[6. 静态属性和静态方法是否可以被继承？是否可以被重写？为什么？](https://www.cnblogs.com/mxmbk/articles/5151095.html)
可以被继承，但是不能被重写。
在一个类中，相同姓名的属性，子类的属性隐藏父类的同名属性，即使它们的类型不同。在子类中，不能通过简单的名称来引用父类的属性。属性必须通过父类类来访问。一般而言，我们不推荐使用属性隐藏，因为这样的代码不易阅读。

java中静态属性和静态方法可以被继承，但是没有被重写(overwrite)而是被隐藏.  
1). 静态方法和属性是属于类的，调用的时候直接通过类名.方法名完成对，不需要继承机制即可以调用。
2). 静态属性、静态方法和非静态的属性都可以被继承和隐藏而不能被重写，因此不能实现多态，不能实现父类的引用可以指向不同子类的对象。
3). 如果在子类重写静态方法加上@Override会直接编译报错,不加@Override重写,用谁的对象/类调用就执行方法,静态方法时属于类的;静态属性同上

7. 什么是内部类？内部类、静态内部类、局部内部类和匿名内部类的区别及作用？
8. [== 和 equals() 和 hashCode() 的区别？](https://blog.csdn.net/zai_xia/article/details/81806446)
1.Java对于equals()方法和hashCode()方法的规定
如果两个对象equals()方法相等则它们的hashCode返回值一定要相同，如果两个对象的hashCode返回值相同，但它们的equals()方法不一定相等。
两个对象的hashCode()返回值相等不能判断这两个对象是相等的，但两个对象的hashcode()返回值不相等则可以判定两个对象一定不相等。
2.hashCode()返回值和 == 的关系
若 == 返回true，则两边的对象的hashCode()返回值必须相等，若 == 返回false，则两边对象的hashCode()返回值可能相等，也可能不等，因为Java中对象默认的equals()方法就是用==实现的。而Java对于equals方法和hashCode方法的规定是如果两个对象equals()方法相等，则hashCode值一定会相同，如果两个对象的hashCode值相同，则它们的equals()方法不一定相等。  
   
9. Integer 和 int 之间的区别？  
  1、Integer是int的包装类，int则是java的一种基本数据类型   
  2、Integer变量必须实例化后才能使用，而int变量不需要   
  3、Integer实际是对象的引用，当new一个Integer时，实际上是生成一个指针指向此对象；而int则是直接存储数据值   
  4、Integer的默认值是null，int的默认值是0. 
     
10. String 转换成 Integer 的方式及原理？
integer.parseInt(string str)方法调用Integer内部的 
parseInt(string str,10)方法,默认基数为10，parseInt内部首先 
判断字符串是否包含符号（-或者+），则对相应的negative和limit进行 
赋值，然后再循环字符串，对单个char进行数值计算Character.digit(char ch, int radix) 
在这个方法中，函数肯定进入到0-9字符的判断（相对于string转换到int）， 
否则会抛出异常，数字就是如上面进行拼接然后生成的int类型数值  
   
11. 自动装箱实现原理？类型转换实现原理？
自动装箱时编译器调用valueOf将原始类型值转换成对象，同时自动拆箱时，编译器通过调用类似intValue(),
doubleValue()这类的方法将对象转换成原始类型值。  

12. 对 String 的了解？


13. String 为什么要设计成不可变的？
String是不可变类有以下几个优点
由于String是不可变类，所以在多线程中使用是安全的，我们不需要做任何其他同步操作。
String是不可变的，它的值也不能被改变，所以用来存储数据密码很安全。
因为java字符串是不可变的，可以在java运行时节省大量java堆空间。因为不同的字符串变量可以引用池中的相同的字符串。如果字符串是可变得话，任何一个变量的值改变，就会反射到其他变量，那字符串池也就没有任何意义了。

浅谈一下String, StringBuffer，StringBuilder的区别？

String是不可变类，每当我们对String进行操作的时候，总是会创建新的字符串。操作String很耗资源,所以Java提供了两个工具类来操作String - StringBuffer和StringBuilder。

StringBuffer和StringBuilder是可变类，StringBuffer是线程安全的，StringBuilder则不是线程安全的。所以在多线程对同一个字符串操作的时候，我们应该选择用StringBuffer。由于不需要处理多线程的情况，StringBuilder的效率比StringBuffer高。

14. [final、finally 和 finalize 的区别？](https://github.com/jeanboydev/Android-Interview/blob/master/Java.md#java_14)
15. [static 关键字有什么作用？](https://github.com/jeanboydev/Android-Interview/blob/master/Java.md#java_15)
16. 列举 Java 的集合以及集合之间的继承关系?
Collection {
  List {
    ArrayList,LinkedList,Vector,Stack
  }  
  Set {
    HashSet,TreeSet,LinkedHashSet
  }   
}  
Map {
  HashMap, LinkedHashMap,ConcurrentHashMap,HashTable,TreeMap
}  
    
17. List、Set、Map 的区别？
https://images.gitbook.cn/6e7001c0-3be3-11e9-af57-196eefd310b5
18. [ArrayList、LinkedList 的区别？](https://github.com/jeanboydev/Android-Interview/blob/master/Java.md#java_18)
19. HashMap，HashTable，ConcurrentHashMap 实现原理以及区别？
20. HashSet 与 HashMap 怎么判断集合元素重复？
21. String、StringBuffer、StringBuilder 之间的区别？
22. [什么是序列化？怎么实现？有哪些方式？](https://github.com/jeanboydev/Android-Interview/blob/master/Java.md#java_22)
23. 对反射的了解？
JAVA反射机制是在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意方法和属性；这种动态获取信息以及动态调用对象方法的功能称为java语言的反射机制。
24. 对注解的了解？
25. 对依赖注入的了解？
26. 对泛型的了解？
27. 泛型中 extends 和 super 的区别？
28. 对 Java 的异常体系的了解？
29. 对解析与分派的了解？
30. [静态代理和动态代理的区别？有什么场景使用？](https://www.cnblogs.com/gonjan-blog/p/6685611.html)
代理模式是常用的java设计模式，他的特征是代理类与委托类有同样的接口，代理类主要负责为委托类预处理消息、过滤消息、把消息转发给委托类，以及事后处理消息等。  
动态代理的优势在于可以很方便的对代理类的函数进行统一的处理，而不用修改每个代理类中的方法。是因为所有被代理执行的方法，都是通过在InvocationHandler中的invoke方法调用的，所以我们只要在invoke方法中统一处理，就可以对所有被代理的方法进行相同的操作了。
   
31. [谈谈对 Java 状态机理解?](https://www.cnblogs.com/pony1223/p/7518226.html)
  
## 线程与并发
  
1. 线程和进程的区别？
  1，进程是资源管理的最小单位，线程是程序执行的最小单位
  2，线程比进程花费更小的CPU资源
  3，线程和进程的关系是 线程属于进程，线程运行在进程空间内
   
2. 开启线程的三种方式  
   1) new Thread().start();  
   2) class MyRunnable immplement Runnable{}  
      new Thread(new MyRunnable).start();  
   3) hanlder.post(new Runnable() {});  
   
3. 如何正确的结束一个Thread?  
	设置结束标志位，再调用thread.interrupt();  
   
4. Thread 与 Runnable 的区别？   
	runnable只是一个接口而已，不会开启一个线程；而thread是一个线程，实现了Runnable接口，通过传入一个runnable实例可以在线程中启动。   
   
5. run() 与 start() 方法的区别？   
	start : 用start方法来启动线程，真正实现了多线程运行，这时无需等待run方法体代码执行完毕而直接继续执行下面的代码。通过调用Thread类的start()方法来启动一个线程，这时此线程处于就绪（可运行）状态，并没有运行，一旦得到cpu时间片，就开始执行run()方法，这里方法 run()称为线程体，它包含了要执行的这个线程的内容，Run方法运行结束，此线程随即终止。   
	run : run()方法只是类的一个普通方法而已，如果直接调用Run方法，程序中依然只有主线程这一个线程，其程序执行路径还是只有一条，还是要顺序执行，还是要等待run方法体执行完毕后才可继续执行下面的代码，这样就没有达到写线程的目的。  
     
6. sleep() 与 wait() 方法的区别？      
	1、这两个方法来自不同的类，sleep来自Thread类，wait 来自Object类。    
	2、最主要是sleep方法没有释放锁，而wait方法释放了锁，使其他线程可以使用同步控制块或者方法。sleep不出让系统资源；wait是进入线程等待池等待，出让系统资源，其他线程可以占用CPU。   
	3、使用范围：wait，notify和notifyAll只能在同步控制方法或者同步控制块里面使用，而sleep可以在任何地方使用  
	4、sleep必须捕获异常，而wait，notify和notifyAll不需要捕获异常。   
   
7. wait 与 notify 关键字的区别？    
   wait会让线程进入等待状态，释放cpu；notify调用后，获取到对象状态锁的代码库会继续执行wait后的代码。
      
8. synchronized 关键字的用法、作用及实现原理？   
	synchronized关键字最主要有以下3种应用方式   
	修饰实例方法,对当前实例加锁，进入同步代码前要获得当前实例的锁   
	修饰静态方法,对当前类对象(当前类的Class对象)加锁，进入同步代码前要获得当前类对象的锁    
	修饰代码块,对代码块{}中的内容加锁，进入同步代码块前要获得给定对象的锁。   
	
	Synchronized 的主要作用：
	1.确保线程互斥的访问同步代码。
	2.保证共享变量的修改能够及时可见。
	3.有效解决重拍排序问题.
   
   
9. (volatile 关键字的用法、作用及实现原理?)[https://www.bookstack.cn/read/interview/java-volatile.md]
	计算机内存模型

计算机在执行程序时，每条指令都是在CPU中执行的，而执行指令过程中，势必涉及到数据的读取和写入。由于程序运行过程中的临时数据是存放在主存（物理内存）当中的，这时就存在一个问题，由于CPU执行速度很快，而从内存读取数据和向内存写入数据的过程跟CPU执行指令的速度比起来要慢的多，因此如果任何时候对数据的操作都要通过和内存的交互来进行，会大大降低指令执行的速度。因此在CPU里面就有了高速缓存。当程序在运行过程中，会将运算需要的数据从主存复制一份到CPU的高速缓存当中，那么CPU进行计算时就可以直接从它的高速缓存读取数据和向其中写入数据，当运算结束之后，再将高速缓存中的数据刷新到主存当中。举个简单的例子，比如下面的这段代码：

i = i + 1;
当线程执行这个语句时，会先从主存当中读取i的值，然后复制一份到高速缓存当中，然后 CPU 执行指令对i进行加1操作，然后将数据写入高速缓存，最后将高速缓存中i最新的值刷新到主存当中。
这个代码在单线程中运行是没有任何问题的，但是在多线程中运行就会有问题了。在多核 CPU 中，每条线程可能运行于不同的 CPU 中，因此 每个线程运行时有自己的高速缓存（对单核CPU来说，其实也会出现这种问题，只不过是以线程调度的形式来分别执行的）。比如同时有两个线程执行这段代码，假如初始时i的值为0，那么我们希望两个线程执行完之后i的值变为2。但是事实会是这样吗？

可能出现这种情况：初始时，两个线程分别读取i的值存入各自所在的 CPU 的高速缓存当中，然后 线程1 进行加1操作，然后把i的最新值1写入到内存。此时线程2的高速缓存当中i的值还是0，进行加1操作之后，i的值为1，然后线程2把i的值写入内存。最终结果i的值是1，而不是2。这就是著名的缓存一致性问题。通常称这种被多个线程访问的变量为共享变量。

为了解决缓存不一致性问题，通常来说有以下两种解决方法：

通过在总线加LOCK#锁的方式
通过 缓存一致性协议
这两种方式都是硬件层面上提供的方式。
在早期的 CPU 当中，是通过在总线上加LOCK#锁的形式来解决缓存不一致的问题。因为 CPU 和其他部件进行通信都是通过总线来进行的，如果对总线加LOCK#锁的话，也就是说阻塞了其他 CPU 对其他部件访问（如内存），从而使得只能有一个 CPU 能使用这个变量的内存。比如上面例子中 如果一个线程在执行 i = i +1，如果在执行这段代码的过程中，在总线上发出了LCOK#锁的信号，那么只有等待这段代码完全执行完毕之后，其他CPU才能从变量i所在的内存读取变量，然后进行相应的操作。这样就解决了缓存不一致的问题。但是上面的方式会有一个问题，由于在锁住总线期间，其他CPU无法访问内存，导致效率低下。

所以就出现了缓存一致性协议。最出名的就是 Intel 的MESI协议，MESI协议保证了每个缓存中使用的共享变量的副本是一致的。它核心的思想是：当CPU写数据时，如果发现操作的变量是共享变量，即在其他CPU中也存在该变量的副本，会发出信号通知其他CPU将该变量的缓存行置为无效状态，因此当其他CPU需要读取这个变量时，发现自己缓存中缓存该变量的缓存行是无效的，那么它就会从内存重新读取。

Volatile原理 - 图1

　Java内存模型

在Java虚拟机规范中试图定义一种Java内存模型（Java Memory Model，JMM）来屏蔽各个硬件平台和操作系统的内存访问差异，以实现让Java程序在各种平台下都能达到一致的内存访问效果。那么Java内存模型规定了程序中变量的访问规则，往大一点说是定义了程序执行的次序。注意，为了获得较好的执行性能，Java内存模型并没有限制执行引擎使用处理器的寄存器或者高速缓存来提升指令执行速度，也没有限制编译器对指令进行重排序。也就是说，在java内存模型中，也会存在缓存一致性问题和指令重排序的问题。

Java内存模型规定所有的变量都是存在主存当中（类似于前面说的物理内存），每个线程都有自己的工作内存（类似于前面的高速缓存）。线程对变量的所有操作都必须在工作内存中进行，而不能直接对主存进行操作。并且每个线程不能访问其他线程的工作内存。

在Java中，执行下面这个语句：

i  = 10;
执行线程必须先在自己的工作线程中对变量i所在的缓存行进行赋值操作，然后再写入主存当中。而不是直接将数值10写入主存当中。那么Java语言本身对 原子性、可见性以及有序性提供了哪些保证呢？

原子性

即一个操作或者多个操作 要么全部执行并且执行的过程不会被任何因素打断，要么就都不执行。
在Java中，对基本数据类型的变量的读取和赋值操作是原子性操作，即这些操作是不可被中断的，要么执行，要么不执行。上面一句话虽然看起来简单，但是理解起来并不是那么容易。看下面一个例子i：请分析以下哪些操作是原子性操作：

x = 10;        //语句1
y = x;         //语句2
x++;           //语句3
x = x + 1;     //语句4
咋一看，有些朋友可能会说上面的4个语句中的操作都是原子性操作。其实只有语句1是原子性操作，其他三个语句都不是原子性操作。

语句1是直接将数值10赋值给x，也就是说线程执行这个语句的会直接将数值10写入到工作内存中。
语句2实际上包含2个操作，它先要去读取x的值，再将x的值写入工作内存，虽然读取x的值以及 将x的值写入工作内存 这2个操作都是原子性操作，但是合起来就不是原子性操作了。
同样的，x++和 x = x+1包括3个操作：读取x的值，进行加1操作，写入新的值。
也就是说，只有简单的读取、赋值（而且必须是将数字赋值给某个变量，变量之间的相互赋值不是原子操作）才是原子操作。不过这里有一点需要注意：在32位平台下，对64位数据的读取和赋值是需要通过两个操作来完成的，不能保证其原子性。但是好像在最新的JDK中，JVM已经保证对64位数据的读取和赋值也是原子性操作了。

从上面可以看出，Java内存模型只保证了基本读取和赋值是原子性操作，如果要实现更大范围操作的原子性，可以通过synchronized和Lock来实现。由于synchronized和Lock能够保证任一时刻只有一个线程执行该代码块，那么自然就不存在原子性问题了，从而保证了原子性。

可见性

可见性是指当多个线程访问同一个变量时，一个线程修改了这个变量的值，其他线程能够立即看得到修改的值。
对于可见性，Java提供了volatile关键字来保证可见性。当一个共享变量被volatile修饰时，它会保证修改的值会立即被更新到主存，当有其他线程需要读取时，它会去内存中读取新值。而普通的共享变量不能保证可见性，因为普通共享变量被修改之后，什么时候被写入主存是不确定的，当其他线程去读取时，此时内存中可能还是原来的旧值，因此无法保证可见性。

另外，通过synchronized和Lock也能够保证可见性，synchronized和Lock能保证同一时刻只有一个线程获取锁然后执行同步代码，并且在释放锁之前会将对变量的修改刷新到主存当中。因此可以保证可见性。

有序性

即程序执行的顺序按照代码的先后顺序执行。

指令重排序，一般来说，处理器为了提高程序运行效率，可能会对输入代码进行优化，它不保证程序中各个语句的执行先后顺序同代码中的顺序一致，但是它会保证程序最终执行结果和代码顺序执行的结果是一致的。
处理器在进行重排序时是会考虑指令之间的数据依赖性，如果一个指令Instruction 2必须用到Instruction 1的结果，那么处理器会保证Instruction 1会在Instruction 2之前执行。

在Java内存模型中，允许编译器和处理器对指令进行重排序，但是重排序过程不会影响到单线程程序的执行，却会影响到多线程并发执行的正确性。

在Java里面，可以通过volatile关键字来保证一定的“有序性”（具体原理在下一节讲述）。另外可以通过synchronized和Lock来保证有序性，很显然，synchronized和Lock保证每个时刻是有一个线程执行同步代码，相当于是让线程顺序执行同步代码，自然就保证了有序性。

另外，Java内存模型具备一些先天的“有序性”，即不需要通过任何手段就能够得到保证的有序性，这个通常也称为 happens-before 原则。如果两个操作的执行次序无法从happens-before原则推导出来，那么它们就不能保证它们的有序性，虚拟机可以随意地对它们进行重排序。

下面就来具体介绍下happens-before原则（先行发生原则）：

程序次序规则：一个线程内，按照代码顺序，书写在前面的操作先行发生于书写在后面的操作
锁定规则：一个unLock操作先行发生于后面对同一个锁额lock操作
volatile变量规则：对一个变量的写操作先行发生于后面对这个变量的读操作
传递规则：如果操作A先行发生于操作B，而操作B又先行发生于操作C，则可以得出操作A先行发生于操作C
线程启动规则：Thread对象的start()方法先行发生于此线程的每个一个动作
线程中断规则：对线程interrupt()方法的调用先行发生于被中断线程的代码检测到中断事件的发生
线程终结规则：线程中所有的操作都先行发生于线程的终止检测，我们可以通过Thread.join()方法结束、Thread.isAlive()的返回值手段检测到线程已经终止执行
对象终结规则：一个对象的初始化完成先行发生于他的finalize()方法的开始
对于程序次序规则来说，我的理解就是一段程序代码的执行在单个线程中看起来是有序的。注意，虽然这条规则中提到“书写在前面的操作先行发生于书写在后面的操作”，这个应该是程序看起来执行的顺序是按照代码顺序执行的，因为虚拟机可能会对程序代码进行指令重排序。虽然进行重排序，但是最终执行的结果是与程序顺序执行的结果一致的，它只会对不存在数据依赖性的指令进行重排序。因此，在单个线程中，程序执行看起来是有序执行的，这一点要注意理解。事实上，这个规则是用来保证程序在单线程中执行结果的正确性，但无法保证程序在多线程中执行的正确性。

第二条规则也比较容易理解，也就是说无论在单线程中还是多线程中，同一个锁如果出于被锁定的状态，那么必须先对锁进行了释放操作，后面才能继续进行lock操作。

第三条规则是一条比较重要的规则，也是后文将要重点讲述的内容。直观地解释就是，如果一个线程先去写一个变量，然后一个线程去进行读取，那么写入操作肯定会先行发生于读操作。

第四条规则实际上就是体现happens-before原则具备传递性。

深入剖析Volatile关键字

Volatile的语义

一旦一个共享变量（类的成员变量、类的静态成员变量）被volatile修饰之后，那么就具备了两层语义：

保证了不同线程对这个变量进行操作时的可见性，即一个线程修改了某个变量的值，这新值对其他线程来说是立即可见的。
　- 禁止进行指令重排序。
先看一段代码，假如线程1先执行，线程2后执行：

//线程1
boolean stop = false;
while(!stop){
    doSomething();
}
//线程2
stop = true;
这段代码是很典型的一段代码，很多人在中断线程时可能都会采用这种标记办法。但是事实上，这段代码会完全运行正确么？即一定会将线程中断么？不一定，也许在大多数时候，这个代码能够把线程中断，但是也有可能会导致无法中断线程（虽然这个可能性很小，但是只要一旦发生这种情况就会造成死循环了）。

下面解释一下这段代码为何有可能导致无法中断线程。在前面已经解释过，每个线程在运行过程中都有自己的工作内存，那么线程1在运行的时候，会将stop变量的值拷贝一份放在自己的工作内存当中。

那么当线程2更改了stop变量的值之后，但是还没来得及写入主存当中，线程2转去做其他事情了，那么线程1由于不知道线程2对stop变量的更改，因此还会一直循环下去。但是用volatile修饰之后就变得不一样了：

　- 使用volatile关键字会强制将修改的值立即写入主存；

使用volatile关键字的话，当线程2进行修改时，会导致线程1的工作内存中缓存变量stop的缓存行无效（反映到硬件层的话，就是CPU的L1或者L2缓存中对应的缓存行无效）；
由于线程1的工作内存中缓存变量stop的缓存行无效，所以线程1再次读取变量stop的值时会去主存读取。
那么在线程2修改stop值时（当然这里包括2个操作，修改线程2工作内存中的值，然后将修改后的值写入内存），会使得线程1的工作内存中缓存变量stop的缓存行无效，然后线程1读取时，发现自己的缓存行无效，它会等待缓存行对应的主存地址被更新之后，然后去对应的主存读取最新的值。
那么线程1读取到的就是最新的正确的值。

Volatile与原子性

从上面知道volatile关键字保证了操作的可见性，但是volatile能保证对变量的操作是原子性吗？

下面看一个例子：

public class Test {
    public volatile int inc = 0;
    public void increase() {
        inc++;
    }
    public static void main(String[] args) {
        final Test test = new Test();
        for(int i=0;i<10;i++){
            new Thread(){
                public void run() {
                    for(int j=0;j<1000;j++)
                        test.increase();
                };
            }.start();
        }
        while(Thread.activeCount()>1)  //保证前面的线程都执行完
            Thread.yield();
        System.out.println(test.inc);
    }
}
大家想一下这段程序的输出结果是多少？也许有些朋友认为是10000。但是事实上运行它会发现每次运行结果都不一致，都是一个小于10000的数字。可能有的朋友就会有疑问，不对啊，上面是对变量inc进行自增操作，由于volatile保证了可见性，那么在每个线程中对inc自增完之后，在其他线程中都能看到修改后的值啊，所以有10个线程分别进行了1000次操作，那么最终inc的值应该是1000*10=10000。

这里面就有一个误区了，volatile关键字能保证可见性没有错，但是上面的程序错在没能保证原子性。可见性只能保证每次读取的是最新的值，但是volatile没办法保证对变量的操作的原子性。

在前面已经提到过，自增操作是不具备原子性的，它包括读取变量的原始值、进行加1操作、写入工作内存。那么就是说自增操作的三个子操作可能会分割开执行，就有可能导致下面这种情况出现：

假如某个时刻变量inc的值为10，
线程1对变量进行自增操作，线程1先读取了变量inc的原始值，然后线程1被阻塞了；
然后线程2对变量进行自增操作，线程2也去读取变量inc的原始值，由于线程1只是对变量inc进行读取操作，而没有对变量进行修改操作，所以不会导致线程2的工作内存中缓存变量inc的缓存行无效，所以线程2会直接去主存读取inc的值，发现inc的值时10，然后进行加1操作，并把11写入工作内存，最后写入主存。
然后线程1接着进行加1操作，由于已经读取了inc的值，注意此时在线程1的工作内存中inc的值仍然为10，所以线程1对inc进行加1操作后inc的值为11，然后将11写入工作内存，最后写入主存。
那么两个线程分别进行了一次自增操作后，inc只增加了1。
解释到这里，可能有朋友会有疑问，不对啊，前面不是保证一个变量在修改volatile变量时，会让缓存行无效吗？然后其他线程去读就会读到新的值，对，这个没错。这个就是上面的happens-before规则中的volatile变量规则，但是要注意，线程1对变量进行读取操作之后，被阻塞了的话，并没有对inc值进行修改。然后虽然volatile能保证线程2对变量inc的值读取是从内存中读取的，但是线程1没有进行修改，所以线程2根本就不会看到修改的值。

根源就在这里，自增操作不是原子性操作，而且volatile也无法保证对变量的任何操作都是原子性的。解决的方法也就是对提供原子性的自增操作即可。

在Java 1.5的java.util.concurrent.atomic包下提供了一些原子操作类，即对基本数据类型的 自增（加1操作），自减（减1操作）、以及加法操作（加一个数），减法操作（减一个数）进行了封装，保证这些操作是原子性操作。atomic是利用CAS来实现原子性操作的（Compare And Swap），CAS实际上是利用处理器提供的CMPXCHG指令实现的，而处理器执行CMPXCHG指令是一个原子性操作。

Volatile与有序性

在前面提到volatile关键字能禁止指令重排序，所以volatile能在一定程度上保证有序性。volatile关键字禁止指令重排序有两层意思：

当程序执行到volatile变量的读操作或者写操作时，在其前面的操作的更改肯定全部已经进行，且结果已经对后面的操作可见，在其后面的操作肯定还没有进行；
在进行指令优化时，不能将在对volatile变量访问的语句放在其后面执行，也不能把volatile变量后面的语句放到其前面执行。
可能上面说的比较绕，举个简单的例子：

//x、y为非volatile变量
//flag为volatile变量
x = 2;        //语句1
y = 0;        //语句2
flag = true;  //语句3
x = 4;         //语句4
y = -1;       //语句5
由于flag变量为volatile变量，那么在进行指令重排序的过程的时候，不会将语句3放到语句1、语句2前面，也不会讲语句3放到语句4、语句5后面。但是要注意语句1和语句2的顺序、语句4和语句5的顺序是不作任何保证的。

并且volatile关键字能保证，执行到语句3时，语句1和语句2必定是执行完毕了的，且语句1和语句2的执行结果对语句3、语句4、语句5是可见的。

Volatile的原理和实现机制

前面讲述了源于volatile关键字的一些使用，下面我们来探讨一下volatile到底如何保证可见性和禁止指令重排序的。下面这段话摘自《深入理解Java虚拟机》：

观察加入volatile关键字和没有加入volatile关键字时所生成的汇编代码发现，加入volatile关键字时，会多出一个lock前缀指令
lock前缀指令实际上相当于一个 内存屏障（也成内存栅栏），内存屏障会提供3个功能：

它 确保指令重排序时不会把其后面的指令排到内存屏障之前的位置，也不会把前面的指令排到内存屏障的后面；即在执行到内存屏障这句指令时，在它前面的操作已经全部完成；
它会 强制将对缓存的修改操作立即写入主存；
如果是写操作，它会导致其他CPU中对应的缓存行无效。   
    
10. transient 关键字的用法、作用及实现原理？ 
	java 的transient关键字为我们提供了便利，你只需要实现Serilizable接口，将不需要序列化的属性前添加关键字transient，序列化对象的时候，这个属性就不会序列化到指定的目的地中。     
    
11. ReentrantLock、synchronized、volatile 之间的区别？     
	synchronized的使用可以保证代码具有 原子性（atomicity）和 可见性（visibility）。     
	volatile则可以保证单次读或写操作的原子性和可见性。 
	ReentrantLock 类实现了 Lock ，它拥有与 synchronized 相同的并发性和内存语义，但是添加了类似锁投票、定时锁等候和可中断锁等候的一些特性。此外，它还提供了在激烈争用情况下更佳的性能。   
	在确实需要一些 synchronized 所没有的特性的时候，比如时间锁等候、可中断锁等候、无块结构锁、多个条件变量或者锁投票。 ReentrantLock 还具有可伸缩性的好处，应当在高度争用的情况下使用它。   
   
12. 什么是线程池，如何使用?   
	线程池就是提前创建若干个线程，如果有任务需要处理，线程池里的线程就会处理任务，处理完之后线程并不会被销毁，而是等待下一个任务。由于创建和销毁线程都是消耗系统资源的，所以当你想要频繁的创建和销毁线程的时候就可以考虑使用线程池来提升系统的性能。    
	Java中有四个比较常用的线程池，分别是FixedThreadPool，SingleThreadExecutor，CachedThreadPool、ScheduledThreadPoolExecutor。    
     
13. 多线程断点续传的实现原理？    
	多线程下载的思想是客户端开启多个线程同时下载,每个线程只负责下载文件的一部分, 当所有线程下载完成的时候,文件下载完毕.    
   
14. 什么是深拷贝和浅拷贝？     
	浅拷贝（Shallow Copy）：①对于数据类型是基本数据类型的成员变量，浅拷贝会直接进行值传递，也就是将该属性值复制一份给新的对象。因为是两份不同的数据，所以对其中一个对象的该成员变量值进行修改，不会影响另一个对象拷贝得到的数据。②对于数据类型是引用数据类型的成员变量，比如说成员变量是某个数组、某个类的对象等，那么浅拷贝会进行引用传递，也就是只是将该成员变量的引用值（内存地址）复制一份给新的对象。因为实际上两个对象的该成员变量都指向同一个实例。在这种情况下，在一个对象中修改该成员变量会影响到另一个对象的该成员变量值。      
	对于深拷贝来说，不仅要复制对象的所有基本数据类型的成员变量值，还要为所有引用数据类型的成员变量申请存储空间，并复制每个引用数据类型成员变量所引用的对象，直到该对象可达的所有对象。也就是说，对象进行深拷贝要对整个对象图进行拷贝！   
	简单地说，深拷贝对引用数据类型的成员变量的对象图中所有的对象都开辟了内存空间；而浅拷贝只是传递地址指向，新的对象并没有对引用数据类型创建内存空间。   

15. Java 中对象的生命周期？   
	1.      创建阶段(Created)    
	2.      应用阶段(In Use)   
	3.      不可见阶段(Invisible)    
	4.      不可达阶段(Unreachable)   
	5.      收集阶段(Collected)    
	6.      终结阶段(Finalized)  
	7.      对象空间重分配阶段(De-allocated)   

16. [对并发编程的了解?](https://www.jianshu.com/p/01188fa8e511)   

17.线程同步
CyclicBarrier、CountDownLatch和Semaphore
CountDownLatch：主要用于同步等待多个线程的操作完成后，再进行相关的处理。
例如：在实际应用中比较常见的情况是，客户端需要启动三个线程，两个线程各自调用一个接口获取相关的数据，然后等待两个获取数据的线程都返回数据后，第三个线程来对数据进行处理。    
CountDownLatch.await()等待指定线程数完成后,再执行后面的操作；CountDownLatch.countdown()表明当前线程已完成; 
      
CyclicBarieer：它允许某一组线程在达到栅栏点（指定的线程数）前，互相等待，发生阻塞，直到最后一个线程到达栅栏点，栅栏才会打开，然后继续执行后面的操作。    
例如：斗地主需要三个人凑齐才会开始，在三个人都点击开始后，游戏才能开始玩，否则等待开始，或者超时离开。     
CyclicBarieer.await();等待所有线程到达指定线程数，然后在执行后面的代码。   
   
semaphore：这个类是用作访问并发控制，可以设置资源最大同时访问的个数。semaphore.acquire获取到许可证，使用完后调用semaphore.release释放。
   
##网络   
1.三次握手
第一次握手：建立连接时，客户端发送syn包（syn=j）到服务器，并进入SYN_SENT状态，等待服务器确认；SYN：同步序列编号（Synchronize Sequence Numbers）。
第二次握手：服务器收到syn包，必须确认客户的SYN（ack=j+1），同时自己也发送一个SYN包（syn=k），即SYN+ACK包，此时服务器进入SYN_RECV状态；
第三次握手：客户端收到服务器的SYN+ACK包，向服务器发送确认包ACK(ack=k+1），此包发送完毕，客户端和服务器进入ESTABLISHED（TCP连接成功）状态，完成三次握手。
   
2.四次挥手
由于TCP连接是全双工的，因此每个方向都必须单独进行关闭。

客户端A发送一个FIN，用来关闭客户A到服务器B的数据传送（报文段4）。
服务器B收到这个FIN，它发回一个ACK，确认序号为收到的序号加1（报文段5）。和SYN一样，一个FIN将占用一个序号。
服务器B关闭与客户端A的连接，发送一个FIN给客户端A（报文段6）。
客户端A发回ACK报文确认，并将确认序号设置为收到序号加1（报文段7）
  
3.Http的状态码含义。
1** 信息，服务器收到请求，需要请求者继续执行操作
2** 成功，操作被成功接收并处理
3** 重定向，需要进一步的操作以完成请求
301 Moved Permanently。请求的资源已被永久的移动到新URI，返回信息会包括新的URI，浏览器会自动定向到新URI。今后任何新的请求都应使用新的URI代替
302 Moved Temporarily。与301类似。但资源只是临时被移动。客户端应继续使用原有URI
304 Not Modified。所请求的资源未修改，服务器返回此状态码时，不会返回任何资源。客户端通常会缓存访问过的资源，通过提供一个头信息指出客户端希望只返回在指定日期之后修改的资源。
4** 客户端错误，请求包含语法错误或无法完成请求
400 Bad Request 由于客户端请求有语法错误，不能被服务器所理解。
401 Unauthorized 请求未经授权。这个状态代码必须和WWW-Authenticate报头域一起使用
403 Forbidden 服务器收到请求，但是拒绝提供服务。服务器通常会在响应正文中给出不提供服务的原因
404 Not Found 请求的资源不存在，例如，输入了错误的URL
5** 服务器错误，服务器在处理请求的过程中发生了错误
500 Internal Server Error 服务器发生不可预期的错误，导致无法完成客户端的请求。
503 Service Unavailable 服务器当前不能够处理客户端的请求，在一段时间之后，服务器可能会恢复正常
   
4.Http request的几种类型。
GET 请求指定的页面信息，并返回实体主体。
POST 向指定资源提交数据进行处理请求（例如提交表单或者上传文件）。数据被包含在请求体中。POST请求可能会导致新的资源的建立和/或已有资源的修改。
PUT 从客户端向服务器传送的数据取代指定的文档的内容。
DELETE 请求服务器删除指定的页面。 
   
5.DELETE 请求服务器删除指定的页面。.Http会话的过程？
建立tcp连接
发出请求文档
发出响应文档
释放tcp连接
    
6.(ThreadLocal)[https://www.jianshu.com/p/377bb840802f]

   
## JVM
 
1. [简述 JVM 内存模型和内存区域？](https://github.com/jeanboydev/Android-Interview/blob/master/Java.md#jvm_1)  
2. [简述垃圾回收器的工作原理？](https://blog.csdn.net/wuzhixiu007/article/details/80116560)  
3. 如何判断对象的生死？垃圾回收算法？新生代，老生代？    
	对虚拟机可用内存空间，即堆空间中的对象进行识别，如果对象正在被引用，那么称其为存活对象，反之，如果对象不再被引用，则为垃圾对象，可以回收其占据的空间，用于再分配。       
	通过引用计数算法或引用可达算法可以判断对象是否存活。    
	Serial收集器（复制算法)：   
	新生代单线程收集器，标记和清理都是单线程，优点是简单高效。   
	Serial Old收集器(标记-整理算法)：   
	老年代单线程收集器，Serial收集器的老年代版本。    
	ParNew收集器(停止-复制算法)：　    
	新生代收集器，可以认为是Serial收集器的多线程版本,在多核CPU环境下有着比Serial更好的表现。   
	Parallel Scavenge收集器(停止-复制算法)：   
	并行收集器，追求高吞吐量，高效利用CPU。吞吐量一般为99%， 吞吐量= 用户线程时间/(用户线程时间+GC线程时间)。适合后台应用等对交互相应要求不高的场景。    
	Parallel Old收集器(停止-复制算法)：   
	Parallel Scavenge收集器的老年代版本，并行收集器，吞吐量优先   
	CMS(Concurrent Mark Sweep)收集器（标记-清理算法）：   
	高并发、低停顿，追求最短GC回收停顿时间，cpu占用比较高，响应时间快，停顿时间短，多核cpu 追求高响应时间的选择   
      
4. 哪些情况下的对象会被垃圾回收机制处理掉？
5. 垃圾回收机制与调用 System.gc() 的区别？   
	Java语言建立了垃圾收集机制，用以跟踪正在使用的对象和发现并回收不再使用(引用)的对象。该机制可以有效防范动态内存分配中可能发生的两个危险：因内存垃圾过多而引发的内存耗尽，以及不恰当的内存释放所造成的内存非法引用。     
　　垃圾收集算法的核心思想是：对虚拟机可用内存空间，即堆空间中的对象进行识别，如果对象正在被引用，那么称其为存活对象，反之，如果对象不再被引用，则为垃圾对象，可以回收其占据的空间，用于再分配。   
	System.gc()函数的作用只是提醒虚拟机：程序员希望进行一次垃圾回收。但是它不能保证垃圾回收一定会进行，而且具体什么时候进行是取决于具体的虚拟机的，不同的虚拟机有不同的对策。    
   
6. [强引用、软引用、弱引用、虚引用之间的区别？](https://github.com/jeanboydev/Android-Interview/blob/master/Java.md#java_53)
7. 强引用设置为 null，会不会被回收？
不会立即回收，等到下次gc才会被回收
   
8. [简述 ClassLoader 类加载机制?](https://blog.csdn.net/m0_38075425/article/details/81627349)     
	当程序主动使用某个类时，如果该类还未被加载到内存中，则JVM会通过加载、连接、初始化3个步骤来对该类进行初始化。    
   
9. 对双亲委派模型的了解？   
	双亲委派模型的工作过程是：   
	如果一个类加载器收到了类加载的请求，它首先不会自己去尝试加载这个类，而是把这个请求委派给父类加载器去完成，每一层次的类加载器都是如此，因此所有的加载请求，最终都应该传送到顶层的启动类加载器中，只有当父加载器反馈自己无法完成这个加载请求（它的搜索范围中没有找到所需的类）时，子加载器才会尝试自己去加载。   
  
10. [String a = "a"+"b"+"c" 在内存中创建几个对象？](https://github.com/jeanboydev/Android-Interview/blob/master/Java.md#java_57)
11. 对 Dalvik、ART 虚拟机的了解？
12. 对动态加载（OSGI）的了解？
13. 常见编码方式有哪些？
14. utf-8 编码中的中文占几个字节？int 型占几个字节？

----------

# Android

## 基础

1. 四大组件是什么？
Activity, Services, BroadcastReaciever
  
2. Activity 的生命周期？
onCreat, onStart, onRestart, onResume, onPause, onStop, onDestroy
   
3. Activity 之间的通信方式？
Intent, SharedPreference, sqlite, file, BroadcastReciever, 静态变量，全局变量，eventbus,
   
4. Activity 各种情况下的生命周期？

5. 横竖屏切换时 Activity 的生命周期
未在AndroidManifest中配置configChangesconfigChanges：，onPause, onStop, onDestory, onCreate, onStart, onResume,
另外还有在活动销毁和重建的时候还会分别调用: onSaveInstanceState() 和 onRestoreInstanceState() 来保存和恢复数据。
配置configChanges后：onConfigurationChanged

6. 前台切换到后台，然后再回到前台时 Activity 的生命周期
A调用 onCreate() 方法 -> onStart() 方法 -> onResume() 方法，此时 A 前台可见。当 A 跳转到 B 时，A 调用 onPause() 方法，然后调用新的 Activity B 中的 onCreate() 方法 -> onStart() 方法 -> onResume() 方法。最后 A 再调用onStop()方法。当 A 再次回到时前台，B 调用 onPause() 方法，A 调用 onRestart() -> onStart() -> onResume() 方法，然后 B 再调用 onStop() -> onDestroy()方法。
    
7. 弹出 Dialog 的时候按 Home 键时 Activity 的生命周期
有 Dialog 和 无 Dialog 按 Home 键效果一样：
onPause,onStop,onRestart,onStart,onResume
   
8. 两个 Activity 之间跳转时的生命周期
启动secondeActivity:first.onPause, second.onCreate, second.onStart, seconde.onResume, first.onStop
推出secondeActivity：seconde.pause, first.onRestart,first.onStart, first.onResume, seoncd.onStop, second.onDestroy
   
9. 下拉状态栏时 Activity 的生命周期
不影响activity的生命周期
    
10. (Activity 与 Fragment 之间生命周期比较？)[https://blog.csdn.net/u012702547/article/details/50253955]
我们按照 Activity 的生命周期为导向，来分析:
a. 在创建的过程中，是 Activity 带领 Fragment 执行生命周期的方法，所以它们生命周期执行的顺序如下:
1. Activity -- onCreate() 
2. Fragment -- onAttach() -> onCreate() -> onCreateView() -> onActivityCreated

b. 接下来:
3. Activity -- onStart() 
4. Fragment -- onStart()

c. 再接下来:
5. Activity -- onResume()
6. Fragment -- onResume()

d. 最后，在销毁时是 Fragment 带领 Activity 执行生命周期的方法:
7. Fragment -- onPause()
8. Activity -- onPause()
9. Fragment -- onStop()
10. Activity -- onStop()
11. Fragment -- onDestroyView() -> onDestroy() -> onDetach()
12. Activity -- onDestroy()

   
11. Activity 的四种 LaunchMode（启动模式）的区别？
Activity四种启动模式: standard(标准模式)、singleTop(栈顶复用模式)、singleTask(栈内复用模式)、singleInstance(单实例模式)。Android 中默认启动模式为 standard，我们可以通过在 AndroidManifest.xml 的 activity 标签下通过 launchMode 属性指定我们想要设置的启动模式。

standard(标准模式)
    标准模式，系统默认模式。每次启动一个 Activity 都会重新创建一个新的实例，不管这个实例是否已经存在。这是一种典型的多实例实现，一个任务栈中可以有多个实例，每个实例也可以属于不同的任务栈。在这种模式下，谁启动了这个 Activity，那么这个 Activity 就运行在启动它的那个 Activity 所在栈中。

singleTop(栈顶复用模式)
    栈顶复用模式。在这种模式下，如果新 Activity 已经位于任务栈的栈顶，那么此 Activity 不会被重新创建，同时它的 onNewIntent 方法会被回调，通过此方法的参数我们可以取出当前请求的信息。如果新 Activity 的实例已存在但不是位于栈顶，那么新 Activity 仍然会重新创建。

singleTask(栈内复用模式)
    栈内复用模式。这是一种单实例模式，在这种模式下，只要 Activity 在一个栈中存在，那么多次启动此 Activity 都不会重新创建实例，和 singleTop 模式一样，系统也会回调其 onNewIntent。
    注意，这里我们分 3 种情况来理解这个 launchMode:
    1. 被启动的 Activity 任务栈不存在:
        此时会新建一个该 Activity 的任务栈，并将 Activity 实例放到任务栈中。
    2. 被启动的 Activity 任务栈存在，但是任务栈中该 Activity 实例不处于栈顶而在栈内:
        此时会先将该 Activity 实例上面的其它 Activity 实例全部出栈(因为该启动模式默认具有 clearTop 效果)并将要启动的 Activity 实例置于栈顶，系统调用其 onNewIntent 方法。
    3. 被启动的 Activity 存在任务栈，而且该 Activity 实例在该任务栈栈顶位置:
        直接复用任务栈中的该 Activity 实例，并调用其 onNewIntent 方法。

    这里我们还需要注意一个 Activity 的属性 TaskAffinity，可以翻译为任务相关性。它标识了一个 Activity 所需要的任务栈的名字，默认情况下，所有 Activity 所需的任务栈的名字为应用的包名。这个属性主要和 singleTask 启动模式或者 allowTaskReparenting 属性配对使用，在其它情况下没有意义，为这个启动的 Activity 的任务栈指定相应的名称。

singleInstance(单实例模式)
    单实例模式。这是一种加强的 singleTask 模式，它除了具有 singleTask 模式的所有特性外，还加强了一点，那就是具有此种模式的 Activity 只能单独地位于一个任务栈中。
    
12. Activity 状态保存与恢复？
当 Activity 在异常情况( 系统内存不足或者系统配置发生了改变等 )被销毁重建后， 在销毁的时候 Activity 会调用 onSaveInstanceState() 方法用于保存 Activity 相关的状态和数据，然后在重建后的 Activity 的中我们可以通过 onCreate() 或者 onRestoreInstanceState() 方法恢复数据，这里我们需要注意的是如果通过 onCreate() 方法恢复，那么得先判断它的 intent 参数 是否为空，如果在 onRestoreInstanceState() 方法恢复就不会，因为只要 onRestoreInstanceState() 方法被调用就说明一定有数据，不会为空。Google 推荐使用 onRestoreInstanceState() 方法。
   
13. [Fragment 各种情况下的生命周期？](https://blog.csdn.net/yz_cfm/article/details/85643141). 
    
14. Activity 和 Fragment 之间怎么通信， Fragment 和 Fragment 怎么通信?
  1.接口
  2.获取实例
  3.广播或eventbus
  4.静态变量或全局变量
      
15. Service 的生命周期？
onCreate->onStartCommand->onDestory  
onCreate->onBind->onUnBind->onDestory  
   
16. Service 的启动方式？
startService和bindService. 
   
17. Service 与 IntentService 的区别?
IntentService会单独启动一个线程运行   
   
18. [Service 和 Activity 之间的通信方式？]()
  1.bindService可以通过binder进行通行，startService的可以通过intent通信
  2.广播
  3.eventbus
  4.全局变量或静态变量

19. [对 ContentProvider 的理解？](https://blog.csdn.net/cbwem/article/details/89762000)
ContentProvider用于不同的应用程序之间实现数据共享的功能，还能保证数据安全性，使用ContentProvider（内容提供器）是Android实现跨程序共享数据的标准方式。ContentProvider可以选择只对哪一部分数据进行共享，从而保证程序中的隐私数据不会有泄露的风险。
   
20. ContentProvider、ContentResolver、ContentObserver 之间的关系？
ContentProvider：把应用程序的私有数据信息暴露给其他应用程序，让其他应用程序可以访问到这些所有数据。如果要让其他应用程序访问，需对外暴露一个URI路径。
ContentResolver：根据URI路径对数据进行CRUD操作。
ContentObserver：Android系统包装好的回调，当ContentProvider数据发生变化时，会执行回调中的方法。ContentResolver发送通知，ContentObserver监听通知。
   
21. 对 BroadcastReceiver 的了解？

22. 广播的分类？使用方式和场景？
（1）普通广播-BroadcastReceiver

通过Context.sendBroadcast发送的广播即为普通广播，发送普通广播是最常见也是使用最多的一种广播发送方式，它的特点就是当有多个BroadcastReceiver同时接收一个广播的时候，它们都是异步接收的的，换句话说就是各个BroadcastReceiver之间接收广播的时候互不干扰，互不影响，由此便可知该广播对于每个BroadcastReceiver来说，各自都无法阻止其它BroadcastReceiver的接收动作。

（2）有序广播-OrderedBroadcastReceiver

通过Context.sendOrderedBroadcast发送的广播即为有序广播，与普通广播的不同在于，接收者是有序接收到广播的并且可以对广播进行修改或是取消广播向下传递。系统根据接收者定义的优先级顺序决定哪个接收者先接收到它，接收者处理完后可以将结果传递给优先级低的接收者也可以停止广播使得其他优先级低的接收者无法接收到该广播。优先级通过android:priority属性定义，数值越大优先级别越高，取值范围：-1000到1000，虽然API文档介绍对sendBroadcast发送的广播无效，不过本人测试同样有效，相同优先级的接收者接收到广播的顺序随机。Android系统收到短信、接到电话后发送的广播都是有序广播，所以可以进行短信或电话的拦截，即取消广播。

PS：有序广播可以在onReceive函数中通过BroadcastReceiver的abortBroadcast接口(这个接口对sendBroadcast发送广播无效)取消广播，通过接口sendOrderedBroadcast(Intent, String, BroadcastReceiver, android.os.Handler, int, String, Bundle)发送的广播即便优先级高的广播取消了广播，接口参数中指定的BroadcastReceiver依然可以在其他接收者处理完后接收到广播。通过BroadcastReceiver的getResultExtras接口获得结果的Bundle再通过Bundle的putString和getString方法修改或获取数据，可以见本文最后的实例代码举例。

（3）普通粘性广播-Sticky Broadcast

如果发送者发送了某个广播，而接收者在这个广播发送后才注册自己的Receiver，这时接收者便无法接收到刚才的广播，为此Android引入了StickyBroadcast，在广播发送结束后会保存刚刚发送的广播（Intent），这样当接收者注册完Receiver后就可以继续使用刚才的广播。如果在接收者注册完成前发送了多条相同Action的粘性广播，注册完成后只会收到一条该Action的广播，并且消息内容是最后一次广播内容。系统网络状态的改变发送的广播就是粘性广播。

粘性广播通过Context的sendStickyBroadcast(Intent)接口发送，需要添加权限<uses-permission android:name=”android.permission.BROADCAST_STICKY”/>

也可以通过Context的removeStickyBroadcast(Intent intent)接口移除缓存的粘性广播。

（4）粘性有序广播-StickyOrderedBroadcast

有序粘性广播其实也和有序广播的特点是差不多的，只不过添加了粘性的特点，通过Context的sendStickyOrderedBroadcast接口发送。
     
23. [动态广播和静态广播有什么区别？]()

24. AlertDialog、popupWindow、Activity 之间的区别？

25. Application 和 Activity 的 Context 之间的区别？

26. Android 属性动画特性？

27. 请列举 Android 中常见的布局（Layout）类型，并简述其用法，以及排版效率。【猎豹移动】

    LinearLayout、RelativeLayout、FrameLayout 的特性对比及使用场景？

28. 对 SurfaceView 的了解？

29. Serializable 和 Parcelable 的区别？

30. Android 中数据存储方式有哪些？

31. 屏幕适配的处理技巧都有哪些?

32. Android 各个版本 API 的区别？

33. 动态权限适配方案，权限组的概念？

34. 为什么不能在子线程更新 UI？

35. ListView 图片加载错乱的原理和解决方案？

36. 对 RecycleView 的了解？

37. Recycleview 和 ListView 的区别？

38. RecycleView 实现原理？

39. Android Manifest 的作用与理解？

40. 多线程在 Android 中的使用？

41. 区别 Animation 和 Animator 的用法，概述实现原理？【猎豹移动】

## 进阶

1. [画出 Android 的大体架构图](https://github.com/jeanboydev/Android-Interview/blob/master/Android.md#android_advance_1)

2. 低版本 SDK 如何使用高版本 API？

3. AsyncTask 如何使用?

4. AsyncTask 机制、原理及不足？

5. 如果在 onStop() 的时候做了网络请求，onResume() 的时候怎么恢复？

6. Handler 机制和底层实现？

7. Handler、Thread、HandlerThread 区别？

   Thread、Looper、MessageQueue、Handler、Message，每个类的功能是什么，这些类之间是什么关系？【猎豹移动】

8. ThreadLocal 原理、实现及如何保证 Local 属性？

9. 自定义 View 的流程？如何机型适配？

10. 自定义 View 的时怎么获取 View 的大小？

11. View 的绘制流程？

12. View 的事件传递分发机制？   
	dispatchTouchEvent、onInterceptorTouchEvent、onTouchEvent   
	在onInterceptorTouchEvent中返回true，可进行拦截,或者在子view中调用requestDisallowInterceptorTouchEvent方法；   

13. requestLayout()，onLayout()，onDraw()，drawChild() 区别与联系？

14. invalidate() 和 postInvalidate() 的区别？   
	[Android中实现view的更新有两组方法，一组是invalidate，另一组是postInvalidate，其中前者是在UI线程自身中使用，而后者在非UI线程中使用。  ](https://www.cnblogs.com/rayray/p/3437048.html)    


15. 如何计算一个 View 的嵌套层级？

16. Android 动画框架及实现原理？

17. 进程和 Application 的生命周期的关系？

18. SpareArray 的实现原理？
	
19. SharedPreferences 的实现眼里？是否进程同步？如何做到同步？

20. ContentProvider 是如何实现数据共享的？

21. ContentProvider 的权限管理？

22. Android 系统为什么会设计 ContentProvider？

23. Android 线程有没有上限？

24. 怎么去除重复代码？

25. Android 中开启摄像头的主要流程？

26. 对 Bitmap 对象的了解？

27. 图片加载原理？

28. 图片压缩原理？   
	inSampleSize   
	Bitmap'常见有2种编码方式：ARGB_8888和RGB_565，ARGB_8888每个像素点4个byte，RGB_565是2个byte   

29. 图片框架实现原理？LRUCache 原理？   
	

30. EventBus 实现原理？

31. ButterKnife 实现原理？
	编译时注解生成一个bind类，运行时调用bind方法后，进行view与Id的绑定。   

32. Volley 实现原理？

33. okhttp 实现原理？
	OkHttp是一个精巧的网络请求库,有如下特性: 

1)支持http2，对一台机器的所有请求共享同一个socket

2)内置连接池，支持连接复用，减少延迟

3)支持透明的gzip压缩响应体

4)通过缓存避免重复的请求

5)请求失败时自动重试主机的其他ip，自动重定向

6)好用的API


34. 服务器只提供数据接收接口，在多线程或多进程条件下，如何保证数据的有序到达？    
	countdownlatch：允许一个或多个线程等待某些操作完成     
	cyclicbarrier:允许多个线程等待到达某个屏障   
	semaphore: 类似线程对资源的控制


35. SQLite 数据库升级，数据迁移问题？  


36. 数据库框架对比和源码分析？

37. CAS介绍，OAuth 授权机制？

38. 谈谈你对安卓签名的理解

39. App 是如何沙箱化，为什么要这么做？

## 混合开发

1. 混合开发的方式？各自优缺点和使用场景？
2. Hybird
3. React Native
4. Weex
5. Flutter
6. Dart
7. 快应用

## Framework

1. 请介绍一下 NDK？
2. 如何加载 ndk 库？如何在 jni 中注册 native 函数，有几种注册方式?【猎豹移动】
3. Android 进程分类？   
	前台进程、可见进程、服务进程、后台进程、空进程    

4. 谈谈对进程共享和线程安全的认识？
5. 谈谈对多进程开发的理解以及多进程应用场景？
6. 什么是协程？
7. 逻辑地址与物理地址，为什么使用逻辑地址？
8. Android 为每个应用程序分配的内存大小是多少？
9. 进程保活的方式？     
	1）设置为前台进程，设置进程优先级     
	2）设置一个像素的activity   
	3) 进程互相唤醒   
	4) JobSheduler   
	5）native fork一个进程，耗电   
  	6）忽略电池优化    

10. 系统启动流程是什么？
11. 一个应用程序安装到手机上的过程发生了什么？
12. App 启动流程，从点击桌面开始（Activity 启动流程）？    
	整个应用程序的启动过程要执行很多步骤，但是整体来看，主要分为以下五个阶段：

一. Step1 - Step 11：
Launcher通过Binder进程间通信机制通知ActivityManagerService，
它要启动一个Activity；

二. Step 12 - Step 16：
ActivityManagerService通过Binder进程间通信机制通知Launcher进入Paused状态；

三. Step 17 - Step 24：
Launcher通过Binder进程间通信机制通知ActivityManagerService，它已经准备就绪进入Paused状态，
于是ActivityManagerService就创建一个新的进程，用来启动一个ActivityThread实例，
即将要启动的Activity就是在这个ActivityThread实例中运行；

四. Step 25 - Step 27：
ActivityThread通过Binder进程间通信机制将一个ApplicationThread类型的Binder对象传递给ActivityManagerService，
以便以后ActivityManagerService能够通过这个Binder对象和它进行通信；

五. Step 28 - Step 35：
ActivityManagerService通过Binder进程间通信机制通知ActivityThread，
现在一切准备就绪，它可以真正执行Activity的启动操作了。

13. 什么是 AIDL？解决了什么问题？如何使用？
14. Binder 机制及工作原理？
15. App 中唤醒其他进程的实现方式？
16. Activity、Window、View 三者的关系与区别？
17. ApplicationContext 和 ActivityContext 的区别？
18. ActivityThread，ActivityManagerService，WindowManagerService 的工作原理？
19. PackageManagerService 的工作原理？
20. PowerManagerService 的工作原理？
21. 权限管理系统（底层的权限是如何进行 grant 的）？
22. 操作系统中进程和线程有什么区别？系统在什么情况下会在用户态和内核态中切换？【猎豹移动】
23. 如果一个 App 里面有多个进程存在，请列举你所知道的全部 IPC 方法。
	aidl、messager、socket、contentprovider、bundle、file序列化

## 性能优化

1. 如何对 Android 应用进行性能分析以及优化?	    
	https://blog.csdn.net/zhangbijun1230/article/details/79449725 
	[Bitmap压缩优化](https://www.jianshu.com/p/3ac26611bc0d)     
		1）质量压缩：bit.compress； 2）采样率压缩：options.inSampleSize；	3）缩放法压缩（martix）	4）RGB_565压缩（ARGB_8888转RGB_565） 5)createScaledBitmap
[转载自](https://www.bookstack.cn/read/interview/android-optimize.md)
ANR

ANR全称Application Not Responding，意思就是程序未响应。

出现场景

主线程被IO操作（从4.0之后网络IO不允许在主线程中）阻塞。
主线程中存在耗时的计算
主线程中错误的操作，比如Thread.wait或者Thread.sleep等
Android系统会监控程序的响应状况，一旦出现下面两种情况，则弹出ANR对话框

应用在5秒内未响应用户的输入事件（如按键或者触摸）
BroadcastReceiver未在10秒内完成相关的处理
如何避免

基本的思路就是将IO操作在工作线程来处理，减少其他耗时操作和错误操作

使用AsyncTask处理耗时IO操作。
使用Thread或者HandlerThread时，调用Process.setThreadPriority(Process.THREAD_PRIORITY_BACKGROUND)设置优先级，否则仍然会降低程序响应，因为默认Thread的优先级和主线程相同。
使用Handler处理工作线程结果，而不是使用Thread.wait()或者Thread.sleep()来阻塞主线程。
Activity的onCreate和onResume回调中尽量避免耗时的代码
BroadcastReceiver中onReceive代码也要尽量减少耗时，建议使用IntentService处理。
如何改善

通常100到200毫秒就会让人察觉程序反应慢，为了更加提升响应，可以使用下面的几种方法

如果程序正在后台处理用户的输入，建议使用让用户得知进度，比如使用ProgressBar控件。
程序启动时可以选择加上欢迎界面，避免让用户察觉卡顿。
使用Systrace和TraceView找出影响响应的问题。
如果开发机器上出现问题，我们可以通过查看/data/anr/traces.txt即可，最新的ANR信息在最开始部分。

OOM

在实践操作当中，可以从四个方面着手减小内存使用，首先是减小对象的内存占用，其次是内存对象的重复利用，然后是避免对象的内存泄露，最后是内存使用策略优化。

减小对象的内存占用

使用更加轻量级的数据结构：例如，我们可以考虑使用ArrayMap/SparseArray而不是HashMap等传统数据结构，相比起Android系统专门为移动操作系统编写的ArrayMap容器，在大多数情况下，HashMap都显示效率低下，更占内存。另外，SparseArray更加高效在于，避免了对key与value的自动装箱，并且避免了装箱后的解箱。

避免使用Enum：在Android中应该尽量使用int来代替Enum，因为使用Enum会导致编译后的dex文件大小增大，并且使用Enum时，其运行时还会产生额外的内存占用。

减小Bitmap对象的内存占用：

inBitmap：如果设置了这个字段，Bitmap在加载数据时可以复用这个字段所指向的bitmap的内存空间。但是，内存能够复用也是有条件的。比如，在Android 4.4(API level 19)之前，只有新旧两个Bitmap的尺寸一样才能复用内存空间。Android 4.4开始只要旧 Bitmap 的尺寸大于等于新的 Bitmap 就可以复用了。

inSampleSize：缩放比例，在把图片载入内存之前，我们需要先计算出一个合适的缩放比例，避免不必要的大图载入。

decode format：解码格式，选择ARGB_8888 RBG_565 ARGB_4444 ALPHA_8，存在很大差异。

ARGB_4444：每个像素占四位，即A=4，R=4，G=4，B=4，那么一个像素点占4+4+4+4=16位
ARGB_8888：每个像素占四位，即A=8，R=8，G=8，B=8，那么一个像素点占8+8+8+8=32位
RGB_565：每个像素占四位，即R=5，G=6，B=5，没有透明度，那么一个像素点占5+6+5=16位
ALPHA_8：每个像素占四位，只有透明度，没有颜色。
使用更小的图片：在设计给到资源图片的时候，我们需要特别留意这张图片是否存在可以压缩的空间，是否可以使用一张更小的图片。尽量使用更小的图片不仅仅可以减少内存的使用，还可以避免出现大量的InflationException。假设有一张很大的图片被XML文件直接引用，很有可能在初始化视图的时候就会因为内存不足而发生InflationException，这个问题的根本原因其实是发生了OOM。

内存对象的重复使用

大多数对象的复用，最终实施的方案都是利用对象池技术，要么是在编写代码的时候显式的在程序里面去创建对象池，然后处理好复用的实现逻辑，要么就是利用系统框架既有的某些复用特性达到减少对象的重复创建，从而减少内存的分配与回收。

复用系统自带资源：Android系统本身内置了很多的资源，例如字符串/颜色/图片/动画/样式以及简单布局等等，这些资源都可以在应用程序中直接引用。这样做不仅仅可以减少应用程序的自身负重，减小APK的大小，另外还可以一定程度上减少内存的开销，复用性更好。但是也有必要留意Android系统的版本差异性，对那些不同系统版本上表现存在很大差异，不符合需求的情况，还是需要应用程序自身内置进去。

ListView ViewHodler

Bitmap对象的复用：在ListView与GridView等显示大量图片的控件里面需要使用LRU的机制来缓存处理好的Bitmap。

inBitmap：使用inBitmap属性可以告知Bitmap解码器去尝试使用已经存在的内存区域，新解码的bitmap会尝试去使用之前那张bitmap在heap中所占据的pixel data内存区域，而不是去问内存重新申请一块区域来存放bitmap。

使用inBitmap，在4.4之前，只能重用相同大小的bitmap的内存区域，而4.4之后你可以重用任何bitmap的内存区域，只要这块内存比将要分配内存的bitmap大就可以。这里最好的方法就是使用LRUCache来缓存bitmap，后面来了新的bitmap，可以从cache中按照api版本找到最适合重用的bitmap，来重用它的内存区域。
新申请的bitmap与旧的bitmap必须有相同的解码格式
避免在onDraw方法里面执行对象的创建：类似onDraw等频繁调用的方法，一定需要注意避免在这里做创建对象的操作，因为他会迅速增加内存的使用，而且很容易引起频繁的gc，甚至是内存抖动。

StringBuilder：在有些时候，代码中会需要使用到大量的字符串拼接的操作，这种时候有必要考虑使用StringBuilder来替代频繁的“+”。

避免内存泄漏

内部类引用导致Activity的泄漏：最典型的场景是Handler导致的Activity泄漏，如果Handler中有延迟的任务或者是等待执行的任务队列过长，都有可能因为Handler继续执行而导致Activity发生泄漏。
Activity Context被传递到其他实例中，这可能导致自身被引用而发生泄漏。
考虑使用Application Context而不是Activity Context
注意临时Bitmap对象的及时回收
注意监听器的注销
注意缓存容器中的对象泄漏：不使用的对象要将引用置空。
注意Cursor对象是否及时关闭
内存优化策略

综合考虑设备内存阈值与其他因素设计合适的缓存大小

onLowMemory()：Android系统提供了一些回调来通知当前应用的内存使用情况，通常来说，当所有的background应用都被kill掉的时候，forground应用会收到onLowMemory()的回调。在这种情况下，需要尽快释放当前应用的非必须的内存资源，从而确保系统能够继续稳定运行。

onTrimMemory()：Android系统从4.0开始还提供了onTrimMemory()的回调，当系统内存达到某些条件的时候，所有正在运行的应用都会收到这个回调，同时在这个回调里面会传递以下的参数，代表不同的内存使用情况，收到onTrimMemory()回调的时候，需要根据传递的参数类型进行判断，合理的选择释放自身的一些内存占用，一方面可以提高系统的整体运行流畅度，另外也可以避免自己被系统判断为优先需要杀掉的应用

资源文件需要选择合适的文件夹进行存放：例如我们只在hdpi的目录下放置了一张100100的图片，那么根据换算关系，xxhdpi的手机去引用那张图片就会被拉伸到200200。需要注意到在这种情况下，内存占用是会显著提高的。对于不希望被拉伸的图片，需要放到assets或者nodpi的目录下。

谨慎使用static对象

优化布局层次，减少内存消耗

使用FlatBuffer等工具序列化数据

谨慎使用依赖注入框架

使用ProGuard来剔除不需要的代码

卡顿优化

导致Android界面滑动卡顿主要有两个原因：

UI线程（main）有耗时操作

视图渲染时间过长，导致卡顿

众所周知，界面的流畅度主要依赖FPS这个值，这个值是通过（1s/渲染1帧所花费的时间）计算所得，FPS值越大视频越流畅，所以就需要渲染1帧的时间能尽量缩短。正常流畅度的FPS值在60左右，即渲染一帧的时间不应大于16 ms。

如果想让应用流畅运行 ：

不要阻塞UI线程；
不要在UI线程之外操作UI；
减少UI嵌套层级
针对界面切换卡顿，一般出现在组件初始化的地方。屏幕滑动卡顿，ui嵌套层级，还有图片加载，图片的话，滑动不加载，监听scrollListener。

2. ANR 产生的原因是什么？怎么定位？
	产生原因：keyinput 5秒内没有响应，broadcastreceiver 10秒内无响应，service 20秒内无响应，将会发生ANR。   
	定位：结合Logcat日志和生成的位于手机内部存储的/data/anr/traces.txt文件进行定位和分析。  
	解决：1）BlockCanary工具；	2）StrictMode严苛模式    

3. OOM 是什么？怎么解决？是否可以 try catch？

4. 内存泄露的解决方法？

5. ddms 和 traceView 的使用？

6. 性能优化如何分析 systrace？

7. 用 IDE 如何分析内存泄漏？

8. Java 多线程引发的性能问题，怎么解决？

9. 启动页白屏、黑屏、太慢怎么解决？
给theme设置一个背景图片
   
10. App 启动崩溃异常怎么捕捉？

    对于 Android App 闪退，可能有哪些原因？请针对每种情况简述分析过程。【猎豹移动】

11. 如何保持应用的稳定性？

12. RecyclerView 和 ListView 的性能对比？

13. Bitmap 如何处理大图？如何预防 OOM？

14. 如何缩小 Apk 的体积?

15. 如何统计启动时长？

16.Binder机制
主要的流程是这样的：
服务端通过Binder驱动在ServiceManager中注册我们的服务。
客户端通过Binder驱动查询在ServiceManager中注册的服务。
ServiceManager通过Binder驱动返回服务端的代理对象。
客户端拿到服务端的代理对象后即可进行进程间通信。
   Server创建了Binder实体，为其取一个字符形式，可读易记的名字。
将这个Binder连同名字以数据包的形式通过Binder驱动发送给ServiceManager，通知ServiceManager注册一个名字为XX的Binder，它位于Server中。
驱动为这个穿过进程边界的Binder创建位于内核中的实体结点以及ServiceManager对实体的引用，将名字以及新建的引用打包给ServiceManager。
ServiceManager收数据包后，从中取出名字和引用填入一张查找表中。但是一个Server若向ServiceManager注册自己Binder就必须通过这个引用和ServiceManager的Binder通信。
Server向ServiceManager注册了Binder实体及其名字后，Client就可以通过名字获得该Binder的引用了。Clent也利用保留的引用向ServiceManager请求访问某个Binder：我申请名字叫XX的Binder的引用。
ServiceManager收到这个连接请求，从请求数据包里获得Binder的名字，在查找表里找到该名字对应的条目，从条目中取出Binder引用，将该引用作为回复发送给发起请求的Client。
   
##  Gradle

1. Glide 源码解析
2. 对热修复和插件化的理解？
3. 插件化原理分析
4. 模块化实现（好处，原因）
5. 项目组件化的理解
6. 描述清点击 Android Studio 的 build 按钮后发生了什么？

## Kotlin

1. 谈谈对 Kotlin 的理解
2. 闭包和局部内部类的区别?

----------

# 网络基础

1. [描述一次网络请求的流程?](https://github.com/jeanboydev/Android-Interview/blob/master/Network.md#quest_network_technological_process)
2. TCP 中 3 次握手和 4 次挥手的过程?
3. TCP 与 UDP 的区别及应用?
4. HTTP 协议
5. HTTP 1.0 与 2.0 的区别
6. HTTP 报文结构
7. HTTP 与 HTTPS 的区别以及如何实现安全性
8. HTTPS 原理
9. 谈谈你对 WebSocket 的理解
10. WebSocket 与 socket 的区别
11. 视频加密传输

----------

# 数据结构与算法

## 数据结构

- 简述常见的数据结构？
- 堆的结构？
- 树、B+ 树、二叉树、红黑树的了解？
- 二叉树的深度优先遍历和广度优先遍历？
- 堆和树的区别？
- 图的了解？

## 算法

- 排序算法有哪些？
- 最快的排序算法是哪个？
- 手写冒泡排序
- 手写快速排序
- 快速排序的过程、时间复杂度、空间复杂度
- 手写堆排序

## 常见算法问题

- 给阿里2万多名员工按年龄排序应该选择哪个算法？
- GC算法(各种算法的优缺点以及应用场景)
- 蚁群算法与蒙特卡洛算法
- 子串包含问题(KMP 算法)写代码实现
- 一个无序，不重复数组，输出N个元素，使得N个元素的和相加为M，给出时间复杂度、空间复杂度。手写算法
- 万亿级别的两个URL文件A和B，如何求出A和B的差集C(提示：Bit映射->hash分组->多文件读写效率->磁盘寻址以及应用层面对寻址的优化)
- 两个不重复的数组集合中，求共同的元素。
- 两个不重复的数组集合中，这两个集合都是海量数据，内存中放不下，怎么求共同的元素？
- 一个文件中有100万个整数，由空格分开，在程序中判断用户输入的整数是否在此文件中。说出最优的方法
- 一张Bitmap所占内存以及内存占用的计算
- 2000万个整数，找出第五十大的数字？
- 求1000以内的水仙花数以及40亿以内的水仙花数
- 烧一根不均匀的绳，从头烧到尾总共需要1个小时。现在有若干条材质相同的绳子，问如何用烧绳的方法来计时一个小时十五分钟呢？
- 5枚硬币，2正3反如何划分为两堆然后通过翻转让两堆中正面向上的硬8币和反面向上的硬币个数相同
- 时针走一圈，时针分针重合几次

----------

# 设计模式与架构

## 设计模式

- 谈谈你对 Android 设计模式的理解
- 项目中常用的设计模式有哪些？
- 手写生产者-消费者模式？
- 手写观察者模式？
- 适配器模式、装饰者模式、外观模式的异同？

## 架构

- MVC、MVP、MVVM 原理和区别？

  请画出 MVC、MVP 的差异？【猎豹移动】

- 对 RxJava 的理解，功能与原理，优缺点？

- 从 0 设计一款 App 整体架构，如何去做？

- Fragment 如果在 Adapter 中使用应该如何解耦？

- 对于应用更新这块是如何做的？(解答：灰度，强制更新，分区域更新)？

- 实现一个 Json 解析器（可以通过正则提高速度）？

----------

# 其他

- 请简单做个自我介绍？

- 为什么离开上家公司？您在前一家公司的离职原因是什么？

- 为什么要做 xxx 岗位（出现所学专业与求职岗位不同时提问）?

- 讲一个你认为做的最好的项目/案例

- 你应聘该岗位的优势是什么？

- 你上家公司的薪水/期望的薪金？

- 你对薪资的要求？

- 谈谈你对跳槽的看法？

- 对待加班看法？

- 自己最擅长的技术点，最感兴趣的技术领域和技术点，做了那些东西？

- 自己的优点和缺点是什么？并举例说明？

- 你朋友对你的评价？

- 说下项目中遇到的棘手问题，包括技术，交际和沟通？

  项目中遇到最大的困难是什么？如何解决的？

- 在五年的时间内，你的职业规划？

- 给你一个项目，你怎么看待他的市场和技术的关系？

- 你一般喜欢从什么渠道获取技术信息和提高自己的能力？

  你的学习方法是什么样的？实习过程中如何学习？实习项目中遇到的最大困难是什么以及如何解决的？

- 如果实际工作后发现自己不适合这个职位怎么办？

  如果通过这次面试我们单位录用了你，但工作一段时间却发现你根本不适合这个职位，你怎么办？

- 工作上与领导意见不同时，怎么办？

- 如果你的主管抢了你的功劳你该怎样？

- 若上司在公开会议上误会你了，该如何解决？

- 工作中你难以和同事、上司相处，你该怎么办？

- 因成绩比较突出，受同事们孤立你怎么看？

- 你和别人发生过争执吗？你是怎样解决的？

- 如果工作失误，给公司造成经济损失，你该怎么办？

- 你对于我们公司了解多少？

- 你为什么愿意到我们公司来工作？

- 你能为我们公司带来什么？

- 你最擅长的技术点，最感兴趣的技术领域和技术点？

- 说说你对行业、技术发展趋势的看法？

- 理想中的工作环境是什么？

- 说说你的家庭？

- 就你申请的这个职位，你认为你还欠缺什么？

- 你做过的哪件事最令自己感到骄傲？说一件最能证明你能力的事情？

- 对这项工作，你有哪些可预见的困难？

- 如果被录用，你将怎样开展工作？

- 希望与什么样的上级共事？

- 你工作经验欠缺，如何能胜任这项工作？ 

- 如果你在这次面试中没有被录用，你怎么打算？

- 除了本公司外，还应聘了哪些公司？

- 你还要什么了解和要问的吗？

- 实习过程中周围同事/同学有哪些值得学习的地方？

- 是否可以实习，可以实习多久？

- 实习过程中做了什么，有什么产出？

- 公司实习最大的收获是什么？

- 评价下自己，评价下自己的技术水平，个人代码量如何？

- 当前的 offer 状况；如果 BATH 都给了offer 该如何选？

- 你对一份工作更看重哪些方面？平台，技术，氛围，城市，还是 money？

- 假如你晚上要去送一个出国的同学去机场，可单位临时有事非你办不可，你怎么办？

- 你看中公司的什么？或者公司的那些方面最吸引你？

- 讲一件你印象最深的一件事情？

- 介绍你做过的哪些项目，介绍一个你影响最深的项目？

- 你做过的哪件事最令自己感到骄傲？

- 都使用过哪些框架、平台？

- 都使用过哪些自定义控件？

- 项目中用了哪些开源库，如何避免因为引入开源库而导致的安全性和稳定性问题？

- 有没有什么开源项目？

- 研究比较深入的领域有哪些？

- 对业内信息的关注渠道有哪些？

- 业余都有哪些爱好？

- 最近都读哪些书？

- 你的梦想是什么？

## 套路

如果有遇到以下这些情况，你可以继续投简历：

- 我们 xx 总不在，会叫 hr 联系你，你先回去等通知
- 面试叫你带上以往作品（工作成绩需要以往作品展示的除外，如：ui）然后面试官一直问你方案是怎么做的
- 遇到面试官敷衍随便问问题

https://gitchat.csdn.net/activity/5c6cf6044bb44360f3370255?utm_source=blog190625
https://www.bookstack.cn/read/interview/java-threadlocal.md

