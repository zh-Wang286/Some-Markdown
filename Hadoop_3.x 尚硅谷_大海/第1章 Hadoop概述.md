[TOC]

# Hadoop组成

Hadoop 1.x 2.x 3.x区别

```mermaid
flowchart TB
	
    subgraph h3[Hadoop 3.x]
	h3l[在组成上没有变化]
	end
	
    subgraph h2[Hadoop 2.x]
	h2l1[MapReduce 计算]
	h2l2[Yarn 资源调度]
	h2l3[HDFS 数据存储]
	h2l4[Common 辅助工具]
	end
	
    subgraph h1[Hadoop 1.x]
	h1l1[MapReduce 计算+资源调度]
	h1l2[HDFS 数据存储]
	h1l3[Common 辅助工具]
	end
```



## HDFS架构概述

```mermaid
flowchart TB
NameNode
2NN
	subgraph Hadoop104
	d104[DataNode]
	t104[1T]
	end
	
	subgraph Hadoop103
	d103[DataNode]
	t103[1T]
	end
	
    subgraph Hadoop102
	d102[DataNode]
	t102[1T]
	end
    
NameNode-->Hadoop102 & Hadoop103 & Hadoop104
%% 2NN-->NameNode
```

HDFS：Hadoop Distributed File System，是一个分布式文件系统

NameNode（nn）：存储文件的原数据，如文件名、目录结构、文件属性（生成时间、副本数、文件权限等），以及每个文件的块列表和块所在的DataNode等。

DataNode（dn）：在本地文件系统存储文件块数据，以及块数据的校验和。

Seconda NameNode（2nn）：每隔一段时间对NameNode原数据备份

## YARN架构概述

YARN：Yet Another Resource Negotiator ，另一种资源协调者，是Hadoop的资源管理器。

```mermaid
flowchart LR
client1([client]) 
client2([client])
rm[Resource Manager]
subgraph nm3[NodeManager3]
    %%direction LR
	subgraph nm3c1[Container]
	    nm3c1am[App Mstr]
	end
    subgraph nm3c2[Container]
	    nm3c2rt[Reduce Task]
	end
    nm3c1-.->nm3c2
end
subgraph nm2[NodeManager2]
    %%direction LR
	subgraph nm2c1[Container]
	    nm2c1am[App Mstr]
	end
    subgraph nm2c2[Container]
	    nm2c2rt[Reduce Task]
	end
    nm2c1-.->nm2c2
end
subgraph nm1[NodeManager1]
    %%direction LR
	subgraph nm1c1[Container]
	    nm1c1am[App Mstr]
	end
    subgraph nm1c2[Container]
	    nm1c1mt[Map Task]
	end
    nm1c1-.->nm1c2
end

rm --> nm1 & nm2 & nm3  
rm --> nm1c1am & nm2c1am & nm3c1am  

client1 & client2 -.->|Jop Submission|rm


nm1c1am-.->nm2c2
nm2c1am-.->nm3c1
nm2c1am-.->nm3c2
```

ResourceManeger(RM)：整个集群资源（内存、CPU等）的老大

NodeManager(NM)：单个节点服务器资源老大

ApplicationMaster(AM)：单个任务运行的老大

Container：容器，相当于一台独立的度武器，里面封装了内存任务所需的资源，如内存、CPU、磁盘、网络等

说明：

- 客户端可以有多个
- 集群上可以运行多个ApplicationMaster
- 每个NodeManager上可以有多个Container

## MapReduce架构概述

MapReduce将计算分为两个阶段：Map和Reduce

1. Map阶段并行处理输入数据
2. Reduce阶段对Map结果进行汇总

```mermaid
flowchart LR
data[(data)]
data --> hadoop101
data --> hadoop102
data --> |Map|hadoop103
data --> hadoop104
data --> hadoop["……"]
hadoop101 --> serve[汇总服务器]
hadoop102 --> serve
hadoop103-->|Reduce|serve
hadoop104 --> serve
hadoop --> serve
```

HDFS、YARN、MapReduce三者关系

![image-20220115171355751](image-20220115171355751.png)

