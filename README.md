# LiveDemo
Live直播

快速集成RTMP的视频推流

首先确保你的电脑是否安装了Homebrew

man brew

如果出现以下页面说明已经安装直接输入 Q 退出，然后执行第一步

![screenshots](https://github.com/zhuzhongshen/LiveDemo/blob/master/screenshots/screenshots01.png)

如果没有安装，则在终端输入以下命令安装

ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

如果安装了想卸载，则输入以下命令：

ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/uninstall)"

第一步 先clone nginx项目到本地

brew tap homebrew/nginx

第二步 安装

brew install nginx-full --with-rtmp-module

第三步,在终端输入

nginx

第四步，打开浏览器打开http://localhost:8080 如果出现以下所示，那么环境就搭建好了
![screenshots](https://github.com/zhuzhongshen/LiveDemo/blob/master/screenshots/screenshots02.png)

第五步,在终端输入

brew info nginx-full

第六步，在终端 Command+F 搜索nginx.conf

![screenshots](https://github.com/zhuzhongshen/LiveDemo/blob/master/screenshots/screenshots03.png)

第七步，进入该路径,以文本编辑形式打开配置文件，直接在最后面插入以下代码
rtmp {
      server { 
          listen 1935;
        application rtmplive { 
             live on; 
             record off;
             }
        } 
}  

![screenshots](https://github.com/zhuzhongshen/LiveDemo/blob/master/screenshots/screenshots04.jpeg)
![screenshots](https://github.com/zhuzhongshen/LiveDemo/blob/master/screenshots/screenshots05.jpeg)

第八步，查看nginx版本号，在终端输入:

nginx -v

![screenshots](https://github.com/zhuzhongshen/LiveDemo/blob/master/screenshots/screenshots06.jpeg)


第九步，重启ngix,把版本号替换成你电脑的nginx的版本号

/usr/local/Cellar/nginx-full/1.10.1/bin/nginx -s reload

接下来就可以试下直播的效果了**
下载VLC客户端
![screenshots](https://github.com/zhuzhongshen/LiveDemo/blob/master/screenshots/screenshots07.jpeg)
![screenshots](https://github.com/zhuzhongshen/LiveDemo/blob/master/screenshots/screenshots08.png)


将视频推流到服务器后，打开VLC，然后File->open network->输入：

rtmp://192.168.1.105:1935/rtmplive/room (192.168.1.105为本机IP地址)
![screenshots](https://github.com/zhuzhongshen/LiveDemo/blob/master/screenshots/screenshots09.png)
![screenshots](https://github.com/zhuzhongshen/LiveDemo/blob/master/screenshots/screenshots10.png)








