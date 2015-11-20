---
layout: post
title: "Spark 配置参数(Sprak Configuration)"
date: 2015-11-21
categories: spark
tags: spark configuration 配置 参数
---



# Spark 配置参数(Sprak Configuration)




<table>
	<tr>
		<td colspan="3">
			<h3> Available Properties </h3>
		</td>
	</tr>
	<tr>
		<td>Property Name</td><td>默认值</td><td>含义</td>
	</tr>
	<tr>
		<td><code>spark.app.name</code></td>
		<td>(None)</td>
		<td>应用程序名称，此名称将会出现在spark UI和log中</td>
	</tr>
	<tr>
		<td><code>spark.driver.core</code></td>
		<td>1</td>
		<td>在集群(cluster)模式下，分配给driver进程的cores数量</td>
	</tr>	
	<tr>
		<td><code>spark.driver.maxResultSize</code></td>
		<td>1G</td>
		<td>对于所有分区（partitions），spark执行action算子的时候，允许的序列化结果的最大值，若结果数据大小超过了这个值，这个任务会被aborded，如果这个参数的值设置得太高，driver容易抛出outOfMemory异常，适当的设置这个值能够避免driver产生outOfMemory异常</td>
	</tr>
	<tr>
		<td><code>spark.driver.memory</code></td>
		<td>1G</td>
		<td>分配非driver进程的内存大小<br/><i>注：这个参数不能在程序中通过SparkContex对象来设置，因为在这个时间结点driver进程已经启动，可在./spark/conf/spark-default.conf文件中设置此参数</i></td>
	</tr>
	<tr>
		<td><code>spark.executor.memory</code></td>
		<td>1G</td>
		<td>设置每个executor内存的大小</td>
	</tr>
	<tr>
		<td><code>spark.extraListeners</code></td>
		<td>(Nonde)</td>
		<td>此处的参数设置为实现了SparkListener接口的类名，多个类名用引文分号“;”隔开。当SparkContext对象初始化的时候，这些类对象的实例将会通过Spark的listener bus创建并注册</td>
	</tr>
	<tr>
		<td><code>spark.local.dir</code></td>
		<td>/tmp</td>
		<td>Spark中用来存放数据的本地目录，存放的数据包括mapreduce后输出的文件，若RDD的StorageLevel为Disk，则此RDD也将会被存放在此目录。可以通过英文分号“;”分隔来设置多个目录</td>
	</tr>
	<tr>
		<td><code>spark.logConf</code></td>
		<td>false</td>
		<td>若设置为true，SparkContext启动后，INFO信息将会被保存</td>
	</tr>
	<tr>
		<td><code>spark.master</code></td>
		<td>(None)</td>
		<td>连接集群manager的url，比如：spark://master:7077</td>
	</tr>
	

	<tr><td colspan="3"><h3>Runtime Environment</h3></td></tr>
	<tr>
		<td>Property Name</td>
		<td>默认值</td>
		<td>含义</td>
	</tr>
	<tr>
		<td><code>spark.driver.extraClassPath</code></td>
		<td>(None)</td>
		<td>Extra classpath entries to prepend to the classpath of the driver</td>
	</tr>
	<tr>
		<td><code>spark.driver.extraJavaOptions</code></td>
		<td>(None)</td>
		<td>driver的JVM参数，比如说GC设置或者其他的一些日志信息，次参数不能在SparkContext对象中设置，因为此时driver已经启动，可在./spark/conf/sprak-default.conf中进行设置</td>
	</tr>
	<tr>
		<td><code>spark.driver.extraLibraryPath</code></td>
		<td>(None)</td>
		<td>通过JVM启动driver时需要加载的库文件路径</td>
	</tr>
	<tr>
		<td><code>spark.driver.userClassPathFirst</code></td>
		<td>false</td>
		<td>(试验性的)在driver中加载类的时候是否优先加载用户添加的jar文件。这样做的原因是能够被用来解决spark的依赖于用户程序依赖之间的冲突，这个特性只能用在集群（cluster）环境下</td>
	</tr>
	<tr>
		<td><code>spark.executor.extraClassPath</code></td>
		<td>(None)</td>
		<td>Extra classpath entris to prepend to the classpath of executors</td>
	</tr>
	<tr>
		<td><code>spark.executor.extraLibraryPath</code></td>
		<td>(None)</td>
		<td>通过JVM启动executor的时候，需要加载的额外的库文件</td>
	</tr>
	<tr>
		<td><code>spark.executor.logs.rolling.maxRetainedFiles</code></td>
		<td>(None)</td>
		<td>Sets the number of latest rolling log files that are going to be retained by the system. Older log files will be deleted. Disabled by default.</td>
	</tr>
	<tr>
		<td><code>spark.executor.rolling.maxSize</code></td>
		<td>(None)</td>
		<td>Set the max size of the file by which the executor logs will be rolled over. Rolling is disabled by default. See spark.executor.logs.rolling.maxRetainedFiles for automatic cleaning of old logs.</td>
	</tr>
	<tr>
		<td><code>spark.executor.logs.rolling.strategy</code></td>
		<td>(none)</td>
		<td>Set the strategy of rolling of executor logs. By default it is disabled. It can be set to "time" (time-based rolling) or "size" (size-based rolling). For "time", use spark.executor.logs.rolling.time.interval to set the rolling interval. For "size", use spark.executor.logs.rolling.size.maxBytes to set the maximum file size for rolling.</td>
	</tr>
	<tr>
		<td>spark.executor.logs.rolling.time.interval</td>
		<td>daily</td>
		<td>Set the time interval by which the executor logs will be rolled over. Rolling is disabled by default. Valid values are `daily`, `hourly`, `minutely` or any interval in seconds. See spark.executor.logs.rolling.maxRetainedFiles for automatic cleaning of old logs.</td>
	</td>
	<tr>
		<td>spark.executor.userClassPathFirst</td>
		<td>false</td>
		<td>（试验性的）和spark.driver.userClassPathFirst功能差不多，不过次属性值针对executor</td>
	</tr>
	<tr>
		<td>spark.executorEnv.[EnvironmentVariableName]</td>
		<td>(None)</td>
		<td>通过EnvironmentVariableName来添加指定的环境变量到executor process中，用户可以通过这个property来设置多个环境变量</td>
	</tr>
	<tr>
		<td>spark.python.profile</td>
		<td>false</td>
		<td>Enable profiling in Python worker, the profile result will show up by `sc.show_profiles()`, or it will be displayed before the driver exiting. It also can be dumped into disk by `sc.dump_profiles(path)`. If some of the profile results had been displayed manually, they will not be displayed automatically before driver exiting. By default the `pyspark.profiler.BasicProfiler` will be used, but this can be overridden by passing a profiler class in as a parameter to the `SparkContext` constructor.</td>
	</tr>
	<tr>
		<td>spark.python.profile.dump</td>
		<td>(nonde)</td>
		<td>The directory which is used to dump the profile result before driver exiting. The results will be dumped as separated file for each RDD. They can be loaded by ptats.Stats(). If this is specified, the profile result will not be displayed automatically.</td>
	<tr>
	<tr>
		<td>spark.python.memory</td>
		<td>512m</td>
		<td>Amount of memory to use per python worker process during aggregation, in the same format as JVM memory strings (e.g. 512m, 2g). If the memory used during aggregation goes above this amount, it will spill the data into disks.</td>
	<tr/>
	<tr>
		<td>spark.python.worker.reuse</td>
		<td>true</td>
		<td>Reuse Python worker or not. If yes, it will use a fixed number of Python workers, does not need to fork() a Python process for every tasks. It will be very useful if there is large broadcast, then the broadcast will not be needed to transfered from JVM to Python worker for every task.</td>
	</tr>
</table>