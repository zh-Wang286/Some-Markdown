## VMware

威睿（英语：VMware, Inc.）是戴尔科技（戴尔电脑母公司）旗下软件公司，提供云计算和硬件虚拟化的软件和服务。

VMware Workstation（曾用名VMware Workstation）是VMware公司推出的一款桌面虚拟计算软件，具有Windows、Linux 版本。此软件可以提供虚拟机功能，使计算机可以同时运行多个不同操作系统。

VMware Workstation的免费版并改名为VMware Workstation Player，付费版定名为VMware Workstation Pro。

![image-20211016132230333](image-20211016132230333.png)

```html
下载链接：
https://www.vmware.com/products/workstation-player/workstation-player-evaluation.html
https://www.vmware.com/products/workstation-pro/workstation-pro-evaluation.html
```

相比之下，player版本免费使用，体积小，可以满足体验的需求；pro功能更全面，支持快照、克隆虚拟机、加密虚拟机等功能。

![image-20211016135140265](image-20211016135140265.png)

（ps：可以试着去搜索VMware Workstation Pro密钥）

## Ubuntu

Ubuntu是基于Debian、以桌面应用为主的Linux发行版，是著名的Linux发行版之一，也是目前最多用户的[Linux版本。

还有其他Linux发行版，比如Debian、CentOS、manjaro …… 只不过我选了Ubuntu，下面内容以Ubuntu18.04为例。

对于刚刚接触Linux的新人来说，建议直接下载ISO格式文件（当然也可以用种子下载ISO），方便后续安装。注意，选择桌面版（desktop）。

```
Ubuntu下载链接：
官方网址（不推荐） https://www.ubuntu.com/download
中国官网 https://cn.ubuntu.com/download/desktop
清华大学开源软件镜像站 https://mirrors.tuna.tsinghua.edu.cn/ubuntu-releases/
中国科学技术大学开源镜像站 https://mirrors.ustc.edu.cn/ubuntu-releases/
```

![image-20211016134922711](image-20211016134922711.png)

## 创建虚拟机

下载并安装完VMware后，便可开始创建虚拟机。这里，推荐本地电脑有6G以上运行内存（打开命令行运行窗口，输入`systeminfo`可查看电脑硬件信息）。

![image-20211016141136879](image-20211016141136879.png)

打开VMware，右上角“文件”-“新建虚拟机”。如果对虚拟机配置不甚了解，这里选择“典型”配置。

![image-20211016135418385](image-20211016135418385.png)

这里选择“安装程序光盘映像文件”，浏览找到上一步我们下载Ubuntu的目录

![image-20211016135721356](image-20211016135721356.png)

这里用户名与密码，即是操作系统的登录账户密码，同时也是`root`账户的密码，密码要牢记，用户名可以在系统中通过`whoami`命令查看。

![image-20211016135900284](image-20211016135900284.png)

设置虚拟机存储路径与分配磁盘容量，这里不建议安装在系统盘（如C盘）。

![image-20211016140239231](image-20211016140239231.png)

![image-20211016140304060](image-20211016140304060.png)

全部设置完成后，即可开始创建虚拟机。内存默认分配4G，后面创建完成后也可修改。

![image-20211016140345661](image-20211016140345661.png)

创建时间视电脑情况而定，10分钟到一个多小时不等，创建完成后，就可以看到Ubuntu的用户登录界面啦。

![image-20211016141331689](image-20211016141331689.png)

输入上面设置的密码，登录成功。可以看到桌面上已有Ubuntu内置的Firefox浏览器与其他应用程序。

![image-20211016141647564](image-20211016141647564.png)

在桌面，右键打开终端，就可以看到我们熟悉的命令行窗口了。

![image-20211016141808800](image-20211016141808800.png)

## 关于中文输入

Ubuntu默认不包含中文输入法，这里以搜狗输入法为例，介绍如何安装中文输入法。

> 搜狗输入法Linux版 https://pinyin.sogou.com/linux/?r=pinyin
>
> 安装指南 https://pinyin.sogou.com/linux/help.php

Linux系统输入法框架有多种，以Ubuntu 18.04为例，默认是不包含`fcitx`框架的，需要我们手动安装。安装完成后再进行后面步骤。

```bash
sudo apt-get install fcitx #安装fcitx框架
sudo apt -f install #如果安装时提示缺少相关依赖，可执行此命令解决
```

打开桌面右上角系统设置，找到“区域与语言”-“管理已安装的语言”

![image-20211016143114158](image-20211016143114158.png)

初次设置时可能没有中文，需要手动安装。这个安装需要一些时间。安装完后，点击“应用到整个系统”，然后关闭窗口，重启电脑。

![image-20211016143808742](image-20211016143808742.png)

通过命令行安装搜狗输入法，安装完后再次重启。

```{bash}
sudo dpkg -i sogoupinyin_2.4.0.3469_amd64.deb # sudo dpkg -i sogoupinyin_版本号_amd64.deb
```

再次登录系统后，即可通过`Ctrl+Shift` 和`Ctrl+Space`控制输入法转换啦！

![image-20211016144925340](image-20211016144925340.png)

