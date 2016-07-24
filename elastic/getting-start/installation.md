# 安装

Elasticsearch至少需要Java 7，在这里建议您使用Oracle JDK版本1.8.0_73。Java的安装因平台而异，所以在这里我们不会去讨论这些细节。Oracle的安装文档上可以在Oracle的网站找到。我只想说，在安装Elasticsearch之前，请通过运行先检查你的Java版本(然后安装，如果需要相应地升级的话):

> `java -version`
> `echo $JAVA_HOME`

一旦我们安装了Java，我们就可以下载并运行Elasticsearch。安装文件可从www.elastic.co/downloads上下载，并且网站也提供过去所有版本的下载。对于每一个版本，你可以选择ZIP或tar 文件，或DEB或RPM软件包进行下载。为简单起见，我们使用tar文件。

让我们像下边这样下载Elasticsearch 5.0.0-alpha4 tar(Windows用户应该下载zip包)

> `curl -L -O https://download.elastic.co/elasticsearch/release/org/elasticsearch/distribution/tar/elasticsearch/5.0.0-alpha4/elasticsearch-5.0.0-alpha4.tar.gz`

然后使用下面的命令解压缩:
> `tar -xvf elasticsearch-5.0.0-alpha4.tar.gz`

然后，它会在你的当前目录中创建一批文件和文件夹。然后，我们进入bin目录，如下所示：
> `cd elasticsearch-5.0.0-alpha4/bin`

现在我们准备开始我们的节点，单个集群(Windows用户应该运行elasticsearch.bat文件):
> `./elasticsearch`

如果一切顺利，你应该看到一堆看起来像下面的消息:
```shell
./elasticsearch
[2014-03-13 13:42:17,218][INFO ][node           ] [New Goblin] version[5.0.0-alpha4], pid[2085], build[5c03844/2014-02-25T15:52:53Z]
[2014-03-13 13:42:17,219][INFO ][node           ] [New Goblin] initializing ...
[2014-03-13 13:42:17,223][INFO ][plugins        ] [New Goblin] loaded [], sites []
[2014-03-13 13:42:19,831][INFO ][node           ] [New Goblin] initialized
[2014-03-13 13:42:19,832][INFO ][node           ] [New Goblin] starting ...
[2014-03-13 13:42:19,958][INFO ][transport      ] [New Goblin] bound_address {inet[/0:0:0:0:0:0:0:0:9300]}, publish_address {inet[/192.168.8.112:9300]}
[2014-03-13 13:42:23,030][INFO ][cluster.service] [New Goblin] new_master [New Goblin][rWMtGj3dQouz2r6ZFL9v4g][mwubuntu1][inet[/192.168.8.112:9300]], reason: zen-disco-join (elected_as_master)
[2014-03-13 13:42:23,100][INFO ][discovery      ] [New Goblin] elasticsearch/rWMtGj3dQouz2r6ZFL9v4g
[2014-03-13 13:42:23,125][INFO ][http           ] [New Goblin] bound_address {inet[/0:0:0:0:0:0:0:0:9200]}, publish_address {inet[/192.168.8.112:9200]}
[2014-03-13 13:42:23,629][INFO ][gateway        ] [New Goblin] recovered [1] indices into cluster_state
[2014-03-13 13:42:23,630][INFO ][node           ] [New Goblin] started
```

没有去阐述过多的细节，我们可以看到名为`New Goblin`节点(这取决于你个人的选择)已经启动开始，并选它自己作为一个单一集群的master。请不要在此刻还担心什么是master。这件重要的事情主要是说，我们在一个集群内启动了一个节点。

如前面提到的，我们可以覆盖群集或节点名称。这可以从从命令行启动Elasticsearch时，按如下进行:
> `./elasticsearch --cluster.name my_cluster_name --node.name my_node_name`

另外要注意的是以`http`标记的那样显示了节点的`HTTP`地址信息(192.168.8.112)和端口(9200)。默认情况下，Elasticsearch使用端口9200，以提供访问其REST API。如有必要，这个端口是可配置的。

### [基本概念](basit-concepts.md)
### [探索集群](exploring-your-cluster.md)
