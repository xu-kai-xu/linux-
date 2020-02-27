1. 系统信息

   | 指令                 | 功能                                                         |
   | -------------------- | ------------------------------------------------------------ |
   | arch                 | 显示机器的处理器架构                                         |
   | uname -m             | 显示机器的处理器架构                                         |
   | uname -r             | 显示正在使用的内核版本                                       |
   | uname --help         | 查看该命令的帮助，显示机器的相关信息                         |
   | dmidecode -q         | 显示硬件系统部分 -(SMBIOS / DMI)                             |
   | hdparm -i /dev/hda   | 罗列一个磁盘的架构特性                                       |
   | hdparm -tT dev/sda   | 在磁盘上执行测试性读取操作                                   |
   | cat /proc/cpuinfo    | 显示 cpu 的信息                                              |
   | cat /proc/meminfo    | 校验内存使用                                                 |
   | cat /proc/interrupts | 显示中断                                                     |
   | cat /proc/swaps      | 显示哪些 swaps 被占用                                        |
   | cat /proc/version    | 显示内核的版本                                               |
   | cat /proc/net/dev    | 显示网络适配器及其统计                                       |
   | cat /proc/mounts     | 显示已加载的文件系统                                         |
   | lspci -tv            | 罗列 pci 设备（Peripheral Component Interconnect，外围设备互联） |
   | lsusb -tv            | 罗列 usb 设备                                                |
   |                      | 其中 -t 表示以树的形式列出设备信息， -v 表示显示设备的详细信息，v 最多连续用三个。 |
   | date                 | 显示系统日期                                                 |
   | cal 2020             | 显示 2020 年的日历                                           |
   | date 052111052018.00 | 设置日期和时间格式                                           |
   | clock -w             | 将时间修改保存到 bios                                        |
   | ntpdate [服务器名称] | 联网更新时间                                                 |

2. 关机

   | 指令                        | 功能                   |
   | --------------------------- | ---------------------- |
   | shutdown -h now             | 关闭系统               |
   | init 0                      | 关闭系统               |
   | telinit 0                   | 关闭系统               |
   | shutdown -h hours:minutes & | 按预定时间关闭系统     |
   | shutdown -c                 | 取消按预定时间关闭系统 |
   | shutdown -r now             | 重启                   |
   | reboot                      | 重启                   |
   | logout                      | 注销                   |

