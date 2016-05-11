FROM ubuntu:14.04

# Install ansible repository
RUN apt-get update && \
    apt-get install -y software-properties-common
RUN apt-add-repository ppa:ansible/ansible

# Pre-install packages to speed IM contextualization
RUN apt-get update && apt-get install -y \
    openssh-server \
    python-dev \
    python-pip \
    unzip \
    gcc \
    openssh-client \
    ansible \
    sshpass \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir /var/run/sshd

RUN echo 'root:indig0!' | chpasswd

RUN sed -ri 's/^PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config

RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config

EXPOSE 22

CMD    ["/usr/sbin/sshd", "-D"]
