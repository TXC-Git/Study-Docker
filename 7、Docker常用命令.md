![在这里插入图片描述](https://img-blog.csdnimg.cn/c687be8724c74e238c21d6e27f46f8d6.png "在这里插入图片描述")

| 命令        | 作用                                                                                                             |
| --------- | -------------------------------------------------------------------------------------------------------------- |
| attach    | 绑定到运行中容器的标准输入, 输出,以及错误流（这样似乎也能进入容器内容，但是一定小心，他们操作的就是控制台，控制台的退出命令会生效，比如redis,nginx…                              |
| build     | 从一个 Dockerfile 文件构建镜像                                                                                          |
| commit    | 把容器的改变提交创建一个新的镜像                                                                                               |
| cp        | 容器和本地文件系统间复制文件/文件夹                                                                                             |
| create    | 创建新容器，但并不启动（注意与docker run 的区分）需要手动启动。start\stop                                                                |
| diff      | 检查容器里文件系统结构的更改【A：添加文件或目录 D：文件或者目录删除 C：文件或者目录更改】                                                                |
| events    | 获取服务器的实时事件                                                                                                     |
| exec      | 在运行时的容器内运行命令                                                                                                   |
| export    | 导出容器的文件系统为一个tar文件。commit是直接提交成镜像，export是导出成文件方便传输                                                              |
| history   | 显示镜像的历史                                                                                                        |
| images    | 列出所有镜像                                                                                                         |
| import    | 导入tar的内容创建一个镜像，再导入进来的镜像直接启动不了容器。/docker-entrypoint.sh nginx -g 'daemon of;'docker ps --no-trunc 看下之前的完整启动命令再用他 |
| info      | 显示系统信息                                                                                                         |
| inspect   | 获取docker对象的底层信息                                                                                                |
| kill      | 杀死一个或者多个容器                                                                                                     |
| load      | 从 tar 文件加载镜像                                                                                                   |
| login     | 登录Docker registry                                                                                              |
| logout    | 退出Docker registry                                                                                              |
| logs      | 获取容器日志；容器以前在前台控制台能输出的所有内容，都可以看到                                                                                |
| pause     | 暂停一个或者多个容器                                                                                                     |
| port      | 列出容器的端口映射                                                                                                      |
| ps        | 列出所有容器                                                                                                         |
| pull      | 从registry下载一个image 或者repository                                                                                |
| push      | 给registry推送一个image或者repository                                                                                 |
| rename    | 重命名一个容器                                                                                                        |
| restart   | 重启一个或者多个容器                                                                                                     |
| rm        | 移除一个或者多个容器                                                                                                     |
| rmi       | 移除一个或者多个镜像                                                                                                     |
| run       | 创建并启动容器                                                                                                        |
| save      | 把一个或者多个镜像保存为tar文件                                                                                              |
| search    | 去docker hub寻找镜像                                                                                                |
| start     | 启动一个或者多个容器                                                                                                     |
| stats     | 显示容器资源的实时使用状态                                                                                                  |
| stop      | 停止一个或者多个容器                                                                                                     |
| tag       | 给源镜像创建一个新的标签，变成新的镜像                                                                                            |
| top       | 显示正在运行容器的进程                                                                                                    |
| unpause   | pause的反操作                                                                                                      |
| update    | 更新一个或者多个docker容器配置                                                                                             |
| version   | 展示docker版本信息                                                                                                   |
| container | 管理容器                                                                                                           |
| image     | 管理镜像                                                                                                           |
| network   | 管理网络                                                                                                           |
| volume    | 管理卷                                                                                                            |

