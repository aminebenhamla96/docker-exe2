#!/bin/bash
docker build -t tomcat:v1 .
docker history ae20a71d367c (EXPOSE 8080)
docker inspect ae20a71d367c 'ExposedPorts'
docker run -d --name tomcatcont -p 20200:8080 tomcat:v1
vi /opt/tomcat/conf/tomcat-users.xml (<user username="logwire" password="docker" roles="standard,manager-script" />)
docker image tag tomcat:v1 aminebenhamla/tomcat
docker push aminebenhamla/tomcat
