---
layout: post
title: iPad作为Windows的扩展屏
subtitle: 依赖于Splashtop Wired XDisplay的实现
description: 屏幕扩展≠屏幕复制or远程控制
author: Xiakai
date: 2020-05-15
header-img: img/first-post.jpg
tags:
  - 日常记录
  - Windows10
---

## 设备

- iPad Air
- Windows10
- Aspire E5-576G

## 方法详述

1. `iPad` 端在 `App Store` 中下载*Splashtop Wired XDisplay HD-显示器扩展与镜像*，如下图所示：![iPad端软件](../img/2020-05-15-01.png)

2. PC 端下载`Splashtop_Wired_XDisplay_Agent`：<https://www.splashtop.com/cn/wiredxdisplay>

3. USB 连接 iPad 和 PC，iPad 端出现与 PC 相同的桌面（镜像模式，默认不开启），PC 桌面出现如下图所示的应用界面：![USB连接后的PC应用界面](../img/2020-05-15-02.png)

4. 点击*设置分辨率*，自动打开**设置/系统/显示**，显示如下：![屏幕排列设置界面](../img/2020-05-15-04.png "设置")

5. 按下 Windows+P 快捷键，屏幕右侧出现四个选项，选择其中的`扩展`，如下图所示：![投影](../img/2020-05-15-03.png "Win+P 投影")。

6. `标识`以分辨屏幕，拖动并排列好屏幕后点击`应用`，结果如图所示：![标识并扩展后的屏幕](../img/2020-05-15-05.png "扩展后的屏幕（全屏幕截图）")![实物截图](../img/2020-05-15-06.jpg "实景展示")

## 后记

- 其实在这之前已经多次尝试过，但是`iPad Air`总是不能作为扩展屏被识别，只能用于屏幕复制，调节画质和帧率后根本无法作为屏幕设备被连接。
- 今天忽然就可以可也并不知道为什么，但在这之前出现了亮度调节条消失（`Fn+向右`快捷键也无法使用）的状况，且亮度解决后依然可用。
