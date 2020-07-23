# 基础镜像使用ubuntu16.04
FROM ubuntu:18.04
ENV DEBIAN_FRONTEND=noninteractive
# 设置apt源
RUN  sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list
RUN  sed -i s@/security.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list
RUN  apt-get clean
# Install basic dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    cmake \
    git \
    wget \
    python-dev \
    python-pip \
    curl \
    vim

# Install anaconda for python 3.6
# RUN wget --quiet https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/Anaconda3-5.0.1-Linux-x86_64.sh -O ~/anaconda.sh && \
#     /bin/bash ~/anaconda.sh -b -p /opt/conda && \
#     rm ~/anaconda.sh && \
#     echo "export PATH=/opt/conda/bin:$PATH" >> ~/.bashrc


RUN apt-get install -y tzdata \
    && echo "Asia/Shanghai" > /etc/timezone \
    && rm -f /etc/localtime \
    && dpkg-reconfigure -f noninteractive tzdata

WORKDIR  /var/www
