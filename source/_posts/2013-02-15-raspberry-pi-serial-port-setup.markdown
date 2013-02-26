---
comments: true
date: 2013-02-15 17:23:40
layout: post
slug: raspberry-pi-serial-port-setup
title: 树莓派串口配置
wordpress_id: 1272
categories: Raspberry Pi
tags:
- minicom
- raspberry pi
- serial port
- wajig
---

树莓派的串口接口是P1接口上面一排（靠近板子边缘的一排）左数第4针（TX）和第五针（RX）





[![](http://guoyong.me/blog/wp-content/uploads/2013/02/RPI-serial_UART-224x300.png)](http://guoyong.me/blog/wp-content/uploads/2013/02/RPI-serial_UART.png)





系统中对应的串口设备是/dev/ttyAMAO，但默认用于内核输出日志的。若想连接串口设备，比如GPS模块，需要改动系统这个默认配置。





配置方法如下（修改2个文件，记得先备份好原始文件）：







  * 修改 /boot/cmdline.txt




    
    $ sudo vi /boot/cmdline.txt
    





将原来的内容




    
    dwc_otg.lpm_enable=0 console=ttyAMA0,115200 kgdboc=ttyAMA0,115200 console=tty1 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline rootwait
    





修改成




    
    dwc_otg.lpm_enable=0 console=tty1 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline rootwait
    







  * 修改/etc/inittab 注释掉下面这一行，一般是文件的最后一行。注释掉就是在行首添加一个英文井号。




    
    $ sudo vi /etc/inittab 




    
    #T0:23:respawn:/sbin/getty -L ttyAMA0 115200 vt100
    





顺便说下命令行下用什么编辑器，我比较习惯用vi。对命令行不太熟悉的同学就用nano吧，用之前google下教程，非常简单。





改好这两个文件后，关机。接好串口设备开机，为了检查串口有没有工作，需要安装个串口通讯软件minicom。




    
    $ wajig install minicom
    





这里我使用了wajig这个工具，它对apt系列工具进行了封装，更易用，强烈推荐。





安装好minicom后，需要先根据你的串口设备进行相应的设置，比如速率什么的




    
    $ sudo minicom -s 





[![](http://guoyong.me/blog/wp-content/uploads/2013/02/minicom_1-266x300.png)](http://guoyong.me/blog/wp-content/uploads/2013/02/minicom_1.png)





选择主菜单的第三项Serial Port Setup，进入下一级菜单。





[![](http://guoyong.me/blog/wp-content/uploads/2013/02/minicom_2-266x300.png)](http://guoyong.me/blog/wp-content/uploads/2013/02/minicom_2.png)





用菜单项的第一个提示字母选择：按A 修改串口设备为 /dev/ttyAMA0，按E修改速率等设置





[![](http://guoyong.me/blog/wp-content/uploads/2013/02/minicom_3-266x300.png)](http://guoyong.me/blog/wp-content/uploads/2013/02/minicom_3.png)





设置好后，主菜单里选择Save setup as dfl保存，然后选择Exit（最后一项Exit from Minicom是退出程序）。如果设置正确，就应该收到一些数据了。按Ctrl+A，再按Z可以查看minicom的帮助，Ctrl+A再按Q退出minicom。





串口设置好了，下一篇介绍gpsd的配置。最后，欢迎订阅微信公众帐号“树莓派玩家”，搜索raspberry_pi或者扫描下面的二维码。





[![](http://guoyong.me/blog/wp-content/uploads/2013/02/qrcode_for_gh_f5648ddbdaf3_258.jpg)](http://guoyong.me/blog/wp-content/uploads/2013/02/qrcode_for_gh_f5648ddbdaf3_258.jpg)



