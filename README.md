# Build Docker image from a Dockerfile
`docker build '<DockerFile-Path>'`

# Creates and runs Docker container from Docker image
`docker run <image-name>`

# Docker container output
`docker run <image-name>`

# Interactive docker container
`docker run -it <image-name>`

# Running detached (in the background) container
`docker run -d <image-name>`

# List running containers
`docker ps`

# Stop running containers
`docker stop <container-id>`

# Name a container then run
`docker run --name <container-name> <image-name>`

# Stop container by using container name
`docker stop <container-name>`

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
