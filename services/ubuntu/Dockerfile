# 基础镜像使用ubuntu16.04
FROM ubuntu:18.04

# 设置apt源

RUN  sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list
RUN  apt-get clean

# 安装 vim ping ifconfig ip tcpdump nc curl iptables python 常用命令
RUN apt-get -y update && apt-get -y install vim iputils-ping net-tools curl

RUN apt-get install -y tzdata \
    && echo "Asia/Shanghai" > /etc/timezone \
    && rm -f /etc/localtime \
    && dpkg-reconfigure -f noninteractive tzdata

WORKDIR  /var/www
