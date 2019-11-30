---
type: blog
title: Linux
categories: Linux
date: 2019-11-1
tags: linux
---

## 1. linux 的基础系统命令
*******************************
在linux中**系统命令**通常是如下的格式：  
`命令名称  【命令参数】 【命令对象】`  
1. 获取登录信息
```bash
# w
# who 
# who am i
```
2. 查看自己使用的shell`ps`
```bash
# ps
```
3. 查看命令的说明`whatis`
```bash
# what is ps
# what is python
```
4. 查看命令的位置`which、whereis`
```bash
# where is ps
# where is python
# which ps
# which python
```
5. 查看帮助文档`man、help、apropos`
```bash
# man ps
# info ps
```
6. 切换用户`su`
```bash
# su hellokitty
```
7. 以管理员身份执行命令`sudo`
```bash
# ls /root(fail)
# sudo ls /root(success)
```
8. 登入和登出相关`logout、exit、adduser、userdel、passwd、ssh`
```bash
# adduser hellokitty
# passwd hellokitty (change password)
# ssh@hellokitty@1.2.3.4
# logout
```
9. 查看系统和主机名`unname、hostname`
```bash
# unname
# hostname
```
10. 重启和关机`rebot、init 6、shutdown、init 0`
```bash
# rebot
```
11. 查看历史命令`history`
```bash
# history
```
___________________________________
## 2. linux常用的实用命令

1. 创建和删除目录`mkdir`、`rmdir`
```bash
# mkdir abc
# mkdir -p abc
# rmdir abc
```
2. 创建和删除文件`touch`、`rm`
```bash
# touch readme.md
# rm readme.md
# rm -rf xyz  
```bash
> `touch`命令用于创建空白文件或者修改文件时间。在Linux系统中有三种文件时间：
- 更改文件内容的时间：`mtime`
- 更改权限的时间: `ctime`
- 最后访问时间: `atime`
> rm有几个重要的参数如下：
- `-i` :交互式删除，每个删除项都要询问
- `-r` :删除目录并且递归删除目录及文件
- `-f` :强制删除，忽略存在的文件，没有任何提示

3. 切换和查看当前的工作目录`cd`、`pwd`
4. 查看目录内容`ls`
* `-l` :以长格式查看文件和目录
* `-a` ：显示以点开头的文件和目录
* `-R` ：遇到目录，递归展开
* `-d` : 只列出目录，不列出内容
* `-s  -t` : 按照大小和时间进行排序
5. 查看文件内容`cat`、`head`、`tail`、`more`、`less`
```bash
# cat readme.md
# head -10 sohu.html
```
6. 拷贝和移动文件`cp`、`mv`
```bash
# cp sohu.html  backup/
# cd backup

# mv sohu.html sohu_index.html
```
7. 查找文件和查找内容`find`、`grep`
* grep 在搜索字符串时可以直接使用正则表达式，如果需要使用正则表达式，则可以用`grep -E`
  
8. 链接`ln`
* 链接可以分为硬链接和软链接，硬链接可以认为是一个指向文件数据的指针。我们平常删除数据时，并没有删除硬盘上的文件，我们删除的是一个指针。而软链接类似于windows里面的快捷方式。   

