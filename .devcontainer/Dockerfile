FROM rust:trixie

ARG USER=user
ENV DEBIAN_FRONTEND=noninteractive

RUN apt update -y && apt install -y \
    sudo \
    locales \
    gcc-mingw-w64-x86-64 \
    g++-mingw-w64-x86-64 \
    libsdl2-dev

RUN locale-gen en_GB.UTF-8 && update-locale

RUN useradd -m $USER && echo "$USER:$USER" | chpasswd && adduser $USER sudo
RUN echo "user            ALL = (ALL) NOPASSWD: ALL" >> /etc/sudoers

RUN printf "alias ll='ls -la'" >> /home/$USER/.bashrc
CMD /bin/bash