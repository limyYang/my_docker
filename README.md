# my_docker

+++ centos7（或者更高版本下）

## **docker安装**

`yum -y update` ：更新一波yum  <br/>

`yum install docker -y` ：yum下载安装docker <br/>

## **docker镜像操作**
`docker pull centos:7.6.1810`:下载centos镜像版本为7.6.7.1810（默认为最新的） <br/>

`docker images`: 查看docker中的所有镜像 <br/>

`docker rmi -f`: 强制删除镜像 <br/>

`docker search -s 10`: 查询star数目超过10的镜像 <br/>

## **docker容器操作（基础）**

`docker run -it --name centos_1 centos`: 创建容器并运行别名为centos_1（centos尽量用image id代替，-it 为进入容器内）<br/>


`docker ps`: 当前docker运行的容器 <br/>

`docker ps -n`: 当前docker前n个运行的容器 <br/>

`docker ps -l`: 当前docker上次运行的容器 <br/>

`docker start 546bjk33`: 启动容器546bjk33 <br/>

`docker restart 546bjk33`: 重新启动容器546bjk33 <br/>

`docker stop 546bjk33`: 停止容器546bjk33（温柔）<br/>

`docker kill 546bjk33`: 停止容器546bjk33（强制）<br/>

`docker rm 546bjk33`: 删除容器546bjk33<br/>

`docker rm -f $(docker ps -a -q)`: 停止容器546bjk33 （强制）<br/>

## **docker容器操作（重要）**

`docker top 546bjk33`: 容器546bjk33运行情况<br/>

`docker inspect 546bjk33`: 容器546bjk33内部细节<br/>

`docker attach 546bjk33`: 进入容器546bjk33<br/>

`docker exec -it 546bjk33 /bin/bash`: 通过命令进入容器546bjk33（在docker中执行容器里的命令）<br/>

`docker ps 546bjk33:/tmp/yum.log /root`: 将容器546bjk33 tmp下的yum.log文件复制到宿主机 /root 路径下<br/>

`docker run -it -p 8888:8080 tomcat`: 创建并启动容器tomcat，映射端口为8888（前端方式启动）<br/>
										这里注意，由于在阿里云上pull的最新版的tomcat的webapps文件夹为空，启动页在webapp.disk里面
										需要进入tomcat中修改文件名字即可，`mv webapps webapps1` `mv webapps.dist webapps`

`docker run -d -p 8888:8080 tomcat`: 创建并启动容器tomcat，映射端口为8888（守护方式启动）<br/>

## **docker进入容器内操作**

`exit`: 退出并停止容器 <br/>

`ctrl+p+q`: 退出容器 <br/>

## **commit**

`docker commit -m="oktomcat_limy" -a="limy" 546bjk33 limy/oktomcat:1.2`: 提交容器546bjk33为limy/oktomcat版本为1.2 <br/>








