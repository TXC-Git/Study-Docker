# 卸载版本
```shell
$ sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-selinux \
                  docker-engine-selinux \
                  docker-engine
```
# 使用yum安装docker
## 安装依赖
```shell
$ sudo yum install -y yum-utils
```
## 添加国内软件源
```shell
$ sudo yum-config-manager \
    --add-repo \
    https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo

$ sudo sed -i 's/download.docker.com/mirrors.aliyun.com\/docker-ce/g' /etc/yum.repos.d/docker-ce.repo

# 官方源
# $ sudo yum-config-manager \
#     --add-repo \
#     https://download.docker.com/linux/centos/docker-ce.repo
```
## 安装docker
```shell
$ sudo yum install docker-ce docker-ce-cli containerd.io
```

# 测试是否安装成功
```shell
docker run --rm hello-world
```

# 其他命令
启动 
```shell
systemctl start docker
```
守护进程重启 
```shell
sudo systemctl daemon-reload
```
重启docker服务
```shell
systemctl restart  docker
```
重启docker服务
```shell
sudo service docker restart
```
关闭docker
```shell
service docker stop
```

# 配置阿里云容器镜像加速
   
依次执行命令：
```shell
sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://qbd2mtyh.mirror.aliyuncs.com"]
}
EOF
sudo systemctl daemon-reload
sudo systemctl restart docker
```

方法二：

cp /etc/docker/daemon.json /etc/docker/daemon_cp.json 
vim /etc/docker/daemon.json
添加如下内容：
{
 "registry-mirrors": ["https://8auvmfwy.mirror.aliyuncs.com"]
}



