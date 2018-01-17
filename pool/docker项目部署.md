一：安装docker
安装依赖包：
yum install -y yum-utils \
           device-mapper-persistent-data \
           lvm2

软件源

yum-config-manager \
     --add-repo \
     https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo

安装软件
yum makecache fast
yum install docker-ce

启动docker
systemctl enable docker
systemctl start docker

建立 docker 用户组

建立 docker 组：
<!-- groupadd docker -->

将当前用户加入 docker 组：
usermod -aG docker $USER

测试 Docker 是否安装正确
docker run hello-world

安装加速器
在 /etc/docker/daemon.json 中写入如下内容（如果文件不存在请新建该文件）
<!-- 
{
  "registry-mirrors": [
    "https://registry.docker-cn.com"
  ]
} -->

之后重新启动服务。
systemctl daemon-reload
systemctl restart docker

二：部署智能工厂
在docker-compose文件夹中执行docker-compose up -d   等待下载并自动安装重启，即可。
(需要手动将智能工厂数据库导入到数据库中，等待智能工厂重新启动)
现在涉及到智能工厂代码更新，目前是重新打包镜像docker build -t jiadongxu/umif:1.0.0，镜像名称和版本必须和执行文件对应即可

使用docker container ls -a 查看到对应的容器ID，使用docker container rm congtainerID

重新运行docker-compose up -d 