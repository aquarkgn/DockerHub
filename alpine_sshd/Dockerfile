FROM alpine:latest

LABEL image.github.author="https://github.com/aquarkgn"

# set TIME_ZONE
ENV TZ Asia/Shanghai
ENV TIME_ZONE=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TIME_ZONE /etc/localtime && echo $TIME_ZONE > /etc/timezone && \
    sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories && \
    apk add tzdata && \
    cp /usr/share/zoneinfo/${TZ} /etc/localtime && \
    echo ${TZ} > /etc/timezone

# config system root passwd:root
ENV ROOT_PASSWORD root
RUN echo "root:${ROOT_PASSWORD}" | chpasswd

# install openssh
RUN apk --update add --no-cache openssh \
    && sed -i s/#PermitRootLogin.*/PermitRootLogin\ yes/ /etc/ssh/sshd_config \
    && rm -rf /var/cache/apk/* /tmp/*

# copy file
COPY docker-entrypoint.sh /usr/local/bin
RUN chmod +x /usr/local/bin/docker-entrypoint.sh

# port 22
EXPOSE 22/tcp

ENTRYPOINT ["docker-entrypoint.sh"]
