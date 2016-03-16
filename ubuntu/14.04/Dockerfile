FROM       ubuntu:14.04

#Pre-installed packages to speed IM contextualization
RUN apt-get update && apt-get install -y \
    openssh-server \
    python-dev \
    python-pip \
    unzip \
    gcc \
    openssh-client \
    sshpass

RUN mkdir /var/run/sshd

RUN pip install ansible==1.9.4

RUN echo 'root:indig0!' | chpasswd

RUN sed -ri 's/^PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config

RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config

EXPOSE 22

CMD    ["/usr/sbin/sshd", "-D"]
