##  centos7 安装mysql
### 一、mysql安装
1.  下载到本地再上传到服务器或者使用wget直接下载    
    wget http://repo.mysql.com/mysql57-community-release-el7-10.noarch.rpm
2.  命令安转软件源  
    sudo rpm -Uvh xxxxx.rpm
3.  安装软件  
    yum install -y mysql-community-server
4.  启动mysql  
    service mysqld start或者systemctl start mysqld.service
5.  检查mysql 的运行状态  
    service mysqld status或者systemctl status mysqld.service

### 二、环境配置

1.  获取root用户临时密码  
    grep 'temporary password' /var/log/mysqld.log
2.  临时密码登录  
    mysql -uroot -p
3.  更新root密码  
    use mysql;  
    update user set authentication_string=password('123456') where user='root;
4. 如果提示ERROR 1819 (HY000): Your password does not satisfy the current policy requirements，需要执行以下命令  
    -   安全策略:set global validate_password_policy=0;
    -   密码长度:set global validate_password_length=1;
    -   更新密码:update user set authentication_string=password('123456') where user='root;
    -   刷新系统相关权限表:flush privileges;
5.  授权其他电脑远程连接  
    GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '123456' WITH GRANT OPTION;  
    FLUSH PRIVILEGES;
6.  my.conf配置(主要是EMM配置)
```
    sql_mode = "STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"
    skip-external-locking
    lower_case_table_names=1
    sort_buffer_size = 2M
    max_allowed_packet = 100M
    innodb_log_file_size = 1024M
    character_set_server=utf8
    key_buffer_size         = 16M
    max_allowed_packet      = 16M
    thread_stack            = 192K
    thread_cache_size       = 8
    expire_logs_days        = 10
    max_binlog_size   = 100M
    expire_logs_days        = 10
    max_binlog_size   = 100M
    query_cache_limit       = 1M
    query_cache_size        = 16M
    general_log=1
    general_log_file=/var/lib/mysql/mysql/general_log.csv
    myisam-recover-options  = BACKUP
```
