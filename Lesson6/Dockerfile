FROM ubuntu:latest
#Prepare platform
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections
RUN apt-get update
RUN apt-get install apt-utils -y
RUN apt-get install git maven openjdk-8-jdk wget -y
WORKDIR /tmp
RUN wget https://apache-mirror.rbc.ru/pub/apache/tomcat/tomcat-8/v8.5.58/bin/apache-tomcat-8.5.58.tar.gz
RUN tar -xvzf apache-tomcat-8.5.58.tar.gz
RUN cp -r apache-tomcat-8.5.58 /usr/tomcat
#Prepare box
WORKDIR /usr/box 
RUN git clone https://github.com/boxfuse/boxfuse-sample-java-war-hello
WORKDIR /usr/box/boxfuse-sample-java-war-hello
RUN mvn package
RUN cp ./target/hello-1.0.war /usr/tomcat/webapps
#Execute tomcat
EXPOSE 8080
CMD ["/usr/tomcat/bin/catalina.sh","run"]