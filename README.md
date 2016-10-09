#DOL配置过程
###1.安装必要环境
####（1）打开虚拟机命令行，输入$ sudo apt-get update并执行
####（2）执行$ sudo apt-get install ant
####（3）执行$ sudo apt-get install openjdk-7-jdk
####（4）执行$ sudo apt-get install unzip
###2.下载必要文件
####（1）在虚拟机中我们可以直接敲命令行
####$ sudo wget 
####http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz 
####$ sudo wget 
####http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip
####（2）或者我们可以直接在
#### http://jingyan.baidu.com/article/c33e3f48a5c153ea15cbb5b2.html
####中下载然后从主机拷到虚拟机里面（但是亲测好像不行）
###3解压我们需要的文件
####（1）打开命令行，输入$ mkdir dol新建dol的文件夹 
####（2）输入$ unzip dol_ethz.zip -d dol将dolethz.zip解压到 dol文件夹中
####（3）输入$ tar -zxvf systemc-2.3.1.tgz解压systemc
###4.编译systemc
####（1）解压后进入systemc-2.3.1的目录下，打开命令行输入$ cd systemc-2.3.1
####（2）新建一个临时文件夹objdir，输入$ mkdir objdir
####（3）进入该文件夹objdir，输入$ cd objdir
####（4）运行configure ，$ ../configure CXX=g++ --disable-async-updates
####得到如下结果即正确：
![MOU icon](http://i1.piimg.com/4851/1b537caece48621f.png)
####（5）编译 $ sudo make install 得到如下结果：
![MOU icon](http://i1.piimg.com/4851/325c016ad4ce64c0.png)
####（6）使用pew命令得到当前路径，待会有用
####（7）进入刚刚dol的文件夹$ cd ../dol修改build_zip.xml文件找到下面这段话，就是说上面编译的systemc位置在哪里，<property name="systemc.inc" value="YYY/include"/><property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>把YYY改成上页pwd的结果（注意，对于  64位 系统的机器，lib-linux要改成lib-linux64）
####然后是编译$ ant -f build_zip.xml all，若成功会显示build successful。接着可以试试运行第一个例子，进入build/bin/mian路径下 $ cd build/bin/main。然后运行第一个例子 $ ant -f runexample.xml -Dnumber=1
####成功结果如图：
![MOU icon](http://i1.piimg.com/4851/ca4c87bbf2a8be1a.png)
###5.runexample
####打开对应文件夹双击打开，下载推荐的软件，得到下图：
![MOU icon](http://i1.piimg.com/4851/62e6603aabd51e11.png)
###6.心得体会
####因为提前配置好了DOL，做的时候没有截图。。。因为实验文档要图文并茂，所以文档上用的是PPT的图片。然后说一下这次配置，总的来说没有什么问题，第二步中我直接下载拷进去试了很多次都不行，没办法只有在里面下载，没有问题只是有点慢，在过程中可能运气比较好，没有遇见问题，最后run example中下载的时候等一下，别急。感觉这次最大收获是学会makedown，感觉挺好用的。
