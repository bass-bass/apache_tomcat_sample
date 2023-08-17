## Docker + Apache + Tomcatによる環境構築テンプレート

## 構築手順
1. `docker-compose up -d --build`
2. `docker cp sample.war tomcat-container:/usr/local/tomcat/webapps/sample.war`
3. `docker exec app sh /usr/local/tomcat/bin/startup.sh`
4. http://localhost:8080/sample
