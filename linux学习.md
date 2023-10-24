### UNIX与Linux的关系

UNIX 是 Linux 的父亲，Linux是类Unix操作系统，Linux是Linux内核

Unix 要早于 Linux，Linux 的初衷就是要替代 UNIX，并在功能和用户体验上进行优化，所以 Linux 模仿了 UNIX（但并没有抄袭 UNIX 的源码），使得 Linux 在外观和交互上与 UNIX 非常类似。

### linux主流发行版本

**Debian**（及其派生版本Ubuntu、Linux Minit、Fedora Core）

**Fedora**（以及相关版本Red Hat Enterprises Linux（ RHEL）、CentOS）

**openSUSE**、**Gentoo Linux**、

### 虚拟机VMware Workstation

虚拟机是虚拟的、安全的、和真实的计算机毫不相干

随意性、便捷性

拍下快照，可以记下当前的虚拟机状态，方便以后恢复到这个状态

### Linux入门不是学“Linux”

1、体验系统

2、学习shell

### Linux四个部分（GNU/Linux）

1、Linux kernel 内核

2、GNU工具

3、GUI Desktop环境

4、Application应用

![image-20230917010147837](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230917010147837.png)

Linux内核：操作系统

1、硬件设备 管理使用

2、软件程序（系统）——》操作软件

3、系统内存

4、文件管理 保存文件，删除文件，修改文件、、、

### Linux文件系统

Linux 文件系统（Ext 系列）就属于索引式文件系统

Linux 默认文件系统 Ext2、Ext3 和 Ext4 之外，还能支持 fat16、fat32、NTFS（需要重新编译内核）等 Windows 文件系统

windows FAT32、NTFS  exFAT

### GNU

为LInux写一些必要的软件

GNU核心：原本在Unix上的一些命令和工具。被模仿到了Linux上

供Linux使用的这套工具：**coreutils** **coreutilities** 软件包

和shell

（1）用来处理文件的工具

（2）用来操作文本的工具

（3）用来管理进程的工具

### 什么是脚本语言？

脚本其实就是短小的、用来让计算机自动化完成一系列工作的程序，这类程序可以用**文本编辑器**修改，**不需要编译**，通常是**解释运行**的。

## ubuntu（linux）下 source、sh、bash、./ 执行脚本的区别是什么？

**1. source命令用法：**

```
source FileName
```

作用:在当前 bash 环境下读取并执行 FileName 中的命令。该 filename 文件可以**无 "执行权限"**。

注：该命令通常用命令 **.** 来替代。

**2. sh、bash的命令用法：**

```
sh FileName
或
bash FileName
```

作用:打开一个子 shell 来读取并执行 FileName 中命令。该 filename 文件可以**无 "执行权限"**。

注：运行一个shell脚本时会**启动另一个命令解释器。**

**3、./的命令用法：**

```
./FileName
```

作用: 打开一个子 shell 来读取并执行 FileName 中命令，该 filename 文件需要 **"执行权限"**。

注：运行一个 shell 脚本时会启动另一个命令解释器。

### shell

命令行shell提供一个命令行界面（**CLI**）、图形shell提供一个图形用户界面（**GUI**）

LInux shell -> CLI Command-Line Interface

### CLI shell

bash shell 基础的shell

zsh MacOS、ash、korn、tcsh

GUI：桌面环境

1、x window

2、KDE

3、GNOME

Unity

cinnamon

#### 进入CLI

**maxwell@maxwell-virtual-machine:~$** 

**maxwell**：用户名

**maxwell-virtual-machine**：计算机名

**~**：用户home目录，当前用户自己的目录，/为根目录

**~/Desktop**：代表当前用户下的桌面目录

**$**：等待用户输入

### 命令

```
ls：展示当前位置的文件
ls -a:展示当前所在位置的文件包括隐藏文件
ll:文件缩写
man ls:某个命令的使用文档,这里是ls
ls -m:逗号分隔文件名
ls -l -a=ll
ls -1:竖列展示文件名
```

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230111221938764.png" alt="image-20230111221938764" style="zoom: 67%;" />

#### **[shift]+{[PageUP]|[Page Down]}**

