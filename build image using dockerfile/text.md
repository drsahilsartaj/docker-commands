| Usage                        | Command                                       |
|------------------------------|-----------------------------------------------|
| Pull image from private registry | `docker pull <private-registry-url>/<image-name>` |
| Name an image                | `docker tag <old-name> <new-name>`           |
| Push an image                | `docker image push <image-name>`             |
| Login to private registry    | `docker login <private-registry-url>`        |
| Save image to file           | `docker save -o <file-name> <image-name>`    |
| Load image from file         | `docker load -i <file-name>`                 |


## Problem 1: 
Your company is still working on that new spam filter! Your colleague Bob made possible improvements to your work and sent you a tar file. Another colleague, Alice, has pushed her version to the company's dockerhub, docker.mycompany.com. It's now up to you to run both containers and find out which runs fastest.

> pull the container your colleague Alice made, spam_alice:v3, from the company's Docker Hub registry, docker.mycompany.com. <br>
`docker pull docker.mycompany.com/spam_alice:v3`

> Run the container you just pulled, docker.mycompany.com/spam_alice:v3 <br>
`docker images` --> listing images <br>
`docker run docker.mycompany.com/spam_alice:v3`

> open the tar file your colleague Bob sent you, spam_bob.tar. <br>
`docker load -i spam_bob.tar`

> run Bob's container, spam_bob:v3 <br>
`docker run spam_bob:v3`

-------

### Dockerfile Instructions

| Usage                                     | Dockerfile Instruction             |
|------------------------------------------|------------------------------------|
| Start a Dockerfile from an image         | `FROM <image-name>` eg. FROM postgres:15.0 **,** FROM hello-world               |
| Add a shell command to image             | `RUN <valid-shell-command>`  --> eg. RUN apt-get update **,** RUN apt-get install -y python3    |

---

### Shell Commands for Building Docker Images

| Usage                                      | Shell Command                              |
|-------------------------------------------|-------------------------------------------|
| Build image from Dockerfile               | `docker build /location/to/Dockerfile`    |
| Build image in current working directory  | `docker build .`                          |
| Choose a name when building an image      | `docker build -t first_image .`           |




