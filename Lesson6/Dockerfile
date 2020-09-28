FROM ubuntu:latest
#Prepare platform
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections
RUN apt-get update
RUN apt-get install apt-utils -y
RUN apt-get install git maven openjdk-8-jdk wget -y
RUN cd /tmp && wget https://apache-mirror.rbc.ru/pub/apache/tomcat/tomcat-8/v8.5.58/bin/apache-tomcat-8.5.58.tar.gz
RUN cd /tmp && tar -xvzf apache-tomcat-8.5.58.tar.gz
RUN cp -r /tmp/apache-tomcat-8.5.58 /usr/tomcat
#Prepare box
RUN mkdir /usr/box/ 
RUN cd /usr/box/ && git clone https://github.com/boxfuse/boxfuse-sample-java-war-hello
RUN cd /usr/box/boxfuse-sample-java-war-hello && mvn package
RUN cp /usr/box/boxfuse-sample-java-war-hello/target/hello-1.0.war /usr/tomcat/webapps
#Execute tomcat
CMD ["/usr/tomcat/bin/catalina.sh","run"]
EXPOSE 8080