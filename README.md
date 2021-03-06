# Gitlab course

## Pre-requisite
```shell
sudo apt-get update  # update repo ref
sudo apt install -y python3.8-venv docker.io # install docker ce package 
```

## Install a virtualenv for docker-compose

```shell
cd 
git clone https://github.com/gitlab-course.git  # git clone your repo locally
cd gitlab-course  # change directory
python3 -m venv venv  # install a python virtualenv
pip3 install docker-compose  # install python package docker-compose 
source venv/bin/activate  # activate the virtual env
docker-compose up -d  # execute docker-compose script for starting all containers
```

### Run portainer for getting gitlab initial password

Get portainer tool up and running
```shell
docker run -d -p 9000:9000 --name portainer -v /var/run/docker.sock:/var/run/docker.sock portainer/portainer-ce:2.0.1 -H unix:///var/run/docker.sock 
# go to container gitlab-course_gitlab-ce_1 and select a exec_console icon 
# enter cat /etc/gitlab/initial_root_password
```

or directly using docker exec  
`docker exec -it gitlab-course_gitlab-ce_1 cat /etc/gitlab/initial_root_password`
Here, it's randomly generated password available for 24 hours   
Copy and paste this password in your browser at 
http://<ip_address>:20000
Log in as root using this password

## Configure manually Gitlab runner 
```shell
docker run --rm -it -v /opt/gitlab-runner-config:/etc/gitlab-runner gitlab/gitlab-runner register
```

## Change gitlab-runner configuration 
Go to `/etc/gitlab-runner`
add `network_mode="gitlab-course_prodnetwork"` at the end of `[runners.docker]` block code
do a `gitlab-runner restart`