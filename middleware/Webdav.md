# Webdav部署手册

> 作者 刘喜男

### 1 介质

| 文件名        | 说明           |
| ------------- | -------------- |
| httpd-yum.tgz | httpd离线yum源 |

### 2 安装

1. 将httpd依赖yum源安装包（httpd-yum.tgz）上传到服务器，并进行解压

   ```shell
   tar -zxvf httpd-yum.tgz -C /root/
   ```

2. 安装

   ```shell
   cd /root/yum/local
   rpm -ivh createrepo-0.9.9-28.el7.noarch.rpm
   ```

3. 备份/etc/yum.repos.d/下所有文件

4. 添加文件/etc/yum.repos.d/CentOS-Local.repo

   ```shell
   vim /etc/yum.repos.d/CentOS-Local.repo
   ```

5. 写入以下内容

   ```shell
   [Local]
   name=Local Yum
   baseurl=file:///root/yum/
   gpgcheck=1
   gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
   enabled=1
   ```

6. 生成yum源的索引及缓存

   ```shell
   createrepo /root/yum
   yum makecache
   ```

7. 执行命令安装httpd服务

   ```shell
   yum install httpd
   ```

8. 启动httpd

   ```shell
   systemctl start httpd
   ```

9. 查看httpd版本

   ```shell
   Httpd -v
   ```



### 3 配置webdav

1. 打开配置文件httpd.conf

   ```shell
   vim /etc/httpd/conf/httpd.conf
   ```

2. 在文件最后加入webdav配置文件路径

   ```shell
   Include conf/webdav.conf
   ```

3. 创建webdav配置文件

   ```shell
   vim /etc/httpd/conf/webdav.conf
   ```

4. 编写webdav配置文件内容

   ```shell
   <IfModule mod_dav.c>
   LimitXMLRequestBody 131072
   Alias /webdav "/opt/www/webdav"
   <Directory /opt/www/webdav>
       Dav On
       Options +Indexes
       IndexOptions FancyIndexing
       AddDefaultCharset UTF-8
       AuthType Basic
       AuthName "WebDAV Server"
       AuthUserFile /etc/httpd/webdav.users.pwd
       Require valid-user
       Order allow,deny
       Allow from all
       Require all granted
   </Directory>
   ```

5. 创建目录

   ```shell
   mkdir -pv /opt/www/webdav
   chown apache:apache /opt/www/webdav
   ```


