---
layout: post
title:  "C# & SQL Server"
date:   2017-06-18 20:48:00 +0800
categories: C#
tags: C# SQL_Server
author: SteveDevin
mathjax: true
---
* content
{:toc}


最近刚做完数据库课程设计, 迫于强迫症用C#写了个异常简陋的界面, 工程已上传GitHub, 有兴趣的朋友可以点击网站底部的GIT链接吐槽一番.
在这边写篇博客记录一下C#对SQL Server的操作：





1.命名空间：
```cs
using System.Data.SqlClient;
```

2.链接字符串的写法:
```cs
string connectString = "Data Source = ; Initial Catalog = ; Persist Security Info = True; User ID = ; Password = ";
```

3.连接数据库
```cs
SqlConnection sqlCnt = new SqlConnection(connectString);
```
与其他形式的连接相同, 数据库的连接需要 使用前和使用结束后的 open、close 与 Dispose 操作

```cs
sqlCnt.Open();
sqlCnt.Close();
sqlCnt.Dispose();
```

4.SqlCommand 对象

4.1常用方法
```cs
SqlCommand cmd = sqlCnt.CreateCommand();
```
或者通过实例化的方式创建 SqlCommand 对象

```cs
SqlCommand cmd = new SqlCommand();
cmd.Connection = sqlCnt;
```

SqlCommand 的常用方法：
```cs
cmd.ExecuteNonQuery();
```
返回受影响的记录个数, 常可以用于判断是否存在符合条件的数据；
样例:
```cs
int succNum = cmd.ExecuteNonQuery();

if(succNum == 0) 
    Console.Write("operator failure");
else 
    Console.Write("operator succeed");
```

```cs
cmd.ExecuteScalar();
```
执行查询，返回首行首列的结果；

```cs
cmd.ExecuteReader()
```

返回一个SqlDataReader对象, 常用于查询, 可以理解为数据库的游标， 如果同一个 SqlDataReader 对象用于多次查询， 需要先 Close一下。
样例：

```cs
SqlDataReader dataReader = cmd.ExecuteReader();

if(! dataReader.Read())
    Console.Write("No query results");
else do
{
    Console.Write(dataReader['index name']);
} while(dataReader.Read());

dataReader.Close();
dataReader.Dispose();
```
4.2 常用成员

```cs
CommandType
```
链接类型

```cs
CommandText
```
查询语句/表明/存储过程

5.尚待补充：

5.1

```cs
System.Data.SqlClient.SqlDataAdapter;
```

5.2

```cs
System.Data.SqlClient.SqlCommandBuilder;
```

5.3

```cs
System.Data.DataSet;
```


6.参考资料/网站

[Rain Man](http://www.cnblogs.com/rainman/archive/2012/03/13/2393975.html)