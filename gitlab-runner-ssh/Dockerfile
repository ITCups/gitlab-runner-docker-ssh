# syntax=docker/dockerfile:1.3-labs
FROM gitlab/gitlab-runner:alpine

RUN mkdir -p /root/.ssh && chmod 700 /root/.ssh && touch /root/.ssh/known_hosts
COPY keys/id_rsa.pub keys/id_rsa /root/.ssh/
RUN chmod 644 /root/.ssh/id_rsa && chmod 600 /root/.ssh/id_rsa
RUN echo -e 'Host *\n\
    StrictHostKeyChecking no\n\
    UserKnownHostsFile /dev/null'\
>> /etc/ssh/ssh_config
# RUN cd /root && \
# 	sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" && \
# 	cd /root/.oh-my-zsh && \
# 	git clone https://github.com/zsh-users/zsh-syntax-highlighting.git && \
# 	echo "source $(pwd)/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ${ZDOTDIR:-$HOME}/.zshrc
