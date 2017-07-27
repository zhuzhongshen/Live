# LiveDemo
Live直播

快速集成RTMP的视频推流

首先确保你的电脑是否安装了Homebrew


<font color=#800000>man brew</font>

如果出现以下页面说明已经安装直接输入 Q 退出，然后执行第一步

![screenshots](https://github.com/zhuzhongshen/LiveDemo/blob/master/screenshots/screenshots01.png)

如果没有安装，则在终端输入以下命令安装

<font color=#800000>ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"</font>

如果安装了想卸载，则输入以下命令：

<font color=#800000>ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/uninstall)"</font>

第一步 先clone nginx项目到本地

<font color=#800000>brew tap homebrew/nginx</font>

第二步 安装

<font color=#800000>brew install nginx-full --with-rtmp-module</font>

第三步,在终端输入

<font color=#800000>nginx</font>

第四步，打开浏览器打开http://localhost:8080 如果出现以下所示，那么环境就搭建好了
![screenshots](https://github.com/zhuzhongshen/LiveDemo/blob/master/screenshots/screenshots02.png)

第五步,在终端输入

<font color=#800000>brew info nginx-full</font>

第六步，在终端 Command+F 搜索nginx.conf

![screenshots](https://github.com/zhuzhongshen/LiveDemo/blob/master/screenshots/screenshots03.png)

第七步，进入该路径,以文本编辑形式打开配置文件，直接在最后面插入以下代码
<font color=#800000>
rtmp {
      server { 
          listen 1935;
        application rtmplive { 
             live on; 
             record off;
             }
        } 
} 
</font>
 

![screenshots](https://github.com/zhuzhongshen/LiveDemo/blob/master/screenshots/screenshots04.jpeg)
![screenshots](https://github.com/zhuzhongshen/LiveDemo/blob/master/screenshots/screenshots05.jpeg)

第八步，查看nginx版本号，在终端输入:

<font color=#800000>nginx -v</font>

![screenshots](https://github.com/zhuzhongshen/LiveDemo/blob/master/screenshots/screenshots06.jpeg)


第九步，重启ngix,把版本号替换成你电脑的nginx的版本号

<font color=#800000>/usr/local/Cellar/nginx-full/1.10.1/bin/nginx -s reload</font>

接下来就可以试下直播的效果了**
下载VLC客户端
![screenshots](https://github.com/zhuzhongshen/LiveDemo/blob/master/screenshots/screenshots07.jpeg)
![screenshots](https://github.com/zhuzhongshen/LiveDemo/blob/master/screenshots/screenshots08.png)


将视频推流到服务器后，打开VLC，然后File->open network->输入：

<font color=#800000>rtmp://192.168.1.105:1935/rtmplive/room (192.168.1.105为本机IP地址)</font>

![screenshots](https://github.com/zhuzhongshen/LiveDemo/blob/master/screenshots/screenshots09.png)
![screenshots](https://github.com/zhuzhongshen/LiveDemo/blob/master/screenshots/screenshots10.png)



