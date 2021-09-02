# zscaler-docker [{deprecated} that procedure showns to be not functional as expected]
(Unofficial) procedure to overpass Zscaler's certificate authority issues in Docker container images

Ref.: http://www.cyberkeeda.com/2021/03/docker-ssl-error-x509-certificate.html

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
