#
# MAINTAINER        Tinding <3055521499@qq.com>
# DOCKER-VERSION    1.5.5
#
# Dockerizing Mariadb: Dockerfile for building Mariadb images
#
FROM house/centos:7.1
MAINTAINER Tinding <3055521499@qq.com>

ENV DATA_DIR /var/lib/mysql

# Install Mariadb
RUN yum install -y mariadb mariadb-server && \
    yum clean all

ADD mysqld_charset.cnf /etc/my.cnf.d/

COPY scripts /scripts
RUN chmod +x /scripts/start
RUN chmod +x /scripts/firstrun_maria

EXPOSE 3306

VOLUME ["/var/lib/mysql"]

ENTRYPOINT ["/scripts/start"]
