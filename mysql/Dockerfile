############################################
# version : gschool:mysql
############################################
FROM centos:6.8

MAINTAINER vnimos

# Configure the environment
ENV LANG en_US.UTF-8

# Install and Configure the Supervisor
RUN yum -y install python-setuptools
RUN easy_install supervisor
COPY supervisord.conf /etc/supervisor/supervisord.conf

# Install for mysql-server
COPY mysql.repo /etc/yum.repos.d/mysql.repo
RUN yum -y install mysql-community-server
#RUN service mysqld start && \
#    mysql -e "grant all privileges on *.* to 'root'@'%' identified by 'Gillion168';" && \  
#    mysql -e "grant all privileges on *.* to 'root'@'localhost' identified by 'Gillion168';" 
RUN yum clean all

VOLUME ["/var/lib/mysql"]
EXPOSE 3306
CMD ["/usr/bin/supervisord"]
