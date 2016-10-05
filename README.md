#README
Student_ID: 14353063
Name: 傅一馨

##Description
The distributed operation layer (DOL) is a software development framework to program parallel applications. The DOL allows to specify applications based on the Kahn process network model of computation and features a simulation engine based on SystemC. Moreover, the DOL provides an XML-based specification format to describe the implementation of a parallel application on a multi-processor systems, including binding and mapping.
![pic](http://ww4.sinaimg.cn/large/0067oVAPgw1f8hk54y8mbj30rz0fcjub.jpg)
##Install
##### (1) 安装虚拟机，配置Ubuntu
 本次实验环境在Linux下进行，于是需要进行虚拟机配置。我选择使用Vmware，且由于上学期已配置完毕，于是这一步可以略过。
##### (2) 在虚拟机下配置ANT和OPENJDK等必要环境
1. 输入命令$	sudo apt-get update 进行软件源的更新。如下图所示可得，成功读取了软件包列表
![pic]("http://ww3.sinaimg.cn/large/0067oVAPgw1f8hl4wkqs6j30fy05had2.jpg")
2. 输入命令$	sudo apt-get install ant来下载/更新安装ant
![pic]("http://ww2.sinaimg.cn/large/0067oVAPgw1f8hl6i2ehuj30g703j75h.jpg")
3. 输入命令$ sudo apt-get install openjdk-7-jdk来更新openjdk
![pic]("http://ww2.sinaimg.cn/large/0067oVAPgw1f8hl6xciiyj30ge03j75p.jpg")
4. 输入命令$	sudo apt-get install unzip来更新unzip，为后续接下文件做准备
![pic]("http://ww3.sinaimg.cn/large/0067oVAPgw1f8hla9jun3j30gf03mmyf.jpg")
##### (3) 解压文件
1. 输入指令$	mkdir dol，新建名为dol的文件夹。由于是做完全部实验才截的图，从结果可以看到文件夹已存在，所以并没有替换。
![pic]("http://ww1.sinaimg.cn/large/0067oVAPgw1f8hlauszvej30hs032dh6.jpg")
2. 输入指令$	unzip dol_ethz.zip -d dol，将dolethz.zip解压到 dol文件夹中，并输入指令$	tar -zxvf systemc-2.3.1.tgz来解压systemc
![pic]("http://ww3.sinaimg.cn/large/0067oVAPgw1f8hlchyz4qj30g104kmzo.jpg")
##### (4) 编译systemc
1. 输入指令$	cd systemc-2.3.1，进入解压后得到的systemc-2.3.1的目录下，并通过指令$	mkdir objdir新建一个临时文件夹objdir，最后输入指令$cd objdir来进入该文件夹objdir
2. 输入指令$	../configure CXX=g++ --disable-async-updates，来运行configure(能根据系统的环境设置一下参数，用于编译)
![pic]("http://ww3.sinaimg.cn/large/0067oVAPgw1f8hlfbd36aj30hx073q5e.jpg")
3. 输入指令$	sudo make install进行编译，编译完后在文件目录能看到include, lib-linux64(对于32位系统，这里是lib-linux)。通过pwd得到并记录当前的工作路径。
![pic]("http://ww4.sinaimg.cn/large/0067oVAPgw1f8hlfur4g3j30hk03nmys.jpg")
##### (5) 编译dol
1. 通过指令$	cd ../dol进入刚刚dol的文件夹
2. 修改build_zip.xml文件
<property name="systemc.inc" value="YYY/include"/>
<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>
把YYY改成上页pwd的结果，由于linux系统为32位，所以不需要将lib-linux要改成lib-linux64
![pic]("http://ww1.sinaimg.cn/large/0067oVAPgw1f8hlgn0pf6j30kf027t9o.jpg")
3. 输入指令$	ant -f build_zip.xml all，来进行编译。如下图所示显示build successful，即编译成功
![pic]("http://ww1.sinaimg.cn/large/0067oVAPgw1f8hlh7abewj30am05s0td.jpg")
##### (6) 运行example1进行检测
1.输入指令$	cd build/bin/main，进入build/bin/mian路径下，然后输入指令$	ant -f runexample.xml -Dnumber=1来运行example1。结果如下图所示，说明成功。
![pic]("http://ww1.sinaimg.cn/large/0067oVAPgw1f8hlmws94kj30dl0cpn17.jpg")

##Experimental experience

实验LAB1中，由于已经配置好了ubuntu，没有像他人一样遇到太多问题。不过在实验中，第一次运行example1进行检测的时候出现了bug。后来才发现是我修改错了build_zip.xml文件，我误以为64位系统是说windows系统为64位，所以将lib-linux改成了lib-linux64，导致了最后build失败。后来再做第二遍的时候，及时醒悟，得以成功build。

不过在实验LAB2中，即在github和虚拟机上搭建远程仓库时，遇到了很多问题。这也是由于是看一眼教程做一步，没有完全理解指令和步骤的前后关联，出了很多问题。特别是在关联远程库时总是出现已经存在origin的报错，导致无法顺利进行后续步骤，但百度后得以解决。

通过本次实验，更深刻的理解了ANT的作用和优点：
Ant是一种基于Java的build工具,用Java的类来扩展,用于自动化调用程序完成项目的编译，打包，测试等。Ant是纯java语言编写的，所示具有很好的跨平台性。因为是由一个内置任务和可选任务组成的。Ant运行时需要一个XML文件(构建文件)。所以较为简单，且容易维护和书写，结构清晰。

在往后的DOL学习中，会进一步努力。



