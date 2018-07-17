Elasticsearch-zabbix
====================

Elasticsearch template and script for zabbix 3.X and elasticsearch 6.x

This project is a fork of Elasticsearch template and script of serialsito
and  Wprosdocimo/Elasticsearch-zabbix

https://github.com/serialsito/Elasticsearch-zabbix

These are made available by me under an Apache 2.0 license.

http://www.apache.org/licenses/LICENSE-2.0.html

How it works
=============

- Put ESzabbix.py in /etc/zabbix/scripts/ in the zabbix node

- Put ESzabbix.conf in  /etc/zabbix/scripts/  and update the connection string

- Put ESzabbix.userparm in the zabbix include parameters dir, in this case "/etc/zabbix/agent_include"

- Import ESzabbix_templates.xml to zabbix server ( update group config please )

Specs
=====

The items here are for monitoring Elasticsearch (presumably for logstash).

The template xml file actually contains three templates:

1. Elasticsearch Node & Cache (which is for node-level monitoring) ---deleted and will add it back

2. Elasticsearch Cluster (cluster state, shard-level monitoring, record count, storage sizes, etc.)

3. Elasticsearch Service (ES service status)

4. Elasticsearch Service (real write test)

~~The node name is expected as a host-level macro {$NODENAME}~~

There are triggers assigned for the cluster state:

0 = Green (OK)

1 = Yellow (Average, depends on "red")

2 = Red (High)


You will likely want to assign a value mapping for the ElasticSearch Cluster Status item.

In any event, the current list of included items is:

* ES Cluster (11 Items)
	- Cluster-wide records indexed per second
	- Cluster-wide storage size
	- ElasticSearch Cluster Status
	- Number of active primary shards
	- Number of active shards
	- Number of data nodes
	- Number of initializing shards
	- Number of nodes
	- Number of relocating shards
	- Number of unassigned shards
	- Total number of records
* ES Node
    - Node discovery
	- Node JVM Heap Mem Used
	- Node Storage Size
	- Records indexed per second
* ES Service (1 Item)
	- Elasticsearch service status
* ES real ( 1 Item )
    - write_a_key

中文
=====
zabbix 监控elasticsearch模板和脚本
我的测试环境是 zabbix 3.2 elasticsearch 6.2.3
请按照上面步骤安装使用。