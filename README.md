## 嵌入式系统实验 _ Lab2_DOL
#### *·Description*
这次实验是对dol进行安装，但是对于dol框架不是很了解，相信会随着实验的进行会有更深的了解的。
#### *·How to install*
首先要配置一些必要的安装环境ant、jdk、unzip：

    $	sudo apt-get update
    $	sudo apt-get install ant
    $ 	sudo apt-get install openjdk-7-jdk
    $	sudo apt-get install unzip       
     
然后下载文件：

    `sudo wget http://www.accellera.org/images/downloads/
					standards/systemc/systemc-2.3.1.tgz`
    `sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip`

解压并编译systemc：

    $	mkdir dol
	$	unzip dol_ethz.zip -d dol
	$	tar -zxvf systemc-2.3.1.tgz
	$	cd systemc-2.3.1
	$	mkdir objdir
	$	cd objdir
	$	../configure --prefix=/usr/local/systemc-2.3.1
	$	sudo make install
	$	pwd
这里的$	../configure --prefix=/usr/local/systemc-2.3.1是我在进行配置的时候一直配置不成功，在网上查了一下要用到这个语句，而不是用实验文档里的语句，这里用pwd记录下路径，然后找到build_zip.xml文件进行修改

    <property name="systemc.inc" value="YYY/include"/>
	<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>

将文件中的YYY改成pwd的结果。
编译dol：

    $	ant -f build_zip.xml all
	$	ant -f runexample.xml -Dnumber=1
当出现BUILD 	SUCCESSFUL就成功了。
#### *·Experimental exper*
配置dol还是蛮简单的，只要按照步骤一步一步配置就行了，配置的时候遇到了点问题，在网上查了资料，废了不少时间，但最后还是顺利的解决了，