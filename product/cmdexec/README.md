# 命令中心

> 作者 刘喜男

## 1. 环境

- JDK1.8+

## 2. 依赖服务

- [ActiveMQ](../../middleware/ActiveMQ.md)
- [Ansible](../../middleware/Ansible.md)

## 3. 介质

| 文件名                   | 说明           |
| ------------------------ | -------------- |
| cmdexeu-1.0.0.100.tar.gz | 命令中心压缩包 |

## 4. 解压

```bash
tar -xzvf cmdexeu-1.0.0.100.tar.gz
```

## 5. 启停

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

## 6. 参数

> run.sh脚本中，只需配置表格中的参数

| 参数名                     | 必填 | 默认值 | 说明                                                         |
| -------------------------- | ---- | ------ | ------------------------------------------------------------ |
| eureka.client.enabled      | 否   | true   | 是否依赖认证服务，默认依赖                                   |
| discovery.server.address   | 是   |        | 配置注册服务的地址 discovery.server.address=<https://192.168.0.1:8761/eureka/> |
| server.host                | 是   |        | 服务绑定IP                                                   |
| server.port                | 是   |        | 服务绑定端口                                                 |
| spring.activemq.broker-url | 是   |        | activemq服务地址，如：“tcp://192.168.55.46:61616”            |
