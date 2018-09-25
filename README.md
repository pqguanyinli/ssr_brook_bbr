## 5kong搭建SSR\BBR代码：

第一步 :```sudo su```

第二步 : ```wget --no-check-certificate https://raw.githubusercontent.com/pqguanyinli/ssr_brook_bbr/master/run.sh && chmod +x run.sh && ./run.sh```

## BIGDONGDONG 搭建谷歌SSR和BBR的方法：（参考）

谷歌VM实例系统里面 没有Debian8了

所以大家改用CentOS6 （就没蓝底那个窗口了）

也可以使用debian9(推荐）
使用debian9 可以只用从第5步开始（当然sudo -i 这一步还是要的）只需2步就可以搭建好。不用装BBR加速器 速度也非常的快 直接破百兆！

1：``` sudo -i ```

(最前面显示root@xxxx)

2：``` wget -N --no-check-certificate https://raw.githubusercontent.com/FunctionClub/YankeeBBR/master/bbr.sh && bash bbr.sh install  ```
 
蓝底窗口按TAB键选NO

选择重启 Y

这里会断开连接，大家可以关掉窗口再重新打开或几秒钟后在界面随便按几个字母 便会提示重新连接。

3：``` sudo -i ```

(最前面显示root@xxxx)

4：``` bash bbr.sh start ```

5：``` wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocksR.sh && chmod +x shadowsocksR.sh  ```

6：``` ./shadowsocksR.sh  ```

输入shadowsocks 密码

输入端口号

其他一路回车（也可自行选择混淆 协议）

在最后出现红底数据以后

谷歌云防火墙规则添加 （位置在谷歌云 VPC网络-防火墙）
点击添加新规则，然后按照一下这个设置好。这样 SSR 设置任何端口都可以使用。并且后续不需要再来防火墙规则做设置了。

![image](https://github.com/pqguanyinli/ssr_brook_bbr/blob/master/images/1.png)


## BIGDONGDONG BROOK 的搭建方法：（参考）

原创技术小哥的网站更多详细设置参见原贴：https://doub.io/brook-jc3/

此方式优点： 属于小众代理，被XX的概率较低，速度和SSR 不相伯仲

缺点：客户端配置不如SSR客户端丰富 比如规则之类的 设置相对麻烦或者要下对应客户端而且并不是全平台。还有就是更正一下视频里说的不支持路由器目前已知支持 软路由系统openwrt,但梅林貌似还没有。如果有我会在这里通知大家。

以下是以谷歌云为例子！！

## Part1首先搭建BBR加速

1：``` sudo -i ```

(最前面显示root@xxxx)

BBR加速 有两套代码，选其一

2（第一套）：``` wget -N --no-check-certificate https://raw.githubusercontent.com/FunctionClub/YankeeBBR/master/bbr.sh && bash bbr.sh install  ```

蓝底窗口按TAB键选NO

选择重启 Y

这里会断开连接，大家可以关掉窗口再重新打开。

3：```sudo -i ```

(最前面显示root@xxxx)

4：``` bash bbr.sh start  ```

## Part2 搭建brook服务端

如果这一步之前有选Y重启的话 需要 先输入 ``` sudo -i ```

5：``` wget -N --no-check-certificate https://softs.fun/Bash/brook.sh && chmod +x brook.sh && bash brook.sh ```

如果失效用这个

``` wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/brook.sh && chmod +x brook.sh && bash brook.sh ```

6：运行脚本后会出现脚本操作菜单，选择并输入 1 就会开始安装

7：输入端口 [1-65535]

(默认: 2333):

大家可以自行输入自己的端口（防火墙开通的）

8：请输入 Brook 密码

(默认: doub.io):

9：选择 Brook

Brook（新版协议，即 [servers]）

Brook Stream（旧版协议，即 [streamservers]，不推荐，除非使用新版协议速度慢）

(默认: 1. Brook（新版协议）):1

协议 : servers 

[信息] Brook 停止成功 !

[信息] Brook 启动中...

[信息] Brook 启动成功 !

9： Brook 用户配置复制或截图
![image](https://github.com/pqguanyinli/ssr_brook_bbr/blob/master/images/2.jpg)


10：如何在手机、电脑（PC/MAC)上使用请参照视频

brook 客户端下载地址:https://github.com/txthinking/brook/releases

谷歌云防火墙规则 （说白了就是创建完实例以后需要再去防火墙那个地方打开相应的端口才可以使用实例）

谷歌云防火墙规则添加 （位置在谷歌云 VPC网络-防火墙）

点击添加新规则，然后按照一下这个设置好。这样 SSR 设置任何端口都可以使用。并且后续不需要再来防火墙规则做设置了。缺点是 所有端口开放。当然也会有一些危险。

![image](https://github.com/pqguanyinli/ssr_brook_bbr/blob/master/images/3.png)


## 在梅林固件路由器下利用ssh 连接路由器离线安装shadowsocks科学上网插件

步骤概括只有三步：

第一步：把插件包shadowsocks.tar.gz拷贝到路由器

第二步：在路由器里解压插件包

第三步：修改执行权限并安装插件

准备工作

1、下载putty，这是一个ssh连接工具

2、下载winscp，用于拷贝离线插件包到路由器

3、在梅林系统里开启ssh选项。

具体步骤：

一、在梅林系统里开启ssh

二、打开winscp，登陆路由器，将shadowsocks.tar.gz拷贝到某个路径

三、打开putty 连接到ssh到路由器，定位到shadowsocks.tar.gz所在路径

执行下面的代码：

//解压插件
```tar -zxvf shadowsocks.tar.gz```

//修改插件的执行权限，使其可执行
```chmod +x shadowsocks/install.sh```

//执行安装程序
```sh shadowsocks/install.sh```

## 在梅林固件路由器下安装V2Ray插件

准备工具：putty (win10)  terminal (mac 自带)

操作步骤：

1、ssh到路由器 
 
2、分别执行以下4条脚本 
```
wget --no-check-certificate https://raw.githubusercontent.com/ssr_brook_bbr/master/v2ray.tar.gz
tar -zxvf  v2ray.tar.gz
chmod +x v2ray/install.sh
sh v2ray/install.sh
```   
另外，还可以将文件压缩包v2ray.tar.gz下载后通过路由器的网页端上传进行离线安装。