3. 文件和目录

   | 指令                      | 功能                                                         |
   | ------------------------- | ------------------------------------------------------------ |
   | cd /home                  | 进入 /home 目录                                              |
   | cd ..                     | 返回上一级目录                                               |
   | cd ../..                  | 返回上两级目录                                               |
   | cd ~user1                 | 进入个人的主目录                                             |
   | cd                        | 进入个人主目录                                               |
   | cd -                      | 返回上次所在目录                                             |
   | pwd                       | 显示绝对工作路径                                             |
   | ls                        | 查看目录中的文件                                             |
   | ls -F                     | 查看文件目录，在文件之后加符号以区分。其中目录之后加 /，可执行文件之后加 \*，符号链接之后加 @，命令管道之后加 \|，sockets 套接字之后加 =，普通文件之后什么都不加 |
   | ls -l                     | 显示文件和目录的详细资料，包括文件类型、权限、所有者用户以及该用户所属的组、修改日期、文件名 |
   | ls -a                     | 显示所有文件，包括隐藏文件                                   |
   | ls \*[0-9]*               | 显示包含数字的文件名和目录名                                 |
   | tree                      | 显示文件和目录由根目录开始的树形结构                         |
   | mkdir dir1                | 创建目录 dir1                                                |
   | mkdir dir1 dir2           | 同时创建两个目录 dir1 dir2                                   |
   | mkdir -p /tmp/dir1/dir2   | 创建目录树，层状结构的目录                                   |
   | rm -f file1               | 删除文件 file1                                               |
   | rmdir dir1                | 删除目录 dir1                                                |
   | rm -rf dir1               | 删除目录 dir1 并同时删除该目录下的内容                       |
   | rm -rf dir1 dir2          | 同时删除两个目录和目录下的内容                               |
   | mv dir1 new_dir           | 重命名/移动一个目录                                          |
   | cp file1 file2            | 复制文件                                                     |
   | cp dir/*                  | 复制目录 dir 下的所有文件到当前工作目录                      |
   | cp -a /tmp/dir1           | 复制目录 /tmp.dir1 到当前工作目录，-a 表示保留链接、文件属性，并复制目录下的所有内容 |
   | cp -a dir1 dir2           | 复制目录 dir1 下的内容到 dir2                                |
   | ln -s file1 link1         | 创建一个指向文件或者或目录的软链接                           |
   | ln file1 link1            | 创建一个指向文件或目录的物理链接                             |
   | touch -t 1812250000 file1 | 修改一个文件或目录的时间戳-（YYMMDDhhmm）                    |
   | iconv -l                  | 列出已知的编码                                               |
   | file filename             | 将文件名为 filename 的文件输出                               |

4. 文件搜索

   | 指令                                      | 功能                                               |
   | ----------------------------------------- | -------------------------------------------------- |
   | find / -name file1                        | 从 / 开始进入根文件系统搜索文件和目录              |
   | find / -user user1                        | 搜索属于用户 user1 的文件和目录                    |
   | find /home/user1 -name \\*.bin            | 在目录 /home/user1 中搜索带有 .bin 结尾的文件      |
   | find /usr/bin -type f -atime +100         | 搜索在过去 100 天内未被使用过的执行文件            |
   | find /usr/bin -type f -mtime -10          | 搜索在过去 10 天内被创建或修改过的文件             |
   | find / -name *.rpm -exec chmod 755 '{}'\; | 搜索以 .rpm 结尾的文件并设定其权限                 |
   | find / -xdev -name *.rpm                  | 搜索以 .rpm 结尾的文件，忽略光驱、磁盘等可移动设备 |
   | locate *.ps                               | 运行`updatedb`命令后寻找以 .ps 结尾的文件          |
   | whereis halt                              | 显示一个二进制文件、源码或 man 的位置              |
   | which halt                                | 显示一个二进制文件或可执行文件的完整路径           |

5. 挂载一个文件系统（这一组不能随便试，需要的时候再查看吧）

   | 指令                                                         | 功能                                                         |
   | ------------------------------------------------------------ | ------------------------------------------------------------ |
   | mount /dev/hda2 /mnt/had2                                    | 确定目录 /mnt/had2 已经存在后，在该目录下挂载一个 /dev/hda2 的盘 |
   | umount  /dev/hda2                                            | 从挂载点退出后卸载磁盘 hda2                                  |
   | fuser -km /mnt/hda2                                          | 当设备繁忙时强行卸载                                         |
   | umount -n  /mnt/hda2                                         | 运行卸载操作而不写入 /etc/mtab 文件，该指令当文件作为只读或当磁盘写满时非常有用 |
   | mount  /dev/fd0/  /mnt/floppy                                | 挂载一个软盘                                                 |
   | mount  /dev/cdrom  /mnt/cdrom                                | 挂载一个 cdrom 或 dvdrom                                     |
   | mount  /dev/hdc  /mnt/cdrecorder                             | 挂载一个 cdrw 或 dvdrw                                       |
   | mount -o loop file.iso  /mnt/cdrom                           | 挂载一个文件或 ios 镜像文件                                  |
   | mount -t vfat  /dev/hda5  /mnt/hda5                          | 挂载一个 windows FAT32 文件系统                              |
   | mount  /dev/sda1  /mnt/usbdisk                               | 挂载一个 usb 闪存盘或闪存设备                                |
   | mount -s smbfs -o username=user,password=-pass //WinClient/share/mnt/share | 挂载一个 windows 网络共享                                    |

6. 磁盘空间

   | 指令                                                         | 作用                                                         |
   | ------------------------------------------------------------ | ------------------------------------------------------------ |
   | df -h                                                        | 显示已经挂载的分区列表                                       |
   | ls -LSr \|more                                               | 以尺寸大小排列目录和文件                                     |
   | du -sh dir1                                                  | 估算目录 dir1 已经使用的磁盘空间                             |
   | du -sk \* \|sort -rn                                         | 以容量大小为依据依次显示文件和目录的大小                     |
   | rpm -q -a --qf '%10{SIZE}t%{NAME}n' \|sort -k1,1n            | 以大小为依据依次显示已安装 rpm 包所使用的空间（fedora，redhat 类系统） |
   | dpkg-query -W -f='\${Installed-Size; 10}t\${Package}n' \|sort -k1,1n | 以大小为依据依次显示已安装的 deb 包所使用的空间（ubuntu，debian 类系统） |

7. 用户和群组

   | 指令                                                         | 功能                                                         |
   | ------------------------------------------------------------ | ------------------------------------------------------------ |
   | groupadd group_name                                          | 创建一个新用户                                               |
   | groupdel group_name                                          | 删除一个用户                                                 |
   | groupmod -n new_group_name old_group_name                    | 重命名一个用户                                               |
   | useradd -c "Firstname Surname" -g admin -d /home/user1 -s /bin/bash user1 | 新建用户：-c，备注；-g，所属用户组；-d，登入目录；-s，用户登录后使用的 shell；uer1 用户名 |
   | useradd user1                                                | 创建新用户                                                   |
   | userdel -r user1                                             | 删除用户，-r，删除主目录和邮件内容                           |
   | usermod -c "User FTP" -g system -d /ftp/user1 -s /bin/nologin user1 | 修改用户属性。-c，备注；-g，用户组；-d，主目录；-s，用户登陆后使用的 shell；user1 用户名 |
   | passwd                                                       | 修改当前用户的口令                                           |
   | passwd user1                                                 | 修改一个用户的口令                                           |
   | chage -E 2005-12-31 user1                                    | 设置用户有效期限                                             |
   | pwck                                                         | 检查 /etc/passwd 的文件格式和语法修正以及存在的用户          |
   | grpck                                                        | 检查 /etc/passwd 的文件格式和语法修正以及存在的群组          |
   | newgrp group_name                                            | 登陆进一个新的群组以改变新创建文件的预设群组                 |

   

8. 文件权限

   | 指令                        | 功能                                                         |
   | --------------------------- | ------------------------------------------------------------ |
   | ls -lh                      | 显示权限                                                     |
   | ls /tmp \|pr -T5 -W$COLUMNS | 将终端划分成五栏显示                                         |
   | chmod ugo+rwx dir1          | 设置目录的所有人（u)、群组（g）以及其他人对目录 dir1（o）拥有 读（r）、写（w）、执行（x）的权限 |
   | chmod go-rwx dir1           | 删除群组（g）和其他人（o）对目录 dir1 的所有权限             |
   | chown user1 file1           | 改变文件 file1 的 所有者为 user1                             |
   | chown -R user1 dir1         | 改变目录的所有者属性，同时改变该目录下的所有文件的所有者为 user1 |
   | chgrp group1 file1          | 改变文件所有的组为 group1                                    |
   | chown user1:group1 file1    | 改变一个文件的所有人和所有组                                 |
   | find / -perm -u+s           | 罗列一个文件中所有使用了 SUID 控制的文件                     |
   | chmod u+s /bin/file1        | 设置一个文件的 SUID 位（运行该文件的用户也被赋予和所有者同样的权限） |
   | chmod u-s /bin/file1        | 禁用一个文件的 SUID 位                                       |
   | chmod g+s /home/public      | 设置一个目录的 SGID 位                                       |
   | chmod g-s /home/public      | 禁用一个目录的 SGID 位                                       |
   | chmod o+t /home/public      | 设置一个文件的 STIKY 位-只允许合法的所有人删除文件           |
   | chmod o-t /home/public      | 禁用一个文件的 STIKY 位                                      |

   

9. 文件的特殊属性

   | 指令            | 功能                                                         |
   | --------------- | ------------------------------------------------------------ |
   | chattr +a file1 | 只允许以追加的方式读写文件                                   |
   | chattr +c file1 | 允许这个文件能被内核自动压缩、解压                           |
   | chattr +d file1 | 在进行文件系统备份时，dump 程序将删除这个1文件               |
   | chattr +i file1 | 设置成不可变的文件，不能被删除、修改、重命名或者链接         |
   | chattr +s file1 | 允许一个文件被安全地删除                                     |
   | chattr +S file1 | 一旦程序对这个文件进行了写操作，使系统立刻把修改的结果写到磁盘 |
   | chattr +u file1 | 若文件被删除，系统会允许你在以后恢复这个被删除的文件         |
   | lsattr          | 显示特殊的属性                                               |

   

10. 打包和压缩文件

    | 指令                                  | 功能                                                  |
    | ------------------------------------- | ----------------------------------------------------- |
    | bunzip2 file.bz2                      | 解压 file1.bz2 文件                                   |
    | bzip2 file1                           | 压缩名为 file1 文件到 .bz2 格式                       |
    | gunzip file1.gz                       | 解压名为 file1.gz 的文件                              |
    | gzip file1                            | 压缩名为 file1 的文件到 .gz 格式                      |
    | gzip -9 file1                         | 最大程度压缩                                          |
    | rar a file1.rar test_file             | 创建一个名为 file1.rar 的压缩包                       |
    | rar a file1.rar file1 file2 dir1      | 同时压缩 file1、file2 以及目录 dir1                   |
    | rar x file1.rar                       | 解压缩 rar 包（没错，是解压命令）                     |
    | unrar x file1.rar                     | 解压缩 rar 包（没错，是解压缩命令）                   |
    | tar -cfv archive.tar file1 file2 dir1 | 压缩文件 file1 和 file2 为 archive.tar 格式的压缩文件 |
    | tar -tf archive.tar                   | 显示压缩包中的内容                                    |
    | tar -xvf archive.tar -C /tmp          | 解压所包到 /tmp 目录下                                |
    | tar -cvfj archive.tar.bz2 dir1        | 创建一个 bzip2 格式的压缩包                           |
    | tar -xvfj archive.tar.bz2             | 解压缩 bzip2 格式的压缩包                             |
    | tar -cvfz archive.tar.gz dir1         | 创建一个 gzip格式的压缩包                             |
    | tar -xvfz archive.tar.gz              | 解压缩文件 archive.tar.gz                             |
    | zip file1.zip file1                   | 创建 zip 格式的压缩包                                 |
    | zip -r file1.zip file1 file2 dir1     | 将目录和文件同时压缩到一个压缩文件 file1.zip          |
    | unzip file1.zip                       | 解压缩文件                                            |

    

11. rpm 包

    | 指令                                                         | 功能                                                         |
    | ------------------------------------------------------------ | ------------------------------------------------------------ |
    | rpm -ivh package.rpm                                         | 安装一个 rpm 包                                              |
    | rpm -ivh --nodeps package.rpm                                | 安装 rpm 包，忽略包的依赖关系警告                            |
    | rpm -U package.rpm                                           | 更新包，但不改变配置文件                                     |
    | rpm -F package.rpm                                           | 更新一个确定已经安装的包                                     |
    | rpm -e package.rpm                                           | 删除安装包                                                   |
    | rpm -qa                                                      | 显示系统中所有已经安装的包                                   |
    | rpm -qa \|grep httpd                                         | 显示所有名称中包含 httpd 的包                                |
    | rpm -qi package_name                                         | 获取一个已经安装的包的特殊信息                               |
    | rpm -qg "system environment/Daemons"                         | 显示一个组件的 rpm 包                                        |
    | rpm -ql package_name                                         | 显示一个已经安装的 rpm 包提供的文件列表                      |
    | rpm -qc package_name                                         | 显示一个已经安装的 rpm 包提供的配置文件列表                  |
    | rpm -q package_name --whatrequires                           | 显示与一个 rpm 包存在依赖关系的列表                          |
    | rpm -q package_name --whatprovides                           | 显示一个 rpm 包所占的体积                                    |
    | rpm -q package_name --scripts                                | 显示在安装/删除期间所执行的脚本                              |
    | rpm -q package_name --changelog                              | 显示一个 rpm 包的修改历史                                    |
    | rpm -qf /etc/httpd/conf/httpd.conf                           | 确认所给文件由哪个 rpm 包提供                                |
    | rpm -qp package.rpm -l                                       | 显示由一个尚未安装的 rpm 包提供的文件列表                    |
    | rpm --import /media/cdrom/RPM-GPG-KEY                        | 导入公钥数字证书                                             |
    | rpm --chekcsig package.rpm                                   | 确认一个 rpm 包的完整性                                      |
    | rpm -qa gpg-pubkey                                           | 确认已安装的所有 rpm 包的完整性                              |
    | rpm -V package_name                                          | 检查文件尺寸、许可、类型、所有者、群组、MD5检查以及最后修改时间 |
    | rpm -Va                                                      | 检查系统中所有已安装的 rpm 包                                |
    | rpm -Vp package.rpm                                          | 确认一个 rpm 包还未安装                                      |
    | rpm2cpio package.rpm \|cpio --extract --make-directories \*bin* | 从一个 rpm 包运行可执行文件                                  |
    | rpm -ivh /usr/redhat/RPMS/'arch'/package.rpm                 | 从一个 rpm 源码安装一个构建好的包                            |
    | rpmbuild --rebuild package_name.src.rpm                      | 从一个 rpm 源码构建一个 rpm 包                               |

    

12. yum 软件包升级器

    | 指令                               | 功能                                                |
    | ---------------------------------- | --------------------------------------------------- |
    | yum install package_name           | 下载并安装一个 rpm 包                               |
    | yum local install package_name.rpm | 安装一个 rpm 包，使用自己的软件仓库解决所有依赖关系 |
    | yum update                         | 更新所有包                                          |
    | yum update packagte_name           | 更新某一个包                                        |
    | yum remove package_name            | 删除某一个包                                        |
    | yum list                           | 列出当前系统中安装的所有包                          |
    | yum search package_name            | 在仓库中搜寻软件包                                  |
    | yum clean packages                 | 删除下载的包                                        |
    | yum clean headers                  | 删除所有头文件                                      |
    | yum clean all                      | 删除所有缓存的包和头文件                            |

    

13. 查看文件内容

    | 指令                      | 功能                                                         |
    | ------------------------- | ------------------------------------------------------------ |
    | cat file1                 | 从第一个字节开始正向查看文件的内容                           |
    | tac file1                 | 从最后一行开始反向查看一个文件的内容                         |
    | more file1                | 查看一个长文件的内容                                         |
    | less file1                | 类似于 more 命令，但是它允许在文件中和正向操作一样的反向操作 |
    | head -2 file1             | 查看一个文件的前两行                                         |
    | tail -2 file1             | 查看一个文件的最后两行                                       |
    | tail -f /var/log/messages | 实时查看被添加到一个文件中的内容                             |

    

14. 文本处理

    | 指令                                                    | 功能                                                   |
    | ------------------------------------------------------- | ------------------------------------------------------ |
    | cat file1 \|command (sed, grep, awk, etc) > result.txt  | 合并一个文件的详细说明文本，并将简介写入一个新的文本中 |
    | cat file1 \|command (sed, grep, awk, etc) >> result.txt | 合并一个文件的详细说明文本，并将简介追加到已有的文本中 |
    | grep Aug /var/log/messages                              | 在文件中查找关键词 Aug                                 |
    | grep ^Aug /var/log/messages                             | 在文件中查找以 Aug 开头的关键词                        |
    | grep [0-9] /var/log/messages                            | 在选择文件中所有包含数字的行                           |
    | grep Aug -R /var/log/*                                  | 在 /var/log 以及子目录中搜索字符串 Aug                 |
    | sed 's/string1/string2/g' example.txt                   | 将 example.txt 文件中的 string1 替换为 string2         |
    | sed '/^$/d' example.txt                                 | 从文件中删除所有空白行                                 |
    | sed '/^#/d; /^$/d' example.txt                          | 从文件中删除所有空白行和注释行                         |
    | echo 'esempio' \| tr '[:lower:]' '[:upper:]'            | 将小写替换为大写                                       |
    | sed -e '1d' result.txt                                  | 从文件中删除第一行                                     |
    | sed -n '/string1/p' result.txt                          | 查看只包含词汇 string1 的行                            |
    | sed -e 's/ *$//' example.txt                            | 删除每一行最后的空白字符                               |
    | sed -e 's/string1//g' example.txt                       | 从文档中删除 string1 并保留剩余全部                    |
    | sed -n '1,5p;5q' example.txt                            | 查看从第一行到第五行的内容                             |
    | sed -n '5p;5q' example.txt                              | 查看第五行                                             |
    | sed -e 's/00*/0/g' example.txt                          | 用单个 0 替换多个 0                                    |
    | cat -n file1                                            | 表示文件的行数                                         |
    | cat example.txt \| awk 'NR%2==1'                        | 删除文件中所有的偶数行                                 |
    | echo a b c \| awk '{print $1}'                          | 查看第一行第一栏                                       |
    | echo a b c \| awk '{print \$1,\$3}'                     | 查看第一行第一栏和第三栏                               |
    | paste file1 file2                                       | 合并两个文件或两栏的内容                               |
    | paste -d '+' file1 file2                                | 合并两个文件或两栏的内容，中间用 + 分隔                |
    | sort file1 file2                                        | 排序两个文件的内容                                     |
    | sort file1 file2 \| uniq                                | 取出两个文件的并集，重复的行只保留一份                 |
    | sort file1 file2 \| uniq -u                             | 删除交集，留下其他的行                                 |
    | sort file1 file2 \| uniq -d                             | 取出两个文件的交集，只留下同时存在两个文件中的文件     |
    | comm -1 file1 file2                                     | 不显示只在第一个文件出现的内容                         |
    | comm -2 file1 file2                                     | 不显示只在第二个文件中出现的内容                       |
    | comm -3 file1 file2                                     | 不显示同时在两个文件中出现的内容                       |

    ---

    sort 命令将文本/文件的每一行作为一个单位相互比较。比价的原则是从首字符向后，依次按 ASCII 码值进行比较，最后按升序输出。

    ---

