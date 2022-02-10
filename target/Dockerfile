FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt update && \
    apt install -y locales vim curl iputils-ping openssh-client openssh-server && \
    locale-gen en_US.UTF-8 && \
    update-locale LAN=en_US.UTF-8 && \
    apt clean && rm -rf /var/lib/apts/lists/* /tmp/* /var/tmp/*

WORKDIR /usr/app

RUN echo 'root:password' | chpasswd

RUN bash -c 'echo "PermitRootLogin yes" >> /etc/ssh/sshd_config'

RUN service ssh restart

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
