# 1.操作系统

#### 桌面级的操作系统

- windows  优势:用户基数大

- mac   优势:适合开发

- Linuc :应用少

  

#### 服务器操作系统

- Linux   安全,稳定,免费 ,占有率高
- Windows Server   付费 占有率低

#### 嵌入式操作系统

- iOS
- Android(基于Linux)



# 2.Linux文件与目录

#### Linux 主要目录速查

- "/:"根目录,一般之存放目录,在Linux下只有一个根目录,所有的东西从这里

  开始

- "/bin": 可执行的二进制文件目录,例: ls,tar,mv,cat等等

- "/boot": 防止Linux系统启动时用到的一些文件,如 Linux的内核文件,相当于访问某一个设备:` /boot/vmlinuz`,系统引导管理器:`/boot/group`

- "dev":存放系统下的设备文件,访问该目录下的某文件,相当于访问某个设备,常用的是挂载光驱`mount/dev/cdrom/mnt`

- "etc":系统配置文件存放的目录,不建议在此目录下存放可执行文件,重要的配置文件有:

  - /etc/inittab
  - /etc/fstab
  - /etc/init.d
  - /etc/X11
  - /etc/sysconfig
  - /etc/xinetd.d

- "/home":系统默认的用户家目录,新增用户账号时,用户的家目录都存在此目录下

  ~表示当前用户家目录

  ~deu表示edu的家目录

- "/lib`/usr/lib` `/usr/local/lib`":系统使用函数库的目录,程序在执行过程中,需要调用一些额外的参数时需要函数库的协助
- `/lost found`系统异常产生错误时,会将一些遗失的片段放置于此目录下
- `/mnt:/media `系统默认光盘挂载点,通常光盘挂在于/mnt/cdrom
- `/opt`:给主机额外安装软件所存放的目录
- `/proc`: 此目录的数据都在内存中,如系统心,外部设备,网络状态,由于数据都放在内存中,所以不占磁盘空间
- `root`:系统管理员root的家目录
- `sbin` ` /usr/sbin`  `usr/local/sbin`  :  放置系统系统管理员使用的可执行的命令 , 如 fdisk、shutdown、mount 等。与 /bin 不同的是，这几个目录是给系统管理员 root 使用的命令，一般用户只能"查看"而不能设置和使用 
-  ` tmp`  :一般用户或正在执行的程序临时存放文件的目录,任何人都可以访问,重要数据不不可放置在此目录下
- `srv`:服务启动后需要访问的数据目录,如www服务需要访问的数据存放在`/src/www`内
- `usr` :应用程序存放目录
  - /usr/bin：存放应用程序
  - /usr/share：存放共享数据
  - /usr/lib：存放不能直接运行的，却是许多程序运行所必需的一些函数库文件
  - /usr/local：存放软件升级包
  - /usr/share/doc：系统说明文件存放目录
  - /usr/share/man：程序说明文件存放目录

- `var`:放置系统执行过程中经常变化的文件
  - /var/log：随时更改的日志文件
  - /var/spool/mail：邮件存放的目录
  - /var/run：程序或服务启动后，其 PID 存放在该目录下

# 3.Linux常用命令

| 序号 | 命令           | 对应英文             | 作用                     |
| ---- | -------------- | -------------------- | ------------------------ |
| 01   | ls             | list                 | 查看当前文件夹下的内容   |
| 02   | pwd            | print wrok directory | 查看当前所在文件夹       |
| 03   | cd [目录名]    | change directory     | 切换文件夹               |
| 04   | touch [文件名] | touch                | 如果文件不存在，新建文件 |
| 05   | mkdir [目录名] | make directory       | 创建目录                 |
| 06   | rm [文件名]    | remove               | 删除指定的文件名         |
| 07   | clear          | clear                | 清屏                     |

