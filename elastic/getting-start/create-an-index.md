# 创建一个索引

现在让我们来创建一个名为“customer”索引，然后重新查看所有的索引。

`curl -XPUT localhost:9200/customer?pretty`

`curl localhost:9200/_cat/indices?v`

第一条命令使用curl的PUT动词创建了一个索引，同时在URL后面加上pretty参数来美化输出的JSON数据。结果应该像下面这样:
```shell
curl -XPUT 'localhost:9200/customer?pretty'

{
	"acknowledged" : true
}

curl 'localhost:9200/_cat/indices?v'

health index    pri rep docs.count docs.deleted store.size pri.store.size
yellow customer   5   1          0            0       495b           495b
```
第二条命令的结果告诉我们现在拥有一个索引，它有5个主分片以及一个副分片，但是没有数据。

你应该注意到了customer索引的状态变成了黄色。从前面的讨论中，我们知道黄色代表着某些分片尚未被分配。这是因为Elastic会为每一个索引创建一个备份分片。考虑到我们现在集群中只有一个节点，备份分片并不会被分配(为了保证高可用性)，直到有新的节点加入到这个集群里面。一旦备份分片被分配到从节点上面，集群状态将会从新变成绿色。

### 上一节: [查看索引](list-all-indices.md)
### 下一节: [修改数据](modifying-your-data.md)