15. 字符设置和文件格式转换（这三个命令需要通过 yum 自行安装）

    | 指令                              | 功能                                      |
    | --------------------------------- | ----------------------------------------- |
    | dos2unix filedos.txt              | 将一个文本文件的格式从  msdos 转换为 unix |
    | unix2dos fileunix.txt             | 将一个文本文件的格式从 unix 转换为 msdos  |
    | recode ..HTML<page.txt> page.html | 将一个文本文件转换为 html 格式            |
    | recode -l \|more                  | 显示所有允许的转换格式                    |

    

16. 文件系统分析

    | 指令                   | 功能                                           |
    | ---------------------- | ---------------------------------------------- |
    | badblocks -v /dev/hda1 | 检查磁盘 hda1 上的坏磁块                       |
    | fsck /dev/hda1         | 修复/检查 hda1 磁盘上的 linux 文件系统的完整性 |
    | fsck.ext2 /dev/hda1    | 修复/检查 hda1 磁盘上 ext2 文件系统的完整性    |
    | e2fsck /dev/hda1       | 修复/检查 hda1 磁盘上 ext2 文件系统的完整性    |
    | e2fsck -j /dev/hda1    | 修复/检查 hda1 磁盘上 ext2 文件系统的完整性    |
    | fsck.ext3 /dev/hda1    | 修复/检查 hda1 磁盘上 ext3 文件系统的完整性    |
    | fsck.vfat /dev/hda1    | 修复/检查 hda1 磁盘上 FAT 文件系统的完整性     |
    | fsck.msdos /dev/hda1   | 修复/检查 hda1 磁盘上 dos 文件系统的完整性     |
    | dosfsck /dev/hda1      | 修复/检查 hda1 磁盘上 dos 文件系统的完整性     |

    

