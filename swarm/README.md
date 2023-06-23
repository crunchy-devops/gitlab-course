# Use Docker Swarm 

## Check 
```shell
docker network ls
brctl show
ip -4 addr show dev docker0
```
## Swarm init
```shell
docker swarm init
docker node ls
docker node update --label-add gitlab=master gitlab-ci-2
docker node inspect --pretty gitlab-ci-2 | grep -A 5 Labels:
docker swarm join --token 8ivc3zbqu2njdmu2ve 172.16.0.21:2377
```

## Check 
```shell
docker network ls
brctl show
ip -4 addr show dev docker0
```

## get back your token 
```shell
docker swarm join-token worker
```

## Run docker-compose for swarm 
```yaml
 docker stack deploy -c docker-compose.yml gitlab
```

## run on runner 
```shell
docker exec -it --user root  gitlab_gitlab-runner.xxxxx /bin/bash
gitlab-runner register --name hello-world \
--url http://170.75.173.181 \
--registration-token GR1348941ydeejiTyn-ZFjzAtCyhSo
```


