FROM ubuntu
MAINTAINER Tiago Vaz Teixeira "tiago.vt@gmail.com"


RUN apt-get update && \
    apt-get install -y --no-install-recommends software-properties-common fontconfig ttf-mscorefonts-installer vim && \
    add-apt-repository ppa:webupd8team/java

RUN \
  echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections && \
  add-apt-repository -y ppa:webupd8team/java && \
  apt-get update && \
  apt-get install -y oracle-java8-installer && \
  rm -rf /var/lib/apt/lists/* && \
  rm -rf /var/cache/oracle-jdk8-installer


 

WORKDIR /usr/local/


ENV TOMCAT_VERSION 8.5.15


# INSTALL TOMCAT
RUN wget -q http://mirror.nbtelecom.com.br/apache/tomcat/tomcat-8/v8.5.15/bin/apache-tomcat-8.5.15.tar.gz && \
    wget -qO- https://www.apache.org/dist/tomcat/tomcat-8/v8.5.15/bin/apache-tomcat-8.5.15.tar.gz.md5 | md5sum -c - && \
    tar zxf apache-tomcat-*.tar.gz

RUN rm apache-tomcat-*.tar.gz
RUN mv apache-tomcat-8.5.15 tomcat

RUN rm -rf /usr/local/tomcat/webapps/docs /usr/local/tomcat/webapps/ROOT /usr/local/tomcat/webapps/examples /usr/local/tomcat/webapps/host-manager

RUN mkdir /usr/local/tomcat/webapps/helloworld


RUN /bin/echo -e '<html> <h1>Hello World!</h1> </html>' > /usr/local/tomcat/webapps/helloworld/index.html


EXPOSE 8080
CMD ["/usr/local/tomcat/bin/catalina.sh", "run"]"]
