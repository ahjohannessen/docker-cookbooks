FROM ubuntu:precise
MAINTAINER Alex Henning Johannessen < ahjohannessen [at] gmail {dot} com>

# Ensure the package repository is up to date
RUN echo "deb http://archive.ubuntu.com/ubuntu precise main universe" > /etc/apt/sources.list

# Install Java 7 Oracle JDK
RUN apt-get update && apt-get -y install python-software-properties
RUN add-apt-repository ppa:webupd8team/java
RUN apt-get update && apt-get -y upgrade
RUN echo oracle-java7-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections
RUN apt-get -y install oracle-java7-installer && apt-get clean
RUN update-alternatives --display java 
RUN echo "JAVA_HOME=/usr/lib/jvm/java-7-oracle" >> /etc/environment

# Install Utils
RUN apt-get -y install git curl && apt-get clean

# Install SBT
RUN curl -O http://repo.scala-sbt.org/scalasbt/sbt-native-packages/org/scala-sbt/sbt/0.13.0/sbt.deb
RUN dpkg --install sbt.deb
RUN rm sbt.deb