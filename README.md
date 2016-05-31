## cedardar.github.io
This is my personal blog involved my research. In this blog, I will share some code or experience about cancer genomics research.

##The SCI-HUB domain now can access in.
http://sci-hub.cc/

http://sci-hub.bz/

http://sci-hub.ac/

##ubuntu 16.04安装有道词典
重新安装ubuntu 16.04后，发现没法安装有道词典1.1.0版本了。利用sudo gdebi youdao-dict_1.1.0-0-ubuntu_amd64.deb
提示gstreamer0.10-plugins-ugly错误，所以就想办法解决该问题。
###首先新建几个文件夹：
```
mkdir extract
mkdir extract/DEBIAN
mkdir build
```
###然后解压deb包
```
dpkg -X youdao-dict_1.1.0-0-ubuntu_amd64.deb extract/
dpkg -e youdao-dict_1.1.0-0-ubuntu_amd64.deb extract/DEBIAN/
```
###修改control文件，在extract/DEBIAN文件夹中
将Depends部分中的gstreamer0.10-plugins-ugly更改为gstreamer1.0-plugins-ugly
###重新打包为deb包
```
dpkg-deb -b extract/ build/
```
新生成的deb包在build文件夹中
###安装即可
```
sudo gdebi youdao-dict_1.1.0-0~ubuntu_amd64.deb
```

初步使用没有发现大问题，取词正常。
已打包的文件可以[直接下载](https://github.com/cedarice/cedarice.github.io/raw/0ff972fb82e6bd996becab7d356100361884a21d/youdao-dict_1.1.0-0%7Eubuntu_amd64.deb)
