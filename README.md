# spark-lineage-plugin
## Demo-Preview

```shell script
21/07/13 15:09:58 INFO SessionState: Created local directory: /var/folders/wx/wn4l9jh57nl_mrdvvp4tw93h0000gn/T/6193e443-9a61-418d-8edf-2b2f5e7b8725_resources
21/07/13 15:09:58 INFO SessionState: Created HDFS directory: /tmp/hive/huzekang/6193e443-9a61-418d-8edf-2b2f5e7b8725
21/07/13 15:09:58 INFO SessionState: Created local directory: /var/folders/wx/wn4l9jh57nl_mrdvvp4tw93h0000gn/T/huzekang/6193e443-9a61-418d-8edf-2b2f5e7b8725
21/07/13 15:09:58 INFO SessionState: Created HDFS directory: /tmp/hive/huzekang/6193e443-9a61-418d-8edf-2b2f5e7b8725/_tmp_space.db
21/07/13 15:09:58 INFO HiveClientImpl: Warehouse location for Hive client (version 1.2.2) is file:/Volumes/Samsung_T5/opensource/spark-lineage-plugin/spark-warehouse
([DcTable(default,t1)],[DcTable(default,t2)])
([DcTable(default,t1)],[DcTable(default,t2)])
```

## Usage
支持对spark-sql进行表级别血缘分析。

## 实现原理
通过拓展org.apache.spark.sql.SparkSessionExtensions插件，支持对sql的logicalPlan进行解析，获取sql的输入表和输出表信息。
```
InsertIntoHiveTable `default`.`t2`, org.apache.hadoop.hive.ql.io.orc.OrcSerde, Map(dt -> Some(2021)), false, false, [id, name]
+- Project [id#1, dix AS name#0]
   +- HiveTableRelation `default`.`t1`, org.apache.hadoop.hive.serde2.lazy.LazySimpleSerDe, [id#1]

```