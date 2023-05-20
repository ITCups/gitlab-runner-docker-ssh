# syntax=docker/dockerfile:1.3-labs
FROM alpine

RUN echo -e 'https://dl-cdn.alpinelinux.org/alpine/v3.16/main/\n\
https://dl-cdn.alpinelinux.org/alpine/v3.16/community/\n\
https://dl-cdn.alpinelinux.org/alpine/edge/testing/\n'\
>> /etc/apk/repositories

RUN apk --no-cache --upgrade add \
    openssh \
    openssh-server \
    git \
    git-lfs \
    curl \
    jq \
    bash \
	  build-base \
    python3 \
    valgrind \
    cppcheck \
	  alpine-sdk \
	  clang15-extra-tools \
	  pcre-dev \
	  lcov \
	  zsh \
    texinfo \
    gitlab-runner \
    cmake \
    gtest \
    gtest-dev \
    check-dev \
    subunit-dev
    # qt6-qtbase-dev

RUN printf 'qwerty\nqwerty\n' | passwd root

RUN mkdir -p /root/.ssh && chmod 700 /root/.ssh && touch /root/.ssh/known_hosts
COPY keys/id_rsa.pub /root/.ssh
RUN cat /root/.ssh/id_rsa.pub >> /root/.ssh/authorized_keys
RUN chmod 600 /root/.ssh/authorized_keys && rm -rf /root/.ssh/id_rsa.pub
RUN ssh-keygen -A


# RUN cd /root && \
# 	sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" && \
# 	cd /root/.oh-my-zsh && \
# 	git clone https://github.com/zsh-users/zsh-syntax-highlighting.git && \
# 	echo "source $(pwd)/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ${ZDOTDIR:-$HOME}/.zshrc

WORKDIR "/root"

ENTRYPOINT ["/usr/sbin/sshd", "-D"]