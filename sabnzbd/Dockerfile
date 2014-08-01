# BUILD-USING:    docker build -t buildingbananas/sabnzbd .
# TEST-USING:     docker run --rm -i -t -h=sabnzbd --name=sabnzbd buildingbananas/sabnzbd /bin/bash
# INIT-USING:
# RUN-USING:      docker run -d -h=sabnzbd --name=sabnzbd buildingbananas/sabnzbd

FROM base/archlinux
MAINTAINER Will Weaver <monkey@buildingbananas.com>

RUN pacman -Sy --noconfirm
RUN pacman -S --noconfirm python2-pyopenssl git
RUN pacman -S --noconfirm python2-cheetah
RUN pacman -S --noconfirm par2cmdline unzip unrar

RUN git clone https://github.com/sabnzbd/sabnzbd.git /sabnzbd

VOLUME /config

expose 8080

ENTRYPOINT python2 /sabnzbd/SABnzbd.py 
CMD --config-file /config/sabnzbd/ --server :8080
