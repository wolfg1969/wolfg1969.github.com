---
layout: post
title: "Raspberry Pi上配置GPSd"
date: 2013-02-26 16:20
comments: true
categories: Raspberry Pi
tags:
- raspberry pi
- gpsd
- gps
- ntp
---

硬件连接
========

我用的是一款型号为UC-915的GPS接收模块，淘宝上购买的，选择的速率是38400bps。它有6个引脚，陶瓷天线的一面朝上，由左到右一次是：

1. GND 接地
2. TX 数据输出
3. RX 命令及数据输入
4. NC 悬空
5. VCC 5V电源
6. NC 悬空

对应树莓派的引脚，接线方法就是：

1. -> 6
2. -> 10
3. -> 8
5. -> 2

引线接好后，接通电源启动树莓派。进入系统后，用minicom命令检查是否正确连接了GPS模块。

配置GPSd
========

查看定位信息
============

同步系统时间
============


