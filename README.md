# docker-demo

### Create your docker hub-id and login to the site: https://hub.docker.com 
Remember your username and password for later usage. 

### Get the docker environment ready
-> Access https://labs.play-with-docker.com/ 

-> Login with your docker username and password.

-> Start a session. Click on Add new instance. 

Docker environment is ready to be used.

### Build and run a sample container.
-> Clone the repository: 
> git clone https://github.com/mamabusi/docker-demo/

-> Go to the directory with the Dockerfile and application code.
> cd docker-demo/python-sample

-> View the simple Dockerfile and understand what it does.

-> Check if there are any existing images.
> docker images 

-> Check if there are any existing containers running.
> docker ps -a 

-> Build your container
$ docker build -t <image_name> .
<Observe the steps run>
 Sending build context to Docker daemon  3.584kB
Step 1/3 : FROM python:latest
latest: Pulling from library/python
0ecb575e629c: Pull complete 
7467d1831b69: Pull complete 
feab2c490a3c: Pull complete 
f15a0f46f8c3: Pull complete 
937782447ff6: Pull complete 
e78b7aaaab2c: Pull complete 
b68a1c52a41c: Pull complete 
ddcd772f47ec: Pull complete 
aef84dafa567: Pull complete 
Digest: sha256:e2cd43d291bbd21bed01bcceb5c0a8d8c50a9cef319a7b5c5ff6f85232e82021
Status: Downloaded newer image for python:latest
 ---> 254d4a8a8f31
Step 2/3 : COPY main.py /
 ---> 1b0013f8d657
Step 3/3 : CMD [ "python", "./main.py" ]
 ---> Running in 8d2890458501
Removing intermediate container 8d2890458501
 ---> 8ae9a3d781d5
Successfully built 8ae9a3d781d5
Successfully tagged mamabusi/classic:latest
 
-> Check the list of images now:
$ docker images
REPOSITORY         TAG       IMAGE ID       CREATED         SIZE
mamabusi/classic   latest    8ae9a3d781d5   4 minutes ago   885MB
python             latest    254d4a8a8f31   9 days ago      885MB

-> Check the list of all containers in all states:
$ docker ps -a 
<Still empty because we have only built the image but we have not run it>
  
-> Run the container now:
$ docker run mamabusi/classic
Output: Hello! Welcome to the demo on Containers. (Picked from the python code)

->  Check the list of all containers in all states:
CONTAINER ID   IMAGE              COMMAND              CREATED              STATUS                          PORTS     NAMES
6dd1bb71562f   mamabusi/classic   "python ./main.py"   About a minute ago   Exited (0) About a minute ago             mystifying_swanson

It is in exited state because the container ran and completed its job. 

-> Lets try and push this image to Docker Hub.


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