17. 初始化一个文件系统

    | 指令                         | 功能                                          |
    | ---------------------------- | --------------------------------------------- |
    | mkfs /dev/hda1               | 在 hda1 分区创建一个文件系统                  |
    | mke2fs /dev/hda1             | 在 hda1 分区创建一个 ext2 的文件系统          |
    | mke2fs -j /dev/hda1          | 在 hda1 分区创建一个 ext3（日志型）的文件系统 |
    | mkfs -t vfat 32 -F /dev/hda1 | 创建一个 fat32 文件系统                       |
    | fdformat -n /dev/fd0         | 格式化一个磁盘                                |
    | mkswap /dev/hda1             | 创建一个 swap 文件系统                        |

    

18. swap 文件系统

    | 指令                      | 功能                       |
    | ------------------------- | -------------------------- |
    | mkswap /dev/hda3          | 创建一个 swap 文件系统     |
    | swapon /dev/hda3          | 启用一个新的 swap 文件系统 |
    | swapon /dev/hda3 dev/hda2 | 启用两个 swap 文件系统     |

    

19. 备份

    | 指令                                                         | 功能                                                   |
    | ------------------------------------------------------------ | ------------------------------------------------------ |
    | dump -0aj -f /temp/home0.bak /home                           | 制作一个 /home 目录的完整备份                          |
    | dump -1aj -f /temp/home0.bak /home                           | 制作一个 /home 目录的备份                              |
    | restore -if /temp/home0.bak                                  | 还原备份文件，i 表示采用交互式方式                     |
    | rsync -rogpav --delete /home/temp                            | 同步删除目录                                           |
    | rsync -rogpav -e ssh --delete /home ip_address:/tmp          | 通过 ssh 协议同步删除目录                              |
    | rsync -az -e ssh --delete /home ip_address:/tmp              | 通过 ssh 协议将一个远程目录同步到本地                  |
    | rsync -az -e ssh --delete /home/local ip_address:/home/public | 通过 ssh 协议将本地目录同步到远程                      |
    | dd bs=1M if=/dev/hda \| gzip \| ssh user@ip_addr 'dd of=hda.gz' | 通过 ssh 协议在远程主机上执行一次备份本地文件的操作    |
    | dd if=/dev/sda of=/tmp/file1                                 | 备份磁盘内容到一个文件                                 |
    | tar -Puf backup.tar /home/user                               | 执行一次对 /home/user 目录的备份操作                   |
    | (cd /tmp/local/ && tar c.) \| ssh -C user@ip_addr 'cd /home/share/ && tar x -p' | 通过 ssh 协议在远程目录中复制一个目录内容              |
    | (tar c /home) \| ssh -C user@ip_addr 'cd /home/backup-home && tar x -p' | 通过 ssh 协议在远程目录中复制一个本地目录              |
    | tar cf- . \| (cd /tmp/backup; tar xf -)                      | 本地将一个目录复制到另一个地方，保留原有权限及链接     |
    | find /home/user1 -name '*.txt' \| xargs cp -av --tar-get-directory=/home/backup/ --parents | 从一个目录查找并复制所有以 .txt 结尾的文件到另一个目录 |
    | find /var/log -name '*.log' \| tar cv --file-from=-\| bzip2 > log.tar.bz2 | 查找所有以 .log 结尾的文件并做成一个 bzip 包           |
    | dd if=/dev/hda of=/dev/fd0/ bs=512 count=1                   | 将 MBR（master boot record） 内容复制到磁盘            |
    | dd if=dev/fd0 of=/dev/hda bs=512 count=1                     | 从已经保存到磁盘的备份中恢复 MBR 内容                  |

    ---

    关于 dump 命令的备份层级的说明：

    备份层级用数字 0-9 表示，0 级表示基本备份，即完全备份系统。对于后续的备份可以用其他数组来代替。1 级备份会保存自从执行 0 级备份以来所有被更改过的文件。2 级备份会保存自从 1 级备份以来更改过的所有文件…依次类推。

    ---

    

