FROM centos:7.9.2009
ENV TOMCAT_VERSION 8.0.50

WORKDIR /work

COPY nginx.repo /etc/yum.repos.d/

RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-* && \
    sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-* && \
    yum -y install sudo vim nginx java-1.8.0-openjdk && \
    curl -O https://archive.apache.org/dist/tomcat/tomcat-8/v${TOMCAT_VERSION}/bin/apache-tomcat-${TOMCAT_VERSION}.tar.gz && \
    tar -xzvf apache-tomcat-${TOMCAT_VERSION}.tar.gz && \
    mv apache-tomcat-${TOMCAT_VERSION} /opt && \
    ln -s /opt/apache-tomcat-${TOMCAT_VERSION} /opt/tomcat

COPY tomcat/server.xml /opt/tomcat/conf/
COPY nginx.conf /etc/nginx/

CMD ["sh", "/opt/tomcat/bin/startup.sh", "&&", "nginx", "-g", "daemon off;"]
