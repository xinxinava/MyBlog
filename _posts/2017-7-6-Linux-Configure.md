---
layout: post
title:  "Linux Configure"
date:   2017-07-6 5:00:18 +0800
categories: Linux
tags: Linux
author: SteveDevin
mathjax: true
---
* content
{:toc}

一个通宵, 终于把Linux系统配置好了,记录一下配置过程：



１.添加字体：
现将要导入的ttf文件复制到一个文件夹fonts中,然后执行：

```sh
cd xxxxx/fonts
chmod u+rwx xxxxx/fonts/*

sudo mkfontscale
sudo mkfontdir
sudo fc-cache -fv

```

2.关于Linux下jekyll的安装：
```sh
sudo apt-get install ruby
sudo apt-get install ruby-dev
sudo install gem
sudo gem install jekyll
sudo gem install jekyll-paginate
```

3.关于Linux下中文输入法的安装：

　　　3.1先从[搜狗拼音官网](http://pinyin.sogou.com/linux/?r=pinyin)下载合适的安装包　xx.deb

　　　3.2 `sudo dpkg -i xx.deb `

　　　3.3 如果没安装fcitx则可以 `sudo apt-get install -f ` 或者　` sudo apt-get install fcitx `　安装

　　　3.4最后根据个人的使用习惯设置一下快捷键,皮肤即可

4.剩下的以后再补充