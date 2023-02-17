# mysql
> [hub_docker_mysql]https://hub.docker.com/_/mysql

## RUN
```shell
$ docker run -p 3306:3306 --env MYSQL_ROOT_PASSWORD=root mysql:latest
```

## docker-compose
```shell
$ docker-compose up -d
```

## 环境变量配置
| 变量            |  默认值 |               备注               |
|---------------|-----:|:------------------------------:|
| MYSQL_ROOT_PASSWORD | root | Set password for login as root |

## 目录和文件映射
当前目录文件夹   ./data:/var/lib/mysql
当前目录配置文件 ./my.cnf:/etc/my.cnf

## 端口映射
主机 3306 ： 容器 3306
