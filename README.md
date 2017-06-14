# Elasticsearch 在线实验环境

## 软件简介

Elasticsearch是基于Lucene的搜索服务器。它提供了一个分布式，多租户的全文搜索引擎，具有RESTful Web界面和无模式的JSON文档。基于RESTful web接口。Elasticsearch是用Java开发的，并作为Apache许可条款下的开放源码发布，是当前流行的企业级搜索引擎。设计用于云计算中，能够达到实时搜索，稳定，可靠，快速，安装使用方便。

所属类型是服务器软件

特点：

稳定，可靠，快速，安装使用方便

## 软件官网

https://en.wikipedia.org/wiki/Elasticsearch

## Dockerfile 使用方法

注意：自5.0以来，Elasticsearch仅在localhostHTTP和传输上默认侦听，因此此映像设置http.host为0.0.0.0（localhost在Docker上下文中不是非常有用）。

因此，此图像不支持开箱即用的集群，必须设置额外的配置才能支持。

支撑聚类意味着具有在生产模式，该模式是更加严格，它执行自举检查Elasticsearch，检查的值特别是当vm.max_map_count其没有命名空间，因此必须设置为可接受的值在主机上（而不是简单地使用--sysctl上docker run）。

添加群集支持的一个示例是通过以下配置docker run：
```
$ docker run -d --name elas elasticsearch -Etransport.host=0.0.0.0 -Ediscovery.zen.minimum_master_nodes=1
```
### Running Containers
您可以elasticsearch简单地运行默认命令：
```
$ docker run -d elasticsearch
```
您还可以传递额外的标志elasticsearch：
```
$ docker run -d elasticsearch -Des.node.name="TestNode"
```
此图像附带一组默认的配置文件elasticsearch，但如果要提供自己的一组配置文件，可以通过以下方式执行/usr/share/elasticsearch/config：
```
$ docker run -d -v "$PWD/config":/usr/share/elasticsearch/config elasticsearch
```
此映像配置有一个卷/usr/share/elasticsearch/data来保存持久索引数据。如果要将数据保存在已装入的卷中，请使用该路径：
```
$ docker run -d -v "$PWD/esdata":/usr/share/elasticsearch/data elasticsearch
```
此图像包括EXPOSE 9200 9300（默认http.port），因此标准容器链接将使其自动可用于链接的容器。

## 资源链接

- https://elasticsearch.cn/
- https://www.elastic.co/products/elasticsearch
- https://en.wikipedia.org/wiki/Elasticsearch
