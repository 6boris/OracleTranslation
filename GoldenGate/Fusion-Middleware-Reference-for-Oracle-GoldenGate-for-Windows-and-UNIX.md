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
>提取组的名称。 提取组的名称最多可包含8个字符。 有关组命名约定，请参阅管理适用于Windows和UNIX的Oracle GoldenGate。

>**SOURCEISTABLE**
创建一个Extract任务，该任务使用Oracle GoldenGate直接装入方法或直接批量加载到SQL * Loader方法从数据库中提取初始加载的整个记录。 如果未指定SOURCEISTABLE，则ADD EXTRACT将创建联机更改同步过程，并且必须指定其他数据源选项之一。 使用SOURCEISTABLE时，请勿指定任何服务选项。 任务参数必须在参数文件中指定。 有关初始加载方法的更多信息，请参阅管理用于Windows和UNIX的Oracle GoldenGate。

>**TRANLOG [bsds_name | LRI_NUMBER]**
指定事务日志作为数据源。 对于Informix和Teradata以外的所有数据库使用此选项。 TRANLOG需要BEGIN选项。 （z / OS上的DB2）您可以在z / OS系统上使用DB2的bsds_name选项来指定事务日志的引导程序数据集文件名，尽管它不是必需的并且未被使用。 您不需要更改现有的TRANLOG参数。 （DB2 LUW）您可以使用DB2 LUW系统的LRI_NUMBER选项为检查点事务日志指定LRI记录值。 （Oracle）从Oracle标准版或企业版11.2.0.3开始，此模式称为经典捕获模式。 Extract直接读取Oracle重做日志。 有关备用配置，请参阅INTEGRATED TRANLOG。

>**INTEGRATED TRANLOG**
（Oracle）在集成捕获模式下添加此提取。 在此模式下，Extract与数据库登录服务器集成，后者将逻辑更改记录（LCR）直接传递到提取。 Extract不会读取重做日志。 在使用INTEGRATEDTRANLOG之前，请使用REGISTER EXTRACT命令。 有关集成捕获的信息，请参阅安装和配置Oracle GoldenGate for Oracle数据库。

>**VAM**
（Informix，MySQL和Teradata）指定称为供应商的Extract API 访问模块（VAM）将用于将更改数据传输到提取。

>**EXTFILESOURCE file_name**
指定一个提取文件作为数据源。 将该选项与辅助抽取组（数据泵）一起使用，充当主要抽取组和目标系统之间的中介。 对于file_name，请指定文件的相对路径或完全限定路径名称，例如dirdat\extfile或c\ggs\dirdat\extfile。

>**EXTTRAILSOURCE trail_name**
指定一个路径作为数据源。 将该选项与辅助抽取组（数据泵）一起使用，充当主要抽取组和目标系统之间的中介。 对于trail_name，请指定路径的相对路径名或完全限定路径名，例如dirdat\aa或c：\ggs\dirdat\aa。

>**VAMTRAILSOURCE VAM_trail_name**
（Teradata）指定VAM路径。 使用Teradata最大保护模式时使用此选项。 对于VAM_trail_name，请指定主Extract组正在写入的VAM路径的相对路径名或完全限定路径名。 使用VAM-sort Extract组读取VAM路径并将数据发送到目标系统。

>**BEGIN {NOW | yyyy-mm-dd[ hh:mi:[ss[.cccccc]]]}**
>指定数据源中开始处理的时间戳
>> **NOW**
>> 对于除DB2 LUW以外的所有数据库，NOW指定发出ADD EXTRACT命令的时间。
>> 对于DB2 LUW，NOW指定START EXTRACT生效的时间。 它
定位到大致与日期和时间匹配的第一条记录。 这是因为包含时间戳的唯一日志记录是提交和中止事务记录，因此只能根据相关的时间戳来计算起始位置。 这是Oracle GoldenGate使用的API的限制。
>除了在ADD EXTRACT语句之前绕过捕获到轨迹的数据外，不要使用NOW作为数据泵提取。
>> **yyyy-mm-dd[ hh:mi:[ss[.cccccc]]]**
>> 


>**EXTSEQNO sequence_number, EXTRBA relative_byte_address**
适用于Oracle的经典捕获模式中的主要提取，NonStop SQL / MX的主要提取，以及数据泵提取。 不支持集成模式下的Oracle Extract。 指定以下任一项：
>> 1.该日志中的Oracle重做日志和RBA的序号，开始捕获数据。
>> 2.NonStop SQL / MX TMF审计跟踪序列号和该文件中的相对字节地址，以开始捕获数据。 这些一起指定了TMF主审计追踪（MAT）中的位置。
>> 3.开始捕获数据的路径中的文件（用于数据泵）。 指定序列号，但不是用于填充的任何零。 例如，如果跟踪文件是c：\ ggs \ dirdat \ aa000026，则可以指定EXTSEQNO 26.默认情况下，处理从跟踪开始处开始，除非使用此选项。


>**EXTRBA relative_byte_address**
适用于z / OS上的DB2。 指定开始捕获数据的事务日志中的相对字节地址。 所需的格式是0Xnnn，其中nnn是1到20位十六进制数（第一个字符是数字零，第二个字符可以是大写或小写字母x）。

>**EOF**
适用于SQL Server和DB2 for i。 将处理配置为在下一条记录将写入的日志文件（或日志）结尾处开始。 任何活动的交易都不会被捕获。

