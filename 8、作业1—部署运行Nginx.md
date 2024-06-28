```shell
#1、搜索镜像 search
#2、下载镜像 pull
#3、运行测试 images
[root@lavm-lboagvwm5z ~]# docker images
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
nginx        latest    605c77e624dd   2 years ago   141MB
centos       latest    5d0da3dc9764   2 years ago   231MB
[root@lavm-lboagvwm5z ~]# docker run -d --name nginx02 -p 443:80 nginx
bfd17651701aff60e7a8edd7e464ddb541a9c8dd721a5397bda63c3378924c98
[root@lavm-lboagvwm5z ~]# docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS                                 NAMES
bfd17651701a   nginx     "/docker-entrypoint.…"   5 seconds ago   Up 4 seconds   0.0.0.0:443->80/tcp, :::443->80/tcp   nginx02

[root@lavm-lboagvwm5z ~]# curl localhost:443
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>

```

