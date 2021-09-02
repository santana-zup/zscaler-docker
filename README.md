# zscaler-docker
(Unofficial) procedure to overpass Zscaler's certificate authority issues in Docker container images

## Tested operation system
Ubuntu 20.04.3 LTS
Docker Server 20.10.8

## prerequirements
- Sudo user
- Docker Server
- Docker Client
- Zscaler chain certificate file (zscaler.pem)

## Procedure
If it doesn't exists already,, create the docker certificates dir
```shell
sudo mkdir -pv /etc/docker/certs.d
```
copy .pem as crt in docker certificates file, reload system certificates and restart docker engine
```shell
sudo cp -v <path to your zscaler pem certificate file>/zscaler.pem /etc/docker/certs.d/zscaler.crt && sudo update-ca-certificates && sudo service docker restart
```
... and try to build your docker image
