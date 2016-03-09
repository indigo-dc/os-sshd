# os-sshd
Docker image with SSHD support, based on the [official Ubuntu Docker Image](https://registry.hub.docker.com/_/ubuntu/)

## Image tags

- indigo-datacloud/ubuntu-sshd:14.04 (trusty)

## Installed packages

Base:

- [Ubuntu Trusty (14.04) minimal](http://packages.ubuntu.com/trusty/ubuntu-minimal)

Image specific:
- [openssh-server](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

Config:

  - `PermitRootLogin yes`
  - `UsePAM no`
  - exposed port 22
  - default command: `/usr/sbin/sshd -D`
  - root password: `indig0!`

## Usage

```bash
$ docker run -d -P --name ubuntu_sshd indigodatacloud/ubuntu-sshd:14.04
$ docker port ubuntu_sshd 22
  0.0.0.0:32774

$ ssh root@localhost -p 32774
# Password is `indig0!`
root@ubuntu_sshd $
```

## Acknowledgement

Based on the [ubuntu-sshd] (https://github.com/rastasheep/ubuntu-sshd)
repository and customized for INDIGO-DataCloud.
