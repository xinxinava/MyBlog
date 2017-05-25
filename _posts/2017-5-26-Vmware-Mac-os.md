---
layout: post
title:  "Vmware & Mac os"
date:   2017-05-26 01:42:18 +0800
categories: System
tags: MacOs
author: SteveDevin
mathjax: true
---
* content
{:toc}

### Vmware 安装 Mac os 的方法

1. 需求: [Vmware workstation player](http://www.vmware.com/products/player/playerpro-evaluation.html)、[unlocker](http://www.insanelymac.com/forum/files/file/339-unlocker/)、Mac os系统镜像
Mac os镜像可从我的百度云链接下载(链接: https://pan.baidu.com/s/1c25rK3I 密码: 3ii6)

2. 关闭Vmware workstation player的情况下运行 unlocker 相应系统下的安装程序, 需要管理员权限.



3. 新建虚拟机, 选择想安装的mac os 版本, 创建完成后：
	1. 若Vmware workstation player版本在11以上，需要用文本编辑器打开虚拟机文件 xx.vmx, 在最后添加一下配置:`smc.version = "0"`
	2. 打开虚拟机设置.
		1. Hardware, USB Controller USB compatibility set as `USB 2.0`
		2. Options, General Enhanced keyboard set as `Use if available(recommended)`
		3. Options, Advanced, Input grabbed set as `High`, Gather debugging information set as `None`, and `check` the Disable memory page trimming.


4. 将下载的 xx.cdr 更改扩展名为 xx.iso, 加载到虚拟机上

5. 接下来就可以安装系统啦

6. 安装好 VMware Tools 后就可以放心开心的食用啦(￣▽￣)"