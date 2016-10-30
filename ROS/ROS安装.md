#ES2016_14353363
ROS安装

> 整篇实验文档按照[ros.org](http://wiki.ros.org/kinetic/Installation/)的Ubuntu指导教程进行，其中实验环境为Ubuntu 15.10

##安装

### 建立sources.list

检查建立sources.list的资源网站，我们找到各个国家的[ROS镜像](http://wiki.ros.org/ROS/Installation/UbuntuMirrors)，竟然中大的镜像[ros资源](http://mirror.sysu.edu.cn/ros/)，以及引用指令，果断使用。

`sudo sh -c '. /etc/lsb-release && echo "deb http://mirror.sysu.edu.cn/ros/ubuntu/ $DISTRIB_CODENAME main" > /etc/apt/sources.list.d/ros-latest.list'`

### 建立秘钥
`sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116`

### 安装

* 检查Ubuntu更新   `sudo apt-get update`
![image](https://cloud.githubusercontent.com/assets/18045191/19835637/f9b4df82-9ec7-11e6-8bdc-7272b98ec8f1.png)

* 安装ROS `sudo apt-get install ros-kinetic-desktop-full` <br>
这里我选的是桌面版全套套件版 <br>
顺利进行。（ps.活了这么久还真不知道中大自己竟然有一个镜像网站）<br>
安装完成（安装时间上镜像网站看了一圈，资源挺少的，资源还挺旧了）

![image](https://cloud.githubusercontent.com/assets/18045191/19835936/c7592d44-9ecd-11e6-9cd4-4208fcc84e40.png)

### 初始化ROSDEP
`sudo rosdep init` <br>
`rosdep update`

![image](https://cloud.githubusercontent.com/assets/18045191/19835947/26b14290-9ece-11e6-9341-496b098c02ce.png)


### 搭建环境

这里我果断选择了第一个指令
`echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc` <br>
`source ~/.bashrc`

### 安装rosinstall

`sudo apt-get install python-rosinstall`

![image](https://cloud.githubusercontent.com/assets/18045191/19835956/52ea79f8-9ece-11e6-84f0-3ae2ef7abab7.png)

安装完毕

![image](https://cloud.githubusercontent.com/assets/18045191/19835973/9b49a052-9ece-11e6-944c-a203db2cfb7a.png)

到这里ROS的安装就完成了。我尝试着试用一下检查是否正常。

## 在ROS中安装Cartographer

这部分根据一份[谷歌文档](https://google-cartographer-ros.readthedocs.io/en/latest/)所编写

### 安装wstool和rosdep
`sudo apt-get update` <br>
`sudo apt-get install -y python-wstool python-rosdep ninja-build`

![image](https://cloud.githubusercontent.com/assets/18045191/19836047/c7298924-9ed0-11e6-9d87-9a198ba0d17c.png)

### 新建一个文件夹 'catkin_ws'.
`mkdir catkin_ws` <br>
`cd catkin_ws` <br>
`wstool init src`

![image](https://cloud.githubusercontent.com/assets/18045191/19836062/1063b8c6-9ed1-11e6-8740-11c2423a3c53.png)

### 合并 the cartographer_ros.rosinstall文件及其依赖性代码(下面其实只有两行指令，第一行因为指令过长，被自动换行看着像两行，为了方便，我已经将两个指令分开)
`wstool merge -t src https://raw.githubusercontent.com/googlecartographer/cartographer_ros/master/cartographer_ros.rosinstall` <br><br>
`wstool update -t src`

![image](https://cloud.githubusercontent.com/assets/18045191/19836122/735c9ad2-9ed2-11e6-8daa-919e09a7c3ae.png)

### 安装 deb 依赖
`rosdep init` <br>
`rosdep update` <br>
`rosdep install --from-paths src --ignore-src --rosdistro=${ROS_DISTRO} -y`

![image](https://cloud.githubusercontent.com/assets/18045191/19836204/2fe362de-9ed4-11e6-9e58-b617b34fa46e.png)

### Build 并且 install
`catkin_make_isolated --install --use-ninja` <br>
`source install_isolated/setup.bash`