---
title: esp8266刷wifi钓鱼固件
date: 2018-10-03 15:38:12
tags: 其他技术
categories: 其他技术
preview: https://startzyp.github.io/imgs/log/2018-10-03/3.png
---

# 1．准备esp8266模块

首先当然你要有一块esp8266模块，像这样的，最好是有底板的，带Micro口的，这些淘宝上都可以搜到的，我的就是淘宝上买的，大概15RMB，以前挺贵的。

![](https://startzyp.github.io/imgs/log/2018-10-03/3.png)

# 2.如何将固件下载到esp8266中

如果是淘宝买的直接用USB安卓线连电脑的那种先要安装TTL转USB CH340的驱动，其实如果有驱动精灵的话，插上驱动精灵扫一下就帮你安装了。反正为没用。

ps:其实其他刷固件的也行.反正为用的刷这个

Flash下载工具：http://espressif.com/zh-hans/support/download/other-tools
将自己的esp8266插到电脑上，确定连接没问题的话打开设备管理器看下自己的串口是多少，我这边是COM4

将下载的Flash下载工具解压，打开ESPFlashDownloadTool_v3.4.9.2.exe，打开是这样的，选择esp8266 DownloadTool

![](https://startzyp.github.io/imgs/log/2018-10-03/4.png)

## 在这里需要注意的几点是:

（1）固件选择之前下载的固件DNS.ino.ino.nodemcu.bin。
（2）地址输入0×00000（可能地址这一栏会出现红色的状况，导致无法烧入固件，此时把下载器关了重启下，然后把地址那栏清空再自己手动输入就好了）。
（3）这边需要将DoNotChgBin勾选起来，否则烧入固件后可能没有wifi，当然不同的板子可能不太一样，这个请大家自行测试。

（4）这边串口按照自己之前查的选择就行了，波特率115200就可以了。

![](https://startzyp.github.io/imgs/log/2018-10-03/5.png)

设置完这些后就点击START开始烧flash，烧完后如果模块正常的话电脑会多出来一个叫HH的wifi，这个wifi就是esp8266发出来的。
如果没有显示HH，就按下esp8266的RST键复位，等个几秒钟就会显示出来。此时你就可以连接HH了。wifi的密码为：m1234567

# 3.用arduino上传web到esp8266

到arduino官网下载适合你自己系统的软件：https://www.arduino.cc/en/Main/Software

我的是Windows系统，arduino版本是1.8.4，安装完后打开工具——开发板——开发板管理器，此时会自动更新，过个数分钟更新完毕后（当然，如果用外网的话可能几秒钟就能解决），搜索eps8266，选择第二个，版本选2.2.0，然后安装。

![](https://startzyp.github.io/imgs/log/2018-10-03/6.png)

如果没有这个的话可以自己添加

文件 -->首选项-->附加开发板程序

然后添加这个 点确定等待更新就有了

http://arduino.esp8266.com/stable/package_esp8266com_index.json

将上面解压后的web源码上传工具的tools放到Arduino根目录里合并，然后返回以下界面，点击文件——新建，新建一个项目，将里面的代码清空，然后点击文件——保存，将项目保存到一个你能找到的位置，点击工具——esp8266 sketch data upload，会出现以下的提示，选择No，会发现新建的项目中多出来一个data文件夹，里面是空的，然后将上面下载的web源码\data里面的三个文件复制到这个文件夹里面。

![](https://startzyp.github.io/imgs/log/2018-10-03/7.png)

然后再返回arduino，点击工具，开发板按照自己买的选择，端口选择自己的端口，其他设置如下图红框里面的。

![](https://startzyp.github.io/imgs/log/2018-10-03/8.png)

设置完后点击esp8266 sketch data upload，这时不会出现提醒，开始上传web页面，等个1分钟左右esp8266上的蓝灯不闪烁了就表示上传完了。
然后电脑连接HH的wifi，浏览器输入192.168.1.1/backdoor.html就能进入web页面了，如下图，路由器型号选择通用型，然后输入你测试的wifi编号，点确定，电脑提示SSID伪造成功，手机就会发现出现了个和你测试的wifi一样的没有加密的wifi，原来的HH会不见了，8266的蓝灯常亮，手机连接那个wifi后过几秒会自动弹出路由器升级的页面，然后输入管理员密码，点击开始升级，此时你的esp8266会将管理员密码保存，升级完后，8266的灯就会灭掉。

切记用连接线一定要找一个好点点数据线。不然电压不稳，各种神奇错误

![](https://startzyp.github.io/imgs/log/2018-10-03/9.png)

电脑重新连接HH，进入web页面后管理员密码会在下面的红框这一块显示，这时，就表示获取密码成功了。

![](https://startzyp.github.io/imgs/log/2018-10-03/10.png)

最后放出固件和web上传工具+web源码的地址

https://startzyp.github.io/imgs/log/2018-10-03/esp8266.zip