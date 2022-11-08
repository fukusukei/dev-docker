FROM debian:bullseye-20221024

ARG USERNAME
ARG GROUPNAME
ARG HTTPS_PROXY
ARG HTTPS_PROXY
ARG USERID
ARG GROUPID

ENV LANG ja_JP.UTF-8
ENV LC_CTYPE ja_JP.UTF-8
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -y \
	&& apt-get install -y curl git sudo locales build-essential \
       libwebkit2gtk-4.0-dev libssl-dev libgtk-3-dev libayatana-appindicator3-dev librsvg2-dev \
	&& apt-get clean \
	&& rm -fr /var/lib/apt/lists/* 

RUN locale-gen ja_JP.UTF-8 \
    && localedef -f UTF-8 -i ja_JP ja_JP.utf8
    
RUN groupadd -g ${GROUPID} ${GROUPNAME} \
    && useradd -d /home/${USERNAME} -m -s /bin/bash -u ${USERID} -g ${GROUPID} ${USERNAME} \
    && gpasswd -a ${USERNAME} sudo \
    && echo "${USERNAME} ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers.d/${USERNAME}

USER ${USERID}

WORKDIR /home/${USERNAME}
