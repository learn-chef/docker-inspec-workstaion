FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt update && \
    apt install -y locales vim curl iputils-ping openssh-client openssh-server iproute2 && \
    locale-gen en_US.UTF-8 && \
    update-locale LAN=en_US.UTF-8 && \
    apt clean && rm -rf /var/lib/apts/lists/* /tmp/* /var/tmp/*

WORKDIR /usr/app

RUN curl -L https://omnitruck.chef.io/install.sh | bash -s -- -P chef-workstation

RUN bash -c 'echo eval "$(chef shell-init bash)" > /root/.bashrc && source /root/.bashrc'
RUN bash -c '/opt/chef-workstation/gitbin/git init'

EXPOSE 22

CMD ["tail","-f","/dev/null"]
