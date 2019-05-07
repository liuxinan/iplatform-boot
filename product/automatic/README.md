# 自动化引擎

> 作者 刘喜男

自动化引擎提供了对编排的预案以及单独的任务脚本的一种执行能力。

## 1. 环境

- JDK1.8+
- 数据库 mysql5.6以上，oracle 11g

## 2. 依赖服务

- [发现服务](../../iplatform-common/DiscoveryService.md)
- [认证服务](../../iplatform-common/AuthService.md)
- [ActiveMQ](../../middleware/ActiveMQ.md)
- [Redis](../../middleware/Redis.md)

## 3. 介质

| 文件名                            | 说明       |
| --------------------------------- | ---------- |
| autoengine-2.0.0.100-SNAPSHOT.jar | 引擎部署包 |
| run.sh                            | 启动脚本   |

## 4. 启停

启动服务

```bash
sh run.sh start
```

停止服务

```bash
sh run.sh stop
```

重启服务

```bash
sh run.sh restart
```

## 5. 参数

> run.sh脚本中，只需配置表格中的参数

| 参数名                                | 必填 | 默认值 | 说明                                                         |
| ------------------------------------- | ---- | ------ | ------------------------------------------------------------ |
| discovery.server.address              | 是   |        | 配置注册服务的地址 discovery.server.address=<https://192.168.0.1:8761/eureka/> |
| server.host                           | 是   |        | 服务绑定IP                                                   |
| server.port                           | 是   |        | 服务绑定端口                                                 |
| spring.activemq.broker-url            | 是   |        | activemq服务地址，如：“tcp://192.168.55.46:61616”            |
| spring.datasource.dataSourceClassName | 是   |        | 数据源驱动，如使用mysql，则配置为“com.mysql.jdbc.Driver”，如使用oracle，则配置为“oracle.jdbc.driver.OracleDriver” |
| spring.datasource.url                 | 是   |        | 数据源地址，如使用mysql，则配置为"jdbc:mysql://192.168.55.50:3306/autodeploy?useUnicode=truecharacterEncoding=utf-8&autoReconnect=true"；如使用oracle，则配置为“jdbc:oracle:thin:@127.0.0.1:1521:bomc” |
| spring.datasource.username            | 是   |        | 数据库用户名                                                 |
| spring.datasource.password            | 是   |        | 数据库密码                                                   |
| spring.datasource.platform            | 是   |        | 数据库类型，如使用mysql，则配置为mysql；如使用oralce，则配置为oracle |
| spring.datasource.validation-query    | 是   |        | 如使用mysql，则配置为“select 1”；如使用oralce，则配置为“select 1 from dual” |
| spring.redis.host                     | 是   |        | redis单点服务地址ip                                          |

## 5. 开发手册

- [预案执行接口](API/预案执行接口.md)
- [任务执行接口](API/任务执行.md)
