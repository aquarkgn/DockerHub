FROM alpine:latest

LABEL image.github.author="https://github.com/aquarkgn"

ENV ENV=$HOME/.ashrc
ENV XRES=1280x800x24

# set TIME_ZONE
ENV TZ Asia/Shanghai
ENV TIME_ZONE=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TIME_ZONE /etc/localtime && echo $TIME_ZONE > /etc/timezone && \
    sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories && \
    apk add tzdata && \
    cp /usr/share/zoneinfo/${TZ} /etc/localtime && \
    echo ${TZ} > /etc/timezone

# install x11vnc
RUN apk update && apk upgrade
RUN apk add sudo supervisor
RUN apk add xvfb x11vnc
RUN apk add xfce4 xfce4-terminal xfce4-xkb-plugin mousepad adwaita-icon-theme
RUN rm -rf /var/cache/apk/* /tmp/*

# set user
ENV ROOT_PASSWORD root
RUN echo "root:${ROOT_PASSWORD}" | chpasswd
RUN addgroup alpine  \
    && adduser -G alpine -s /bin/sh -D alpine \
    && echo "alpine:alpine" | chpasswd \
    && echo "alpine ALL=(ALL) ALL" >> /etc/sudoers \
    && chown -R alpine:alpine /home/alpine/

# vnc config
ADD etc /etc
ADD config/xfce4/terminal/terminalrc /home/alpine/.config/xfce4/terminal/terminalrc
ADD config/xfce4/xfconf/xfce-perchannel-xml/xfce4-desktop.xml /home/alpine/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-desktop.xml

WORKDIR /home/alpine

EXPOSE 5900

CMD ["/usr/bin/supervisord","-c","/etc/supervisord.conf"]