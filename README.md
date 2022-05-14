# Gitlab course

## Pre-requisite
```shell
sudo apt-get update  # update repo ref
sudo apt install -y python3.8-venv docker.io # install docker ce package 
```

## Install a virtualenv for docker-compose

```shell
cd 
git clone https://github.com/crunchy-devops/gitlab-course.git
cd gitlab-course
python3 -m venv venv
pip3 install docker-compose
source venv/bin/activate
docker-compose up -d
```




You can find a randomly generated password available for 24 hours   
See the file `/etc/gitlab/initial_root_password`  
```shell
sudo cat /etc/gitlab/initial_root_password
```
Log in as root using this password
