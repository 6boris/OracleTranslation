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
# 前言
* 自动忽略掉....

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
```sql
INFO MANAGER
INFO MGR
```

## 1.3 SEND MAGAGER
>&emsp;&emsp;使用SEND MANAGER检索活动Manager进程的状态或检索Manager参数文件中配置的动态端口信息。

* **语法**
```sql
SEND MANAGER
[CHILDSTATUS [DEBUG]]
[GETPORTINFO [DETAIL]
[GETPURGEOLDEXTRACTS]
```

>**CHILDSTATUS [DEBUG]**
检索由Manager启动的进程的状态信息。 DEBUG返回分配给进程的端口号。
**GETPORTINFO [DETAIL]**
默认情况下，检索已分配给进程及其相应进程ID的当前端口列表。 DETAIL提供使用DYNAMICPORTLIST参数定义的所有端口的列表。
**GETPURGEOLDEXTRACTS**
显示有关使用Manager参数文件中的PURGEOLDEXTRACTS参数设置的跟踪维护规则的信息。

* **案列**

* 案列1
>发送管理器CHILDSTATUS DEBUG返回类似于以下内容的子进程状态。基本的CHILDSTATUS选项返回相同的显示，不包含端口列。

```sql
ID Group Process Retry Retry Time Start Time Port
1 ORAEXT 2400 0 None 2011/01/21 21:08:32 7840
2 ORAEXT 2245 0 None 2011/01/23 21:08:33 7842
```

* 案列2
>**SEND MANAGER GETPORTINFO DETAIL** 返回类似于以下内容的动态端口列表。
```sql
Entry Port Error Process Assigned Program
0 8000 0 2387 2011-01-01 10:30:23
1 8001 0
2 8002 0
```

* 案列3
>**SEND MANAGER GETPURGEOLDEXTRACTS** 会输出以下的类似信息

```sql
PurgeOldExtracts Rules
Fileset MinHours MaxHours MinFiles MaxFiles UseCP
S:\GGS\DIRDAT\EXTTRAIL\P4\* 0 0 1 0 Y
S:\GGS\DIRDAT\EXTTRAIL\P2\* 0 0 1 0 Y
S:\GGS\DIRDAT\EXTTRAIL\P1\* 0 0 1 0 Y
S:\GGS\DIRDAT\REPTRAIL\P4\* 0 0 1 0 Y
S:\GGS\DIRDAT\REPTRAIL\P2\* 0 0 1 0 Y
S:\GGS\DIRDAT\REPTRAIL\P1\* 0 0 1 0 Y
OK
Extract Trails
Filename Oldest_Chkpt_Seqno IsTable IsVamTwoPhaseCommit
S:\GGS\8020\DIRDAT\RT 3 0 0
S:\GGS\8020\DIRDAT\REPTRAIL\P1\RT 13 0 0
S:\GGS\8020\DIRDAT\REPTRAIL\P2\RT 13 0 0
S:\GGS\8020\DIRDAT\REPTRAIL\P4\RT 13 0 0
S:\GGS\8020\DIRDAT\EXTTRAIL\P1\ET 14 0 0
S:\GGS\8020\DIRDAT\EXTTRAIL\P2\ET 14 0 0
S:\GGS\8020\DIRDAT\EXTTRAIL\P4\ET 14 0 0
```

## 1.4 START MAGAGER
>用 STTART MANAGER 来启动管理进程，这适用于非群集环境。 在Windows群集中，应该从群集管理器停止Manager。

* **语法**
```sql
START MANAGER
[, CPU number]
[, PRI number]
[, HOMETERM device_name]
[, PROCESSNAME process_name]
```

>**CPU number**
适用于SQL / MX。 指定要用于该过程的CPU的编号。 有效值为数字0 - 15，缺省值为-1，分配1比上次启动的Manager高1。
**PRI number**
适用于SQL / MX。 指定提取进程优先级。 有效值为数字1 - 199，默认值为-1，与经理进程优先级相同。
**HOMETERM device_name**
适用于SQL / MX。 指定要使用的设备的名称，并且必须是终端或进程。 它可以输入Guardian $或OSS / G / xxxxx格式。 未定义$ zhome时，默认值为$ zhome或当前会话HOMETERM。
**PROCESSNAME process_name**
适用于SQL / MX。 以字母数字字符串指定进程名称，最多5个字符，可以输入Guardian $或OSS / G / xxxxx格式。 缺省值是系统生成的进程名称。