9.  压缩\解压缩\归档\解归档`gzip`、`gunzip`、`xz`、`tar`
```bash
# gunzip redis-4.0.10.tar.gz
# tar -xvf redis-4.0.10.tar
```
10.  其它工具`sort`、`uniq`、`diff`、`tr`、`cut`、`paste`、`file`、`wc`
11.  管道和重定向  
* 管道的使用：`|` 
```bash
# find ./ | wc -1   % 查找当前目录下的文件个数 
# ls | cat - n    % 列出当前路径下的文件加，给每一项加一个编号
# cat record.log | grep AAA | grep - v BBB | wc - 1 % 查找record.log 中的AAA，但不包含BBB的个数
```
* 输出重定向和错误重定向：`- > / >>  / 2 >`
```bash
[root@iZwz97tbgo9lkabnat2lo8Z ~]# cat readme.txt
banana
apple
grape
apple
grape
watermelon
pear
pitaya
[root@iZwz97tbgo9lkabnat2lo8Z ~]# cat readme.txt | sort | uniq > result.txt
[root@iZwz97tbgo9lkabnat2lo8Z ~]# cat result.txt
apple
banana
grape
pear
pitaya
watermelon
```
* 输入重定向：` - <`
```bash
[root@iZwz97tbgo9lkabnat2lo8Z ~]# echo 'hello, world!' > hello.txt
[root@iZwz97tbgo9lkabnat2lo8Z ~]# wall < hello.txt
[root@iZwz97tbgo9lkabnat2lo8Z ~]#
Broadcast message from root@iZwz97tbgo9lkabnat2lo8Z (Wed Jun 20 19:43:05 2018):
hello, world!
[root@iZwz97tbgo9lkabnat2lo8Z ~]# echo 'I will show you some code.' >> hello.txt
[root@iZwz97tbgo9lkabnat2lo8Z ~]# wall < hello.txt
[root@iZwz97tbgo9lkabnat2lo8Z ~]#
Broadcast message from root@iZwz97tbgo9lkabnat2lo8Z (Wed Jun 20 19:43:55 2018):
hello, world!
I will show you some code.
```
12. 别名
* *alias*
```bash
[root@iZwz97tbgo9lkabnat2lo8Z ~]# alias ll='ls -l'
[root@iZwz97tbgo9lkabnat2lo8Z ~]# alias frm='rm -rf'
[root@iZwz97tbgo9lkabnat2lo8Z ~]# ll
...
drwxr-xr-x  2 root       root   4096 Jun 20 12:52 abc
...bash
[root@iZwz97tbgo9lkabnat2lo8Z ~]# frm abc
```
* *unlias*
```bash
[root@iZwz97tbgo9lkabnat2lo8Z ~]# unalias frm
[root@iZwz97tbgo9lkabnat2lo8Z ~]# frm sohu.html
-bash: frm: command not found
```

13. 其它程序
* 时间和日期 `date / cal`
```bash
[root@iZwz97tbgo9lkabnat2lo8Z ~]# date
Wed Jun 20 12:53:19 CST 2018
[root@iZwz97tbgo9lkabnat2lo8Z ~]# cal
      June 2018
Su Mo Tu We Th Fr Sa
                1  2
 3  4  5  6  7  8  9
10 11 12 13 14 15 16
17 18 19 20 21 22 23
24 25 26 27 28 29 30
[root@iZwz97tbgo9lkabnat2lo8Z ~]# cal 5 2017
      May 2017
Su Mo Tu We Th Fr Sa
    1  2  3  4  5  6
 7  8  9 10 11 12 13
14 15 16 17 18 19 20
21 22 23 24 25 26 27
28 29 30 31
```
* 录制操作脚本
```bash
script
```
* 给用户发送消息
```bash
mesg / write / wall / mail
```
## 3. 文件系统
### 文件和路径
1. 命名规则：文件名的最大长度与文件系统类型有关，一般情况下，文件名不应该超过255个字符，虽然绝大多数的字符都可以用于文件名，但是最好使用英文大小写字母、数字、下划线、点这样的符号。文件名中虽然可以使用空格，但应该尽可能避免使用空格，否则在输入文件名时需要用将文件名放在双引号中或者通过\对空格进行转义。
2. 扩展名：在Linux系统下文件的扩展名是可选的，但是使用扩展名有助于对文件内容的理解。有些应用程序要通过扩展名来识别文件，但是更多的应用程序并不依赖文件的扩展名，就像file命令在识别文件时并不是依据扩展名来判定文件的类型
3. 隐藏文件：以点开头的文件在Linux系统中是隐藏文件（不可见文件）。
### 目录结构
```bash
1.  */bin* - 基本命令的二进制文件。
2.  */boot* - 引导加载程序的静态文件。
3.  */dev* - 设备文件。
4.  */etc* - 配置文件。
5.  */home* - 普通用户主目录的父目录。
6.  */lib* - 共享库文件。
7.  */lib64* - 共享64位库文件。
8.  */lost+found* - 存放未链接文件。
9.  */media* - 自动识别设备的挂载目录。
10.  */mnt* - 临时挂载文件系统的挂载点。
11.  */opt* - 可选插件软件包安装位置。
12.  */proc* - 内核和进程信息。
13.  */root* - 超级管理员用户主目录。
14.  */run* - 存放系统运行时需要的东西。
15.  */sbin* - 超级用户的二进制文件。
16.  */sys* - 设备的伪文件系统。
17.  */tmp* - 临时文件夹。
18.  */usr* - 用户应用目录。
19.  */var* - 变量数据目录。
```
### 访问权限
1. *chmod* 改变文件模式比特
```bash
[root@iZwz97tbgo9lkabnat2lo8Z ~]# ls -l
...
-rw-r--r--  1 root       root 211878 Jun 19 16:06 sohu.html
...
[root@iZwz97tbgo9lkabnat2lo8Z ~]# chmod g+w,o+w sohu.html
[root@iZwz97tbgo9lkabnat2lo8Z ~]# ls -l
...
-rw-rw-rw-  1 root       root 211878 Jun 19 16:06 sohu.html
...
[root@iZwz97tbgo9lkabnat2lo8Z ~]# chmod 644 sohu.html
[root@iZwz97tbgo9lkabnat2lo8Z ~]# ls -l
...
-rw-r--r--  1 root       root 211878 Jun 19 16:06 sohu.html
说明：通过上面的例子可以看出，用chmod改变文件模式比特有两种方式：一种是字符设定法，另一种是数字设定法。  
除了chmod之外，可以通过umask来设定哪些权限将在新文件的默认权限中被删除。
...
```
2. *chown* - 改变文件所有者。
```bash
[root@iZwz97tbgo9lkabnat2lo8Z ~]# ls -l
...
-rw-r--r--  1 root root     54 Jun 20 10:06 readme.txt
...
[root@iZwz97tbgo9lkabnat2lo8Z ~]# chown hellokitty readme.txt
[root@iZwz97tbgo9lkabnat2lo8Z ~]# ls -l
...bash
-rw-r--r--  1 hellokitty root     54 Jun 20 10:06 readme.txt
```
### 磁盘管理
1. 列出文件系统的磁盘使用状况: *df*
```bash
[root@iZwz97tbgo9lkabnat2lo8Z ~]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1        40G  5.0G   33G  14% /
devtmpfs        486M     0  486M   0% /dev
tmpfs           497M     0  497M   0% /dev/shm
tmpfs           497M  356K  496M   1% /run
tmpfs           497M     0  497M   0% /sys/fs/cgroup
tmpfs           100M     0  100M   0% /run/user/0
```
2. 磁盘分区操作: *fdisk*
```bash
[root@iZwz97tbgo9lkabnat2lo8Z ~]# fdisk -l
Disk /dev/vda: 42.9 GB, 42949672960 bytes, 83886080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk label type: dos
Disk identifier: 0x000a42f4
   Device Boot      Start         End      Blocks   Id  System
/dev/vda1   *        2048    83884031    41940992   83  Linux
Disk /dev/vdb: 21.5 GB, 21474836480 bytes, 41943040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```
3. 格式化文件系统 *mkfs*
4. 文件系统检查 *fsck*
5. 挂载/卸载： *mount / umount*

