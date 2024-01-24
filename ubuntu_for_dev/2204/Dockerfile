FROM ubuntu:22.04

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ Asia/Seoul
ENV PYTHONIOENCODING UTF-8
ENV LC_CTYPE C.UTF-8
RUN sed -i "s/http:\/\/archive.ubuntu.com/http:\/\/mirror.kakao.com/g" /etc/apt/sources.list
WORKDIR /root
SHELL ["/bin/bash", "-c"]

RUN apt-get update && apt-get upgrade -y 
RUN apt-get install vim git gcc ssh curl wget gdb sudo zsh libffi-dev build-essential libssl-dev libc6-i386 libc6-dbg gcc-multilib make netcat -y
RUN apt-get install tmux jq xz-utils bash-completion htop dstat patch ca-certificates locales bsdutils coreutils util-linux -y
RUN apt-get install -y python3 python3-pip python3-venv 
RUN apt-get -y autoclean && apt-get -y autoremove && apt-get -y clean && rm -rf /var/lib/apt/lists/*

RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
RUN source .bashrc 
RUN nvm install node
RUN nvm use node

RUN apt-get install -y gcc g++

RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh