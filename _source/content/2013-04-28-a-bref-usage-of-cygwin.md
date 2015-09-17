# Cygwin：在window下用linux的方式工作

- date: 2013-04-28 23:17
- tags: 技术, Cygwin

---------------------------------------

## 缘起

咧威习惯了linux之后，换到Windows没有命令行就特别不爽。另一个原因是咧威的朋友CXY在学校没有自己的电脑，只能去机房或者网吧，用linux不方便，虚拟机占资源太大。

## Cygwin VS MinGW

这个两个都是在windows体验Linux的工具。[MinGW](http://zh.wikipedia.org/wiki/MinGW "MinGW") (Minimalist GNU for Windows) 很精简，只提供了常用的软件，对中文支持不太好。而[Cygwin](http://zh.wikipedia.org/wiki/Cygwin "Cygwin")
提供了大量的工具，更能满足在Windows上用Linux方式工作的需求，希望它能够帮助你摆脱对Windows的依赖。

### 安装

点击[下载](http://cygwin.com/setup.exe) setup.exe，下载完后双击即可开始安装。

####1. 选择第一个从网上下载安装。
![setup1](/media/2013-04-28-a-bref-usage-of-cygwin/setup1.jpg)

####2. 选择安装的目录，咧威选择的是U盘的目录，根据你自己的情况而定.然后选择“All Users”所有用户都可以使用。
![setup2](/media/2013-04-28-a-bref-usage-of-cygwin/setup2.png)

#### 3. 选择一个用来放安装文件的目录,我起了“CygwinInstall-file”这个名字，跟安装目录相区别
![setup3](/media/2013-04-28-a-bref-usage-of-cygwin/setup3.png)

#### 4. 弹出“文件夹不存在，是否创建”，选择“是”
![setup4](/media/2013-04-28-a-bref-usage-of-cygwin/setup4.png)

#### 5. 选择第一个“Direct Connection”直接连接
![setup5](/media/2013-04-28-a-bref-usage-of-cygwin/setup5.png)

#### 6. 在“User URL：” 那一栏输入 ftp://ftp.iij.ad.jp/pub/cygwin/ 然后点击“Add” 就是自动选择 ftp://ftp.iij.ad.jp/pub/cygwin/ 最后点击“下一步”就行了
![setup6](/media/2013-04-28-a-bref-usage-of-cygwin/setup6.png)

#### 7. 在"Search" 输入 gcc 搜索，然后点击Devel组前的+号，找到 gcc4-core gcc4-g++，
![setup7](/media/2013-04-28-a-bref-usage-of-cygwin/setup7.png)

#### 点击Skip变成如图所示
![setup8](/media/2013-04-28-a-bref-usage-of-cygwin/setup8.png)

#### 8. 同理搜索并选择一下安装包
 -  Devel组：make 
 -  Editors组： vim vim-common 

#### 9. 最后一路点击“下一步”就可以了,以后再需要再安装什么软件，再次重复上述步骤，搜索安装就OK了。

## 配置

#### 1. 如何访问Windows的盘符

执行 mount 命令后可以看到Windows下的盘符被映射到 /cygdrive 特殊目录下。

	$ mount
	F:/Cygwin/bin on /usr/bin type ntfs (binary,auto)   注释：F盘为安装Cygwin所在的盘
	F:/Cygwin/lib on /usr/lib type ntfs (binary,auto)
	F:/Cygwin on / type ntfs (binary,auto)
	C: on /cygdrive/c type ntfs (binary,posix=0,user,noumount,auto)
	D: on /cygdrive/d type ntfs (binary,posix=0,user,noumount,auto)
	E: on /cygdrive/e type ntfs (binary,posix=0,user,noumount,auto)
	F: on /cygdrive/f type vfat (binary,posix=0,user,noumount,auto)

也就是说，例如，/cygdrive/c 对应的就是C盘。Cygwin 还提供了 cygpath 命令来实现Windows平台和Cygwin之间名称的变换，如下所示：

	$ cygpath -u C:\\Windows   注释： -u 代表 --unix 记住是C:\\而不是C:\
	/cygdrive/c/Windows		   注释：  把C:\Windows 转换成在Cygwin的路径

	$ cygpath -w ~/			   注释： -w 代表 --windows ～/ 是用户的home目录
	F:\Cygwin\home\think\	   注释：  F： 是咧威安装Cygwin的目录所在的盘，think是咧威的用户名


####2. 用户主目录不一致的问题

Cygwin 确定用户主目录有几个不同的依据，要按照顺序确定主目录：首先查看系统的 HOME 环境变量，其次查看 /etc/passwd 中为用户设置的主目录。有的软件遵照这个原则，而有些 Cygwin 应用如 SSH，却没有使用 HOME 环境变量而是直接使用 /etc/passwd 中的设置。要想避免在同一个 Cygwin 环境下有两个不同的用户主目录设置，可以采用下面两种方法。

方法1：修改 Cygwin 启动的批处理文件（如：C:\cygwin\Cygwin.bat ），在批处理的开头添加如下的一行代码，就可以防止其他软件在 Windows 引入的 HOME 环境变量被带入到 Cygwin 中。

    set HOME= 

方法2：如果希望使用 HOME 环境变量指向的主目录，则可通过手工编辑 /etc/passwd 文件，将其中的用户主目录修改成 HOME 环境变量所指向的目录。

####3. 命令行补齐忽略文件名大小写

Windows 的文件系统忽略文件名的大小写，在 Cygwin 下最好对命令行补齐进行相关设置，以忽略大小写，这样使用起来更方便。

编辑文件 ~/.inputrc ，在其中添加设置“set completion-ignore-case on”，或者取消已有的相关设置前面的井（#）号注释符。修改完毕后，再重新进入 Cygwin，这样就可以实现命令行补齐对文件名大小写的忽略。

####4.将Cygwin 添加到右键菜单里
![setup9](/media/2013-04-28-a-bref-usage-of-cygwin/setup9.png)

在实际使用中，要在Cygwin 用cd 进入某个盘，某个文件夹里有点麻烦，我一般是一路鼠标双击进入之后右键，打开Cygwin 就是在当前目录了。

配置方式如下：

1. 在cygwin命令行执行如下命令，如果出现命令未找到，说明chere程序没有安装，使用cygwin的setup.exe安装chere。
    
    ```
    chere -i -fp -c -t mintty
    ```

2. 默认只添加文件夹和驱动器的右键菜单，
新建以 **.reg** 为后缀名的文件。方法：右击，在“右键菜单”中选择“新建”，在“新建”中选择文本文档，然后重命名，连同 **.txt** 也改了 。例如我新建的是 **menu.reg** 。选择它右键，在打开方式选择“记事本”。输入以下：

    ```
    Windows Registry Editor Version 5.00

    [HKEY_CLASSES_ROOT\Directory\Background\shell\cygwin_bash]  
    @="打开 Cygwin"  
    [HKEY_CLASSES_ROOT\Directory\Background\shell\cygwin_bash\command]  
    @="F:\\cygwin\\bin\\mintty.exe -e f:\\cygwin\\bin\\bash -c \"/bin/xhere /bin/bash.exe\""  
    ```
    
**注意：** ```@="F:\\\cygwin``` 中的F：改为你Cygwin安装所在的盘。我这里是F盘。然后双击这个文件，点击“是”就OK了。

如果出现 **“您在注册表编辑器中只能导入二进位注册文件”** 的错误, 用记事本打开然后另存为 **ANSI 编码格式**。如果不改名保存提示“是否替换” 选择 “是”。

![setup10](/media/2013-04-28-a-bref-usage-of-cygwin/setup10.png)

##开始体验Cygwin的linux工作方式

以后如果需要，再次打开 setup.exe 重新上述方法即可

推荐的学习linux资料当然[鸟哥私房菜](http://linux.vbird.org/ "鸟哥私房菜")啦，从左边的导航栏开始看起，从“新手建议”——>“开始阅读之前”——>……最后

>**注意：**简体主站就不去看了，翻译得不是很好，宁愿你去搜索鸟哥私房菜的电子书。第三章和第四章也可以不用看了，这和安装Linux相关，而我们已经在Windows下构建好了Linux

	
##有什么问题可以在下面评论
	
		


	


