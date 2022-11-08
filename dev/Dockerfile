FROM ubuntu:20.04

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
	&& apt-get install -y curl git sudo python build-essential locales language-pack-ja-base language-pack-ja iproute2 python3-pip \
	&& apt-get clean \
	&& rm -fr /var/lib/apt/lists/* \
    && locale-gen ja_JP.UTF-8 \
    && localedef -f UTF-8 -i ja_JP ja_JP.utf8 \
    && groupadd -g ${GROUPID} ${GROUPNAME} \
    && useradd -d /home/${USERNAME} -m -s /bin/bash -u ${USERID} -g ${GROUPID} ${USERNAME} \
    && gpasswd -a ${USERNAME} sudo \
    && echo "${USERNAME} ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers.d/${USERNAME}

USER ${USERID}

WORKDIR /home/${USERNAME}