```
[Shift]+[Page Up]    ## 往前翻页 

[Shift]+[Page Down] ## 往后翻页
```

### Linux目录

Linux一切皆文件

```
cd /  跳转至根目录
```

正斜线 / Linux

反斜线 \ windows

Linux没有盘符的概念

/:根目录

/bin:二进制文件,GNU工具,存放多用户级,存放着最经常使用的命令。

```
cd .. 返回上一目录
```

**/cdrom:**光盘所在

**/etc:**系统配置文件目录

存放所有的系统管理所需要的配置文件和子目录。

**/home**:主目录,显示所有用户目录

**/lib:**库目录,存在的依赖,

存放着系统最基本的动态连接共享库，其作用类似于 Windows 里的 DLL 文件。几乎所有的应用程序都需要用到这些共享库。

**/lost+found:**突然情况

**/mnt:**挂载目录,U盘

系统提供该目录是为了让用户临时挂载别的文件系统的，我们可以将光驱挂载在 /mnt/ 上，然后进入该目录就可以查看光驱里的内容了。

**/proc:**伪文件系统,管理**内存空间**

虚拟的目录，它是系统内存的映射，我们可以通过直接访问这个目录来获取系统信息。

**/run:**运行目录

**/tmp:**临时目录(temp)

**/var:**可变目录,log

这个目录中存放着在不断扩充着的东西，我们习惯将那些经常被修改的目录放在这个目录下。包括各种日志文件。

**/boot**:启动目录

存放的是启动 Linux 时使用的一些核心文件，包括一些连接文件以及镜像文件

**/dev**设备目录

存放的是 Linux 的外部设备，在 Linux 中访问设备的方式和访问文件的方式是相同的。

**/media:**媒体目录

自动识别一些设备，例如U盘、光驱等等，当识别后，Linux 会把识别的设备挂载到这个目录下。

**/opt:**可选目录

这是给主机额外安装软件所摆放的目录。比如你安装一个ORACLE数据库则就可以放到这个目录下。默认是空的。

**/root:**root用户的主目录,管理员

**/sbin:**系统二进制目录, GNU高级管理员使用的命令工具

存放的是系统管理员使用的系统管理程序。

**/srv:**服务目录,本地服务

存放一些服务启动之后需要提取的数据。

**/usr:**用户二进制目录,GNU工具

这是一个非常重要的目录，用户的很多应用程序和文件都放在这个目录下，类似于 windows 下的 program files 目录。

**/usr/bin**:当前用户安装的软件

**/usr/src：**内核源代码默认的放置目录。

FHS:Linux文件系统层级标准

```
cd = cd ~ 返回当前用户目录
```

#### Ctrl C 撤销正在进行的命令

#### 文件目录

相对路径 绝对路径

```
Documents/doc/1.txt  当前目录下的相对路径
./Documents/doc/1.txt  当前目录.下面的相对路径
~/Documents/doc/1.txt  代表绝对路径,~是/home/maxwell
```

文件扩展匹配符号

*:多个符号

?:一个占位符号

元字符通配符

f[a-z]ck    

&& 可以组合命令

```
touch 文件 可以更新修改时间,但是不会覆盖
```

#### cp

```
cp 要复制的文件 复制到哪儿 -i
强制加  -i  询问用户是否覆盖文件,否则会直接覆盖掉原来的文件内容
cp /home/maxwell/Documents/doc/* /home/maxwell/Downloads/      把doc目录下的所有文件copy到/home/maxwell/Downloads/之下
而cp /home/maxwell/Documents/doc /home/maxwell/Downloads/ -r 需要加-r递归的将包括文件夹在内的 copy到指定目录下
```

crtl+左右 快速进退

ctrl L 制表符空白

CTRL U 截断删除光标之前的

CTRL A 光标移至最前,CTRL E 光标移至最后 

 CTRL K 截断删除光标后面的所有

#### Linux链接文件

**ln** 命令产生硬链接。

1 **符号链接（Symbolic Link）(软链接)**----快捷方式    原文件/文件夹必须存在

在符号连接中，文件实际上是一个文本文件，其中包含的有另一文件的位置信息。

