# 
# MAINTAINER        TinDing<3055521499@qq.com>
# DOCKER-VERSION    1.7.1
#
# Dockerizing CentOS7: Dockerfile for building CentOS images
#Thank for 
FROM       centos:7.1.1503
MAINTAINER Tinding <3055521499@qq.com>

RUN cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
#ENV TZ "Asia/Shanghai"
ENV TERM xterm

ADD aliyun-mirror.repo /etc/yum.repos.d/CentOS-Base.repo
ADD aliyun-epel.repo /etc/yum.repos.d/epel.repo


RUN yum install -y curl wget tar bzip2 unzip vim-enhanced passwd sudo yum-utils hostname net-tools rsync man && \
    yum install -y gcc gcc-c++ git make automake cmake patch logrotate python-devel libpng-devel libjpeg-devel && \
    yum install -y --enablerepo=epel pwgen python-pip && \
    yum clean all

RUN pip install supervisor
ADD supervisord.conf /etc/supervisord.conf

RUN mkdir -p /etc/supervisor.conf.d && \
    mkdir -p /var/log/supervisor

EXPOSE 22

ENTRYPOINT ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisord.conf"]