## 4 编辑器 **vim** 
1. 启动`vim`。可以通过`vi`或`vim`命令来启动`vim`，启动时可以指定文件名来打开一个文件，如果没有指定文件名，也可以在保存的时候指定文件名。
```bash
[root@iZwz97tbgo9lkabnat2lo8Z ~]# vim guess.py
```
2. 命令模式、编辑模式和末行模式：启动`vim`进入的是命令模式（也称为`Normal`模式），在命令模式下输入英文字母i会进入编辑模式（`Insert`模式），屏幕下方出现-- `INSERT` --提示；在编辑模式下按下`Esc`会回到命令模式，此时如果输入英文:会进入末行模式，在末行模式下输入`q!`可以在不保存当前工作的情况下强行退出`vim`；在命令模式下输入`v`会进入可视模式（`Visual`模式），可以用光标选择一个区域再完成对应的操作。

3. 保存和退出`vim`：在命令模式下输入`: `进入末行模式，输入`wq`可以实现保存退出；如果想放弃编辑的内容输入`q!`强行退出，这一点刚才已经提到过了；在命令模式下也可以直接输入`ZZ`实现保存退出。如果只想保存文件不退出，那么可以在末行模式下输入`w`；可以在`w`后面输入空格再指定要保存的文件名。
4. 光标操作：
* 在命令模式下可以通过`h、j、k、l`来控制光标向左、下、上、右的方向移动，可以在字母前输入数字来表示移动的距离，例如：`10h`表示向左移动`10`个字符。
* 在命令模式下可以通过`Ctrl+y`和`Ctrl+e`来实现向上、向下滚动一行文本的操作，可以通过`Ctrl+f`和`Ctrl+b`来实现向前和向后翻页的操作。
* 在命令模式下可以通过输入英文字母`G`将光标移到文件的末尾，可以通过`gg`将光标移到文件的开始，也可以通过在`G`前输入数字来将光标移动到指定的行。
5. 文本操作
* 删除：在命令模式下可以用`dd`来删除整行；可以在dd前加数字来指定删除的行数；可以用`d$`来实现删除从光标处删到行尾的操作，也可以通过`d0`来实现从光标处删到行首的操作；如果想删除一个单词，可以使用`dw`；如果要删除全文，可以在输入`:%d`（其中:用来从命令模式进入末行模式）。
* 复制和粘贴：在命令模式下可以用`yy`来复制整行；可以在`yy`前加数字来指定复制的行数；可以通过`p`将复制的内容粘贴到光标所在的地方。
* 撤销和恢复：在命令模式下输入`u`可以撤销之前的操作；通过`Ctrl+r`可以恢复被撤销的操作。
* 对内容进行排序：在命令模式下输入`%!sort`。
6. 查找和替换
* 查找操作需要输入/进入末行模式并提供正则表达式来匹配与之对应的内容，例如：`/doc.*\.`，输入n来向前搜索，也可以输入N来向后搜索。
* 替换操作需要输入:进入末行模式并指定搜索的范围、正则表达式以及替换后的内容和匹配选项，例如：`:1,$s/doc.*/hello/gice`，其中：
    * `g` - `global`：全局匹配。
    * `i` - `ignore case`：忽略大小写匹配。
    * `c` - `confirm`：替换时需要确认。
    * `e` - `error`：忽略错误。
