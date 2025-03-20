# Docker Commands I've Learned

This file lists key Docker commands I've mastered, with examples and notes.

# Docker Run 

This creates and starts a container from a specified image. If the image isn't on our system, Docker pulls from Docker Hub.

**Example**: *docker run nginx*  
**With Options**: *docker run --name my_container nginx* names the container "my_container"  

# Docker Pull
Downloads image from Docker Hub (or another registry) without running it.

**Example**: *docker pull unbuntu:latest*  
Images are blueprints for containers. We can specify versions like ubuntu:24.04.2 instead of latest.  

# Docker PS
Lists running containers.
There are different options:
- -a: Shows all containers (running or stopped).
- -l: Shows the latest created container.
- -q: Shows only container IDs 

# Docker Stop

Gracefully stops a running container.  
**Example**: *docker stop abc123* stops the container with container ID abc123  
Containers aren't deleted when stopped. They are just paused. 

# Docker Start
restarts a stopped container.  
**Example**: *docker start abc123* brings the container back to life.  

# Docker RM
Deletes a stopped container.
Options:
- -f: Forcefully removes it (even if the container is running).  
- -v: Deletes associated volumes.  
**Example**: *docker rm my_container* 

# Docker RMI
Deletes an image from our local system.
**Example**: *docker rmi nginx* removes the nginx image.  
Frees up space, but we can't remove an image if a container (even stopped) is using it. So we have to delete the container first.  

# Docker Images
Lists all images stored locally.
**Command**: *docker images*  
Shows image names, tags, IDs, and sizes.  

# Docker Exec
Runs a command inside a running container.  
**Example**: *docker exec my_container bash* opens a shell inside "my_container".  
Options:
- -i: Interactive mode (keeps STDIN open).  
- -t: Allocates a terminal (makes it feel like a real shell).  
- -d: runs in the background.  

Changes don't persist after a restart unless committed using docker commit.

# Docker Ports (Port Mapping)

Maps a port on your host machine to a port inside the container, allowing external access.  
**Example**: *docker run -p 8080:80 nginx* maps port 8080 on our laptop to port 80 in the container (where nginx listens).  
Containers are isolated by default. port mapping bridges that gap.

# Docker Login
**Command**: *docker login*  
Authenticates us with Docker Hub using a username and password. This step is required before pushing images to our Docker Hub account.  

# Docker Push

**Command**: *docker push image_name:tag*  
Uploads a local image to a registry (e.g., Docker Hub).  
We need to tag our image with our Docker Hub username first.  
**Example**: *docker tag myapp myuser/myapp:1.0*  

# Docker Build
**Command**: *docker build -t image_name:tag path*  
Builds an image from a Dockerfile in the specified path (. means current directory).  
**Example**: *docker build -t myapp:1.0 .*  
The Dockerfile contains instructions (e.g., install dependencies, copy files) to create our custom image.  

# Docker Restart
**Command**: *docker restart containernameorid*  
Stops and then starts a container, resetting its state.  
**Example**: *docker restart my_container*  

# Docker Inspect
**Command**: *docker inspect containernameorid*  
Returns detailed JSON info about a container or image (e.g., network settings, volumes).  
**Example**: *docker inspect my_container*  
Great for troubleshooting and scripting.  

# Docker Commit
**Command**: *docker commit container_name_or_id new_image_name:tag*  
Creates a new image from a container's current state.  
**Example**: *docker commit my_container myapp:updated*  
Useful for saving changes made inside a container (e.g., after installing something via docker exec).  

## Life Cycle:

- **Images**: Built (docker build) or pulled (docker pull), stored locally (docker images), and deleted (docker rmi).  
- **Containers**: Created and started (docker run), stopped (docker stop), restarted (docker restart), or removed (docker rm).  