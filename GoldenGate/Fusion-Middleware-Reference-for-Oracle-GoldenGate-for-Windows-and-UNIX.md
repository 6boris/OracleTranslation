# Oracle® Fusion Middleware
* Reference for Oracle GoldenGate for Windows and UNIX

## 注意
| 作者   | 刘嘉                          |
:---:|:---:
| 用途   |       翻译了Oracle GoldenGate官方文档   |
| 时间   |  2018-03-18         |
| 邮箱   | kylesliu@outlook.com        |
| GitHub | https://github.com/kylesliu |
| 本文地址 | https://github.com/kylesliu |

| 相关文档 |
:---:
|     [本文翻译地址][1]    |
|     [本文原文地址][1]    |
|     [本文翻译地址][1]    |
# 目录
# 前言

## 内容方面
>我的英语不太好，想通过翻译来提高自己的英语水平，现在有些专有名词可能翻译不出来。

# 1 Oracle GoldenGate GGSCI 命令
## 1.1 Oracle GoldenGate 命令摘要
>本部分总结了GGSCI命令并包含以下内容使用

* ==Summary of Extract Commands==
* Summary of Replicat Commands
* Summary of the ER Command
* Summary of Wallet Commands
* Summary of Credential Store Commands
* Summary of Trail Commands
* Summary of Parameter Commands
* Summary of Database Commands
* Summary of Trandata Commands
* Summary of Checkpoint Table Commands
* Summary of Oracle Trace Table Commands
* Summary of Oracle GoldenGate Data Store Commands
* Summary of Oracle GoldenGate Monitor JAgent Commands
* Summary of Oracle GoldenGate Automatic Heartbeat Commands
* Summary of Miscellaneous Oracle GoldenGate Commands

### 1.1.1 Summary of Manager Commands
>&emsp;&emsp;使用Manager命令来控制Manager进程。 Manager是Oracle GoldenGate的父进程，负责管理其进程和文件，资源，用户界面以及报告阈值和错误。


| 命令 | 描述 |
:---:|:---:
|	INFO MANAGER	|	返回有关Manager端口和子进程的信息|
|	SEND MANAGER	|	返回有关正在运行的Manager进程的信息	|
|	START MANAGER	|	启动Manager进程	|
|	STATUS MANAGER	|	返回Manager进程的状态	|
|	STOP MANAGER	|	停止Manager进程	|

### 1.1.2 Summary of Extract Commands

| 命令        | 描述 |
| ----------- | ---- |
| ADD EXTRACT | 创建  Extract Group  |
| ALTER EXTRACT | 修改 Extract Group      |
| CLEANUP EXTRACT | 删除 Extract Group 的运行记录      |
| DELETE EXTRACT | 删除  Extract Group  |
| KILL EXTRACT | 强制结束 Extract Group  |
| LAG EXTRACT | 精确获取 Extract Group 的抽取记录的时间差    |
| REGISTER EXTRACT | 在数据库中注册 Extract Group    |
| SEND EXTRACT | 获取  Extract Group 信息     |
| START EXTRACT | 开始   Extract Group     |
| STATS EXTRACT | 返回 Extract 处理的信息      |
| STATUS EXTRACT | 获取 Extract Group 的状态      |
| STOP EXTRACT | 停止 Extract Group      |
| UNREGISTER EXTRACT | 在数据库中取消注册 Extract Group      |

### 1.1.3 Summary of Replicat Commands
### 1.1.4 Summary of the ER Commands
### 1.1.5 Summary of Wallet Commands
### 1.1.6 Summary of Credential Store Commands
### 1.1.7 Summary of Trail Commands
### 1.1.8 Summary of Parameter Commands
### 1.1.9 Summary of Database Commands
### 1.1.10 Summary of Trandata Commands
### 1.1.11 Summary of Checkpoint Table Commands
### 1.1.12 Summary of Oracle Trace Table Commands
### 1.1.13 Summary of Data Store Commands
### 1.1.14 Summary of Monitor JAgent Commands
### 1.1.15 Summary of Automatic Heartbeat Commands
### 1.1.16 Summary of Miscellaneous Commands

## 1.2 INFO MAGAGER
>&emsp;&emsp;使用INFO MANAGER（或INFO MGR）确定Manager进程是否正在运行以及进程ID。 如果管理器正在运行，则会显示端口号。 该命令是STATUS MANAGER的别名。

* 语法
```sql?linenums
SEND MANAGER
[CHILDSTATUS [DEBUG]]
[GETPORTINFO [DETAIL]
[GETPURGEOLDEXTRACTS]
```


```sql
SEND MANAGER
[CHILDSTATUS [DEBUG]]
[GETPORTINFO [DETAIL]
[GETPURGEOLDEXTRACTS]
```

## 1.3 SEND MAGAGER
## 1.4 START MAGAGER
## 1.5 STATUS MAGAGER
## 1.6 STOP MAGAGER
## 1.7 ADD EXTRACT
## 1.8 ALTER EXTRACT
## 1.9 CLEANUP EXTRACT
## 1.10 DELETE EXTRACT
## 1.11 INFO EXTRACT
## 1.12 KILL EXTRACT
## 1.13 LAG EXTRACT
## 1.14 REGISTER EXTRACT
## 1.15 SEND EXTRACT
## 1.16 START EXTRACT
## 1.17 STATS EXTRACT
## 1.18 STATUS EXTRACT
## 1.19 STOP EXTRACT
## 1.20 UNREGISTER EXTRACT
## 1.21 ADD REPLICAT
## 1.22 ALTER REPLICAT
## 1.23 CLEANUP REPLICAT
## 1.24 DELETE REPLICAT
## 1.25 INFO REPLICAT
## 1.26 KILL REPLICAT
## 1.27 LAG REPLICAT
## 1.28 REGISTER REPLICAT
## 1.29 SEND REPLICAT
## 1.30 START REPLICAT
## 1.31 STATS REPLICAT
## 1.32 STATUS REPLICAT
## 1.33 STOP REPLICAT
## 1.34 SYNCHROIZE REPLICAT
## 1.35 UNREGISTER REPLICAT
## 1.36 ER
## 1.37 CREATE WALLET
## 1.38 OPEN WALLET
## 1.39 PURGE WALLET
## 1.40 ADD MASTERKEY
## 1.41 INFO MASTERKEY
## 1.42 ADD CREDENTIALSTORE
## 1.43 PURGE WALLET
## 1.44 PURGE WALLET
## 1.45 PURGE WALLET


# 2 Oracle GoldenGate Native 命令
# 3 Oracle GoldenGate 参数
# 4 Collector Parameters
# 5 Column Conversion Functions
# 6 User Exit Functions









  [1]: https://github.com/kylesliu/OracleTranslation/blob/master/GoldenGate/Fusion-Middleware-Reference-for-Oracle-GoldenGate-for-Windows-and-UNIX.md