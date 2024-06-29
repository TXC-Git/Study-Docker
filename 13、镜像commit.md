**docker commit 从容器创建一个新的镜像。**

```shell
docker commit 提交容器副本使之成为一个新的镜像！
# 语法
docker commit -m="提交的描述信息" -a="作者" 容器id 要创建的目标镜像名:[标签名]
```
**测试**
```shell
# 1、从Docker Hub 下载tomcat镜像到本地并运行 -it 交互终端 -p 端口映射
docker run -it -p 8080:8080 tomcat
# 注意：坑爹：docker启动官方tomcat镜像的容器，发现404是因为使用了加速器，而加速器里的
tomcat的webapps下没有root等文件！
# 下载tomcat官方镜像，就是这个镜像（阿里云里的tomcat的webapps下没有任何文件）
# 进入tomcat查看cd到webapps下发现全部空的，反而有个webapps.dist里有对应文件，cp -r
到webapps下！
root@aba865b53114:/usr/local/tomcat# cp -r webapps.dist/* webapps
# 2、删除上一步镜像产生的tomcat容器的文档
docker ps # 查看容器id
docker exec -it 容器id /bin/bash
/usr/local/tomcat # ce webapps/
/usr/local/tomcat/webapps # ls -l # 查看是否存在 docs文件夹
/usr/local/tomcat/webapps # curl localhost:8080/docs/ # 可以看到 docs 返回的
内容
/usr/local/tomcat/webapps # rm -rf docs # 删除它
/usr/local/tomcat/webapps # curl localhost:8080/docs/ # 再次访问返回404
# 3、当前运行的tomcat实例就是一个没有docs的容器，我们使用它为模板commit一个没有docs的
tomcat新镜像， tomcat02
docker ps -l # 查看容器的id
# 注意：commit的时候，容器的名字不能有大写，否则报错：invalid reference format
docker commit -a="kuangshen" -m="no tomcat docs" 1e98a2f815b0 tomcat02:1.1
sha256:cdccd4674f93ad34bf73d9db577a20f027a6d03fd1944dc0e628ee4bf17ec748
[root@kuangshen /]# docker images # 查看，我们自己提交的镜像已经OK了！
REPOSITORY TAG IMAGE ID CREATED
SIZE
tomcat02 1.1 cdccd4674f93 About a minute
ago 649MB
redis latest f9b990972689 9 days ago
104MB
tomcat latest 927899a31456 2 weeks ago
647MB
centos latest 470671670cac 3 months ago
237MB
# 4、这个时候，我们的镜像都是可以使用的，大家可以启动原来的tomcat，和我们新的tomcat02来
测试看看！
[root@kuangshen ~]# docker run -it -p 8080:8080 tomcat02:1.1
# 如果你想要保存你当前的状态，可以通过commit，来提交镜像，方便使用，类似于 VM 中的快照！
```