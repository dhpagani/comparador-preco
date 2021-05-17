FROM openjdk:15-buster

eNV TZ America/Sao_Paulo

RUN apt-get update \
    && export DEBIAN_FRONTEND=noninteractive \    
    && apt-get -y install --no-install-recommends curl ca-certificates \ 
    git zip unzip wget curl nano vim locales net-tools openssh-client  &&
    apt-get -y upgrade --no-install-recommends && apt-get autoremove -y

RUN wget https://github.com/deluan/zsh-in-docker/releases/download/v1.1.1/zsh-in-docker.sh)  \
    chmod +x zsh-in-docker.sh && \
    zsh-in-docker.sh \
    -a 'SPACESHIP_PROMPT_ADD_NEWLINE="false"' \
    -a 'SPACESHIP_PROMPT_SEPARATE_LINE="false"' \
    -p git \
    -p https://github.com/zsh-users/zsh-autosuggestions \
    -p https://github.com/zsh-users/zsh-completions \
    -p https://github.com/zsh-users/zsh-history-substring-search \
    -p https://github.com/zsh-users/zsh-syntax-highlighting \
    -p 'history-substring-search' \
    -a 'bindkey "\$terminfo[kcuu1]" history-substring-search-up' \
    -a 'bindkey "\$terminfo[kcud1]" history-substring-search-down'

RUN /bin/zsh

COPY ./zsh/.p10k.zsh /root
COPY ./zsh/.tmux.conf /root

RUN chsh -s /usr/bin/zsh

ENTRYPOINT [ "/bin/zsh" ]
CMD ["-l"]