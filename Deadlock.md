## 死锁

### 死锁停在第几次的截图
![](http://a4.qpic.cn/psb?/V149UnPL1VXJy8/.Nq0mIfP8ymG2Diyoi.2jDooJYrf4DDbP75iXMyGnyA!/c/dFsBAAAAAAAA&ek=1&kp=1&pt=0&bo=EwHNABMBzQADCC0!&sce=0-12-12&rf=0-18)

### 产生死锁的4个必要条件
	1. 互斥条件：一个资源每次只能被一个进程使用
	2. 请求与保持条件：一个进程因请求资源而阻塞时，对已获得的资源保持不放
	3. 不剥夺条件:进程已获得的资源，在末使用完之前，不能强行剥夺
	4. 循环等待条件:若干进程之间形成一种头尾相接的循环等待资源关系

### 程序产生死锁的解释
![](http://a3.qpic.cn/psb?/V149UnPL1VXJy8/mUopI4aEXOYwDUryFcbrG63beHjYaXcAR4y9Y54z*r4!/c/dAYBAAAAAAAA&ek=1&kp=1&pt=0&bo=kQHnAZEB5wEDCC0!&sce=0-12-12&rf=0-18)

	1. 调用main函数
	2. 新建对象Deadlock调用函数Deadlock
	3. 创建类A的对象a和类B的对象b
	4. 创建线程t
	5. 设定线程等待时间
	6. 调用t.start()后，线程t被插入到调度队列中，当调度到它的时候，就跑run（）里面的代码
	7. 对象a调用函数methodA请求类B的对象b作为参数资源
	8. 调度队列中的线程不断被调度，当调度到t.start()的时候，跑run里面的代码，此时对象b调用函数methodB请求类A的对象a作为参数资源，但此时对象a在线程t被调度，产生了死锁。



