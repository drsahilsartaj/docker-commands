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

----

## Managing files in the docker images
**COPYing files into an image** (The COPY instruction copies files from our local machine into the image we're building): <br>
`COPY <src-path-on-host> <dest-path-on-image>`

**COPYing folders**: <br>
`COPY <src-folder> <dest-folder>`

**Downloading files**: <br>
`RUN curl <file-url> -o <destination> --> Download a file` <br>
`RUN unzip <dest-folder>/<filename>.zip --> Unzip a file` <br>
`RUN rm <copy_directory>/<filename>.zip --> Remove the original zip file` <br> **(Paste in the Dockerfile)**

## Problem 2:
**Q**. Copying files into an image, You've created an Ubuntu and python3-based image to run your data pipeline. Update your Dockerfile so your image includes the pipeline.py file in which you defined the pipeline.

> To the end of the Dockerfile, add the Docker instruction, which copies the pipeline.py file in your current working directory (/home/repl) to the /app folder in the image you want to build. <br>
`To copy the pipeline.py file into the docker, we need to update the Dockerfile by COPY` <br>
`nano Dockerfile --> open the Dockerfile by nano` <br>
`COPY /home/repl/pipeline.py /app/ --> paste in the docker file to add`
---
**Q**. Copying folders, After creating an ubuntu and python3 image with your pipeline python code in it, you realize you actually need your entire pipeline_v3 project in the Docker image to be able to install its dependencies. There is a Dockerfile in the current working directory to start from that already has python3 installed

> Add the instruction to copy all pipeline_v3 project files into the /app directory in your Docker image. You can find the files in the /pipeline_v3/ directory, which is in the current working directory on your local machine.

`nano Dockerfile` <br>
`COPY /pipeline_v3/ /app/`

> Using the terminal, run the command to build an image called pipeline_v3 from the Dockerfile in your current working directory. <br>
`docker build -t pipeline_v3 .`
---
**Q**. Working with downloaded files, Your previous image worked, and you were able to finalize your pipeline python code! You can now create the next version of your image. Let's create a Dockerfile from scratch, add instructions and then build it.

> 1. Create a file called Dockerfile in the current working directory. <br>
`nano Dockerfile` <br>
> 2. Add the first instruction to the Dockerfile so that it will build on top of the ubuntu image. Add instructions to the Dockerfile so that it runs apt-get update and apt-get install -y python3 curl unzip. <br>
`FROM ubuntu`
`RUN apt-get update`
`RUN apt-get install -y python3 curl unzip` --> Add this script in the Dockerfile`

> 3. Add instructions to the Dockerfile to: Download the zip file from https://assets.datacamp.com/production/repositories/6082/datasets/31a5052c6a5424cbb8d939a7a6eff9311957e7d0/pipeline_final.zip to /pipeline_final.zip. Unzip the file And remove the zip. You can use three separate instructions or make it a single instruction to keep your image smaller. <br>
`1. Open the Dockerfile using `nano Dockerfile` <br>
`2. Add `RUN curl https://assets.datacamp.com/production/repositories/6082/datasets/31a5052c6a5424cbb8d939a7a6eff9311957e7d0/pipeline_final.zip -o /pipeline_final.zip` to the end of the Dockerfile.` <br>
`3. Add `RUN unzip /pipeline_final.zip` to the end of the Dockerfile.` <br>
`4. Add `RUN rm /pipeline_final.zip` to the end of the Dockerfile.` <br>
`5. Save the file and exit nano using CTRL+s and CTRL+x`

> 4. Using the terminal, run the command to build an image called pipeline from the Dockerfile in your current working directory. <br>
`docker build -t pipeline .`
----



