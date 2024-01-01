FROM ubuntu:22.04

ARG DEBIAN_FRONTEND=noninteractive

ENV TZ Asia/Seoul
ENV PYTHONIOENCODING UTF-8
ENV LC_CTYPE C.UTF-8

WORKDIR /root

RUN apt update && apt install -y netcat
RUN apt install -y vim git gcc ssh curl wget gdb sudo zsh python3 python3-pip python3-venv libffi-dev build-essential libssl-dev libc6-i386 libc6-dbg gcc-multilib make

RUN dpkg --add-architecture i386
RUN apt update
RUN apt install -y libc6:i386

RUN python3 -m pip install --upgrade pip