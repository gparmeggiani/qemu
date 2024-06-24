FROM ubuntu:22.04

ARG USERNAME=dev

ENV DEBIAN_FRONTEND=noninteractive
ENV SHELL /bin/bash

RUN apt update && apt install -y \
    build-essential \
    libglib2.0-dev \
    libgcrypt20-dev \
    libfdt-dev \
    libpixman-1-dev \
    zlib1g-dev \
    ninja-build \
    libnfs-dev \
    libiscsi-dev \
    flex \
    bison \
    python-is-python3 \
    python3-venv \
    wget \
    curl \
    git


RUN apt-get update && apt-get install -y \
    bash-completion \
    vim \
    telnet \
    gdb \
    python3-pip

RUN pip3 install \
    qemu.qmp \
    pyserial

RUN groupadd --gid 1000 $USERNAME \
    && useradd --uid 1000 --gid 1000 -m $USERNAME \
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

RUN SNIPPET="export PROMPT_COMMAND='history -a' && export HISTFILE=/commandhistory/.bash_history" \
    && mkdir /commandhistory \
    && touch /commandhistory/.bash_history \
    && chown -R $USERNAME /commandhistory \
    && echo $SNIPPET >> "/home/$USERNAME/.bashrc"

RUN mkdir -p /home/$USERNAME/.vscode-server/e∏xtensions \
    && chown -R $USERNAME /home/$USERNAME/.vscode-server
