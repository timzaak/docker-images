# docker-images
主要是因为网络原因才诞生次项目。
### Feature

1. 基于 Github Action 构建 docker image
2. 基于 Github Action 迁移 docker Image

## 现有Docker
### ElsatciSearch
elasticsearch: 7.17.2, 补充了 IK、ANSJ 插件，USER 切换成 ROOT，ANSJ 是我自行打包。 镜像没啥问题，就是 ANSJ 的配置不是开箱可用的，必须二次更改。
### bakup
用于备份mysql、pg数据，并将数据推送到 OSS。 最好配上 uptime-kuma 做监控。
```sh
docker run -v -d crontab_config_file:/etc/crontab -v oss_config_file:~/.ossutilconfig -v /tmp:/back bakup:1.0
```
备份脚本exmample:
```sh
#!/bin/sh

now=$(date +"%s_%Y-%m-%d")
out_path="/backup/${now}_${MYSQL_DATABASE}.sql.gz"
/usr/bin/mysqldump --opt -h ${MYSQL_HOST} -u ${MYSQL_USER} -p${MYSQL_PASSWORD} ${MYSQL_DATABASE} | gzip ${out_path}  && \
ossutil cp ${out_path} oss://${BUCKET}/mysql/  && \
curl -fsS -m 10 --retry 3 -o /dev/null https://hc-ping.com/your-uuid-here


/usr/bin/pg_dump -U postgres ${PG_DATABASE} | gzip > "/backup/${now}_pg_${PG_DATABASE}_backup.sql.gz"

```
