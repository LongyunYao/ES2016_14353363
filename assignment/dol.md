# ES2016_14353363 <br> ——dol实验

**实验之前的知识预备**
<br><br>
在上一周我们已经在实验的最后尝试着运行了example1，实验过程具体见readme.md文件。
通过实验我们可以知道运行方法是<br>

 > 找在dol的文件目录下<br>
 > 进入 `build->bin->main`文件夹中<br>
 > 执行 `$ ant -f runexample.xml -Dnumber=1` 指令

![编译代码](https://cloud.githubusercontent.com/assets/18045191/19696054/2e57e9d6-9b18-11e6-87d6-62ea7a63928c.png)

知道了这些，我们就可以开始进行本次实验的代码理解以及操作了。

##1. example1的理解

首先查看example1的dol图，我们先根据dol图理解一下xml代码
<center>
![example1](https://cloud.githubusercontent.com/assets/18045191/19696770/395bd97a-9b1b-11e6-8ba3-b2fddefba9b3.png)
</center>

再查看xml文件
<center>
![image](https://cloud.githubusercontent.com/assets/18045191/19696878/94e22a7e-9b1b-11e6-9a4f-a4f7c20286c8.png)
</center>

<center>
![channel](https://cloud.githubusercontent.com/assets/18045191/19697351/9b68293c-9b1d-11e6-85d9-f1ad931c9064.png)
</center>

 > 通过三张图我们可以发现

<center>
<table>
<tr>
    <th>生产者generator</th>
    <th>平方模块square</th>
    <th>消费者consumer</th>
    <th>channels C1</th>
    <th>channels C2</th>
</tr>
<tr align="center">
    <td align>output端口 "1"</td>
    <td align>output端口 "2" <br> & <br>input端口 "1"</td>
    <td align>input端口 "1"</td>
    <td align>output端口 "1"  <br> & <br>input端口 "0"</td>
    <td align>output端口 "1"  <br> & <br>input端口 "0"</td>
</tr>
</table>
</center>

接下来就是将它们级联串起来
<center>
![image](https://cloud.githubusercontent.com/assets/18045191/19698259/2946c1d4-9b21-11e6-96b8-5020de74b394.png)
![image](https://cloud.githubusercontent.com/assets/18045191/19698316/620fb516-9b21-11e6-9e8f-ccec4eee515f.png)
</center>


这一步结束之后，整个dol图就完成了，虽然其实本次实验最重要的并不是这个。。。

---

在看本次实验最重要的模块——square之前，我们先看生产者和消费者怎么定义的

![image](https://cloud.githubusercontent.com/assets/18045191/19698509/215d3c18-9b22-11e6-97c4-11eeab405b7d.png)

大概看懂了代码之后，我们就可以开始看square函数了
<center>
![image](https://cloud.githubusercontent.com/assets/18045191/19698722/0872172c-9b23-11e6-89be-1a888523fef8.png)
</center>

代码不难读懂，我们已经知道本文头图产生的原因了，接下来就是完成本次实验，将平方改成立方。

##2. example1的修改
<center>
![image](https://cloud.githubusercontent.com/assets/18045191/19698875/8d6bb834-9b23-11e6-8f42-da232288f3f5.png)
</center>

**修改完毕之后，将**`dol->build->bin->main`**中的**`example1`**文件夹删除掉，根据本文开头的命令行编译运行检查结果。（如果不删除，ant会直接运行你之前已经编译好的文件）**

正在编译

![image](https://cloud.githubusercontent.com/assets/18045191/19699092/74cc6c3c-9b24-11e6-9f17-24606a5b1de4.png)

运行结果

![image](https://cloud.githubusercontent.com/assets/18045191/19699119/8f245df6-9b24-11e6-95c9-e77bec04576e.png)

实验结果正确，达到实验目的。

##3. example2的理解

前面example1瞎掰扯了那么久是为了以后回头看这份文档不用一脸懵逼，上道之后的dol实验我就不这么详细的解释了。

修改之后的代码&修改的地方
<center>
![image](https://cloud.githubusercontent.com/assets/18045191/19699274/50659886-9b25-11e6-9cf8-04247b86d282.png)
</center>

* 修改的原因
通过下图，我们可以很明显的发现，连接生产者和消费者之间的square由下面代码完成，并且，通过修改range便可以控制square的个数，因此我们只需要将初始化的N的value定义为2，就能够起到控制迭代的次数。

<center>
![image](https://cloud.githubusercontent.com/assets/18045191/19699340/91b461b4-9b25-11e6-9fc4-ff37d1bbe853.png)
</center>

观察dot图发现，我们成功的达到了本次的实验目标。

<center>
![image](https://cloud.githubusercontent.com/assets/18045191/19699512/30f9b8c8-9b26-11e6-98d0-6f78367d33ee.png)
</center>

到此，Lab3完结，撒花。