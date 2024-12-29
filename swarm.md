## swarm (cluster)
```bash
docker system info | grep Swarm
docker swarm init
docker swarm leave --force
# generate a manager token
docker swarm join-token manager
# generate a manager worker
docker swarm join-token worker
```
## node
```bash
docker node ls
docker node inspect <nodeid>
docker node rm <nodeid>
# promote a worker as a manager
docker node promote <workerid>
# demote a manager as a worker
docker node demote <managerid>
```
## service
```bash
docker service ls
docker service create --name <named> <image-name>
docker service create --name myservice httpd
# create a service with desired state = 5
docker service create --replicas 5 --name myservice httpd
# create service forwarding a port
docker service create --name <named> --replicas <count> -p <source-port>:<dest-port> <image>
docker service create --name myservice --replicas 5 -p 8000:80 httpd
docker service rm myservice
docker service scale <named>=<new desired state>
docker service scale myservice=10
# get the details of containers created by service
docker service ps <service-name>
docker service ps myservice

```
## docker stack

- similar to docker compose, but it has support for docker swarm
- collection of docker swarm services
- creates docker service for every service declared in the docker-stack.yaml file

```yaml
# docker-stack.yaml

services:
  service1:
    image: service1
    deploy:
      replicas: 5
    ports:
      - 4000:4000

  service2:
    image: service2
    deploy:
      replicas: 5
    ports:
      - 4001:4000
```

```bash

docker stack ls
docker stack deploy --compose-file <filename> <stack name>
docker stack deploy --compose-file docker-stack.yaml mystack
docker stack rm <stack-name>

```
