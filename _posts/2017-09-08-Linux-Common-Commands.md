---
layout:     post
title:      Linux常用命令
subtitle:   常用的Linux命令大全
date:       2017-09-08
author:     Mlin
header-img: img/post-bg-linuxcmd.jpg
catalog: true
tags:
    - Linux
    - CMD
    - shell
---


> 本文首次发布于 [Mlin Blog](http://happymiki.top)、[简书](http://www.jianshu.com/u/3f05018752b8)，作者 [@木林(Mlin)](http://github.com/happymiki) ,转载请保留原文链接。

> 上一篇文章 [《uboot主Makefile分析》](https://happymiki.github.io/2017/09/03/uboot主Makefile/)。


# 前言
linux命令是对Linux系统进行管理的命令。对于Linux系统来说，无论是中央处理器、内存、磁盘驱动器、键盘、鼠标，还是用户等都是文件，Linux系统管理的命令是它正常运行的核心，与之前的DOS命令类似。linux命令在系统中有两种类型：内置Shell命令和Linux命令。想要在Linux系统之中随心所欲的行走那就离不开掌握常用的Linux命令，下面就以ubuntu下的命令为例整理的Linux常用的命令。

# 目录
- 一、文件目录操作命令
	- (1) ls（list，列表）
	- (2) cd（change directory，更改目录）
	- (3) pwd（print work directory，打印工作目录）
	- (4) mkdir（make directory，创建文件夹）
	- (5) mv（move，移动）
	- (6) touch
	- (7) cp（copy，复制）
	- (8) rm（remove，去除，删除）
	- (9) cat
	- (10)rmdir（remove directory，删除文件夹）
	- (11)nl
	- (12)more
	- (13)less
	- (14)head
	- (15)tail
	- (16) ln（link，连接文件）
	- (17) man
	- (18) apt-get
- 二、文件查找命令
	- (1) which	
	- (2) whereis
	- (3) locate
- 三、vim编辑器常用命令	
	- (1) 保存，退出
	- (2) 查找
	- (3) 快速切换行
	- (4) 设置显示行号
	- (5) 行删除
	- (6) 行复制、粘贴
# 正文
## 一、文件目录操作命令
#### (1) ls（list，列表）
**作用：**列出目标目录中所有的子目录和文件。

**用法：**

	ls [选项] [目录名]

	ls -a	显示所有文件，包括隐藏文件
	ls -l	以详细信息显示
	ls -a -l
	ls -l -a
	ls -la
	ls -al	四种方式都是可以的

ls -l显示的详细信息中：

	-rw-r--r--
	
	drwxr-xr-x

一共10个字符，第一个字符表示文件类型，后面9个字符表示文件权限。

文件类型：

	-：表示普通文件。普通文件指文本文件和二进制文件，如a.c  1.txt a.out都是普通文件
	d：表示文件夹，d是directory的缩写
	l：表示符号连接文件，后面会用->打印出它指向的文件
	s：表示socket文件
	p：表示管道文件 pipe

#### (2) cd（change directory，更改目录）
作用：用来切换目录

用法：

	cd [目录名]

涉及到相对路径和绝对路径 

	/    代表系统根目录
	~    代表用户所在目录
	-    代表前一次目录
	..   代表上一层目录
	.    代表当前目录

#### (3) pwd（print work directory，打印工作目录）
作用：查看”当前工作目录“的完整路径

用法：

	pwd [选项]

格式：pwd -P  显示出实际路径，而非使用连接（link）路径。 

#### (4) mkdir（make directory，创建文件夹）
作用：创建空文件夹

用法：

	mkdir [选项] 目录...

命令参数：

	-m, --mode=模式，设定权限<模式> (类似 chmod)，而不是 rwxrwxrwx 减 umask
	-p, --parents  可以是一个路径名称。此时若路径中的某些目录尚不存在,加上此选项后,系统将自动建立好那些尚不存在的目录,即一次可以建立多个目录; 
	-v, --verbose  每次创建新目录都显示信息
	--help   显示此帮助信息并退出
	--version  输出版本信息并退出

#### (5) mv（move，移动）
作用：在目录间移动文件，重命名文件

用法：

	mv [选项] 源文件或目录 目标文件或目录

命令参数：

	-b ：若需覆盖文件，则覆盖前先行备份。 
	-f ：force 强制的意思，如果目标文件已经存在，不会询问而直接覆盖；
	-i ：若目标文件 (destination) 已经存在时，就会询问是否覆盖！
	-u ：若目标文件已经存在，且 source 比较新，才会更新(update)
	-t  ： --target-directory=DIRECTORY move all SOURCE arguments into DIRECTORY，即指定mv的目标目录，该选项适用于移动多个源文件到一个目录的情况，此时目标目录在前，源文件在后。


#### (6) touch
作用：创建空文件

用法：

	touch [选项]... 文件...

命令参数:

	-a   或--time=atime或--time=access或--time=use 　只更改存取时间。
	-c   或--no-create 　不建立任何文档。
	-d 　使用指定的日期时间，而非现在的时间。
	-f 　此参数将忽略不予处理，仅负责解决BSD版本touch指令的兼容性问题。
	-m   或--time=mtime或--time=modify 　只更改变动时间。
	-r 　把指定文档或目录的日期时间，统统设成和参考文档或目录的日期时间相同。
	-t 　使用指定的日期时间，而非现在的时间。

#### (7) cp（copy，复制）
作用：复制文件或文件夹

用法：

	cp [选项]... [-T] 源 目的
	或：cp [选项]... 源... 目录
	或：cp [选项]... -t 目录 源...

	cp -r 用来复制文件夹
	cp -f 强制复制

实际操作时：一般都是cp -f复制文件，cp -rf复制文件夹

#### (8) rm（remove，去除，删除）
作用：用来删除文件，文件夹

用法：

	rm [选项] 文件… 

命令参数：

	-r, -R, --recursive   指示rm将参数中列出的全部目录和子目录均递归地删除。
	-f, --force    忽略不存在的文件，从不给出提示。
	-i, --interactive 进行交互式删除
	-r, -R, --recursive   指示rm将参数中列出的全部目录和子目录均递归地删除。

常用：
rm -r 文件
rm -rf 文件夹
	
#### (9) cat
作用：直接在命令行下显示文件内容

用法：

	cat [选项] [文件]...

cat主要有三大功能：

	1.一次显示整个文件:cat filename
	2.从键盘创建一个文件:cat > filename 只能创建新文件,不能编辑已有文件.
	3.将几个文件合并为一个文件:cat file1 file2 > file

#### (10)rmdir（remove directory，删除文件夹）
作用：删除空文件夹
用法：

	rmdir [选项]... 目录...

命令参数：

	-p 递归删除目录dirname，当子目录删除后其父目录为空时，也一同被删除。
	-v, --verbose  显示指令执行过程 

rmdir和rm -r的区别：rmdir只能删除空文件夹，而rm -r可以删除空文件夹和非空文件夹

#### (11)nl
作用：显示行号查看文件内容

用法：

	nl [选项]... [文件]...

#### (12)more
作用：more命令和cat的功能一样都是查看文件里的内容，但有所不同的是more可以按页来查看文件的内容，还支持直接跳转行等功能。

用法：

	more [-dlfpcsu ] [-num ] [+/ pattern] [+ linenum] [file ... ] 


#### (13)less
作用：less 与 more 类似，但使用 less 可以随意浏览文件，而 more 仅能向前移动，却不能向后移动，而且 less 在查看之前不会加载整个文件。

用法：

	less [参数]  文件 

#### (14)head
作用：显示行号查看文件内容

用法：

	head [参数]... [文件]...  

命令参数：

	-q 隐藏文件名
	-v 显示文件名
	-c<字节> 显示字节数
	-n<行数> 显示的行数

#### (15)tail
作用：用于显示指定文件末尾内容，不指定文件时，作为输入信息进行处理。常用查看日志文件。

用法：

	tail[必要参数][选择参数][文件]   

命令参数：

	-f 循环读取
	-q 不显示处理信息
	-v 显示详细的处理信息
	-c<数目> 显示的字节数
	-n<行数> 显示行数
	--pid=PID 与-f合用,表示在进程ID,PID死掉之后结束. 
	-q, --quiet, --silent 从不输出给出文件名的首部 
	-s, --sleep-interval=S 与-f合用,表示在每次反复的间隔休眠S秒 

#### (16) ln（link，连接文件）
基础：windows中快捷方式，实际上快捷方式和它指向的文件是独立的两个文件，两个都占硬盘空间，只不过用户访问快捷方式时，其效果等同于访问指向的文件。	

作用：创建软连接文件

用法：

	ln -s 源文件名 符号连接文件名

举例：ln -s src.c，linker.c，	linker.c就是
src.c的一个符号连接文件

linux中有两种连接文件：
一种叫软连接（符号连接），等同于windows中快捷方式，一种叫硬连接

硬连接：ln 源文件名 连接文件名
硬连接实际上和源文件在硬盘中是同一个东西，效果类似于硬盘上的一个文件，在文件系统上，在我们看来有好多个文件一样。每次删除一个文件时，只要他还有其他的硬连接存在，这个文件就不会被真正删除。只有等所有的连接文件都删除掉了，这个文件才会被真正从硬盘上删除。


#### (17) man
作用：查询man手册，获得帮助信息
用法：

	man 1 ls		1表示查询的是linux命令
	man 2 xxx		2表示查询的是linux api
	man 3 xxx		3表示查询的是C库函数

注意：在man手册中查询时，退出按Q键（Q就是quit的缩写）

#### (18) apt-get
作用：在ubuntu中用来在线安装、卸载软件的程序

用法：

	apt-get update			更新源
	apt-get install xxx		安装软件
	apt-get remove xxx		卸载软件

**说明：apt-get 安装软件的原理和必要性。**

linux操作系统的发行版，内核版本，定制性，造成了linux中软件的不兼容性。在linux中安装软件是一件困难的事情，装了软件能不能用不一定。ubuntu解决了这个问题，ubuntu就适合某个发行版（ubuntu10.04）的所有软件做了一个列表，然后用户通过apt-get install的方式安装软件，就会实时连接到ubuntu服务器，服务器会根据你的ubuntu版本，给你下载合适的软件来安装。这样确保了软件的兼容性。


## 文件查找命令
#### (1) which
作用：which指令会在PATH变量指定的路径中，搜索某个系统命令的位置，并且返回第一个搜索结果。

用法：

	which 可执行文件名称 

命令参数：

	-n 　指定文件名长度，指定的长度必须大于或等于所有文件中最长的文件名。
	-p 　与-n参数相同，但此处的包括了文件的路径。
	-w 　指定输出时栏位的宽度。
	-V 　显示版本信息

#### (2) whereis
作用：定位可执行文件、源代码文件、帮助文件在文件系统中的位置。

用法：

	whereis [-bmsu] [BMS 目录名 -f ] 文件名

命令参数：

	-b   定位可执行文件。
	-m   定位帮助文件。
	-s   定位源代码文件。
	-u   搜索默认路径下除可执行文件、源代码文件、帮助文件以外的其它文件。
	-B   指定搜索可执行文件的路径。
	-M   指定搜索帮助文件的路径。
	-S   指定搜索源代码文件的路径。

#### (3) locate
作用：很快速的搜寻档案系统内是否有指定的档案

用法：

	locate [选择参数] [样式]

#### (4) find
作用：用于在文件树种查找文件，并作出相应的处理 

用法：

	find pathname -options [-print -exec -ok ...]


## 三、vim编辑器常用命令
vim是vi的升级版

*使用vi来打开/创建一个文件，vi pathname
*vi的两种模式：
命令模式：当vi打开时默认为命令模式，要转入输入模式，需要按a或者i键。在命令模式下，此时键盘上输入的所有东西都被vi当作命令来对待。
在命令模式下，最好不要乱输入。此时应该输入相应的命令，来让vi做相应的事。
输入模式：输入模式用来向文件输入内容。可以从命令模式中按a或者i进入输入模式。进入输入模式后，就可以随意按键盘进行输入了。输入完成后如果要保存，要先退回到命令模式（因为保存也是一种命令）。在输入模式下按ESC键退回到命令模式。
注：注意看屏幕左下角，当命令模式时无提示信息或者提示文件名等信息，等处于输入模式时，提示 -- INSERT --
#### (1) 保存，退出

	:wq			保存并且退出
	:w			只保存不推出
	:q			不保存退出		进来看了一下没改退出
	:q!			不保存强制退出
	:wq!		保存并强制退出

#### (2) 查找
在命令模式下，输入/xxx，就可以查找到xxx

#### (3) 快速切换行
在命令模式下，输入:num，就可以快速切换到num行

#### (4) 设置显示行号
在命令模式下，输入:set nu，就可以显示行号

注：设置不显示行号，命令模式输入:set nonu
设置永久显示行号，需要修改vi的配置文件。打开vi的配置文件~/.vimrc，在其中输入set nu即可。

#### (5) 行删除
命令模式下，先将光标移动到要删除的行，然后输入dd
如果要删除连续多行，譬如要删除连续的3行，使用3dd 

#### (6) 行复制、粘贴
复制：命令模式下，nyy
粘贴：命令模式下，p
细节，复制时要把光标放在多行的第一行，粘贴时实际
粘贴到当前光标所在行的下一行。


# 结语
