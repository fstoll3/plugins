FROM ubuntu:latest

MAINTAINER Reinhard Pointner <rednoah@filebot.net>


RUN apt-get update \
 && apt-get install -y --no-install-recommends openjdk-11-jre-headless libjna-jni libmediainfo0v5 libchromaprint-tools p7zip-full p7zip-rar gnupg1 curl file inotify-tools \
 && rm -rvf /var/lib/apt/lists/*


RUN apt-key adv --fetch-keys https://raw.githubusercontent.com/filebot/plugins/master/gpg/maintainer.pub  \
 && echo "deb [arch=amd64] https://get.filebot.net/deb/ stable main" > /etc/apt/sources.list.d/filebot.list \
 && apt-get update \
 && apt-get install -y --no-install-recommends filebot \
 && rm -rvf /var/lib/apt/lists/*


VOLUME /data
VOLUME /volume1


ENV HOME /data
ENV LANG C.UTF-8
ENV FILEBOT_OPTS "-Dapplication.deployment=docker -Duser.home=$HOME"


WORKDIR /volume1


ENTRYPOINT ["filebot"]
