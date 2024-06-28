安装portainer使用如下命令：
```shell
docker run -d -p 9200:9000 \
--restart=always -v /var/run/docker.sock:/var/run/docker.sock \
--privileged=true portainer/portainer
```