# Bash 简介

使用命令行shell，例如Bash，你可以向操作系统发出说明，这里有两种使shell工作的方式：
 * 与命令行提示符进行交互
 * 执行shell脚本自动执行任务

Bash代表 "Bourne Again Shell", 他是基于GNU开发的Bourne shell, 是大多数Linux操作系统发行版的默认shell。<br/>

以下是不同类型的shell：
  * sh   - Bourne Shell
  * bash - Bourne Again Shell
  * csh  - C shell
  * tcsh - Turbo C shell
  * ksh  - Korn shell

在你的系统上，/etc/shells文件列出了所有可用的shell，请注意在Linux上，/bin/sh是bash的软链接。

```
$ cat /etc/shells
/bin/sh
/bin/bash
/sbin/nologin
/bin/tcsh
/bin/csh
```

在Linux的/etc/passwd文件中每一个用户（行）的最后一个字段表明了该用户的默认shell类型，你可能注意到了bash被设置成了账户用户的默认shell。

```
$ grep westos /etc/passwd
westos:x:1001:1001::/home/westos:/bin/bash
```

## Bash命令行代码

一旦你登录典型的Linux系统，您在提示符下键入的任何命令都是使用bash shell命令行模式执行的。您键入的行包含命令后跟可选参数，参数应该用一个
或多个空格分开。<br/>

接下来的例子展示了tar命令在命令行被执行，并且3个参数是是被空格分开的。

```
tar cvfz etc.tar.gz /etc/
```

您可以从命令行执行以下任一操作:
 * Bash 内建
 * Bash 函数
 * Bash 别名
 * 外部非Bash程序位于系统中的某个位置


## Bash脚本代码

bash shell脚本是一个文件，其中包含bash shell可以理解的一系列命令。然后你运行一个bash shell脚本文件，该bash文件中的命令按顺序逐个执行。<br/>

使用bash脚本可以自动完成一些任务。例如，你可以通过写脚本来备份一些程序文件到指定位置。
