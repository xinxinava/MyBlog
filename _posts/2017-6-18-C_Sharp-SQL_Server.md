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
与其他形式的连接相同, 数据库的连接需要 使用前和使用结束后的 open 与 close 操作

```cs
sqlCnt.Open();
sqlCnt.Close();
```

4.SqlCommand 对象

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

```cs
cmd.ExecuteScalar();
```
执行查询，返回首行首列的结果；

```cs
cmd.ExecuteReader()
```
返回一个SqlDataReader对象, 常用于查询, 可以理解为数据库的游标， 如果同一个 SqlDataReader 对象用于多次查询， 需要先 Close一下。

5.直接贴代码吧....
```cs
 private void button1_Click(object sender, EventArgs e)
        {
            string news = richTextBox1.Text;
            string name = textBox1.Text;
            string ID = null;

            string connectString = "Data Source = ; Initial Catalog = ; Persist Security Info = True; User ID = ; Password = ";

            SqlConnection sqlCnt = new SqlConnection(connectString);
            sqlCnt.Open();

            SqlCommand cmd = sqlCnt.CreateCommand();

            string strcmd = "select name, ID from Admins where name='" + name + "';";

            cmd.CommandText = strcmd;
            SqlDataReader require = cmd.ExecuteReader();

            if(! require.Read())
            {
                MessageBox.Show("请以管理员身份发布新闻");
            }
            else
            {
                ID = require[1].ToString();

                strcmd = "insert into News values('" + ID + "', getdate(), '" + news + "');";
                cmd.CommandText = strcmd;

                require.Close();


                int succCount = cmd.ExecuteNonQuery();
                if (succCount == 0)
                    MessageBox.Show("发布失败");
                else MessageBox.Show("发布成功");

            }

            require.Close();
            sqlCnt.Close();
        }
```

时间太紧迫了， 先写到这， 以后再细化