不同媒体介质之间能使用软链接,可以跨文件系统,可对目录进行软链接

```
ln -s 1.java 1_islinkfile
```

2**,硬链接（Hard Link）**  副本   

不同媒体介质之间不能使用软链接,只有在同一个文件系统才可以创建

硬连接的作用是**允许一个文件拥有多个有效路径名**，这样用户就可以建立硬连接到重要文件，以防止“误删”的功能。文件真正删除的条件是与之相关的所有硬连接文件均被删除

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230112163608218.png" alt="image-20230112163608218" style="zoom: 67%;" />

软链接inode与源文件不同,硬链接inode与原文件相同

#### mv

移动或者重命名

```
cd !$  移动到上一条命令最后一个路径
```

#### rm

非常危险的一个命令

必须用 rm -i

#### mkdir

```
mkdir -p java/js
创建多级目录
```

#### file   查看文件格式

#### 查看文件

**less**  和  **more**  以及**cat -A** 显示空格和tab

**tail** 查看末尾几行

**head** 查看末尾几行

```
tail -n 数字 文件名
head -n 数字 文件名
```

![image-20230112180101235](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230112180101235.png)

### Linux系统进程

#### ps命令

https://wangchujiang.com/linux-command/c/ps.html

报告当前系统的进程情况

```
ps -l
ps -aux
ps -aux | grep 进程名字   查看改名字进程情况
```

把所有进程显示出来，并输出到ps001.txt文件

```shell
ps -aux > ps001.txt
ps aux > 1.txt
ps aux | grep ssh > 2.txt

```

#### kill

```
kill PID
```

#### mount 挂载

Linux下，mount挂载的作用，就是将一个设备（通常是存储设备）挂接到一个已存在的目录上。访问这个目录就是访问该存储设备。![image-20230113171932495](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230113171932495.png)

/dev/sdb1不是它的目录吗？

虽然/dev是个目录，但/dev/sdb1不是目录。可以发现ls/dev/sdb1无法执行。/dev/sdb1，是一个类似指针的东西，指向这个分区的原始数据块。mount前，系统并不知道这个数据块哪部分数据代表文件，如何对它们操作。

```
mount /dev/sdb1 /mnt/   从某路径挂载到另外一个地方
umount /mnt  取消该路径的挂载
```

#### df du

- **df**（英文全称：disk free）：列出文件系统的整体磁盘使用量
- **du**（英文全称：disk used）：检查磁盘空间使用量
- **fdisk**：用于磁盘分区

```
df -h  查看所有分区文件挂载点
```

```
du -h 当前目录磁盘使用情况
```



<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230112225728520.png" alt="image-20230112225728520" style="zoom: 67%;" />

## fdisk

fdisk 是 Linux 的磁盘分区表操作工具。

#### sort文件排序

```
sort 文件.txt -n
sort 文件.txt -M
```

### 压缩解压文件

tar先打包成一个文件，然后用gzip压缩

.Z 是已过时的压缩工具Unix时期

gzip ->.gz    zip->.zip        bzip2->.bz2

#### tar

利用tar命令，可以把一大堆的文件和目录全部打包成一个文件，这对于备份文件或将几个文件组合成为一个文件以便于网络传输是非常有用的。

**打包**和**压缩**。打包是指将一大堆文件或目录变成一个总的文件；压缩则是将一个大的文件通过一些压缩算法变成一个小文件。

```
-x, --extract, --get       从归档中解出文件
-c, --create               创建一个新归档
-t, --list                 列出归档内容
-f, --file=ARCHIVE         使用归档文件或 ARCHIVE 设备
-j, --bzip2                通过 bzip2 过滤归档
- v                        显示所有过程
-z, --gzip, --gunzip, --ungzip   通过 gzip 过滤归档

```

例子

```
tar -zcvf my_doc.tar.gz ./doc
将doc的文件打包后压缩成my_doc.tar.gz

tar -zxvf my_doc.tar.gz -C ./Documents 
将my_doc.tar.gz解压到指定目录 要加-C
```

