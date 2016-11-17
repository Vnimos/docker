############################################
# version : ipf:nginx
############################################
FROM centos:6.8

MAINTAINER vnimos 

# Install and Configure the Supervisor
RUN yum -y install python-setuptools
RUN easy_install supervisor
COPY supervisord.conf /etc/supervisor/supervisord.conf

# Install for nginx
RUN yum -y install pcre-devel openssl-devel gd-devel gcc

RUN groupadd -r nginx
RUN useradd -r -g nginx nginx
ADD nginx-1.7.10.tar.gz  /opt/ 
WORKDIR /opt/nginx-1.7.10
RUN ./configure --prefix=/usr/ --sbin-path=/usr/sbin/nginx --conf-path=/etc/nginx/nginx.conf --error-log-path=/var/log/nginx/error.log --http-log-path=/var/log/nginx/access.log --pid-path=/var/run/nginx/nginx.pid --lock-path=/var/lock/nginx.lock --user=nginx --group=nginx --with-http_ssl_module --with-http_flv_module --with-http_image_filter_module --with-http_stub_status_module --with-http_gzip_static_module --with-pcre --with-file-aio --http-client-body-temp-path=/var/tmp/nginx/client/ --http-proxy-temp-path=/var/tmp/nginx/proxy/ --http-fastcgi-temp-path=/var/tmp/nginx/fcgi/ --http-uwsgi-temp-path=/var/tmp/nginx/uwsgi --http-scgi-temp-path=/var/tmp/nginx/scgi
RUN make && make install
RUN mkdir -p /var/tmp/nginx/client/

#COPY nginx.conf /etc/nginx/nginx.conf
RUN rm -rf /opt/nginx-1.7.10

WORKDIR /root/
EXPOSE 80 
CMD ["/usr/bin/supervisord"]
