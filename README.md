# Synergy-Support
记录Synergy的使用和对源码的理解
csdn链接：https://blog.csdn.net/yudelian/article/details/116461854
Synergy源码：https://github.com/symless/synergy-core


背景：如果需要同时操作多个电脑，每个电脑配置个手机太麻烦，如果不同的电脑共享一套鼠标和键盘就太爽了。

现在介绍下Ubuntu和windows共享鼠标键盘

工具下载链接：链接：https://pan.baidu.com/s/1XO0Y00o6MdOmM357_unDvg    提取码：cev1 

 

Ubuntu安装Synergy:
1、安装Synergy

先用alien把rpm包（synergy-1.5.0-r2278-Linux-x86_64_566018.rpm）转换为deb包

sudo dpkg -i synergy_1.5.0-2_amd64.deb

2、有可能会提示少canberra-gtk-module，则安装

sudo apt-get install libcanberra-gtk-module

3、如果弹窗提示少qt什么的，然后重启

sudo apt-get install sni-qt

Windows端安装Synergy，直接安装exe包就行
 

源码编译学习：https://segmentfault.com/a/1190000023512582

开源地址：https://github.com/symless/synergy-core

 

用法：

我这边Ubuntu作为server，windows作为client，因为发现Ubuntu作为client时，锁屏登录有问题

问题：

1、server向client屏幕移动时，看不到鼠标，但是键盘有反应

解决：这是因为两个设备的分辨率和缩放比例不一样导致的，设置完全一样时便可以正常工作。我的设备分辨率是1920*1080，缩放为100%

 由于我自己的Ubuntu是18.04,无法设置125%的缩放，比较头疼，缩放设置为100%时，windows的体验并不是很好

期待后面能找到Ubuntu18.04设置125%缩放的方法

Ubuntu18.04修改DPi字体缩放比例为125%：https://blog.csdn.net/qq_34626094/article/details/113112668

 

2、可以设置热键，切换屏幕、锁定在某个屏幕等，后续再探索

 

3、现在发现一个问题，server的剪切板里的文字、图片截图可以在client端用，但是client端的剪切板不能再server端用，这个后续关注一下。

现在发现一个方法：

就是ubuntu和windows都是分辨率1920*1080，缩放都是100%，这样windows的字体会整体比较小，费眼睛，怎么只让应用的字体变大而缩放不便呢？

解决：我在windows上找到了此方法：只放大文字与应用和文字同时放大（参考：https://zhuanlan.zhihu.com/p/148767985）

打开系统设置-->轻松使用-->显示（不同于系统设置里的显示）



放大文本”只是把系统里的文字放大，其它的如窗口，图标都不变化。

“让内容更醒目”则不同，它会同时放大窗口、图标和文字。

这样感觉完美