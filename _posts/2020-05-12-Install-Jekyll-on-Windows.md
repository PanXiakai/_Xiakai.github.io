---
layout: post
title: Windows下Jekyll的安装
subtitle: According to https://achuan.io/2019-03-29-Jekyll-installation.html
date: 2020-05-12
author: Xiakai
header-img: img/home-bg-art.jpg
catalog: true
tags:
  - Jekyll
  - Windows
---

## Install Ruby+Devkit

### 下载

- 下载地址：`https://github.com/oneclick/rubyinstaller2/releases/download/RubyInstaller-2.6.6-1/rubyinstaller-devkit-2.6.6-1-x64.exe`(recommended)
- 官方已有

### 更新源（官方源下载过慢）

- 查看当前源：任意位置打开命令行，输入`gem sources -l`，得到如下结果

  ```shell
  D:\Software\Ruby27-x64\Ruby27-x64
  λ gem sources -l
  *** CURRENT SOURCES ***

  https://rubygems.org/
  http://gems.ruby-china.com
  ```

- 删除默认源：输入`gem sources -r https://rubygems.org/`，执行结果如下

  ```shell
  D:\Software\Ruby27-x64\Ruby27-x64
  λ gem sources -r https://rubygems.org/
  https://rubygems.org/ removed from sources
  ```

- 添加新源：输入`gem sources -a http://gems.ruby-china.com`，执行结果如下

  ```shell
  D:\Software\Ruby27-x64\Ruby27-x64
  λ gem sources -a http://gems.ruby-china.com
  http://gems.ruby-china.com added to sources
  ```

## Install the Jekyll Gem

- 输入`gem install jekyll`，等待几分钟直至显示安装完成信息。

## Install Github-Pages

- Install Bundler: 输入`gem install bundler`，执行结果如下

  ```shell
  D:\Software\Ruby27-x64\Ruby27-x64
  λ gem install bundler
  Fetching bundler-2.1.4.gem
  Successfully installed bundler-2.1.4
  Parsing documentation for bundler-2.1.4
  Installing ri documentation for bundler-2.1.4
  Done installing documentation for bundler after 7 seconds
  1 gem installed
  ```

- jekyll 安装补充

  ```shell
  D:\Software\Ruby27-x64\Ruby27-x64
    λ gem install jekyll-paginate
    Fetching jekyll-paginate-1.1.0.gem
    Successfully installed jekyll-paginate-1.1.0
    Parsing documentation for jekyll-paginate-1.1.0
    Installing ri documentation for jekyll-paginate-1.1.0
    Done installing documentation for jekyll-paginate after 0 seconds
    1 gem installed
  ```

## 本地调试

### 初始化全新网页

- 输入`jekyll new <网址> && <网址>`

  ```shell
  D:\Software\Ruby27-x64
  λ jekyll new Xiakai.io && Xiakai.io
  Running bundle install in D:/Software/Ruby27-x64/Xiakai.io...
  ```

### 调试

- 进入博客文件夹，打开本地调试

  ```shell
  D:\Software\Ruby27-x64
  λ cd XiakaiPan.github.io\

  D:\Software\Ruby27-x64\XiakaiPan.github.io (master -> origin)
  λ jekyll serve
  Configuration file: D:/Software/Ruby27-x64/XiakaiPan.github.io/_config.yml
              Source: D:/Software/Ruby27-x64/XiakaiPan.github.io
      Destination: D:/Software/Ruby27-x64/XiakaiPan.github.io/_site  Incremental build: disabled. Enable with --incremental
      Generating...
      Jekyll Feed: Generating feed for posts
                      done in 0.429 seconds.
  Auto-regeneration: enabled for 'D:/Software/Ruby27-x64/XiakaiPan.github.io'
      Server address: http://127.0.0.1:4000
  Server running... press ctrl-c to stop.
  ```

## **_以下可选_**

## Install a Syntax Highlighter

- Install Rouge

  - 输入`gem install rouge`，执行结果如下

  ```shell
  D:\Software\Ruby27-x64\Ruby27-x64
    λ gem install rouge
    Fetching rouge-3.19.0.gem
    Successfully installed rouge-3.19.0
    Parsing documentation for rouge-3.19.0
    Installing ri documentation for rouge-3.19.0
    Done installing documentation for rouge after 6 seconds
    1 gem installed
  ```

  - 安装 gem 依赖文件

  ```shell
  gem install minima
  gem install tzinfo-data
  gem install wdm
  ```

  - Question

    - 中断初始化之后，重新初始化后出现下列错误

    ```shell
    D:/Software/Ruby27-x64/Ruby27-x64/lib/ruby/2.7.0/bundler/resolver.rb:290:in `block in verify_gemfile_dependencies_are_found!': Could not find gem 'tzinfo (~> 1.2) x64-mingw32' in any of the gem sources listed in your Gemfile. (Bundler::GemNotFound)
    ```

### **未解决**

## Reference

- `http://jekyll-windows.juthilo.com/`
