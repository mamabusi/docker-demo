# docker-demo

### List your images:
docker image ls

###  Delete a specific image:
$ docker image rm [image name]

###  Delete all existing images:
$ docker image rm $(docker images -a -q)

### List all existing containers (running and not running):
$ docker ps -a

###  Stop a specific container:
$ docker stop [container name]

###  Stop all running containers:
$ docker stop $(docker ps -a -q)

###  Delete a specific container (only if stopped):
$ docker rm [container name]

###  Delete all containers (only if stopped):
$ docker rm $(docker ps -a -q)

### Display logs of a container:
$ docker logs [container name]
