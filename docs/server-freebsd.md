# FreeBSD / HardenedBSD server setup

It is only possible to install Algo on existing systems only. We support only 11 version for now.

## System preparation

Ensure that the following kernel options are enabled:

```
# sysctl kern.conftxt | grep -iE "IPSEC|crypto"
options	IPSEC
options IPSEC_NAT_T
device	crypto
```

## Available roles

* vpn
* ssh_tunneling
* dns_adblocking

## Additional variables

* rebuild_kernel - set to `true` if you want to let Algo to rebuild your kernel if needed (takes a lot of time)

## Installation

```shell
ansible-playbook deploy.yml -t local,vpn -e "server_ip=$server_ip server_user=$server_user IP_subject_alt_name=$server_ip Store_CAKEY=N" --skip-tags cloud
```
