```shell

# 1、搜索镜像
[root@kuangshen ~]# docker search mysql
NAME DESCRIPTION
STARS
mysql MySQL is a widely used, open-source
relation… 9488
# 2、拉取镜像
[root@kuangshen ~]# docker pull mysql:5.7
5.7: Pulling from library/mysql
54fec2fa59d0: Already exists
bcc6c6145912: Pull complete
951c3d959c9d: Pull complete
05de4d0e206e: Pull complete
319f0394ef42: Pull complete
d9185034607b: Pull complete
013a9c64dadc: Pull complete
e745b3361626: Pull complete
03145d87b451: Pull complete
3991a6b182ee: Pull complete
62335de06f7d: Pull complete

通过Docker File 来添加（了解）
DockerFile 是用来构建Docker镜像的构建文件，是由一些列命令和参数构成的脚本。
我们在这里，先体验下，后面我们会详细讲解 DockerFile ！
测试：
Digest:
sha256:e821ca8cc7a44d354486f30c6a193ec6b70a4eed8c8362aeede4e9b8d74b8ebb
Status: Downloaded newer image for mysql:5.7
docker.io/library/mysql:5.7

# 3、启动容器 -e 环境变量！
# 注意： mysql的数据应该不丢失！先体验下 -v 挂载卷！ 参考官方文档
[root@kuangshen home]# docker run -d -p 3310:3306 -v
/home/mysql/conf:/etc/mysql/conf.d -v /home/mysql/data:/var/lib/mysql -e
MYSQL_ROOT_PASSWORD=123456 --name mysql01 mysql:5.7
4763fa5c68c4323688102f57938fb10996a0fb902d2812349286529f9378f16c
# 4、使用本地的sqlyog连接测试一下 3310
# 5、查看本地的 /home/mysql 目录
[root@kuangshen data]# pwd
/home/mysql/data
[root@kuangshen data]# ls
.. ... . test # 可以看到我们刚刚建立的mysql数据库在本地存储着
# 6、删除mysql容器
[root@kuangshen data]# docker rm -f mysql01 # 删除容器，然后发现远程连接失败！
mysql01
[root@kuangshen data]# ls
.. ... . test # 可以看到我们刚刚建立的mysql数据库在本地存储着

```