7. 参数设定在输入:进入末行模式后可以对vim进行设定。
* 设置`Tab`键的空格数：`set ts=4`
* 置显示/不显示行号：`set nu / set nonu`
* 设置启用/关闭高亮语法：`syntax on / syntax off`
* 设置显示标尺（光标所在的行和列）： `set ruler`
* 设置启用/关闭搜索结果高亮：`set hls / set nohls`
- 说明：如果希望上面的这些设定在每次启动vim时都能生效，需要将这些设定写到用户主目录下的`.vimrc`文件中。
8. 高级技巧
* 比较多个文件
```bash
[root@iZwz97tbgo9lkabnat2lo8Z ~]# vim -d foo.txt bar.txt
```
* 打开多个文件
```bash
[root@iZwz97tbgo9lkabnat2lo8Z ~]# vim foo.txt bar.txt hello.txt
```
- 启动`vim`后只有一个窗口显示的是`foo.txt`，可以在末行模式中输入ls查看到打开的三个文件，也可以在末行模式中输入`b <num>`来显示另一个文件，例如可以用`:b 2`将`bar.txt`显示出来，可以用`:b 3`将`hello.txt`显示出来。
- 拆分和切换窗口：  
可以在末行模式中输入`sp`或`vs`来实现对窗口的水平或垂直拆分，这样我们就可以同时打开多个编辑窗口，通过按两次`Ctrl`+w就可以实现编辑窗口的切换，在一个窗口中执行退出操作只会关闭对应的窗口，其他的窗口继续保留。
- 映射快捷键：在`vim`下可以将一些常用操作映射为快捷键来提升工作效率。

    * 例子1：在命令模式下输入`F4`执行从第一行开始删除10000行代码的操作。
```bash
:map <F4> gg10000dd。
```

    * 例子2：在编辑模式下输入__main直接补全为:
```bash
if __name__ == '__main__':
:inoremap __main if __name__ == '__main__':
```
* 说明：上面例子`2`的`inoremap`中的`i`表示映射的键在编辑模式使用，` nore`表示不要递归，这一点非常重要，否则如果键对应的内容中又出现键本身，就会引发递归（相当于进入了死循环）。如果希望映射的快捷键每次启动`vim`时都能生效，需要将映射写到用户主目录下的`.vimrc`文件中。
*  录制宏：
    * 在命令模式下输入`qa`开始录制宏（其中a是寄存器的名字，也可以是其他英文字母或`0-9`的数字）。

    * 执行你的操作（光标操作、编辑操作等），这些操作都会被录制下来。

    * 如果录制的操作已经完成了，按`q`结束录制。

    * 通过`@a`（`a`是刚才使用的寄存器的名字）播放宏，如果要多次执行宏可以在前面加数字，例如`100@a`表示将宏播放`100`次。

    * 可以试一试下面的例子来体验录制宏的操作，该例子来源于`Harttle Land`网站，该网站上提供了很多关于`vim`的使用技巧，有兴趣的可以去了解一下。 