>**LSN value**
适用于Informix和SQL Server。 指定开始捕获数据的事务日志中的LSN。 指定的LSN应该存在于日志备份或在线日志中。 此选项的别名是EXTLSN。
>对于SQL Server，LSN由其中的一个组成，具体取决于数据库如何返回它：
>>  1.冒号分隔的十六进制字符串（8：8：4）填充了前导零和0X前缀，如0X00000d7e：0000036b：01bd
>>  2.冒号分隔的十进制字符串（10：10：5）用前导零填充，如0000003454：0000000875：00445
>>   3.C用0X前缀冒号分隔的十六进制字符串，不带前导零，如0Xd7e：36b：1bd
>>   4.不带前导零的冒号分隔的十进制字符串，如3454：875：445所示
>>   5.十进制字符串，如3454000000087500445

>在前面的例子中，第一个值是虚拟日志文件号，第二个是虚拟日志中的段号，第三个是条目号。 您可以使用如下查询来查找指定事务的LSN：
```sql
SELECT [  Current LSN], [Transaction Name], [Begin Time]
    FROM fn_dblog(null, null)
  WHERE Operation = 'LOP_BEGIN_XACT'
      AND [Begin Time] >= 'time';
```
>您在查询中应使用的时间格式应类似于'2015/01/30 12：00：00.000'，而不是'2015-01-30 12：00：00.000'。
您可以确定特定事务开始的时间，然后查找相关的LSN，然后在具有相同开始时间的两个事务之间进行定位。

>EOF | LSN value
对DB2 LUW有效。 在Extract启动时指定事务日志中的起始位置。

>PAGE data_page, ROW row_ID
对Sybase有效。 指定数据页面和行，它们一起定义Sybase事务日志中的起始位置。 由于开始位置必须是开始于最接近或位于指定PAGE和ROW的事务的第一条记录，因此提取报告将显示以下位置：
>1.**Positioning To**是用PAGE和ROW指定的记录的位置。
2.**Positioning To** 是在第一个BEGIN记录在或之后找到的Positioning To定位。
3.**First Record Position** 是第一个有效记录在或之后 Positioned To定位.

>SEQNO sequence_number
适用于DB2 for i。 在系统序列号（或长度最多为20位数的十进制数）时或之后开始捕获。

>SCN value
Oracle系统更改号码（SCN）。 此选项对于经典捕捉和集成模式下的提取均有效。 对于集成模式下的Extract，SCN值必须大于Extract在数据库中注册的SCN

>PARAMS file_name
指定Oracle GoldenGate目录中缺省dirprm以外的位置中的Extract参数文件的完整路径名。

>REPORT file_name
指定Extract报告文件的完整路径名称，而不是Oracle GoldenGate目录中默认的dirrpt位置。

>THREADS n
适用于Oracle经典捕捉模式。 指定提取维护以读取重做日志的生产者线程的数量。
>在Oracle RAC配置中需要指定生产者线程的数量。 这些是提取线程，用于读取各个RAC节点上的不同重做日志。 该值必须与要从中捕获重做数据的节点数相同。


>**PASSIVE**
指定此提取组以被动模式运行，并且只能通过在目标系统上启动或停止别名提取组来启动和停止。 源目标连接将不由该组建立，而由目标的别名提取建立。
>该选项可用于常规提取组或数据泵提取组。 只应由源系统上的任何一个提取者使用，该提取者将通过网络将数据发送到目标上的远程路径。 有关如何配置被动和别名解压缩组的说明，请参阅管理用于Windows和UNIX的Oracle GoldenGate。


>**DESC 'description'**
指定组的描述，例如“在Serv1上提取account_tab”。 用单引号括起描述。 您可以使用缩写关键字DESC或完整的描述

>**CPU number**
适用于SQL / MX。 指定要用于该过程的CPU的编号。 有效值为数字0 - 15，缺省值为-1，分配1比上次启动的Manager高1。

>**PRI number**
适用于SQL / MX。 指定提取进程优先级。 有效值为数字1 - 199，默认值为-1，与经理进程优先级相同。

>**HOMETERM device_name**
适用于SQL / MX。 指定要使用的设备的名称，并且必须是终端或进程。 它可以输入Guardian $或OSS / G / xxxxx格式。 未定义$ zhome时，默认值为$ zhome或当前会话HOMETERM

>**PROCESSNAME process_name**
适用于SQL / MX。 指定过程名称，最多5个字符的字母数字字符串，可以输入Guardian $或OSS / G / xxxxx格式。 缺省值是系统生成的进程名称。

>**SOCKSPROXY {host_name | IP_address}[:port] [PROXYCSALIAS credential_store_alias [PROXYCSDOMAIN credential_store_domain]**
用于别名提取。 指定代理服务器的DNS主机名或IP地址。 如果您的DNS服务器无法访问，您可以使用其中一个来定义主机，但必须使用IP地址。 如果您使用的是IP地址，请使用IPv6或IPv4映射地址，具体取决于目标系统的堆栈。 您必须指定PROXYCSALIAS。 另外，您可以指定要使用的端口以及凭证存储域。

>**RMTNAME passive_extract_name**
用于别名提取。 指定被动提取名称，如果不同于别名提取的名称.


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



# 2 Oracle GoldenGate Native 命令
# 3 Oracle GoldenGate 参数
# 4 Collector Parameters
# 5 Column Conversion Functions
# 6 User Exit Functions 









  [1]: https://github.com/kylesliu/OracleTranslation/blob/master/GoldenGate/Fusion-Middleware-Reference-for-Oracle-GoldenGate-for-Windows-and-UNIX.md