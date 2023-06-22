# Use Docker Swarm 

## Check 
```shell
docker network ls
brctl show
ip -4 addr show dev docker0
```
## Swarm init

docker swarm join --token SWMTKN-1-3o9zd9f0ut0dh2nca4erg0r195elkfalfhzqk060hdtdxvag8p-09dfhzc8ivc3zbqu2njdmu2ve 172.16.0.21:2377

## Check 
```shell
docker network ls
brctl show
ip -4 addr show dev docker0
```

## get back the token 
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