FROM tomcat:8-jre11

RUN rm -rf /var/local/tomcat/webapps/*

COPY target/*.war /var/local/tomcat/webapps/ROOT.war

CMD [ "catalina.sh", "run" ]
