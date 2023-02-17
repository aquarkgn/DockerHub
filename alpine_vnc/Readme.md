# About
x11vnc on alpine linux

## RUN
```shell
$ docker run -p 5900:5900 gnofdocker/alpine_vnc
```

## x11vnc login user
| user   |  passwd | port |
|--------|--------:|:----:|
| alpine |  alpine | 5900 |

## 环境变量配置
| 变量            |  默认值 |               备注               |
|---------------|-----:|:------------------------------:|
| ROOT_PASSWORD | root | Set password for login as root |