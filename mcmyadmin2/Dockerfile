# BUILD-USING:    docker build -t buildingbananas/mcmyadmin2 .
# DEV-USING       docker run --rm -i -t -P -h=mcmyadmin2 --name=mcmyadmin2-dev --entrypoint=/bin/bash buildingbananas/mcmyadmin2 -s
# TEST-USING:     docker run --rm -i -t -P -h=mcmyadmin2 --name=mcmyadmin2-test buildingbananas/mcmyadmin2 /bin/bash
# RUN-USING:      docker run -d -p 8080:8080 -h=mcmyadmin2 --name=mcmyadmin2 -e password=test buildingbananas/mcmyadmin2


# McMyAdmin2 build instructions found at http://www.mcmyadmin.com/#/download
FROM ubuntu:latest
MAINTAINER Will Weaver <monkey@buildingbananas.com>

RUN apt-get update -y
RUN apt-get upgrade -y
RUN apt-get install -y wget unzip zip openjdk-7-jre mono-complete

RUN useradd -m -s /bin/bash minecraft

WORKDIR /usr/local
RUN wget http://mcmyadmin.com/Downloads/etc.zip
RUN unzip etc.zip; rm etc.zip

WORKDIR /home/minecraft/McMyAdmin
RUN chown -R minecraft:minecraft /home/minecraft

USER minecraft

RUN wget http://mcmyadmin.com/Downloads/MCMA2_glibc26_2.zip
RUN unzip MCMA2_glibc26_2.zip; rm MCMA2_glibc26_2.zip
RUN ./MCMA2_Linux_x86_64 -setpass passwd -configonly -nonotice

CMD ./MCMA2_Linux_x86_64

