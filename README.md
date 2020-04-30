### Build a Docker image:

```
docker build -t <image name>:<image tag> <Docker Context directory>
```

Example (Inside the directory that contains the Dockerfile):

```
docker build -t myapp:latest .
```

### Run a docker container

```
docker run <args> <image name>:<image tag>
```

Example:
```
docker run -dit myapp:latest
```

### Check running containers

```
docker ps # Shows running containers
docker ps -a # Show running and stopped containers
```

### Check docker images

```
docker images
```

### Running a container

```
docker run <args> <image name>:<image tag>
```

Example:
```
docker run -dit myapp:latest
```

### Executing commands inside a container

```
docker exec <args> <container> <command>
```

Example entering shell in a running container:
```
docker exec -it mycontainer /bin/sh
```
