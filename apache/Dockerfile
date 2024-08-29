FROM centos:7

RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-* && \
    sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-* && \
    yum -y update && yum clean all && \
    yum -y install vim curl httpd wget unzip && \
    wget -t 3 https://corretto.aws/downloads/latest/amazon-corretto-11-x64-linux-jdk.tar.gz && \
    wget -t 3 https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.79/bin/apache-tomcat-9.0.79.tar.gz && \
    mkdir -p /usr/lib/jvm/java && \
    mkdir -p /usr/local/tomcat && \
    tar -xzvf amazon-corretto-11-x64-linux-jdk.tar.gz -C /usr/lib/jvm/java --strip-components 1 && \
    tar -xzvf apache-tomcat-9.0.79.tar.gz -C /usr/local/tomcat --strip-components 1 && \
    ln -s /usr/lib/jvm/java/bin/java /usr/bin/java

COPY httpd/httpd.conf /etc/httpd/conf/
COPY httpd/httpd-proxy.conf /etc/httpd/conf.d/
COPY tomcat/server.xml /usr/local/tomcat/conf/

CMD ["/usr/sbin/apachectl", "-DFORGROUND"]