docker build -t emm-mysql .

docker run -d -p 3306:3306 emm-mysql

docker logs 5713d96

终止状态的容器可以用 docker container ls -a 命令看到

docker stop container 

docker container rm 

docker images

docker image rm 


docker run --name umif --link mongodb:umif-mongo -d -p 1200:1200 umif

docker exec e791cd0d8e02 mysqldump --all-databases --password=root > mysql.backup

docker build -t jiadongxu/emm-mysql:1.0.0 .
docker push jiadongxu/emm-mysql:1.0.0


docker-compose up -d

清理所有停止的容器
docker container prune 


在使用数据卷容器时，必须使用-v标志移除容器。如果您不使用-v标志，则卷将作为悬挂卷结束并保留在本地磁盘中docker rm -v

要删除所有悬挂卷，请使用以下命令
docker volume rm `docker volume ls -q -f dangling=true`


mongodump -h 127.0.0.1:1206 --archive=dev.gz --gzip --db dev -u dev -p dev@123