```
tar -cf archive.tar foo bar  # 从文件 foo 和 bar 创建归档文件 archive.tar。
tar -tvf archive.tar         # 详细列举归档文件 archive.tar 中的所有文件。
tar -xf archive.tar          # 展开归档文件 archive.tar 中的所有文件。
```

```
tar -cf all.tar *.jpg
# 这条命令是将所有.jpg的文件打成一个名为all.tar的包。-c是表示产生新的包，-f指定包的文件名。

tar -rf all.tar *.gif
# 这条命令是将所有.gif的文件增加到all.tar的包里面去。-r是表示增加文件的意思。

tar -uf all.tar logo.gif
# 这条命令是更新原来tar包all.tar中logo.gif文件，-u是表示更新文件的意思。

tar -tf all.tar
# 这条命令是列出all.tar包中所有文件，-t是列出文件的意思
```

```
tar -cvf archive.tar foo bar  # 从文件foo和bar创建archive.tar。
tar -tvf archive.tar         # 详细列出archive.tar中的所有文件。
tar -xf archive.tar          # 从archive.tar提取所有文件。
```



####  zip格式

压缩： zip -r [目标文件名].zip [原文件/目录名]
解压： unzip [原文件名].zip
注：-r参数代表递归

#### tar格式（该格式仅仅打包，不压缩）

打包：tar -cvf [目标文件名].tar [原文件名/目录名]
解包：tar -xvf [原文件名].tar
注：c参数代表create（创建），x参数代表extract（解包），v参数代表verbose（详细信息），f参数代表filename（文件名），所以f后必须接文件名。

#### tar.gz格式

方式一：利用前面已经打包好的tar文件，直接用压缩命令。

压缩：gzip [原文件名].tar
解压：gunzip [原文件名].tar.gz

方式二：一次性打包并压缩、解压并解包

打包并压缩： tar -zcvf [目标文件名].tar.gz [原文件名/目录名]
解压并解包： tar -zxvf [原文件名].tar.gz
注：z代表用gzip算法来压缩/解压。

#### tar.bz2格式

方式一：利用已经打包好的tar文件，直接执行压缩命令：

压缩：bzip2 [原文件名].tar
解压：bunzip2 [原文件名].tar.bz2
方式二：一次性打包并压缩、解压并解包

打包并压缩： tar -jcvf [目标文件名].tar.bz2 [原文件名/目录名]
解压并解包： tar -jxvf [原文件名].tar.bz2
注：小写j代表用bzip2算法来压缩/解压。

#### 分号;在命令里的作用

可以并列执行命令

#### sleep 和 jobs

```
sleep 300& 后台执行,300秒后结束
jobs -l 查看后台sleep进程
```

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230113175329644.png" alt="image-20230113175329644" style="zoom: 67%;" />

#### 外部命令 内建命令

```
type 命令      查看命令类型
```

外部命令就是需要跳出该bash shell来执行的命令

#### history 查看历史命令

```
!历史命令的行号     执行该条命令
```

#### alias 别名

```
alias -p    查看别名列表
```

---

### 环境变量

```
printenv   显示系统全局变量
printenv 变量名   显示特定的变量含义
echo $变量名  打印特定变量
```

全局变量 业界为大写下划线隔开

局部变量 业界为小写下划线隔开

```
export 变量="含义"      定义全局变量
unset 变量              删除变量
```

配置PATH路径(**只是暂时的,并非永久配置**)

```
PATH=$PATH:路径
```

永久配置(对应不同的配置文件)

```
echo 'export PATH=/home/xxx/bin:$PATH' >>~/.bashrc
source ~/.bashrc
```



配置系统环境变量    不同发行版文件

```
~/.bashrc
~/.bash_profile
~/.profile
~/.bash_login
```

### package manager system PMS 软件包管理系统

软件安装,更新,卸载

工具依赖

不同厂商有不同服务器系统,所以不同发行版有不同的包管理系统

有两个命令    dpkg   rpm

```
dpkg --> Debian
dpkg:  apt-get  apt-cache  aptitude  解决工具依赖问题   
```

#### apt-get、apt和aptitude的区别在哪？

https://www.zhihu.com/question/43534144

- 列出所有可更新的软件清单命令：**sudo apt update**
- 升级软件包：**sudo apt upgrade**

