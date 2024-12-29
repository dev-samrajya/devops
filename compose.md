## docker compose

- used to deploy multiple microservices at once
- does not work with docker swarm
- create a file named docker-compose.yaml in a parent directory of all microservices

```yaml
# docker-compose.yaml

services:
  service1:
    build: ./service1/
    ports:
      - 4000:4000

  mysql:
    build: ./mysql-db
    volumes:
      - mysql-volume:/var/lib/mysql
```

```bash
# check the status of microservices
> docker compose ls
# create images for all microservices
> docker compose build
# create containers for all microservices
> docker compose up -d
# remove the containers
> docker compose down
# remove the containers as well as the images
> docker compose down --rmi all

```
