# 数据库
## MariaDB
[mariadb-docker-official-1]: https://hub.docker.com/_/mariadb "mariadb --- Docker Official Images"
[phpmyadmin-docker-official-1]: https://hub.docker.com/r/phpmyadmin/phpmyadmin "Official phpMyAdmin Docker image"
[xampp-docker-1]: https://hub.docker.com/r/tomsik68/xampp "tomsik68/xampp"

- [mariadb --- Docker Official Images][mariadb-docker-official-1]
- [Official phpMyAdmin Docker image][phpmyadmin-docker-official-1]
- [tomsik68/xampp][xampp-docker-1]: This image is intended for PHP+MySQL development. For convenience, it also runs SSH server to connect to. **Both MySQL and phpmyadmin use default XAMPP password**.

启动`mariadb`数据库:
```shell
$ docker run --name mariadb -v /data/db/mariadb:/var/lib/mysql --env MYSQL_ROOT_PASSWORD=mariadb -d mariadb
```
查询`mariadb`网络地址：
```shell
docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' mariadb
```

运行`phpMyAdmin`，管理`mariadb`的网页服务器：
```shell
$ docker run --name mariadbadmin -d --link mariadb:db -p 8080:80 phpmyadmin/phpmyadmin
```
网页地址：[http://localhost:8080](http://localhost:8080)

## Postgresql
[postgres-docker-official-1]: https://hub.docker.com/_/postgres "Postgres --- Docker official images"
[pgadmin-docker-1]: https://hub.docker.com/r/dpage/pgadmin4 "dpage/pgadmin4"

- [Postgres --- Docker official images][postgres-docker-official-1]
- [dpage/pgadmin4][pgadmin-docker-1]

## Monitors
[navicat-docker]: https://hub.docker.com/r/navicat/navicatmonitor "navicat/navicatmonitor"

- [navicat/navicatmonitor][navicat-docker]

graph LR;   A-->B   B-->C   C-->D   D-->A