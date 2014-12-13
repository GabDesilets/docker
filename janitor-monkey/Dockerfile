# Need to put SimianArmy configs in this directory along w/ AWS creds
FROM ubuntu:12.04

MAINTAINER Matt Smith

RUN apt-get install -y python-setuptools python-dev build-essential
RUN easy_install pip
RUN apt-get install -y git openjdk-6-jdk
RUN git clone https://github.com/Netflix/SimianArmy
RUN pip install awscli
RUN apt-get install -y vim

ENV JAVA_HOME /usr/lib/jvm/java-6-openjdk-amd64
RUN cd /SimianArmy && ./gradlew build
ADD credentials /root/.aws/credentials
ADD client.properties /SimianArmy/src/main/resources/
ADD janitor.properties /SimianArmy/src/main/resources/
ADD simianarmy.properties /SimianArmy/src/main/resources/
ADD volumeTagging.properties /SimianArmy/src/main/resources/

CMD cd /SimianArmy && ./gradlew jettyRun
