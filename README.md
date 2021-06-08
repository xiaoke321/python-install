# python-install
python无网络源码编译 安装ssl 等问题报错  

# 第一步， python官网下载源代码并解压  
进入解压目录：  
./configure --prefix=/opt/sunke/python378 --with-openssl=/usr/local/ssl  
make -j8  
make install



# 第二部，安装libressl替换openssl  
官网下载liressl源码并解压：http://www.libressl.org/ （尽量下载3版本以上）  
进入解压目录：    
./configure --prefix=/usr/local/ssl  
make -j8  
make install  

修改lib库文件使libressl安装目录下的lib文件全局有效  
vim  /etc/ld.so.conf.d/local.conf  写入 /usr/local/ssl/lib  
使环境生效：ldconfig -v  

替换 之前的openssl 软链接（记得备份）:  
mv /usr/bin/openssl /usr/bin/openssl.bak  
ln -s /usr/local/ssl/bin/openssl /usr/bin/openssl


