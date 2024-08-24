
# General

Container access controlled by:
- Namespaces
  - `mnt` (filesystemmount/)
  - `pid` (processes)
  - `net` (network devices)
  - `ipc` (inter-process communication, including message queues, shared memory etc.)
  - `uts` (UNIX Time-sharing system, hotname & natwork name)
  - `time` (system clock offsets)
  - `cgroup` (control groups root directory)
- Control Groups (cgroups)

Most containers run without elevated privileges, so they cannot access protected *sys-calls*.
> Create a privileged container in Docker using the `--privileged` flag


# Image Operations

### List all images
```bash
docker images
```

### Create image from Dockerfile
```bash
docker build -t kiada:latest .
```

### View all layers/operations of an image and their sizes
```bash
docker history kiada:latest
```

### Add a new custom tag to an image
```bash
docker tag kiada scjones/kiada:0.1
```

### Push image to docker hub
```bash
docker login -u scjones docker.io
docker push scjones/kiada:0.1
```

### Remove image
```bash
docker rmi scjones/kiada:0.1
```

# Container Operations

### Create a new container from an image
```bash
docker run --name kiada_container -p 1234:8080 -d scjones/kiada:0.1
```

### List all running containers
```bash
docker ps
```

### Get additional information about a container
```bash
docker inspect kiada_container
```

### View the container logs
```bash
docker logs kiada_container
```

### Stop a container
```bash
docker stop kiada_container
```

### Delete (remove) a container
```bash
docker rm kiada_container
```

### Open an interactive terminal shell in a container
```bash
docker exec -it kiada_container bash
```

### Limit CPU resources accessible to a container
```bash
docker run --cpuset-cpus="1,2"... # Specific CPUs
docker run --cpus="0.5"... # Use 0.5 cores
```

### Limit container memory
```bash
docker run --memory="100m"... # Limit to 100MB
```

# Linux Commands

### List running processes
```bash
ps aux
ps aux | grep app.js # Filter to only app.js 
```


# kubectl

Default kubeconfig file is at `~/.kube/config`. Can also set location via the `KUBECONFIG` environment variable e.g.:
```bash
$ export KUBECONFIG =/ path/ to/ custom/ kubeconfig
```

### Get cluster info
```bash
k cluster-info
```

### Get nodes
```bash
k get nodes
```

