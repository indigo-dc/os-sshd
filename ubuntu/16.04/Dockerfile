FROM ubuntu:14.04

# Install ansible repository
RUN apt-get update -y
RUN apt-get install software-properties-common -y
RUN apt-add-repository ppa:ansible/ansible

# Pre-install packages to speed IM contextualization
RUN apt-get update && \
    apt-get install -y \
        ansible \
        cloud-init \
        gcc \
        openssh-client \
        openssh-server \
        python-dev \
        python-pip \
        sshpass \
        unzip \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir /var/run/sshd

RUN echo 'root:indig0!' | chpasswd

RUN sed -ri 's/^PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config

RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config

RUN wget https://github.com/OpenNebula/addon-context-linux/releases/download/v4.14.3/one-context_4.14.3.deb && dpkg -i one-context_4.14.3.deb

RUN rm -f /etc/one-context.d/00-network; rm -f /etc/one-context.d/01-dns; rm -f /etc/one-context.d/05-hostname; rm -f /etc/one-context.d/06-gen-env; rm -f /etc/one-context.d/07-grow-rootfs

COPY one-contextd /usr/sbin/one-contextd

EXPOSE 22

CMD    /etc/init.d/vmcontext start; /usr/sbin/sshd -D
