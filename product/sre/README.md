#  SRE

> 作者 刘喜男

## 1. 环境

- JDK1.8+
- 数据库 mysql5.6以上，oracle 11g

## 2. 依赖服务

- [发现服务](../../iplatform-common/DiscoveryService.md)
- [认证服务](../../iplatform-common/AuthService.md)
- [自动化引擎](../../product/automatic/README.md)
- [ActiveMQ](../../middleware/ActiveMQ.md)
- [Redis](../../middleware/Redis.md)

  ​

## 3. 介质

| 文件名                        | 说明            |
| -------------------------- | ------------- |
| sre-service-1.0.0.100.jar  | service后台程序包  |
| sre-ui-1.0.0.100.jar       | UI端程序包        |
| sre-schedule-1.0.0.100.jar | 任务调度程序包       |
| service_run.sh             | service后台启动脚本 |
| ui_run.sh                  | UI端启动脚本       |
| schedule_run.sh            | 任务调度启动脚本      |

## 4. 启停

启动服务

```bash
sh service_run.sh start
sh ui_run.sh start
sh schedule_run.sh start
```

停止服务

```bash
sh service_run.sh stop
sh ui_run.sh stop
sh schedule_run.sh stop
```

 重启服务

```bash
sh service_run.sh restart
sh ui_run.sh restart
sh schedule_run.sh restart
```

## 4. 参数

> service_run.sh

| 参数名                                      | 必填   | 默认值  | 说明                                       |
| ---------------------------------------- | ---- | ---- | ---------------------------------------- |
| discovery.server.address                 | 是    |      | 配置注册服务的地址 discovery.server.address=https://192.168.0.1:8761/eureka/ |
| eureka.instance.metadataMap.tenant       | 是    |      | 租户                                       |
| server.host                              | 是    |      | 服务绑定IP                                   |
| server.port                              | 是    |      | 服务绑定端口                                   |
| spring.activemq.broker-url               | 是    |      | activemq服务地址，如：“tcp://192.168.55.46:61616” |
| spring.datasource.dataSourceClassName    | 是    |      | 数据源驱动，如使用mysql，则配置为“com.mysql.jdbc.Driver”，如使用oracle，则配置为“oracle.jdbc.driver.OracleDriver” |
| spring.datasource.url                    | 是    |      | 数据源地址，如使用mysql，则配置为"jdbc:mysql://192.168.55.50:3306/sre?useUnicode=true&characterEncoding=utf-8&autoReconnect=true"；如使用oracle，则配置为“jdbc:oracle:thin:@127.0.0.1:1521:bomc” |
| spring.datasource.username               | 是    |      | 数据库用户名                                   |
| spring.datasource.password               | 是    |      | 数据库密码                                    |
| spring.datasource.platform               | 是    |      | 数据库类型，如使用mysql，则配置为mysql；如使用oralce，则配置为oracle |
| spring.datasource.validation-query       | 是    |      | 如使用mysql，则配置为“select 1”；如使用oralce，则配置为“select 1 from dual” |
| spring.dynamicdatasource.enable          | 是    |      | 开启动态数据源，配置为true，开启动态数据源                  |
| spring.dynamicdatasource.names           | 是    |      | 动态数据源名称，多个名称之前用逗号“,”分隔，例如：name1,name2    |
| spring.dynamicdatasource.name1.dataSourceClassName | 是    |      | 名称为name1的动态数据源的dataSourceClassName       |
| spring.dynamicdatasource.name1.url       | 是    |      | 名称为name1的动态数据源的url                       |
| spring.dynamicdatasource.name1.username  | 是    |      | 名称为name1的动态数据源的用户名                       |
| spring.dynamicdatasource.name1.password  | 是    |      | 名称为name1的动态数据源的密码                        |
| spring.dynamicdatasource.name2.dataSourceClassName | 是    |      | 名称为name2的动态数据源配置同name1                   |
| sync-datasource.province                 | 是    |      | 同步数据源功能针对的省份，目前支持湖北省，配置为hubei即可。         |
| sync-datasource.cmdb-type                | 是    |      | cmdb类型，new：新cmdb；old：旧cmdb，湖北省配置为old     |
| sync-datasource.userinfo-type            | 是    |      | 用户信息类型，dynamic：动态的；static：静态的，湖北省配置为dynamic |
| sync-datasource.cilist-url               | 是    |      | 新cmdb的接口地址，http://192.168.55.46:50010/cmdbservice/api/v1/cmdb/info/cilist |
| sync-datasource.agent-username           | 是    |      | 静态用户信息的用户名                               |
| sync-datasource.agent-password           | 是    |      | 静态用户信息的密码                                |
| tsd.url                                  | 是    |      | opentsdl的url，http://192.168.55.41:4242   |
| spring.redis.host                        | 是    |      | redis单点服务ip                              |
| spring.redis.port                        | 是    |      | redis单点服务端口                              |

> ui_run.sh

| 参数名                                | 必填   | 默认值  | 说明                                       |
| ---------------------------------- | ---- | ---- | ---------------------------------------- |
| discovery.server.address           | 是    |      | 配置注册服务的地址 discovery.server.address=https://192.168.0.1:8761/eureka/ |
| eureka.instance.metadataMap.tenant | 是    |      | 租户                                       |
| server.host                        | 是    |      | 服务绑定IP                                   |
| server.port                        | 是    |      | 服务绑定端口                                   |

> 


> schedule_run.sh

| 参数名                                   | 必填   | 默认值  | 说明                                       |
| ------------------------------------- | ---- | ---- | ---------------------------------------- |
| discovery.server.address              | 是    |      | 配置注册服务的地址 discovery.server.address=https://192.168.0.1:8761/eureka/ |
| eureka.instance.metadataMap.tenant    | 是    |      | 租户                                       |
| server.host                           | 是    |      | 服务绑定IP                                   |
| server.port                           | 是    |      | 服务绑定端口                                   |
| flyway.enabled                        | 是    |      | 是否开启flyway，配置为false                      |
| spring.activemq.broker-url            | 是    |      | activemq服务地址，如：“tcp://192.168.55.46:61616” |
| spring.datasource.dataSourceClassName | 是    |      | 数据源驱动，如使用mysql，则配置为“com.mysql.jdbc.Driver”，如使用oracle，则配置为“oracle.jdbc.driver.OracleDriver” |
| spring.datasource.url                 | 是    |      | 数据源地址，如使用mysql，则配置为"jdbc:mysql://192.168.55.50:3306/sre?useUnicode=true&characterEncoding=utf-8&autoReconnect=true"；如使用oracle，则配置为“jdbc:oracle:thin:@127.0.0.1:1521:bomc” |
| spring.datasource.username            | 是    |      | 数据库用户名                                   |
| spring.datasource.password            | 是    |      | 数据库密码                                    |
| spring.datasource.platform            | 是    |      | 数据库类型，如使用mysql，则配置为mysql；如使用oralce，则配置为oracle |
| spring.datasource.validation-query    | 是    |      | 如使用mysql，则配置为“select 1”；如使用oralce，则配置为“select 1 from dual” |
| tsd.url                               | 是    |      | opentsdl的url，http://192.168.55.41:4242   |
| spring.redis.host                     | 是    |      | redis单点服务ip                              |
| spring.redis.port                     |      |      | redis单点服务端口                              |




