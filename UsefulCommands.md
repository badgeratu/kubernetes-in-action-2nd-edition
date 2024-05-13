
# General

Container access controlled by:
- Namespaces
  - mnt (filesystemmount/)
  - pid (processes)
  - net (network devices)
  - ipc (inter-process communication, including message queues, shared memory etc.)
  - 
- Control Groups (cgroups)

# Image Operations

## List all images
docker images

## Create image from Dockerfile
docker build -t kiada:latest .

## View all layers/operations of an image and their sizes
docker history kiada:latest

## Add a new custom tag to an image
docker tag kiada scjones/kiada:0.1

## Push image to docker hub
docker login -u scjones docker.io
docker push scjones/kiada:0.1

## Remove image
docker rmi scjones/kiada:0.1

# Container Operations

## Create a new container from an image
docker run --name kiada_container -p 1234:8080 -d scjones/kiada:0.1

## List all running containers
docker ps

## Get additional information about a container
docker inspect kiada_container

## View the container logs
docker logs kiada_container

## Stop a container
docker stop kiada_container

## Delete (remove) a container
docker rm kiada_container

## Open an interactive terminal shell in a container
docker exec -it kiada_container bash


# Linux Commands

## List all running processes
ps aux

## List a single running process
ps aux | grep app.js


