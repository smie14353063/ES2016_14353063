# 基于Ubuntu14.04的ROS安装配置
Studen_ID: 14353063		Name:傅一馨

##一、实验步骤
##### 1.建立source.list
将计算机设置为可以接受来自 packages.ros.org. ROS Jade的软件。

	sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) 
	main" > /etc/apt/sources.list.d/ros-latest.list'

![pic](D:\OneDrive\Third_Academic_1\Embed\LAB05\lab5_01.png)


##### 2. 设置Key
	sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key
	0xB01FA116
![pic](D:\OneDrive\Third_Academic_1\Embed\LAB05\lab5_02.png)


##### 3. 安装
首先，通过update确保Debian软件包索引是最新的。

	sudo apt-get update
![pic](D:\OneDrive\Third_Academic_1\Embed\LAB05\lab5_03.png)

然后选择Desktop-Full Install进行安装。

	sudo apt-get install ros-jade-desktop-full
![pic](D:\OneDrive\Third_Academic_1\Embed\LAB05\lab5_04.png)

##### 4. 初始化rosdep
在使用ROS之前需要初始化rosdep。 rosdep能够为要编译的源安装系统依赖项，并且需要在ROS中运行一些核心组件。

	sudo rosdep init
![pic](D:\OneDrive\Third_Academic_1\Embed\LAB05\lab5_05.png)

	rosdep update

![pic](D:\OneDrive\Third_Academic_1\Embed\LAB05\lab5_06.png)


##### 5.环境搭建
如下代码可以使ROS环境变量在每次启动新shell时自动添加到bash会话中。

	echo "source /opt/ros/jade/setup.bash" >> ~/.bashrc
	source ~/.bashrc
	source /opt/ros/jade/setup.bash
![pic](D:\OneDrive\Third_Academic_1\Embed\LAB05\lab5_07.png)


##### 6. 安装rosinstall
rosinstall是ROS中独立的常用命令行工具。 它能够使用一个命令轻松下载ROS软件包的许多源代码树。

	sudo apt-get install python-rosinstall
![pic](D:\OneDrive\Third_Academic_1\Embed\LAB05\lab5_08.png)


##### 7. 检测ROS安装配置情况
	 apt-get source ros-jade-laser-pipeline
 

##二、实验感想
####(1)实验中遇到的问题
1.指令运行失败：sudo rosdep init

错误原因：正如报错所说，是网络异常问题。需要在虚拟机的网管设置里设置NAT连接。设置好后网络恢复正常，即可顺利完成初始化。

![pic](D:\OneDrive\Third_Academic_1\Embed\LAB05\lab5_10.png)

2.指令运行失败：apt-get source ros-jade-laser-pipeline

![pic](D:\OneDrive\Third_Academic_1\Embed\LAB05\lab5_11.png)
####(2)心得感想
　　本次实验中，进行了ROS的配置与验证。

　　正如ppt中所说，配置全程基本都是复制粘贴，但是通过仔细阅读教程，学习理解了ROS配置过程中一些步骤的作用和必要原因。

　　通过本次实验，学习了ROS在Ubuntu上的安装方法，为下周的实验做出准备。