20. 光盘

    | 指令                                                         | 作用                                      |
    | ------------------------------------------------------------ | ----------------------------------------- |
    | cdrecord -v gracetime=2 dev=/dev/cdrom -eject blank=fast -force | 清空一个可复写的光盘内容                  |
    | mkisofs /dev/cdrom > cd.iso                                  | 在磁盘上创建一个光盘的 iso 镜像文件       |
    | mkisofs /dev/cdrom \|gzip > cd_iso.gz                        | 在磁盘上创建一个压缩的光盘的 iso 镜像文件 |
    | mkisofs -J -allow-leading-dots -R -V "Label1 CD" -iso-level 4 -o ./cd.iso data_cd | 创建一个目录的 iso 镜像文件               |
    | cdrecord -v dev=/dev/cdrom cd.iso                            | 刻录一个 iso 镜像文件                     |
    | gzip -dc cd_iso.gz \|cdrecord dev=/dev/cdrom -mount -o loop cd.iso /mnt/iso | 刻录一个压缩了的 iso 镜像文件             |
    | cdrecord --scanbus                                           | 扫描总线以识别 scsi 通道                  |
    | dd if=/dev/hdc \|md5sum                                      | 校验一个设备的 md5素描编码，例如一张 cd   |
    | mount -o loop cd.iso /mnt/iso                                | 挂载一个 iso 镜像文件                     |

    

21. 网路

    | 指令                                             | 功能                   |
    | ------------------------------------------------ | ---------------------- |
    | ifconfig ens32                                   | 显示以太网的配置       |
    | ifup ens32                                       | 启用网络设备           |
    | ifdown ens32                                     | 禁用网络设备           |
    | ifconfig ens32 192.168.1.1 netmask 255.255.255.0 | 控制 ip 地址           |
    | ifconfig ens32 promisc                           | 设置 ens32 为混杂模式  |
    | dhclient ens32                                   | 以 dhcp 模式启用 ens32 |

    