* **案列**

* 案列1
```sql
START MANAGER, CPU 2, PRI 148, HOMETERM /G/zhome, PROCESSNAME $ogmgr
```

## 1.5 STATUS MAGAGER
>用 **STATUS MANAGER** 来查看Manager是否正在运行，如果Manager正在运行着显示其端口号。

* 语法
```sql
STATUS MANAGER
```
## 1.6 STOP MAGAGER
>用 **STOP MANAGER** 来停止 Manager 进程，这适用于非群集环境。 在Windows群集中，应该从群集管理器停止Manager。

* 语法
```sql
STOP MANAGER [!]
```
>(感叹号表示)，表示直接停止Manager，不再确认。

## 1.7 ADD EXTRACT
>使用**ADD EXTRACT**创建一个Extract组。 除非指定了SOURCEISTABLE任务或aliasExtract，否则ADD EXTRACT将创建一个使用检查点的联机组，以便在运行之间保持处理连续性。

>对于DB2 for i，该命令为所有日志建立了全局起点，并且是必需的第一步。 发出ADD EXTRACT命令后，可以通过使用具有适当日记选项的ALTER EXTRACT命令，选择性地将任何给定日记定位到特定日记序列号。

>CDC记录。在处理第一个DML时，Informix CDC记录包含在逻辑日志中。日志中的每条记录都与一个称为LSN（日志序列号）的位置相关联。只有当初始化完成后，才能够遵守基于LSN的定位。首次添加解压缩时，必须使用INFO EXTRACT命令确保已完成初始化（持续时间取决于Extract参数文件中的表的数量）。然后确保显示的LSN编号与显示为提取报告文件中处理的第一条记录的LSN相匹配。例如，如果**INFO EXTRACT**返回的LSN编号为LSN：892：0X1235018，则报告文件中的消息必须是处理的第一条记录的LSN的位置：892：0X1235018，2014年4月16日上午2:56:58。当初始提取日志定位完成时，您可以发出停止或终止命令，尽管之前没有;在导致任何捕获重新启动之前这样做总是从数据库日志的EOF位置开始。

>Oracle GoldenGate每个Oracle GoldenGate Manager实例最多支持5,000个并发Extract和Replicat组。 在支持的级别上，所有组都可以通过GGSCI命令（如**INFO**和**STATUS**命令）进行控制和查看。 Oracle GoldenGate建议将组合数量的Extractand Replicat组保持在默认级别300或更低，以便有效管理您的环境。

>对于所有关键字和输入，此命令的大小不能超过500个字节，包括您为DESC选项输入的任何文本。

