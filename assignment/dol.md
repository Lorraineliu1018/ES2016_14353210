## Lab2: DOL实例分析&编程

### 改完的.*dot截图
#### example2
![](http://a4.qpic.cn/psb?/V149UnPL1VXJy8/yBWx6O45RcPlXxBE3QL*xbeTfgrhfJsjtWa3rt.am4s!/b/dMcAAAAAAAAA&ek=1&kp=1&pt=0&bo=*AFTAfwBUwEDCC0!&sce=50-1-1&rf=viewer_311&t=5)
#### example1
![](http://a4.qpic.cn/psb?/V149UnPL1VXJy8/dnZduecm4b2br3LMyF9ZaCZvn6QiOZKW6zRX4M7FPj4!/b/dMcAAAAAAAAA&ek=1&kp=1&pt=0&bo=.gFkAfoBZAEDCC0!&sce=0-12-12&rf=viewer_311&t=5)

### 修改方式
#### example2
***
##### 由于example2的架构是通过迭代3次定义了3个square模块，所以只需要将迭代次数改为2次就行。即：
![](http://a4.qpic.cn/psb?/V149UnPL1VXJy8/WBRxcRbBgWHy93lzC8mTm5sbRhQg*gJfWxbGiV*PmGU!/b/dMcAAAAAAAAA&ek=1&kp=1&pt=0&bo=MAEeADABHgADACU!&sce=0-12-12&rf=viewer_311&t=5)

#### example1
***
##### 由于square模块中对信号进行处理，而square_ fire函数为信号处理函数，所以只需要修改square_fire的内容即可，即在文件square.c中进行修改。如下图，将对输入信号的处理i=i * i,修改成i=i * i * i。
![](http://a3.qpic.cn/psb?/V149UnPL1VXJy8/QlBzb3Wam*HJt50SPv*cAgTIQGBwr1gI32qzmfqbggs!/b/dMYAAAAAAAAA&ek=1&kp=1&pt=0&bo=cAAUAHAAFAADCC0!&sce=0-12-12&rf=viewer_311&t=5)

### 实验感想
1. /src文件夹内包含两种文件：*.c以及*.h，就是 实现 的模块，就是*.dot的框框的功能描述。每个模块实现两个接口，xxx_init和xxx_fire两个函数，分别是初始化这个模块的功能与活动。其中xxx是模块的名称。
2. generator_init作为generator模块的初始化函数，将当前位置置为0，设置生产者的长度。生产者从0开始不停地往后累加，每次生成一个整型或者浮点型的数字。
3. generator_fire是信号产生函数,consumer_fire是信号消费函数。两个函数都满足：如果当前位置大于生产长度就会销毁进程。
4. 在本次实验中，每一个模块和每一条线都有两个端口，每个端口都有一个对应的端口名。
5. .xml文件中connection是把线和框连接起来。
6. 如果example文件中的/src文件夹中的文件发生修改，需要将\build\bin\main 下对应的example文件夹删除后重新run才能够有修改与更新。

	


