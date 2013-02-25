---
comments: true
date: 2013-01-03 21:02:27
layout: post
slug: play-raspberry-pi-day1
title: Raspberry Pi 跨年之旅 - 第一天
wordpress_id: 1139
categories:
- Linux
tags:
- Linux
- raspberry pi
---

2012年12月30日，元旦5天假期开始。公司是文艺公司，所以连放五天假。天气寒冷，不想到户外活动。想起了买来后一直没动过的树莓派，决定趁着有时间赶紧玩一玩。



先去到官网，读了下Quick Start文档，下载Raspbian “wheezy”映像文件。



接着开始准备硬件：







  1. SD卡：闲置的一个PNY Class 6 4GB


  2. 键盘鼠标：闲置的一套罗技无线键鼠 型号K260


  3. 电源：TP-LINK无线路由器WR703N的电源，输出电源5V，电流1A


  4. 显示设备：家里的液晶电视，有HDMI接口


  5. 无线网卡：闲置的腾达150M USB无线网卡


  6. 4口USB Hub一个


  7. 罗技摄像头



[![树莓派需要的硬件](http://guoyong.me/blog/wp-content/uploads/2013/01/IMG_4230-150x150.jpg)](http://guoyong.me/blog/wp-content/uploads/2013/01/IMG_4230.jpg)



安装Raspbian系统到SD卡，用的是dd命令，详细过程参考[这里](http://elinux.org/RPi_Easy_SD_Card_Setup)



接好各个部分，开机！结果，没显示。。。（我确定电视已经切换到正确的信号源）。一番搜索，[官网论坛](http://www.raspberrypi.org/phpBB3/viewtopic.php?f=28&t=23624)里找到一样的问题，里面指出了[解决方法](http://elinux.org/R-Pi_Troubleshooting#Display)。



修改SD卡根目录下的config.txt文件（后话：这个文件在扩展root文件系统后的路径是/boot/config.txt），两处地方：




    
    <code>config_hdmi_boost=4
    hdmi_force_hotplug=1
    </code>



重新开机，看到启动画面了！



系统进入了raspi-config程序，一定要设置键盘布局，layout要改成US（我是用了一会儿发现按键不对才用运行raspi-config修改的）。locale也选en_US为默认，把zh_CN的几个也选上。选择时区，最后选定扩展root文件系统至SD卡。



初始设置完成后，系统进入LXDE桌面。打开wpa_gui程序（桌面上有图标），设置无线网络。这里也遇到个小弯路，家里路由器的安全设置设置了仅使用AES加密方式，结果wpa_supplicant不支持，修改路由器设置后成功连接Wifi。



连上网后，apt-get更新系统，安装熟悉的各种工具：wajig, git, ......



马上clone了自己之前写的后台播放豆瓣电台的[Python程序](https://github.com/wolfg1969/fmbox)，wajig安装几个依赖后，运行成功，比起折腾路由器上折腾OpenWRT真是轻松多了。



想到自己还有一个闲置的液晶显示器，VGA接口的，于是马上到京东上下单购买HDMI到VGA的转接线，预计第二天就可以到了。



当天的几张照片：



[![](http://guoyong.me/blog/wp-content/uploads/2013/01/IMG_4165-e1357225571542-150x150.jpg)](http://guoyong.me/blog/wp-content/uploads/2013/01/IMG_4165.jpg)



[![](http://guoyong.me/blog/wp-content/uploads/2013/01/IMG_4168-e1357225618376-150x150.jpg)](http://guoyong.me/blog/wp-content/uploads/2013/01/IMG_4168.jpg)



[![](http://guoyong.me/blog/wp-content/uploads/2013/01/IMG_4170-e1357225409692-150x150.jpg)](http://guoyong.me/blog/wp-content/uploads/2013/01/IMG_4170.jpg)



待续。。。 （图像显示自动旋转了90度，将就下吧）



