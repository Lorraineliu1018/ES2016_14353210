## Description
   Distributed operation layer (DOL) is a software development framework to program parallel applications. The DOL allows to specify applications based on the Kahn process network model of computation and features a simulation engine based on SystemC. Moreover, the DOL provides an XML-based specification format to describe the implementation of a parallel application on a multi-processor systems, including binding and mapping.

## How To Install
### 1. 安装一些必要的环境
	$	sudo apt-get update
	$	sudo apt-get install ant	
	$ 	sudo apt-get install openjdk-7-jdk
	$	sudo apt-get install unzip
### 2. 下载文件
	sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz
	sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip
### 3. 解压文件
#### 新建dol的文件夹 
	$	mkdir dol
#### 将dolethz.zip解压到 dol文件夹中
	$	unzip dol_ethz.zip -d dol
#### 解压systemc
	$	tar -zxvf systemc-2.3.1.tgz
### 4. 编译systemc
#### 解压后进入systemc-2.3.1的目录下
	$	cd systemc-2.3.1
#### 新建一个临时文件夹objdir
	$	mkdir objdir
#### 进入该文件夹objdir
	$	cd objdir
#### 运行configure(能根据系统的环境设置一下参数，用于编译)
	$	../configure CXX=g++ --disable-async-updates
##### 运行后截图
![](http://a1.qpic.cn/psb?/V149UnPL1VXJy8/SRiWzFDqI1qUi7dJksFaKAq3jGSa0B0ywmMBXwPFSRI!/c/dMgAAAAAAAAA&ek=1&kp=1&pt=0&bo=1ALQAdQC0AEDCC0!&sce=0-12-12&rf=0-18)
#### 编译
	$	sudo make install
##### 编译完后文件目录如下($ cd ..        $ ls
![](http://a4.qpic.cn/psb?/V149UnPL1VXJy8/cEbGTFm0dQ9jbxt32rLjbY3XkNstVYxCTjPFG.vK7p4!/c/dFsBAAAAAAAA&ek=1&kp=1&pt=0&bo=ewJbAHsCWwADCC0!&sce=0-12-12&rf=0-18)
#### 记录当前的工作路径
	$	pwd
![](http://a3.qpic.cn/psb?/V149UnPL1VXJy8/TZbshTt2q8iwM.efsmHJqAplXwNjbpzBQWP7C2.OR1w!/c/dAYBAAAAAAAA&ek=1&kp=1&pt=0&bo=wQEpAMEBKQADCC0!&sce=0-12-12&rf=0-18)
### 5. 编译dol
#### 进入刚刚dol的文件夹
	$	cd ../dol
#### 修改build_zip.xml文件
    找到下面这段话，就是说上面编译的systemc位置在哪里，
	<property name="systemc.inc" value="YYY/include"/>
	<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>
	把YYY改成上页pwd的结果（注意，对于  64位 系统的机器，lib-linux要改成lib-linux64）
#### 然后是编译
	$	ant -f build_zip.xml all
#### 若成功会显示
	build successful
#### 接着可以试试运行第一个例子
	进入build/bin/mian路径下
	$	cd build/bin/main
	然后运行第一个例子
	$	ant -f runexample.xml -Dnumber=1
#### 成功结果如图
![](http://a4.qpic.cn/psb?/V149UnPL1VXJy8/wsWxZ.C*G*O8yKsRp7Bf7YGAazIOEo1*Hlwx1*rXi.c!/c/dMcAAAAAAAAA&ek=1&kp=1&pt=0&bo=1QLRAdUC0QEDCC0!&sce=0-12-12&rf=0-18)


## Experimental experience
1. 打开虚拟机后，需要打开虚拟机各项服务后,sudo apt-get update等各项指令才能运行成功，如下图：
![](http://a3.qpic.cn/psb?/V149UnPL1VXJy8/xKakWY4n8EoqbQJYYexH0zSLGBymK2ue19hMqk2vzVg!/c/dAYBAAAAAAAA&ek=1&kp=1&pt=0&bo=fAFrAHwBawADCC0!&sce=0-12-12&rf=0-18)
2. 如果打开各项服务后仍然指令仍然无法运行成功考虑换源。换成阿里云或163的源都可以：

	![](http://a4.qpic.cn/psb?/V149UnPL1VXJy8/8TPBpc4agOhkge29*OYsqJZ7je4BZ*UjWzL.dqBSjV4!/b/dMcAAAAAAAAA&ek=1&kp=1&pt=0&bo=6wAkAOsAJAADCC0!&sce=0-12-12&rf=viewer_311&t=5)

	![](http://a3.qpic.cn/psb?/V149UnPL1VXJy8/VoLUwDnXn0pftfPQB2qzlB7zMVYxQjgV1flI*THVSNU!/c/dAYBAAAAAAAA&ek=1&kp=1&pt=0&bo=mgCAAJoAgAADACU!&sce=0-12-12&rf=0-18)

	![](http://a4.qpic.cn/psb?/V149UnPL1VXJy8/YYCTBnJu2NbAQgOaxOIj7voF3jZdxPRmetQlfeIZXPM!/c/dMcAAAAAAAAA&ek=1&kp=1&pt=0&bo=LAIvACwCLwADCC0!&sce=0-12-12&rf=0-18)
3. 下载的两个文件尽量放在home文件夹中，如果放在home文件夹的子文件夹中容易使得最后一步runexample失败。
4. make和ant的区别：make是基于C语言，而ant是基于Java语言。
