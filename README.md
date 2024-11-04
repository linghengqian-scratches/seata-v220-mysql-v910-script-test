# seata-v220-mysql-v910-script-test

- For https://github.com/apache/shardingsphere/issues/33523 .
- Verified under Ubuntu 22.04.4 LTS with `Docker Engine`.

```shell
docker compose up -d
docker compose logs --follow mysql
```

- The error log is as follows,

```shell
$ docker compose logs --follow mysql
mysql-1  | 2024-11-04 15:55:53+00:00 [Note] [Entrypoint]: Entrypoint script for MySQL Server 9.1.0-1.el9 started.
mysql-1  | 2024-11-04 15:55:54+00:00 [Note] [Entrypoint]: Switching to dedicated user 'mysql'
mysql-1  | 2024-11-04 15:55:54+00:00 [Note] [Entrypoint]: Entrypoint script for MySQL Server 9.1.0-1.el9 started.
mysql-1  | 2024-11-04 15:55:54+00:00 [Note] [Entrypoint]: Initializing database files
mysql-1  | 2024-11-04T15:55:54.299540Z 0 [System] [MY-015017] [Server] MySQL Server Initialization - start.
mysql-1  | 2024-11-04T15:55:54.300502Z 0 [System] [MY-013169] [Server] /usr/sbin/mysqld (mysqld 9.1.0) initializing of server in progress as process 80
mysql-1  | 2024-11-04T15:55:54.311414Z 1 [System] [MY-013576] [InnoDB] InnoDB initialization has started.
mysql-1  | 2024-11-04T15:55:54.535957Z 1 [System] [MY-013577] [InnoDB] InnoDB initialization has ended.
mysql-1  | 2024-11-04T15:55:55.935816Z 6 [Warning] [MY-010453] [Server] root@localhost is created with an empty password ! Please consider switching off the --initialize-insecure option.
mysql-1  | 2024-11-04T15:55:58.303620Z 0 [System] [MY-015018] [Server] MySQL Server Initialization - end.
mysql-1  | 2024-11-04 15:55:58+00:00 [Note] [Entrypoint]: Database files initialized
mysql-1  | 2024-11-04 15:55:58+00:00 [Note] [Entrypoint]: Starting temporary server
mysql-1  | 2024-11-04T15:55:58.450109Z 0 [System] [MY-015015] [Server] MySQL Server - start.
mysql-1  | 2024-11-04T15:55:58.628278Z 0 [System] [MY-010116] [Server] /usr/sbin/mysqld (mysqld 9.1.0) starting as process 125
mysql-1  | 2024-11-04T15:55:58.639081Z 1 [System] [MY-013576] [InnoDB] InnoDB initialization has started.
mysql-1  | 2024-11-04T15:55:58.865099Z 1 [System] [MY-013577] [InnoDB] InnoDB initialization has ended.
mysql-1  | 2024-11-04T15:55:59.143669Z 0 [Warning] [MY-010068] [Server] CA certificate ca.pem is self signed.
mysql-1  | 2024-11-04T15:55:59.143717Z 0 [System] [MY-013602] [Server] Channel mysql_main configured to support TLS. Encrypted connections are now supported for this channel.
mysql-1  | 2024-11-04T15:55:59.147037Z 0 [Warning] [MY-011810] [Server] Insecure configuration for --pid-file: Location '/var/run/mysqld' in the path is accessible to all OS users. Consider choosing a different directory.
mysql-1  | 2024-11-04T15:55:59.173088Z 0 [System] [MY-011323] [Server] X Plugin ready for connections. Socket: /var/run/mysqld/mysqlx.sock
mysql-1  | 2024-11-04T15:55:59.173180Z 0 [System] [MY-010931] [Server] /usr/sbin/mysqld: ready for connections. Version: '9.1.0'  socket: '/var/run/mysqld/mysqld.sock'  port: 0  MySQL Community Server - GPL.
mysql-1  | 2024-11-04 15:55:59+00:00 [Note] [Entrypoint]: Temporary server started.
mysql-1  | '/var/lib/mysql/mysql.sock' -> '/var/run/mysqld/mysqld.sock'
mysql-1  | Warning: Unable to load '/usr/share/zoneinfo/iso3166.tab' as time zone. Skipping it.
mysql-1  | Warning: Unable to load '/usr/share/zoneinfo/leap-seconds.list' as time zone. Skipping it.
mysql-1  | Warning: Unable to load '/usr/share/zoneinfo/leapseconds' as time zone. Skipping it.
mysql-1  | Warning: Unable to load '/usr/share/zoneinfo/tzdata.zi' as time zone. Skipping it.
mysql-1  | Warning: Unable to load '/usr/share/zoneinfo/zone.tab' as time zone. Skipping it.
mysql-1  | Warning: Unable to load '/usr/share/zoneinfo/zone1970.tab' as time zone. Skipping it.
mysql-1  | 
mysql-1  | 2024-11-04 15:56:00+00:00 [Note] [Entrypoint]: /usr/local/bin/docker-entrypoint.sh: sourcing /docker-entrypoint-initdb.d/init-user-db.sh
mysql-1  | mysql: [Warning] Using a password on the command line interface can be insecure.
mysql-1  | mysql: [Warning] Using a password on the command line interface can be insecure.
mysql-1  | mysql: [Warning] Using a password on the command line interface can be insecure.
mysql-1  | mysql: [Warning] Using a password on the command line interface can be insecure.
mysql-1  | 
mysql-1  | 2024-11-04 15:56:01+00:00 [Note] [Entrypoint]: Stopping temporary server
mysql-1  | 2024-11-04T15:56:01.155431Z 14 [System] [MY-013172] [Server] Received SHUTDOWN from user root. Shutting down mysqld (Version: 9.1.0).
mysql-1  | 2024-11-04T15:56:02.536742Z 0 [System] [MY-010910] [Server] /usr/sbin/mysqld: Shutdown complete (mysqld 9.1.0)  MySQL Community Server - GPL.
mysql-1  | 2024-11-04T15:56:02.536780Z 0 [System] [MY-015016] [Server] MySQL Server - end.
mysql-1  | 2024-11-04 15:56:03+00:00 [Note] [Entrypoint]: Temporary server stopped
mysql-1  | 
mysql-1  | 2024-11-04 15:56:03+00:00 [Note] [Entrypoint]: MySQL init process done. Ready for start up.
mysql-1  | 
mysql-1  | 2024-11-04T15:56:03.171524Z 0 [System] [MY-015015] [Server] MySQL Server - start.
mysql-1  | 2024-11-04T15:56:03.345301Z 0 [System] [MY-010116] [Server] /usr/sbin/mysqld (mysqld 9.1.0) starting as process 1
mysql-1  | 2024-11-04T15:56:03.354258Z 1 [System] [MY-013576] [InnoDB] InnoDB initialization has started.
mysql-1  | 2024-11-04T15:56:03.570584Z 1 [System] [MY-013577] [InnoDB] InnoDB initialization has ended.
mysql-1  | 2024-11-04T15:56:03.788960Z 0 [Warning] [MY-010068] [Server] CA certificate ca.pem is self signed.
mysql-1  | 2024-11-04T15:56:03.789003Z 0 [System] [MY-013602] [Server] Channel mysql_main configured to support TLS. Encrypted connections are now supported for this channel.
mysql-1  | 2024-11-04T15:56:03.793291Z 0 [Warning] [MY-011810] [Server] Insecure configuration for --pid-file: Location '/var/run/mysqld' in the path is accessible to all OS users. Consider choosing a different directory.
mysql-1  | 2024-11-04T15:56:03.826415Z 0 [System] [MY-011323] [Server] X Plugin ready for connections. Bind-address: '::' port: 33060, socket: /var/run/mysqld/mysqlx.sock
mysql-1  | 2024-11-04T15:56:03.826481Z 0 [System] [MY-010931] [Server] /usr/sbin/mysqld: ready for connections. Version: '9.1.0'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server - GPL.
```