* 语法
```sql
ADD EXTRACT group_name
{, SOURCEISTABLE |
	, TRANLOG [bsds_name | LRI_number] |
	, INTEGRATED TRANLOG |
	, VAM |
	, EXTFILESOURCE file_name |
	, EXTTRAILSOURCE trail_name |
	, VAMTRAILSOURCE VAM_trail_name}
[, BEGIN {NOW | yyyy-mm-dd[ hh:mi:[ss[.cccccc]]]} |
[, EXTSEQNO sequence_number, EXTRBA relative_byte_address |
[, EOF |
[, LSN value |
[, EXTRBA relative_byte_address |
[, EOF | LSN value |
[, PAGE data_page, ROW row_ID |
[, SEQNO sequence_number
[, SCN value]
[, THREADS n]
[, PASSIVE]
[, PARAMS file_name]
[, REPORT file_name]
[, DESC 'description']
[, CPU number]
[, PRI number]
[, HOMETERM device_name]
[, PROCESSNAME process_name]
[, SOCKSPROXY {host_name | IP_address}[:port] [PROXYCSALIAS credential_store_alias
[PROXYCSDOMAIN credential_store_domain]]]
[, RMTNAME passive_Extract_name]
[, DESC 'description']
```
>**group_name**
>**SOURCEISTABLE**
>**TRANLOG [bsds_name | LRI_NUMBER]**
>**INTEGRATED TRANLOG**
>**VAM**
>**EXTFILESOURCE file_name**
>**EXTTRAILSOURCE trail_name**
>VAMTRAILSOURCE VAM_trail_name
>BEGIN {NOW | yyyy-mm-dd[ hh:mi:[ss[.cccccc]]]}
>yyyy-mm-dd[ hh:mi:[ss[.cccccc]]]
>EXTSEQNO sequence_number, EXTRBA relative_byte_address
>EXTRBA relative_byte_address
>EOF
>LSN value
>EOF | LSN value
>PAGE data_page, ROW row_ID
>SEQNO sequence_number
>SCN value
>PARAMS file_name
>REPORT file_name
>THREADS n
>PASSIVE
>DESC 'description'
>CPU number
>PRI number
>HOMETERM device_name
>PROCESSNAME process_name
>SOCKSPROXY {host_name | IP_address}[:port] [PROXYCSALIAS credential_store_alias [PROXYCSDOMAIN credential_store_domain]
>RMTNAME passive_extract_name

* **案列**

* 案列1
>下面创建一个名为finance的Extract组，用于从事务日志中提取数据库更改。 提取开始于用**ADD EXTRACT**创建组时创建的记录。

```sql
ADD EXTRACT finance, TRANLOG, BEGIN NOW
```

* 案列2
>下面创建一个名为finance的Extract组，用于从Oracle RAC日志中提取数据库更改。 提取从组创建时生成的记录开始。 有四个RAC实例，这意味着将有四个提取线程。

```sql
ADD EXTRACT finance, TRANLOG, BEGIN NOW, THREADS 4
```

* 案列3
>下面创建一个名为finance的Extract组，用于从事务日志中提取数据库更改。 提取从2011年1月21日8:00生成的记录开始。

```sql
ADD EXTRACT finance, TRANLOG, BEGIN 2011-01-21 08:00
```

* 案列4
>以下创建一个集成捕获提取组。

```sql
ADD EXTRACT finance, INTEGRATED TRANLOG, BEGIN NOW
```

* 案列5
>以下内容创建一个名为finance的Extract组，以最高性能或最大保护模式与Teradata TAM进行交互。 Teradata资源不使用BEGIN点。

```sql
ADD EXTRACT finance, VAM
```

* 案列6
>以下创建一个名为finance的VAM-sort Extract组。 该过程从VAM trail / ggs / dirdat / vt读取。

```sql
ADD EXTRACT finance, VAMTRAILSOURCE dirdat/vt
```

* 案列7
>以下内容将创建一个名为finance的数据泵提取组。 它从Oracle GoldenGate路径读取c:\ ggs\dirdat\lt。

```sql
ADD EXTRACT finance, EXTTRAILSOURCE dirdat\lt
```

* 案列8
>以下内容会创建一个名为load的初始加载Extract。

```sql
ADD EXTRACT load, SOURCEISTABLE
```

* 案列9
>以下内容创建一个名为finance的被动提取组，用于从事务日志中提取数据库更改。

```sql
ADD EXTRACT finance, TRANLOG, BEGIN NOW, PASSIVE
```

* 案列10
>以下创建一个名为financeA的别名提取组。 别名Extract与源系统sysA上名为finance的被动提取相关联。 该系统上的管理器正在使用端口7800。

```sql
ADD EXTRACT financeA, RMTHOST sysA, MGRPORT 7800, RMTNAME finance
```

* 案列11
>以下示例在重做日志中的特定Oracle系统更改编号（SCN）上创建并定位Extract。

```sql
ADD EXTRACT finance TRANLOG SCN 123456
ADD EXTRACT finance INTEGRATED TRANLOG SCN 123456
```

* 案列12
>以下示例创建一个指定要使用的主机的别名提取。

```sql
ADD EXTRACT apmp desc "alias extract" RMTHOST lc01abc MGRPORT 7813 RMTNAME ppmp SOCKSPROXY lc02def:3128 PROXYCSALIAS proxyAlias
```

* 案列13
>以下示例在SQL / MX系统上创建一个提取。

```sql
ADD EXTRACT ext exttcp, CPU 3, PRI 148, HOMETERM $ZTN0.#PTHBP32, PROCESSNAME $ext1
```

* 案列14
>以下示例在DB2 LUW系统上创建一个提取。

```sql
ADD EXTRACT extcust, TRANLOG LRI 8066.322711
```

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