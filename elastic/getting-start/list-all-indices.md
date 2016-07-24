# 显示所有索引

让我们看一下现在的索引:
`curl localhost:9200/_cat/indices?v`

返回的结果是:
`health index pri rep docs.count docs.deleted store.size pri.store.size`

这意味着我们现在还没有任何索引存在与当前的集群中。

### 上一节: [集群的健康状态](cluster-health.md)
### 下一节: [创建一个索引](create-an-index.md)