# Java高阶面试题(P6~P7)

###1. 什么是 transient 变量？

答案：transient 变量是指不会被序列化的变量。

----

###2. 什么是同步（synchronization）

答案: 在多线程环境中，同步是指控制多个线程访问共享资源的方式。没有同步的话，可能出现一个线程正在读取或使用共享资源，同时另一个线程却在修改它的情况，这会造成严重的错误。

----

###3. 在 JDK 1.2 中，stop(), suspend() 和 resume() 这三个方法有什么变化？

答案:它们都被标注为 “deprecated”，也就是应该避免使用。

----

###4. null 是一个关键字吗？

答案:不是。

----

###5. 线程停止运行后是什么状态？

答案:线程停止运行后，就变成 DEAD 状态。


----

###6. 什么是集合 API（Collection API）？

答案:集合 API 是指一组用于帮助处理对象集合的类和接口。

###7. List 接口是做什么的？

答案:List 接口是用来处理有序且允许重复的对象集合的接口。

----



### 8. 什么时候应该将类定义为 final？

答案:不希望有子类的时候；
不希望功能被扩展的时候。

----


###9. 能否将抽象方法声明为静态的？

答案:不允许，这样做会导致编译错误：illegal combination of modifiers abstract and static

###10. 能否将接口声明为抽象的？

答案:可以。声明接口的时候加不加上 abstract 没有区别。


---

###11. 能否声明一个内容为空的接口？

答案:可以。

----

###12. 能否将接口声明为 final？

答案:不允许，这样做会导致编译错误。因为接口必须要有子类。

---


###13. 如何处理 ClassCastException？

答案:在强制类型转换之前用 instanceof 判断是否可以转换。

---



###14. 一个对象什么时候可以被回收（garbage collection）？

答案:当程序不可访问（unreachable）该对象的时候，该对象可以被回收。

---

###15. 所有线程都要实现的一个方法是什么？

答案:run() 方法，不论该线程是继承自 Thread 类或是实现了 Runnable 接口。

----

###16. 当异常没有被捕获时，会发生什么？

答案:当前线程所在的线程组会执行一个叫 uncaughtException() 的方法，最后程序会异常退出。

---

###17. 构造方法中如何使用 this() 和 super()？

答案:前者用来调用当前类的其他构造方法；后者用来调用父类的构造方法。


---


###18. 什么情况下垃圾收集器会执行对象的 finalize() 方法？

答案:当垃圾收集器检测到该对象不可访问（unreachable）时，会执行该对象的 finalize() 方法。


---

###19. 方法重载（overloading）有什么要求？

答案:方法的名称必须一样；方法的参数声明必须不一样。

---

###20. 编译器什么情况下会提供缺省构造方法（default constructor）？

答案:当一个类没有其他构造方法的时候，编译器会为其提供缺省的构造方法。

---

###21. 非静态内部类可以使用哪些修饰符（modifier）？

答案:非静态内部类可以使用 final 或 abstract 修饰符。

---