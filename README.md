# Build Docker image from a Dockerfile
`docker build <DockerFile-Path>` <br>

# To name the image 
`docker build --tag <image-name> .` <br>
In the place of **image-name**, use the image's name. Here, **.** “dot” represents the current directory.
Remember: use the Dockerfile as the source

# Check list of images
`docker image ls` or `docker images`

# Creates and runs Docker container from Docker image
`docker run <image-name>`

# To give name of container
`docker run --name <container_name> <image_name>`

# Interactive docker container
`docker run -it <image-name>` <br>
**NOTE**: When type `exit` inside the container, the container **stops** automatically

# Running detached (in the background) container
`docker run -d <image-name>` <br>
**NOTE**: The container keeps running in the background after you **exit**

# List running containers
`docker ps`

# List all containers (including stopped ones)
`docker ps -a`

# Stop running containers
`docker stop <container-id>`

# Access a Running Container
`docker exec -it <container_id> bash`

# Docker Start Container
`docker start <container-id>`

# Filtering running containers
`docker ps -f "name=<container-name>"`

# Container logs
`docker logs <container-id>`

# Live logs
`docker logs -f <container-id>`

# Remove stopped container
`docker container rm <container-id>`

# Pulling image
`docker pull <image-name>`

# Pulling image versions
`docker pull <image-name>:<version>`

# listing images
`docker images`

# Remove an image
`docker image rm <image-name>`

# Cleans Up Stopped Containers
`docker container prune`
### **Note**: This command removes all stopped containers from your system to free up space. Running containers remain safe!

# Cleans Up Stopped Images
`docker container prune -a`

### **Note**: This command removes images which are not used by any running container, so remove all unused images (like dangling images)


# docker-compose up vs docker run <image_name>
> `docker-compose` works with multiple services, and `docker run` works on a single service. Like **Running multiple containers together (app + DB)** --> Use docker-compose up and **Running a single container** --> Use docker run <image-name>

> If your **Dockerfile** contains multiple FROM statements (multiple images), only the **last one** is used to create the final image.

> When to Use docker-compose up? <br>
>> If you need multiple containers (e.g., a web app + database). <br>
>> If your app has dependencies running as separate services.<br>
 
> Example: If you have an ubuntu image, then we have to use docker run else, we have multiple containers/images like ubuntu+db then we use docker-compose to run the services.
