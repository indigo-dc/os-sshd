# os-sshd
Docker image with SSHD support, based on the [official CentOS Docker Image](https://registry.hub.docker.com/_/centos/)

## Image tags

- indigodatacloud/centos-sshd:6

## Installed packages

Base:

- [CentOS (6) minimal](https://hub.docker.com/_/centos/)

Image specific:
- [openssh-server](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
- openssh-clients, openssh-server, python-distribute, wget, openssh-client, sshpass, ansible

Config:

  - `PermitRootLogin yes`
  - exposed port 22
  - default command: `/usr/sbin/sshd -D`
  - root password: `indig0!`

## Usage

```bash
$ docker run -d -P --name centos_sshd indigodatacloud/centos-sshd:6
$ docker port centos_sshd 22
  0.0.0.0:32774

$ ssh root@localhost -p 32774
# Password is `indig0!`
root@centos_sshd $
```
