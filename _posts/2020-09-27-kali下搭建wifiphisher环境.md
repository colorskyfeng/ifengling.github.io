---
layout: post
title: kali2.0搭建Wifiphisher钓鱼环境遇到的问题
categories: [环境搭建]
tags: [无线安全]
description: Sample placeholder post.
---

0x00 准备
---------------------------------------------------
{% highlight ruby %}
Kali 2.0
无线网卡 （兼容kali无驱动安装）
{% endhighlight %}

0x01 配置apt源
---------------------------------------------------
1）备份
{% highlight ruby %}
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak 
{% endhighlight %}

2）修改
{% highlight ruby %}
sudo vim /etc/apt/sources.list
{% endhighlight %}
将source.list文件内容替换成下面的
{% highlight ruby %}
deb http://mirrors.aliyun.com/ubuntu/ trusty main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-backports main restricted universe multiverse
{% endhighlight %}

3）更新
{% highlight ruby %}
sudo apt-get update
{% endhighlight %}


相关报错
1、	提示没有公钥错误时，执行命令
{% highlight ruby %}
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6AF0E1940624A220 
{% endhighlight %}
#此处6AF0E1940624A220需要是错误提示的key

2、	提示缺少dirmngr时，执行命令
{% highlight ruby %}
sudo apt-get install dirmngr
{% endhighlight %}

3、	提示依赖包故障时
{% highlight ruby %}
sudo apt-get remove libgmime*  #此处的libgmime对应途中的红框内容
{% endhighlight %}

0x02 安装 python3-pip
---------------------------------------------------
下载python3对应的pip
 {% highlight ruby %}
wget  https://bootstrap.pypa.io/get-pip.py
{% endhighlight %}

 
等待下载成功后，执行脚本对pip3进行安装
 {% highlight ruby %}
python3 get-pip.py
{% endhighlight %}


0x03 安装wifipisher
---------------------------------------------------
 {% highlight ruby %}
 下载最新的代码
git clone https://gitee.com/mirrors/Wifiphisher.git 
切换到 Wifiphisher目录
cd Wifiphisher 
安装依赖
sudo python setup.py install 

{% endhighlight %}



