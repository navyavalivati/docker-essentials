# Docker Commands I've Learned

This file lists key Docker commands I've mastered, with examples and notes.

# Docker Run 

This creates and starts a container from a specified image. If the image isn't on our system, Docker pulls from Docker Hub.

-- **Example**: docker run nginx
-- **With Options**: docker run --name my_container nginx names the container "my_container"

# Docker pull