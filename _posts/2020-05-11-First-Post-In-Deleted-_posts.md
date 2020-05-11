---
layout:		post			
title:		My First Post		
subtitle:	Hello World, Hello Blog	
date:		2020-05-11		
author:		Xiakai
header-img:	img/first-post.jpg	
catalog:	true			
tags:					
    - 日常记录
---
> 这是我的第一篇有内容的博客

# 关于格式
+ 添加了首行引用，应该不会再有正文首行的奇怪缩进了吧。
+ 然而即使删除首行引用也不再有首行前凸的现象了。

# Solved Problem
1. `_config.yml`中的缩进问题：`tags`下若使用`Tab`而非`空格`将导致段首的相关信息无法生成信息表格（见`Preview changes`），需要使用四个`空格`来完成缩进。
2. `post内容`不显示的原因：删除原`post内容`并手动创建对应文件夹时，将`_posts`写成了`_post`，导致其中的`post`文本一直无法识别并显示。

