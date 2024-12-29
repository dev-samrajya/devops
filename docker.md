# docker

## docker images

docker image ls
docker image pull <name>
docker image inspect <name>
docker image rm <name>
docker image build -t <name> .

## docker container

docker container ls
docker container ls -a
docker container create <name>
docker container inspect <idname>
docker container start <idname>
docker container stop <idname>
docker container rm <idname>
docker container rm --force <idname>

docker container run <image-name>
docker container run --name <named-cont> <image-name>
docker container run --name <named-cont> -d <image-name>

# run a container with teletype and interactive mode
# -i: interactive (in future, you can interact with the container)
# -t: teletype (get terminal for the container to run extra commands)
# -d: run container in detached mode
docker container run --name <named-cont> -i -t -d <image-name>
docker container run --name <named-cont> -itd <image-name>
docker container run --name myhttpd -itd httpd

docker container logs <idname>
docker container logs myhttpd

# execute a command inside a container
docker container exec -it <idname> <command>
docker container exec -it myhttpd date
docker container exec -it myhttpd bash
# docker container exec -it myhttpd sh

# run a container with port forwarding enabled
docker container run --name <name-cont> -itd -p <local-port>:<container-port> <image nameid>
docker container run --name myhttpd -itd -p 8000:80 httpd


## docker volume

docker volume ls
docker volume create mysql-volume

# create a container with volume to persist the data
docker container run --name mysql -itd -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root -v mysql-volume:/var/lib/mysql mysql

docker volume rm <volume-name>
docker volume rm mysql-volume



## exercise 1
docker container run --name myhttpd -d httpd

- host a custom website inside a container by customizing image
- create index.html
  <h1>This is my first website running inside container</h1>
- create Dockerfile
    FROM httpd
    COPY index.html /usr/local/apache2/htdocs/
    EXPOSE 80

- build image
  docker image build -t mywebsite .

- create a container
  docker container run -itd --name mywebsite -p 8000:80 mywebsite

## exercise 3
- host a website using nginx container
<h1>Welcome to mywebsite running under nginx</h1>
FROM nginx
COPY index.html /usr/share/nginx/html/
EXPOSE 80

docker image build -t mywesite2 .
docker container run --name mywebsite2 -itd -p 8001:80 mywebsite2n

## exercise 4
- host a website using nginx
<h1>This is website 3 running in nginx container</h1>
FROM nginx
COPY index.html /usr/share/nginx/html/
EXPOSE 80

docker image build -t mywebsite3 .
docker container run --name mywebsite3 -itd -p 8002:80 mywebsite3

## exercise 5
- run a python program inside container
# create a python code (code.py)
print("hello hell")
FROM python
WORKDIR /src
COPY code.py .
CMD python code.py

docker image build -t pythonapp .
docker container run --name pythonapp pythonapp

## exercise 6
- run a python flask application inside container
app.py

from flask import Flask
app = Flask(__name__)
@app.route('/', methods=['GET'])
def root():
    return "Welcome to the flask server"
@app.route('/test', methods=['GET'])
def test():
    return "this is a test route"
app.run(host="0.0.0.0", port=5000, debug=True)

FROM python
WORKDIR /src
COPY app.py .
EXPOSE 5000
RUN pip install flask
CMD python app.py

docker image build -t pythonapp .
docker container run --name pythonapp pythonapp


## Customizing Docker Images

```bash
# FROM: select base docker image
# WORKDIR: select working directory
# COPY: copy file from local machine to image
# EXPOSE: expose port for external access
# CMD:
# - used to run a command inside a container
# - every image must contain one and only one CMD instruction
# RUN: run a command while building the image
```
