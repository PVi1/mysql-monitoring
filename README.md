# Mysql/Mariadb monitoring

## Description

Yet another module for mysql monitoring
Supports multiple instances and multi-master replication with low-level discovery
Please, ensure that you are using mysqld that supports multi-source replication, e.g. mysql 5.7 or mariadb 10+

## Requirements
- Store MySQL credentials in /etc/zabbix/.my.cnf
```
[mysql]
user=zabbix
password=zabbix_pass
[mysqladmin]
user=zabbix
password=zabbix_pass
```

## Installing
- Create user for monitoring, e.g.
```
GRANT PROCESS, REPLICATION CLIENT ON *.* TO 'zabbix'@'localhost' IDENTIFIED BY 'SECRETPASS'
```
- Put mm.sh into /etc/zabbix folder
- Put mm.items into /etc/zabbix folder
- Run 
```
chmod +x /etc/zabbix/mm.sh
```
- Put mm.conf into /etc/zabbix/zabbix_agentd.conf.d/
- Uncomment & set Server for Active checks in zabbix_agentd.conf
- Check if Hostname value in zabbix_agentd.conf and /etc/hosts matches
- Import template to zabbix - mm.xml
- Apply “Template App Mysql Monitoring” template to host