### 安装第三方软件

在github上看项目之前,一定要看README.md

在看软件依赖

看操作系统安装方式

```
echo 'eval $(thefuck --alias)
# You can use whatever you want as an alias, like for Mondays:
eval $(thefuck --alias fuck)' >> ~/.bashrc
```

### 用户与权限

用户的id  ---->  UID

```
cat /etc/passwd   查看用户目录
```

除root和普通用户以外,Linux还存在许多系统账户

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230114225557732.png" alt="image-20230114225557732" style="zoom: 80%;" />

用户名:密码:UID:用户组ID:备注,用户描述:用户home目录:默认使用的shell

```
sudo cat /etc/shadow    查看密码相关信息
```

```
sudo useradd 用户名          添加用户
sudo userdel 用户名		  删除用户
usermod           修改一些用户配置
```

#### group 组

组:共享资源的权限

```
groupadd 组名
groupdel 组名
```

#### 文件权限与属性

```
lrwxrwxrwx   1 root root         7 1月  10 23:49 bin -> usr/bin/
l代表是链接文件,如果是d则是目录  -是文件
b                    则表示为装置文件里面的可供储存的接口设备(可随机存取装置)；
c                    则表示为装置文件里面的串行端口设备，例如键盘、鼠标(一次性读取装置)。
有三组rwx,分别代表组创始人权限   组下属成员权限  其他组成员权限
r代表文件可读
w代表文件可写
x代表文件可执行
```

在Linux系统中，用户是按组分类的，一个用户属于一个或多个组。

**chgrp**：更改文件属组

```
chgrp [-R] 属组名 文件名
```

- -R：递归更改文件属组

**chown**：更改文件属主，也可以同时更改文件属组

```
chown [–R] 属主名 文件名
chown [-R] 属主名:属组名 文件名
```

**chmod**：更改文件9个属性

Linux文件属性有两种设置方法，一种是数字，一种是符号。

rwx：4+2+1=7

```
chmod 777 文件名     设置权限rwxrwxrwx
chmod 664 文件名     设置权限rw-rw-r--
```

**u, g, o** 来代表三种身份的权限

**a** 则代表 **all**，即全部的身份。读写的权限可以写成 **r, w, x**

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230115140358000.png" alt="image-20230115140358000" style="zoom:80%;" />

---

### vim 编辑器之神

#### vim的基础配置

在home创建.vimrc文件

```
touch .vimrc
vim .vimrc
set syntax=on
set tabstop=4
set softtabstop=4
set number
set enc=utf-8
set showmatch
:wq
source ./.vimrc
```



两个模式:普通模式(操作文件),插入模式

打开vim是普通模式,进入插入模式insert  按**i**

退出插入模式,按**ESC**

**HJKL**   ←↓↑→

使用 "30j" 或 "30↓" 的组合按键

**CTRL F** 向下翻页

**CTRL B**向上翻页

CTRL E向下翻页连续

CTRL Y向上翻页连续

数字 <space> 光标移动至右边第n个

shift G 最下面

gg 最上面

还有命令模式(:)

:wq    :保存并退出

:w      :保存

:q        :退出

:q!       :不保存退出

:w filename    :另存为新的文档

:n1,n2 w [filename]     将 n1 到 n2 的内容储存成 filename 这个档案。

i:光标之前插入

a:光标之后插入

o:直接enter到下一行输入

u:撤销刚才的操作

dd:删除一整行

x:删除光标所在字符  X为向前删除一个字符

dw:删除光标所在之后的单词

b:跳跃单词首字母,以及往前跳跃

e:跳跃单词尾字母

E:大跳

w:往后跳跃单词

W:大跳

shift 6 :跳至行首

0:跳至行首

shift 4 :跳至行尾

r:替换单个字符

p:粘贴向后  P:粘贴向前

J:将光标所在行与下一行的数据结合成同一行

.   重复前一个动作

yw:复制这个单词

y$:复制该字符到行尾

yy:复制游标所在的那一行(常用)

**可视化模式**  选择文本

v:随意可视化复制的内容  y复制

V:按行复制y

