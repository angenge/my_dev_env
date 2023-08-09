FROM nvidia/cuda:11.7.0-base-ubuntu20.04
LABEL maintainer="cmos"
ENV TZ "Zsia/Shanghai"
ENV DEBIAN_FRONTEND=noninteractive
ENV PATH="/root/miniconda3/bin:${PATH}"

RUN rm -rf /etc/apt/sources.list && \
    rm -rf /etc/apt/sources.list.d/*

ADD sources.list /etc/apt/sources.list
ADD vimrc /root/.vimrc
ADD condarc /root/.condarc

RUN apt-get update && \
    apt-get install -y build-essential && \
    apt-get install -y vim wget curl && \
    apt-get install -y language-pack-zh* && \
    apt-get install -y fonts-droid-fallback ttf-wqy-zenhei ttf-wqy-microhei fonts-arphic-ukai fonts-arphic-uming && \
    apt-get install -y git-all && \
    apt-get clean all && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    wget --no-check-certificate https://mirrors.tuna.tsinghua.edu.cn/anaconda/miniconda/Miniconda3-py310_23.3.1-0-Linux-x86_64.sh && \
    sh Miniconda3-py310_23.3.1-0-Linux-x86_64.sh -b && \
    rm Miniconda3-py310_23.3.1-0-Linux-x86_64.sh && \
    conda install -y cmake make

WORKDIR /root/
