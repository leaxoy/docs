# 集群的健康状态

让我们从集群健康检测开始，通过它我们可以查看集群的状态。我们使用`curl`工具，但是也可以使用其它任意可以进行`HTTP/Rest`请求的工具。假定现在依然在启动Elastic的集群上，同时打开另外一个终端。

使用 [`_cat API`](../cat-apis) 来进行健康检测。
`curl localhost:9200/_cat/health?v`

结果是:
```
epoch      timestamp cluster       status node.total node.data shards pri relo init unassign
1394735289 14:28:09  elasticsearch green           1         1      0   0    0    0        0
```

可以看出来，集群的名字是`elasticsearch`， 并且健康状态是`green`。

无论什么时候查看集群的状态，结果总是`green`, `yellow` 或者 `red`之一。绿色代表一切正常(功能健全), 黄色代表数据可以被访问到但是备份的分片尚未被分配(功能健全)，红色代表由于某些原因，数据并不能被正常的访问到。即使状态是红色的，它依然可以提供一些功能(比如：提供可用的分片中的数据)，但是你要尽快修复它。

从上面回应的信息看，可以发现只有一个节点，因为没有任何数据，所以没有任何分片。默认情况下，elasticssearch 使用`unicast Network`来发现同一台机器上的其他节点。你可以在同一台机器上启动多个节点，他们会自动加入同一个集群中。在这种情况下，你会看到多个节点。

使用下面的命令获取多个节点:

`curl localhost:9200/_cat/nodes?v`

结果是:
```
host         ip        heap.percent ram.percent load node.role master name
mwubuntu1    127.0.1.1            8           4 0.00 d         *      New Goblin
```

可以看到一个名字为`New Goblin`的节点，它是这个集群中唯一的节点。

### 上一节: [查看索引](list-all-indices.md)
### 下一节: [查看索引](list-all-indices.md)