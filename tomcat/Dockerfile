############################################
# version : ipf:tomcat
############################################
FROM centos:6.8

MAINTAINER vnimos 

# Configure the environment
ENV LANG en_US.UTF-8

# Install and Configure the Supervisor
RUN yum -y install python-setuptools
RUN easy_install supervisor
COPY supervisord.conf /etc/supervisor/supervisord.conf

# Install and Configure the tomcat
ADD apache-tomcat-7.0.56.tar.gz jdk-7u79-linux-x64.tar.gz  /opt/ 

# Configure for jdk
ENV JAVA_HOME /opt/jdk1.7.0_79
ENV JRE_HOME /opt/jdk1.7.0_79/jre
ENV PATH /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/opt/jdk1.7.0_79/bin:/opt/jdk1.7.0_79/jre/bin

EXPOSE 8080 
CMD ["/usr/bin/supervisord"]
