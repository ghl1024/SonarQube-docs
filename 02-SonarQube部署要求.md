# SonarQube部署要求


## 先决条件

唯一先决条件是在计算机中安装jdk8，可以是Oracle JRE 8 或者 OpenJDK8。在MacOs系统中强烈建议安装JDK而不是JRE，因为JRE安装完成后无法正确完全设置JAVA环境。



## 硬件要求
- 2GB内存以上，1GB可用内存。
- 磁盘空间量取决于您使用SonarQube分析的代码量，20GB+。
- 必须安装在具有出色读写性能的硬盘上，因ES索引，运行时大量IO操作。



## 支持的平台

### JAVA
- Oracle JRE 8 
- OpenJDK 8
- 不支持IBMJRE、GCJ、Oracle JRockit。

### 数据库
- PostgreSQL 8、9
- MS SQLServer 2014 (MSSQL Server 12.0)
- MS SQLServer 2016 (MSSQL Server 13.0)
- Oracle 11G 12C  XE Editions
- MySQL5.6 5.7 
  - 必须配置UTF-8字符集
  - 只支持InnoDB存储引擎，不支持MyISAM
  - 只能和mysql-connector-java jar支持

### 浏览器
- IE 11
- Edge Latest
- FireFox Latest
- Chrome Latest
- Opera 未测试
- Safari Latest

## Linux操作系统注意
### 不能以root用户直接运行sonarqube。
### 设置内核参数
```
#临时
sysctl -w vm.max_map_count=262144
sysctl -w fs.file-max=65536
ulimit -n 65536
ulimit -u 2048


#永久
 /etc/sysctl.d/99-sonarqube.conf
 /etc/limits.d/99-sonarqube.conf
 
 
sonarqube   -   nofile   65536
sonarqube   -   nproc    2048
```
