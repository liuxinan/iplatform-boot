# 自动化部署

> 作者 刘喜男

## 1. 环境

- JDK1.8+
- 数据库 mysql5.6以上，oracle 11g

## 2. 依赖服务

- 发现服务
- 认证服务
- 自动化引擎
- 命令中心
- ActiveMQ
- Redis
- Ansible
- Webdav

## 3. 介质

| 文件名                           | 说明              |
| -------------------------------- | ----------------- |
| autodeploy-service-1.0.0.100.jar | service后台程序包 |
| autodeploy-ui-1.0.0.100.jar      | UI端程序包        |
| serv_run.sh                      | 服务端启动脚本    |
| ui_run.sh                        | UI端启动脚本      |

## 4. 启停

启动服务

```bash
sh serv_run.sh start
sh ui_run.sh start
```

停止服务

```bash
sh serv_run.sh stop
sh ui_run.sh stop
```

 重启服务

```bash
sh serv_run.sh restart
sh ui_run.sh restart
```

## 4. 参数

> serv_run.sh

| 参数名                                | 必填 | 默认值 | 说明                                                         |
| ------------------------------------- | ---- | ------ | ------------------------------------------------------------ |
| discovery.server.address              | 是   |        | 配置注册服务的地址 discovery.server.address=https://192.168.0.1:8761/eureka/ |
| server.host                           | 是   |        | 服务绑定IP                                                   |
| server.port                           | 是   |        | 服务绑定端口                                                 |
| spring.activemq.broker-url            | 是   |        | activemq服务地址，如：“tcp://192.168.55.46:61616”            |
| spring.datasource.dataSourceClassName | 是   |        | 数据源驱动，如使用mysql，则配置为“com.mysql.jdbc.Driver”，如使用oracle，则配置为“oracle.jdbc.driver.OracleDriver” |
| spring.datasource.url                 | 是   |        | 数据源地址，如使用mysql，则配置为"jdbc:mysql://192.168.55.50:3306/autodeploy?useUnicode=true&amp;characterEncoding=utf-8&autoReconnect=true"；如使用oracle，则配置为“jdbc:oracle:thin:@127.0.0.1:1521:bomc” |
| spring.datasource.username            | 是   |        | 数据库用户名                                                 |
| spring.datasource.password            | 是   |        | 数据库密码                                                   |
| spring.datasource.platform            | 是   |        | 数据库类型，如使用mysql，则配置为mysql；如使用oralce，则配置为oracle |
| spring.datasource.validation-query    | 是   |        | 如使用mysql，则配置为“select 1”；如使用oralce，则配置为“select 1 from dual” |
| spring.redis.host                     | 是   |        | redis单点服务地址ip                                          |

> ui_run.sh

| 参数名                   | 必填 | 默认值 | 说明                                                         |
| ------------------------ | ---- | ------ | ------------------------------------------------------------ |
| discovery.server.address | 是   |        | 配置注册服务的地址 discovery.server.address=https://192.168.0.1:8761/eureka/ |
| server.host              | 是   |        | 服务绑定IP                                                   |
| server.port              | 是   |        | 服务绑定端口                                                 |
| webdav.url               | 是   |        | webdav服务地址，如http://192.168.55.230                      |

