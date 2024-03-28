ARG BUILD_VERSION

FROM ubuntu

# This Dockerfile contains things useful for an interactive development environment
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID
ENV LANG en_US.utf8

# these are installed for terminal/dev convenience.  If more tooling for build is required, please
RUN apt update \
    && apt-get install -y locales \
    && localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8 \
    && apt install -fy vim sudo \
    && apt install -fy apt-utils lsb-release bash-completion curl docker.io \
    && apt install -y build-essential clang ccache flex bison g++ gawk \
    gcc-multilib g++-multilib gettext git libncurses-dev libssl-dev \
    python3-distutils rsync unzip zlib1g-dev file wget \
    && :

RUN groupadd -g $USER_GID $USERNAME \
    && useradd -s /bin/bash -u $USER_UID -g $USER_GID -G docker,sudo -m $USERNAME \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME \
    && :

RUN curl https://raw.githubusercontent.com/restyled-io/restyler/master/bin/restyle-path -o /usr/local/bin/restyle-path \
    && chmod +x /usr/local/bin/restyle-path \
    && :
