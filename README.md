# ES2016_14353363

Embedded Systems Lab
#Description

分布式操作层（DOL）是一个框架，它能够使应用程序（半）自动映射到多处理器SHAPES架构平台。<br>
DOL允许指定基于KPN模型计算的应用程序，并且能够设定一个基于SystemC的模拟引擎。<br>
同时，劳工部提供了一个基于XML的规范格式，来描述在一个多处理器系统中并行应用程序的执行，包括绑定和映射操作。
<br>

#Install
实验之前给Ubuntu配置好必要的环境（ant工具，jdk，unzip工具）

* $ sudo apt-get update
* $ sudo apt-get install ant
* $ sudo apt-get install openjdk-7-jdk
* $ sudo apt-get install unzip
<br><br>

##下载文件

提前下载好[systemc-2.3.1.tgz](http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz)和[dol_ethz.zip](http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip)文件，拖进ubuntu中备用。
<br>
<br>

##解压文件

* 新建dol的文件夹 <br>
`$	mkdir dol`
* 将dolethz.zip解压到 dol文件夹中 <br>
`$	unzip dol_ethz.zip -d dol`
* 解压systemc <br>
`$	tar -zxvf systemc-2.3.1.tgz`
<br>
<br>

##编译systemc

* 解压后进入systemc-2.3.1的目录下<br>
`$	cd systemc-2.3.1`<br>
* 新建一个临时文件夹objdir<br>
`$	mkdir objdir`<br>
* 进入该文件夹objdir<br>
`$	cd objdir`<br>
* 运行configure(能根据系统的环境设置一下参数，用于编译)<br>
`$	../configure CXX=g++ --disable-async-updates`<br>
![贴图1](https://cloud.githubusercontent.com/assets/18045191/19217689/b50cb02c-8e13-11e6-8101-761451c6ad42.png "运行结果1")<br>
* 编译<br>
`$	ant -f build_zip.xml all`<br>
![贴图2](https://cloud.githubusercontent.com/assets/18045191/19217722/5a4c7dce-8e14-11e6-98f2-f1b2e8dd30ea.png "运行结果2")<br>
* 然后运行第一个例子<br>
`$	cd build/bin/main` <br>
`$	sudo ant -f runexample.xml -Dnumber=1`
![贴图3](https://cloud.githubusercontent.com/assets/18045191/19217747/12cac842-8e15-11e6-854f-a51e55d58be0.png "运行结果3")<br>
<br>
<br>

#Experimental experience

经过本次试验，对于github有了一定基础的了解（其实很久以前就已经注册了github，但是一直只是下下资料什么的），开始使用github进行一些工程的上传。但是对于ant什么的还是亿脸懵逼，打开runexample.xml文件，感觉目前并不能够从中读出什么很有用的内容。<br>
今后的实验感觉还是任重道远，需要学习的东西还是很多的。
