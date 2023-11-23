**打造Ubuntu专属系统：**

安装Ubuntu图形化界面：

```csharp
//更新服务器：
apt-get update
apt-get upgrade -y
apt-get dist-upgrade -y
//安装图形化界面：
apt-get install ubuntu-desktop
//开始安装桌面环境所需软件包（里面包括系统面板、窗口管理器、文件浏览器、终端等桌面应用程序）
apt install gnome-panel gnome-settings-daemon metacity nautilus gnome-terminal ubuntu-desktop
```

配置VNC（不是内置的很卡，没解决之前没啥用）：

```csharp
apt-get install tightvncserver	//安装VNC
sudo apt remove realvnc-vnc-server	//卸载VNC
vncserver 		//启动VNC
vncserver -kill :1   //关闭已启动的VNC：
vncserver -geometry 2560x1440 :1	//启动一个新的VNC，VNC的端口号仍为1：
cp ~/.vnc/xstartup ~/.vnc/xstartup.bak		//备份VNC的xstartup配置文件
vim ~/.vnc/xstartup			    //修改VNC的xstartup配置文件

//按I键进入编辑模式，并将配置文件修改为新的配置文件：     
//原有的配置文件
#!/bin/sh
xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession
-----------------------------------------------------------------------------------------------------
//新的配置文件
#!/bin/sh
export XKL_XMODMAP_DISABLE=1
export XDG_CURRENT_DESKTOP="GNOME-Flashback:GNOME"
export XDG_MENU_PREFIX="gnome-flashback-"
gnome-session --session=gnome-flashback-metacity --disable-acceleration-check &
//按Esc键，然后输入`:wq`并按Enter键，保存退出文件，再运行vncserver -kill :1
```

安装Ubuntu常用软件：

```csharp
sudo apt-get install unrar	//安装解压软件unrar
```



**Ubuntu 20.4 没有language support：**

```clike
locale -a		//检查是否安装了中文语言包，查看是否有：zh_CN.utf8
sudo apt-get install language-pack-zh-hans	//安装中文语言包，输入以下命令：
locale-gen zh_CN.UTF-8	//添加中文支持
```



**删除操作：**

```csharp
rm -rf XXX	//删除XXX文件夹
rm -f XXX.XXX	//删除文件
```



**jobs命令：**

```csharp
jobs		      //显示被挂起的进程
jobs -l		//显示更详细的信息
```



**CTRL命令：**

```csharp
ctrl+z	//挂起进程或程序
ctrl+c	//停止进程或程序
```



**防火墙操作：**

```csharp
sudo ufw status	//查看防火墙状态
```





