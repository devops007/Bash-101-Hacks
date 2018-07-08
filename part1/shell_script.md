# 第一个shell脚本

让我们来创建一个简单的shell脚本来备份你的家目录。

```
$ vi backup1.sh
tar cvfz /backup/westos.tar.gz /home/westos
```

当你执行这个刚创建的脚本，会提示你没有权限的信错误息。

```
$ ./backup1.sh
-bash: ./backup1.sh: Permission denied
```

正如你看到的提示，这个脚本没有执行权限。所有，第一次使用chmod命令为这个脚本分配可执行权限，之后，
再次从命令行执行这个脚本，显示如下：

```
$ ls -l backup1.sh
-rw-r--r--. 1 westos westos 3 Aug 06 23:22 backup1.sh


$ chmod u+x backup1.sh


$ ./backup1.sh
```

你可以使用如下三种方式的任意一种来执行shell脚本：<br/>

1. cd到脚本所在的目录，键入"./"后接脚本名称来执行，例如：

```
$ cd /home/westos
$ ./backup1.sh
```

2. 使用绝对路径在任何位置执行shell脚本

```
/home/ramesh/backup1.sh
```

3. 增加脚本所在的目录到PATH环境变量，然后直接输入脚本名称去执行。使用这种方式，你不需要在脚本之前输入"./"或者绝对路径

```
export PATH=$PATH:/home/ramesh
backup1.sh
```

方法2和方法3的有点在于你不必再cd到脚本所在的目录去执行它。<br/>

让我们再增强一下shell脚本

```
$ vi backup2.sh
#!/bin/bash
# Take a backup of a specific user home directory
USERNAME=westos
BACKUP_LOCATION=/backup #Location to store the backup
tar cvfz $BACKUP_LOCATION/$USERNAME.tar.gz /home/$USERNAME
echo "Backup of $UASERNAME home directory completed."
```

注意：
 * #!/bin/bash: 这是shell脚本第一行必须要声明的，"#!"称为声明解释器，其后是解释器的完整路径，该路径用于执行脚本中的其余命令
 * 以"#"开头的每一行都是注释，你可以对完整或部分行书写注释，如果一行以"#"开头，则视其为注释行。在命令结束时，你也可以使用#评论该行
 * USERNAME是保存需要备份的用户名的变量
 * BACKUP_LOCATION是保存备份位置的变量


关于"#!/bin/bash"行，以下的方式也是可以的：

 * #!/bin/bash 作为第一行，表示用使用bash shell去执行脚本，作为最好的练习方式，建议使用此方式
 * #!bin/sh 作为第一行，将使用/bin/sh（sh其实是bash的软链接）去执行脚本中的shell命令
 * #在第一行完全不声明"#!"符号，则默认使用bash去执行，因为bash是Linux的默认的shell
