##  centos7 安装nginx
### 一、nginx安装
1.  添加 Nginx 的下载源到 yum    
    sudo rpm -Uvh http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm
2.  yum 命令来安装 Nginx  
    sudo yum install -y nginx
3.  启动nginx  
    sudo systemctl start nginx.service
4.  nginx自启动  
    sudo systemctl enable nginx
5.  开启 Nginx  
    service nginx start
6.  停止 Nginx  
    service nginx stop
7.  重启 Nginx  
    service nginx restart
8.  查看 Nginx 状态  
    service nginx status

### 二、环境配置
