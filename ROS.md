# Ubuntu14.04安装和配置ROS

## 安装ROS
### 配置Ubuntu的软件源
1. 配置Ubuntu要求允许接受restricted、universe和multiverse的软件源,可以根据下面的链接配置:https://help.ubuntu.com/community/Repositories/Ubuntu
2. 配置成如下图所示即可，一般情况下，这些配置都是默认的。
![](http://upload-images.jianshu.io/upload_images/273380-3f5b0289d8e8e560.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 添加软件源到sources.list
	1. 设置软件源的代码如下：sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
	2. 一旦添加了正确的软件源，操作系统就知道去哪里下载程序，并根据命令自动安装软件。

### 设置密钥
	sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116

### 安装
	1. 首先确认你的Debian的软件包索引是最新的。Debian计划是一个致力于创建一个自由操作系统的合作组织。我们所创建的这个操作系统名为 Debian。Debian系统目前采用Linux内核或者FreeBSD内核。
		$ sudo apt-get update
	2. 在ROS中有许多不同的函数库和工具，建议是完全安装，也可以根据自己的要求分别安装。完全安装时的工具包括ROS、rqt、可视化环境rviz、通用机器人库robot-generic libraries、2D（如stage）和3D（如Gazebo）仿真环境2D/3D simulators、导航功能包集navigation and 2D/3D（移动、定位、地图绘制、机械臂控制）、感知库perception（如视觉、激光雷达、RGB-D摄像头等）。
		$ sudo apt-get install ros-indigo-desktop-full

### 初始化rosdep
	rosdep不仅能够使你更方便的安装一些系统依赖程序包，而且ROS的一些主要部件的运行也需要rosdep。
	$ sudo rosdep init	
	$ rosdep update

### 安装rosinstall
	rosinstall命令是一个使用的非常频繁的命令，使用这个命令可以轻松的下载许多ROS软件包。
	$ sudo apt-get install python-rosinstall

### 设置环境
	添加ROS的环境变量，这样，当你打开你新的shell时，你的bash会话中会自动添加环境变量。
	$ echo "source /opt/ros/indigo/setup.bash" >> ~/.bashrc
	# 使环境变量设置立即生效
	$ source ~/.bashrc

### 安装Tutorials
	$ apt-get source ros-jade-laser-pipeline

## 实验心得
	1. ROS(Robot Operating System）是一个机器人软件平台，它能为异质计算机集群提供类似操作系统的功能。
	2. ROS提供一些标准操作系统服务，例如硬件抽象，底层设备控制，常用功能实现，进程间消息以及数据包管理。ROS是基于一种图状架构，从而不同节点的进程能接受，发布，聚合各种信息（例如传感，控制，状态，规划等等）。目前ROS主要支持Ubuntu。
	3. ROS（Robot Operating System，下文简称“ROS”）是一个适用于机器人的开源的元操作系统。它提供了操作系统应有的服务，包括硬件抽象，底层设备控制，常用函数的实现，进程间消息传递，以及包管理。它也提供用于获取、编译、编写、和跨计算机运行代码所需的工具和库函数。
	4. ROS 的主要目标是为机器人研究和开发提供代码复用的支持。ROS是一个分布式的进程（也就是“节点”）框架，这些进程被封装在易于被分享和发布的程序包和功能包中。ROS也支持一种类似于代码储存库的联合系统，这个系统也可以实现工程的协作及发布。这个设计可以使一个工程的开发和实现从文件系统到用户接口完全独立决策（不受ROS限制）。同时，所有的工程都可以被ROS的基础工具整合在一起。



