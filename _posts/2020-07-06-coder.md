---
title: Coder
date: 2020-07-06 00:00:00
categories:
- dev/Other
tags:
---

“相信在不久的将来，人工智能将在很大程度上代替程序员的编码工作，程序员无需亲自实现每一个细节，只需要告诉机器人想要实现怎样的功能。这将使得程序变得更为复杂，几乎没人能够做到对一个系统的代码有全面的掌握。程序可以通过自然语言进行编写，每个人都可以开发属于自己的程序，就像写文章一样容易。”


AppStore搜索应用：
http://itunes.apple.com/search?entity=software&term=你的应用程序名称

AppStore获取应用的信息： 
http://itunes.apple.com/lookup?id=你的应用程序的ID

没有符号表文件也能定位崩溃位置：
https://www.cnblogs.com/ciml/p/7422872.html

一种检测JB和获取识别码的方式：
https://iosre.com/uploads/default/original/2X/4/43fb84226f3140bc755001c1cb061aac5f629653.png
#include <sys/mount.h>
struct statfs buf;
statfs("/", &buf);
NSLog(@"%s", buf.f_mntfromname);
char* prefix = "com.apple.os.update-";
if(strstr(buf.f_mntfromname, prefix)) {
    NSLog(@"未JB, 识别码=%s", buf.f_mntfromname+strlen(prefix));
}
else {
    NSLog(@"JB");
}

如何防止statfs被hook：
statfs是一个bsd内核调用, 直接使用svc 80指令

如何防止svc指令被hook：
随机寻找系统模块中的一个svc指令, 然后BL跳转过去执行