全选操作:gg  v  G

在选中情况下:按o可以首尾切换

CTRL v 多行选择

在v模式下:按0补全角落

vaw:选中一个单词

vab选中包括括号在内的

vaB选中大括号在内的

va<选中中括号在内的

v选中行    <  >左右缩进

shift+~:大小写切换

v选中+u:切换成小写   U切换成大写

#### 查找和替换

临时设置行号    :set number

```
/要查找的词 enter  按n选择下一个按N上一个  向后搜索
?要查找的词 enter  按n选择下一个按N上一个  向前搜索
:s/待替换词/替换词/g   单行全部替换
:%s/待替换词/替换词/g  全局全部替换
:%s/待替换词/替换词/gc  询问每次替换操作
:行号,行号s/待替换词/替换词/g  全部替换[行号,行号]的词
```

行号+gg跳转相应行

## shell 教程

Shell 脚本（shell script），是一种为 shell 编写的脚本程序。

Shell 是一个用 C 语言编写的程序，它是用户使用 Linux 的桥梁。Shell 既是一种命令语言，又是一种程序设计语言。

### 运行 Shell 脚本有两种方法：

**1、作为可执行程序**

将上面的代码保存为 test.sh，并 cd 到相应目录：

```
chmod +x ./test.sh  #使脚本具有执行权限
./test.sh  #执行脚本
```

**2、作为解释器参数**

这种运行方式是，直接运行解释器，其参数就是 shell 脚本的文件名，如：

```
/bin/sh test.sh
/bin/php test.php
```

#### shell变量

```
your_name="qinjx"
echo $your_name
echo ${your_name}
```

使用 readonly 命令可以将变量定义为只读变量，只读变量的值不能被改变。

使用 unset 命令可以删除变量。

```
unset variable_name
```

- **1) 局部变量** 局部变量在脚本或命令中定义，仅在当前shell实例中有效，其他shell启动的程序不能访问局部变量。
- **2) 环境变量** 所有的程序，包括shell启动的程序，都能访问环境变量，有些程序需要环境变量来保证其正常运行。必要的时候shell脚本也可以定义环境变量。
- **3) shell变量** shell变量是由shell程序设置的特殊变量。shell变量中有一部分是环境变量，有一部分是局部变量，这些变量保证了shell的正常运行

#### 定义数组

在 Shell 中，用括号来表示数组，数组元素用"空格"符号分割开。

**字符串截取**

**#**、**##** 表示从左边开始删除。一个 **#** 表示从左边删除到第一个指定的字符；两个 **#** 表示从左边删除到最后一个指定的字符。

**%**、**%%** 表示从右边开始删除。一个 **%** 表示从右边删除到第一个指定的字符；两个 **%** 表示从左边删除到最后一个指定的字符。

删除包括了指定的字符本身。

**shell 传递参数**

```
*#!/bin/bash*
*# author:菜鸟教程*
*# url:www.runoob.com*

**echo** "Shell 传递参数实例！";
**echo** "执行的文件名：$0";
**echo** "第一个参数为：$1";
**echo** "第二个参数为：$2";
**echo** "第三个参数为：$3";
```

```
$ chmod +x test.sh 
$ ./test.sh 1 2 3
Shell 传递参数实例！
执行的文件名：./test.sh
第一个参数为：1
第二个参数为：2
第三个参数为：3
```

**获取数组中的所有元素**

使用 **@** 或 ***** 可以获取数组中的所有元素

在数组前加一个感叹号 **!** 可以获取数组的所有键

#### echo

echo输出的字符串总结

===================================================================

​    能否引用变量  |  能否引用转移符  |  能否引用文本格式符(如：换行符、制表符)

单引号 |      否      |       否       |               否

双引号 |      能      |       能       |               能

无引号 |      能      |       能       |               否              

===================================================================

**>** 重定向输出到某个位置，替换原有文件的所有内容。

**>>** 重定向追加到某个位置，在原有文件的末尾添加内容。

**<** 重定向输入某个位置文件。

**2>** 重定向错误输出。

**2>>** 重定向错误追加输出到文件末尾。

**&>** 混合输出错误的和正确的都输出。