
<img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200316180139687.png" alt="image-20200316180139687" style="zoom: 50%;" />
## 伪分布式运行模式

### 配置文件

1. 配置core-site.xml

```
<!--指定HDFS中NameNode的地址-->
<property> 
	<name>fs.defaultFS</name>
	<value>hdfs://master:9000</value> 
</property>

<!--指定Hadoop运行时产生文件的存储路径-->
<property> 
	<name>hadoop.tmp.dir</name>
	<value>/opt/hadoop-2.7.2/data/tmp</value> 
</property>
```

2. 配置hadoop-env.sh

```
加入JAVA_HOME
```

3. 配置hdfs-site.xml

```
<!--指定HDFS副本数量-->
<property> 
	<name>dfs.replication</name>
	<value>1</value> 
</property>

```

### 启动集群

1. 格式化NameNode（第一次启动时）	`bin/hdfs namnode -format`
2. 启动NameNode     `sbin/hadoop-daemon.sh start namenode`
3. 启动DataNode      `sbin/hadoop-daemon.sh start datanode`

### 查看集群启动情况

* `jps`
* web端  `ip:50070`

### 配置yarn集群

1. 配置yarn-env.sh     加入`JAVA_HOME`
2. 配置yarn-site.xml     

```
<!--Reducer获取数据的方式-->
<property> 
	<name>yarn.nodemanager.aux-services</name>
	<value>mapreduce_shuffle</value> 
</property>

<!--指定Yarn的ResourceManager的地址-->
<property> 
	<name>yarn.resourcemanager.hostname</name>
	<value>master</value> 
</property>
```

3. 配置mapred-env.sh     加入`JAVA_HOME`
4. 配置mapred-site.xml

```
将mapred-site.xml.template重命名为mapred-site.xml。

<!--指定MR运行在Yarn上-->
<property> 
	<name>mapreduce.framework.name</name>
	<value>yarn</value> 
</property>
```

### 启动集群

1. 启动前必须保证NameNode和DataNode已经启动。
2. 启动ResourceManager    `sbin/yarn-daemon.sh start resourcemanager`
3. 启动NodeManager    `sbin/yarn-daemon.sh start nodemanager`

### 配置历史服务器

1. 配置mapred-site.xml

```
<!--历史服务器端地址-->
<property> 
	<name>mapreduce.jobhistory.address</name>
	<value>master:10020</value> 
</property>

<!--历史服务器Web端地址-->
<property> 
	<name>mapreduce.jobhistory.webapp.address</name>
	<value>192.168. 1.106:19888</value> 
</property>
```

2. 启动历史服务器   `sbin/mr-jobhistory-daemon.sh start historyserver`
3. 查看历史服务器是否启动  `jps`
4. web端    `ip:8088`
5. 查看jobhistory    `http://master:19888/jobhistory`

### 配置日志的聚合

* 日志聚合的概念：应用运行完成以后，将程序运行的日志信息上传的HDFS

* 日志聚合的好处：可以方便地查看程序运行的详情，方便开发调试

* 注意：开启日志聚合功能，需要重启NodeManager、ResourceManager和HistoryManager

1. 配置yarn-site.xml

```
<!--日志聚合功能使能-->
<property> 
	<name>yarn.log-aggregation-enable</name>
	<value>true</value> 
</property>

<!--日志保留时间设置为七天-->
<property> 
	<name>yarn.log-aggregation.retain-seconds</name>
	<value>604800</value> 
</property>
```

2. 关闭NodeManager、ResourceManager、HistoryManager

```
 sbin/mr-jobhistory-daemon.sh stop historyserver
 sbin/yarn-daemon.sh stop nodemanager
 sbin/yarn-daemon.sh stop resourcemanager
```

3. 重启NodeManager、ResourceManager、HistoryManager

```
sbin/yarn-daemon.sh start resourcemanager
sbin/yarn-daemon.sh start nodemanagerjps
sbin/mr-jobhistory-daemon.sh start historyserver
```

