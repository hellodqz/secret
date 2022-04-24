### 卷操作
```
docker volume create vol1 # 创建一个卷,如卷名为vol1 
docker volume ls # 查看所有的卷 
docker volume inspect vol1 # 查看指定卷的信息，如卷vol1
# 启动一个挂载卷的容器，如将卷名为"vol1"挂载到容器的/home/fengbingchun目录;新建的容器名为"yyyy"; -P,随机端口映射，容器内部端口随机映射到主机的端口
docker run -it -P --name yyyy --mount source=vol1,target=/home/fengbingchun fengbingchun/ubuntu:16.04 /bin/bash
docker inspect yyyy # 查看容器中卷的具体信息，卷的信息在"Mounts"字段内，"yyyy"为容器名
docker volume rm vol1 # 删除卷，如卷名为"vol1"，需要卷"vol1"没有被任何容器使用时才能删除
docker volume prune # 删除所有没有被使用的卷
```
### 挂载主机目操作
```
# 挂载一个本地主机的目录到容器中去,新建的容器名为"test"; -P,随机端口映射，容器内部端口随机映射到主机的端口;
# "/home/GitHub"为本地主机目录，本地目录的路径必须是绝对路径；"/home/fengbingchun"为挂载到容器此目录；Docker挂载主机目录的默认权限是读写
docker run -it -P --name test --mount type=bind,source=/home/GitHub,target=/home/fengbingchun fengbingchun/ubuntu:16.04 /bin/bash # linux
docker run -it -P --name test --mount type=bind,source=e:\GitCode,target=/home/fengbingchun fengbingchun/ubuntu:16.04 /bin/bash # windows
docker inspect yyyy # 查看容器中挂载主机目录的具体信息，挂载主机目录的配置信息在"Mounts"字段内，"yyyy"为容器名
```
### docker常用命令
1. docker ps查看是否安装成功
2. docker run --name mysql5.6 -p 3306:3306 -v D:/workspace/database/mysql/mysql5.6:/var/lib/mysql -v D:/workspace/database/mysql/mysql5.6/conf:/etc/mysql/conf.d -v D:/workspace/database/mysql/mysql5.6/logs:/var/log/mysql -e MYSQL_ROOT_PASSWORD=swarm -d mysql:5.6
