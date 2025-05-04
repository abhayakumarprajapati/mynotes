# to create image

docker build -t myapp .

# to create containers 
 
docker run --name firstcontainer -p 3000:3000 -d myapp

# show containers and images

docker ps
docker images

# stop container 
docker stop <container_id>
# delete container
docker rm <container_id>

# delete image
docker rmi myapp
mongodb://admin:pass@localhost:27020/

# docker compose

 *docker-compose down*
Stop the containers.

Remove the containers.

Remove the default network created by Docker Compose.

 *docker-compose up -d*

 Starts the containers in the background (detached), so your terminal is free.

