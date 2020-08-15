---
layout:     post
title:      （新 ※必看）解决VMware由于卸载不干净导致安装出现“用户在命令行上发出了 EULAS_AGREED=1，表示不接受许可协议。”
subtitle:   学习修行
date:       2020-03-24
author:     Zhangyoung
header-img: 
catalog: 	 true
tags:
    - 学习修行
---

**要是大家也遇到这个问题，请务必看完我的，再去操作。谢谢！**
       这个问题折磨了我两天，终于解决了，对于我经常要用虚拟机的人，安装不了真的很头疼。

       大家可以看下这个安装日志，尝试了多少次就失败了多少次。
![](https://img-blog.csdnimg.cn/20200324161341565.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3MzgwNTc1,size_16,color_FFFFFF,t_70)
安装时出现这个：
![](https://img-blog.csdnimg.cn/20200324161506158.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3MzgwNTc1,size_16,color_FFFFFF,t_70)
是由于之前卸载不干净，所导致的，所以我在网上搜了很多，比如powershell下，使用安装包后加“/c”命令清除安装注册信息，再次安装即可。但是我使用这个命令执行，直接就执行安装程序，根本就没有安装程序已成功清除……的这个提示。还有的方法是取找到这个路径下的C:\Program Files (x86)\CommonFiles\VMware\InstallerCache的里面的就的MSI文件执行安装，但是我的也安装不了旧的版本，启动过一会就闪退。
![](https://img-blog.csdnimg.cn/20200324162838986.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3MzgwNTc1,size_16,color_FFFFFF,t_70)
后来，我又去搜了一下，去看了我之前看的网页里面，发现他们用来清理安装注册信息的安装包都是2018年发布的，例如：VMware-workstation-full-15.0.2-10952284.exe，而我用的是最新的安装包（VMware-workstation-full-15.5.2-15785246.exe，这是2020年3月发布的）。所以我去网上找了他们所距离的安装包，再次在powershell里使用命令“D:\MI\Downloads\Programs\VMware-workstation-full-15.0.2-10952284.exe /c”再点击确定。然后运行我的最新的安装包就能成功安装了。
       这里要注意的是，清除安装信息必须使用很旧的安装包，最好是我这个VMware-workstation-full-15.0.2-10952284.exe，版本号为15.0.2的安装包，高于这个版本，使用命令----/c，是不会弹出清除安装信息对话框的！
       希望能够帮到大家，最后我附上我上文说的VMware-workstation-full-15.0.2-10952284.exe的下载地址：[点此下载](https://download3.vmware.com/software/wkst/file/VMware-workstation-full-15.0.2-10952284.exe?HashKey=db56b8c60ad82b772965fbfe7e321830&ext=.exe&params=%7B%22custnumber%22%3A%22JWRkcEBlQGV3dA%3D%3D%22%2C%22sourcefilesize%22%3A%22511.84+MB%22%2C%22dlgcode%22%3A%22WKST-1502-WIN%22%2C%22languagecode%22%3A%22cn%22%2C%22source%22%3A%22DOWNLOADS%22%2C%22downloadtype%22%3A%22manual%22%2C%22eula%22%3A%22Y%22%2C%22downloaduuid%22%3A%22411a51c6-9b6d-470e-9c47-73d17d8113e3%22%2C%22purchased%22%3A%22N%22%2C%22dlgtype%22%3A%22Product+Binaries%22%2C%22productversion%22%3A%2215.0.2%22%2C%22productfamily%22%3A%22VMware+Workstation+Pro%22%7D&AuthKey=1585035857_b5b275b750f13ec18dc9d16d5dea6ae2&ext=.exe)