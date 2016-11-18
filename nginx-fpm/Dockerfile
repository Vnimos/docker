############################################
# version : ipf:nginx
############################################
FROM centos:nginx
MAINTAINER vnimos 

# Configure the environment
ENV LANG en_US.UTF-8

# Install and Configure the Supervisor
COPY supervisord.conf /etc/supervisor/supervisord.conf

# Install for php-fpm
RUN yum -y install php-mysql php-fpm php-mbstring && yum clean all
COPY fastcgi_params /etc/nginx/fastcgi_params

EXPOSE 80 
CMD ["/usr/bin/supervisord"]
