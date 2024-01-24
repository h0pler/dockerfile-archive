FROM ubuntu:22.04

ARG DEBIAN_FRONTEND=noninteractive

ENV TZ Asia/Seoul
ENV PYTHONIOENCODING UTF-8
ENV LC_CTYPE C.UTF-8

RUN sed -i "s/http:\/\/archive.ubuntu.com/http:\/\/mirror.kakao.com/g" /etc/apt/sources.list

WORKDIR /root

SHELL ["/bin/bash", "-c"]

RUN apt-get update && apt-get upgrade -y 
RUN apt install vim git gcc ssh curl wget gdb sudo zsh libffi-dev build-essential libssl-dev libc6-i386 libc6-dbg gcc-multilib make netcat -y
RUN apt-get install -y python3 python3-pip python3-venv 

ENV NVM_DIR /root/.nvm
ENV NODE_VERSION install

RUN curl https://raw.githubusercontent.com/creationix/nvm/v0.38.0/install.sh | bash \
  && . $NVM_DIR/nvm.sh \
  && nvm install $NODE_VERSION \
  && nvm alias default $NODE_VERSION \
  && nvm use default

ENV NODE_PATH $NVM_DIR/v$NODE_VERSION/lib/node_modules
ENV PATH $NVM_DIR/versions/node/v$NODE_VERSION/bin:$PATH

RUN apt-get install -y gcc g++

RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

RUN mkdir /var/run/sshd
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
