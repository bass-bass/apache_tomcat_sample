## Docker + Apache/Nginx + Tomcatによる環境構築テンプレート

## 構築手順

### apache
1. `cd apache`
2. `docker-compose up -d --build`
3. `docker cp sample.war apache-container:/usr/local/tomcat/webapps/sample.war`
4. `docker exec app sh /usr/local/tomcat/bin/startup.sh`
5. http://localhost:8080/sample

### nginx
1. `cd nginx`
2. `docker-compose up -d --build`
3. `docker cp sample.war nginx-container:/usr/local/tomcat/webapps/sample.war`
5. http://localhost:8080/sample
