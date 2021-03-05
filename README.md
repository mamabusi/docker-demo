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
> docker build -t <image_name> .

```
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
 ```
 
-> Check the list of images now:
> docker images

```
REPOSITORY         TAG       IMAGE ID       CREATED         SIZE
mamabusi/classic   latest    8ae9a3d781d5   4 minutes ago   885MB
python             latest    254d4a8a8f31   9 days ago      885MB
```

-> Check the list of all containers in all states:
> docker ps -a 
[Still empty because we have only built the image but we have not run it]
  
-> Run the container now:
> docker run mamabusi/classic (image_name)

```
Output: Hello! Welcome to the demo on Containers. (Picked from the python code)
```

->  Check the list of all containers in all states:
> docker ps -a

```
CONTAINER ID   IMAGE              COMMAND              CREATED              STATUS                          PORTS     NAMES
6dd1bb71562f   mamabusi/classic   "python ./main.py"   About a minute ago   Exited (0) About a minute ago             mystifying_swanson
```
It is in exited state because the container ran and completed its job. 

-> Lets try and push this image to Docker Hub.
> docker push [image_name]

```
Using default tag: latest
The push refers to repository [docker.io/mamabusi/classic]
f930e38f6727: Preparing 
7d999a918ae9: Preparing 
5b164865b353: Preparing 
302cf02dcc7c: Preparing 
e3d73f29c674: Preparing 
10bf86ff9f6a: Waiting 
da654bc8bc80: Waiting 
4ef81dc52d99: Waiting 
909e93c71745: Waiting 
7f03bfe4d6dc: Waiting 
denied: requested access to the resource is denied
```

Observe the error. This is because we have to login to our docker account before pushing. 
-> Login to docker account
> docker login

> docker push [image_name]

-> Tag image with the path in docker hub repository
> docker tag <image_name> YOUR_DOCKERHUB_NAME/[image_name]

```
Using default tag: latest
The push refers to repository [docker.io/mamabusi/classic]
f930e38f6727: Pushed 
7d999a918ae9: Mounted from library/python 
5b164865b353: Mounted from library/python 
302cf02dcc7c: Mounted from library/python 
e3d73f29c674: Mounted from library/python 
10bf86ff9f6a: Mounted from library/python 
da654bc8bc80: Mounted from library/python 
4ef81dc52d99: Mounted from library/python 
909e93c71745: Mounted from library/python 
7f03bfe4d6dc: Mounted from library/python 
latest: digest: sha256:f0472aaaf58ebee83aad48ad8ce0ec6606b4493794d9ee5a0268bc783514452e size: 2424
```

-> Go to DockerHub and view your image. 

-> Check the list of containers
> docker ps -a OR docker container ls --all

[Note the container_id]

-> Stop and remove the containers
> docker container stop <Container_id>

> docker container rm <Container_id> or <Container_name>


-> Remove the images
> docker image rm [image_name]


### Firing up a Web application container
https://hub.docker.com/r/tutum/hello-world

-> Pull the tutum/hello-world image from docker hub
> docker pull tutum/hello-world

-> Run the container image on port 80
> sudo docker run -d -p 80 tutum/hello-world
```
[Note the container_id]
 ```
 
-> Fetch the external port
> sudo docker port [container_id] 80

```
0.0.0.0:[note the port]
```

-> Try the below curl command
> curl http://localhost:[port]/

```
<html>
<head>
        <title>Hello world!</title>
        <link href='http://fonts.googleapis.com/css?family=Open+Sans:400,700' rel='stylesheet' type='text/css'>
        <style>
        body {
                background-color: white;
                text-align: center;
                padding: 50px;
                font-family: "Open Sans","Helvetica Neue",Helvetica,Arial,sans-serif;
        }

        #logo {
                margin-bottom: 40px;
        }
        </style>
</head>
<body>
        <img id="logo" src="logo.png" />
        <h1>Hello world!</h1>
        <h3>My hostname is 97dd670032f9</h3>    </body>
</html>
```

------------------------------------------------------------------------------------------------------



Additional Commands:
-> Running a remote image that is there on dockerhub and then remove off container after exiting :
> docker run --rm -it mamabusi/demo


-> List your images:
> docker image ls

-> Delete a specific image:
> docker image rm [image name]

-> Delete all existing images:
> docker image rm $(docker images -a -q)

-> List all existing containers (running and not running):
> docker ps -a

-> Stop a specific container:
> docker stop [container name]

-> Stop all running containers:
> docker stop $(docker ps -a -q)

-> Delete a specific container (only if stopped):
> docker rm [container name]

-> Delete all containers (only if stopped):
> docker rm $(docker ps -a -q)

-> Display logs of a container:
> docker logs [container name]


