FROM ubuntu:latest
#Prepare platform
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections
RUN apt-get update
RUN apt-get install apt-utils -y
RUN apt-get install git maven openjdk-8-jdk wget -y
RUN cd /tmp && wget https://apache-mirror.rbc.ru/pub/apache/tomcat/tomcat-8/v8.5.58/bin/apache-tomcat-8.5.58.tar.gz
RUN cd /tmp && tar -xvzf apache-tomcat-8.5.58.tar.gz
RUN cp -r /tmp/apache-tomcat-8.5.58 /usr/tomcat