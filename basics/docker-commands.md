# Docker Commands I've Learned

This file lists key Docker commands I've mastered, with examples and notes.

# Docker Run 

This creates and starts a container from a specified image. If the image isn't on our system, Docker pulls from Docker Hub.

**Example**: *docker run nginx*  
**With Options**: *docker run --name my_container nginx* names the container "my_container"  

# Docker Pull
Downloads image from Docker Hub (or another registry) without running it.

**Example**: *docker pull redis:latest* 
Images are blueprints for containers. We can specify versions like redis:6.2 instead of latest.  

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
