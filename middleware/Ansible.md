# Ansible部署手册

> 作者 刘喜男

## 1 前提

- 查看python版本

  python -V 

  版本必须在2.6以上

## 2 介质

| 文件名      | 说明                      |
| ----------- | ------------------------- |
| redhat6.zip | redhat6下ansible离线yum源 |
| redhat7.zip | redhat7下ansible离线yum源 |

## 3 安装

以redhat6举例,使用root用户操作，相关zip包在程序包ansible文件夹中

1. 根据系统版本将相应版本的本地源上传至目标机

   > redhat6.zip

2. 解压redhat6.zip至部署目录

   ```shell
   unzip redhat6.zip -d /opt/BOCO
   ```

3. 移动BOCO-base.repo BOCO-epel.repo至/etc/yum.repos.d/

   ```shell
   cd /opt/BOCO/BOCO-repo
   mv BOCO-base.repo BOCO-epel.repo /etc/yum.repos.d/
   ```

4. 建立本地源缓存（备份本地原有yum文件）

   ```shell
   yum makecache
   ```

5. 安装ansible

   ```shell
   yum install ansible
   ```

6. 查看安装状态

   ```shell
   ansible --version
   ```
