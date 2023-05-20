# syntax=docker/dockerfile:1.3-labs
FROM ubuntu:20.04

ARG DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y \
    openssh-server \
    build-essential \
    curl \
    git \
    git-lfs \
    jq \
    bash \
    valgrind \
    cppcheck \
    lcov \
    texinfo \
    gitlab-runner \
    cmake \
    googletest \
    check \
    clang-format \
 && rm -rf /var/lib/apt/lists/*

RUN printf 'qwerty\nqwerty\n' | passwd root
RUN mkdir -p /run/sshd
RUN mkdir -p /root/.ssh && chmod 700 /root/.ssh && touch /root/.ssh/known_hosts
COPY keys/id_rsa.pub /root/.ssh
RUN cat /root/.ssh/id_rsa.pub >> /root/.ssh/authorized_keys
RUN chmod 600 /root/.ssh/authorized_keys && rm -rf /root/.ssh/id_rsa.pub
RUN ssh-keygen -A

WORKDIR "/root"

ENTRYPOINT ["/usr/sbin/sshd", "-D"]