```shell
#1、下载镜像 pull
[root@lavm-lboagvwm5z ~]# docker pull tomcat
Using default tag: latest
latest: Pulling from library/tomcat
0e29546d541c: Pull complete 
9b829c73b52b: Pull complete 
cb5b7ae36172: Pull complete 
6494e4811622: Pull complete 

[root@lavm-lboagvwm5z ~]# docker images
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
nginx        latest    605c77e624dd   2 years ago   141MB
tomcat       latest    fb5657adc892   2 years ago   680MB
centos       latest    5d0da3dc9764   2 years ago   231MB

#2、运行
[root@lavm-lboagvwm5z ~]# docker run -d --name tomcatjdc -p 443:8080 tomcat
5c53f8bb0b1ab590cb419a864a8b03142a0eddd6277d8f2cb6c4c9124b665849
[root@lavm-lboagvwm5z ~]# docker ps
CONTAINER ID   IMAGE     COMMAND             CREATED         STATUS         PORTS                                     NAMES
5c53f8bb0b1a   tomcat    "catalina.sh run"   4 seconds ago   Up 3 seconds   0.0.0.0:443->8080/tcp, :::443->8080/tcp   tomcatjdc

#问题：此时访问http://116.198.232.132:443/访问，显示404，这是因为阿里云的docker镜像默认最小安装，网页文件未保存在webapps中，但在webapps.dist中

#3、将webapps.dist中的文件拷贝到webapps中，刷新页面，即可访问成功
[root@lavm-lboagvwm5z ~]# docker exec -it 5c53f8bb0b1a /bin/bash
root@5c53f8bb0b1a:/usr/local/tomcat# ls
BUILDING.txt	 LICENSE  README.md	 RUNNING.txt  conf  logs	    temp     webapps.dist
CONTRIBUTING.md  NOTICE   RELEASE-NOTES  bin	      lib   native-jni-lib  webapps  work
root@5c53f8bb0b1a:/usr/local/tomcat# cd webapps
root@5c53f8bb0b1a:/usr/local/tomcat/webapps# ls
root@5c53f8bb0b1a:/usr/local/tomcat/webapps# cd ..
root@5c53f8bb0b1a:/usr/local/tomcat# cd webapps.dist
root@5c53f8bb0b1a:/usr/local/tomcat/webapps.dist# ls
ROOT  docs  examples  host-manager  manager
root@5c53f8bb0b1a:/usr/local/tomcat/webapps.dist# cd ..
root@5c53f8bb0b1a:/usr/local/tomcat# cp -rf webapps.dist/* webapps/
root@5c53f8bb0b1a:/usr/local/tomcat# ls
BUILDING.txt	 LICENSE  README.md	 RUNNING.txt  conf  logs	    temp     webapps.dist
CONTRIBUTING.md  NOTICE   RELEASE-NOTES  bin	      lib   native-jni-lib  webapps  work

```

