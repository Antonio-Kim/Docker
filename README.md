# DevOps2021
Here are some of the useful commands needed to use Dockers. All the Docker commands are found at https://docs.docker.com/engine/reference/commandline/docker/.

| Docker Commands                  | Description                                                       |
|----------------------------------|-------------------------------------------------------------------|
| docker images                    | Lists all the images                                              |
| docker pull \<_image_\>          | pull an image from registry                                       |
| docker rmi \<_image_\>           | removes an image                                                  |
| docker image prune               | removes all the dangling images                                   |
| docker ps -a                     | lists all the containers                                          |
| docker run \<_image_\>           | runs a container from an image                                    |
| docker rm \<_container_\>        | removes a container                                               |
| docker stop \<_container_\>      | stops a container                                                 |
| docker start -a \<_container_\>  | run a stopped container                                           |
| docker exec -it \<_container_\>  | executes a command inside the  command with stdin/stdout enabled  |
| docker system prune              | clears (almost) everything                                        |
| docker logs -f \<_container_\>   | shows output of stopped container                                 |
| docker search \<_image_\>        | search for an image from registry                                 |
| docker build . -t \<image name\> | create a Docker image in the current directory with assigned name |
| docker login                     | Log in to Docker Hub                                              |

## Hello-world of building an image
Create a script in a directory like below
```bash
echo "Hello world!"
```
save it as hello.sh. Run it to ensure that it works. Create a "Dockerfile" (without any extensions) using the following script:
```Dockerfile
FROM alpine 3.13

WORKDIR /usr/src/app # Set this as the working directory 
COPY hello.sh . # copy the hello.sh to the working directory
RUN chmod +x hello.sh # set the permission to be executable

CMD ./hello.sh
```
Now run ```docker build . -t hello-world``` and it will create a Docker image called "hello-world" 

## Upload the Docker image
Create a repository on Docker hub, then run the following commands to push the image to Docker Hub
```bash
docker tag <image name> <username>/<repository>
docker push <username>/<repository>
```

## Some interesting notes
- A volume is simply a folder (or a file) that is shared between the host machine and the container. You can set the execution to be done in host by adding __-v__ and the directory you wish to be set on __docker run__ 
- What is the difference between __CMD__ and __ENTRYPOINT__? https://stackoverflow.com/questions/21553353/what-is-the-difference-between-cmd-and-entrypoint-in-a-dockerfile
