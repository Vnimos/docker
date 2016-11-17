############################################
# version : ipf:redis
############################################
FROM centos:6.8

MAINTAINER vnimos 

# Install and Configure the Supervisor
RUN yum -y install python-setuptools
RUN easy_install supervisor
COPY supervisord.conf /etc/supervisor/supervisord.conf

# Install for redis
ADD redis-3.0.0.tar.gz /opt/
WORKDIR /opt/redis-3.0.0
RUN yum -y install gcc
RUN make MALLOC=libc && make install
RUN mkdir -p /etc/redis/dump
COPY redis7381.conf /etc/redis/

WORKDIR /root/
EXPOSE 7381
CMD ["/usr/bin/supervisord"]
