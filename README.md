# Build Docker image from a Dockerfile
`docker build <DockerFile-Path>` <br>

# To name the image 
`docker build --tag <image-name> .` <br>
In the place of **image-name**, use the image's name. **.** “dot” represents the current directory.
Remember: use the Dockerfile as the source

# Check list of images
`docker image ls` or `docker images`

# Creates and runs Docker container from Docker image
`docker run <image-name>`

# To give name of container
`docker run --name <container_name> <image_name>`

# Interactive docker container
`docker run -it <image-name>`

# Running detached (in the background) container
`docker run -d <image-name>`

# List running containers
`docker ps`

# Stop running containers
`docker stop <container-id>`

# Stop container by using container name
`docker stop <container-name>`

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
