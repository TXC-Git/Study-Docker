```shell
#ElasticSearch + kibana
#存在的问题
	#ES暴露的端口很多
	#ES十分消耗内存
	#ES的数据一般需要放置到安全目录 需要挂载？
	# --net somenetwork ? 网络配置
#启动ElasticSearch
docker run -d --name ElasticSearch  -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:tag

#启动Es，整个Linux就卡住了  使用docker stats 查看内存占用情况

#Es是十分耗内存的

#使用docker stats查看资源占用情况

#查看es是否启动成功


```

