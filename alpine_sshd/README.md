# alpine-sshd

## RUN
```shell
$ docker run -p 2222:22 --env ROOT_PASSWORD=MyRootPW123 gnofdocker/alpine_sshd
```

## 环境变量配置
| 变量            |  默认值 |               备注               |
|---------------|-----:|:------------------------------:|
| ROOT_PASSWORD | root | Set password for login as root |

## root pwd default
ROOT_PASSWORD:root