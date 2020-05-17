---
layout: post
title: 手机作为电脑的扬声器;PowerShell下载;Go环境配置
subtitle: 基于同步听的实现
description: TODO
author: Xiakai
date: 2020-05-17
tags:
  - 日常记录
  - Android
  - PowerShell
  - Go环境配置
---

## 计算机扬声器扩展

### 软件准备

- 手机端、电脑端下载“同步听”

### RealmeX 打开 USB 调试

- 设置-关于手机-版本信息-版本号（点击 7 下进入开发者模式）-返回设置-其他设置-开发者选项-USB 调试。

## PowerShell 命令行下载

- 语句格式：`wget -Uri "https://labfile.oss-cn-hangzhou.aliyuncs.com/courses/1300/tcpip.zip" -OutFile "tcpip.zip"`

## Go 环境配置

> 参考：<https://www.runoob.com/go/go-environment.html>

- 安装包下载：<https://golang.google.cn/doc/install?download=go1.14.3.windows-amd64.msi>
- 安装（似乎不用设置环境变量）
- 使用：go run filename-运行；go build filename-生成二进制文件
