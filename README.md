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

Useful links:

* https://docs.docker.com/
* https://www.toptal.com/linux/separation-anxiety-isolating-your-system-with-linux-namespaces
* https://0xax.gitbooks.io/linux-insides/content/Cgroups/linux-cgroups-1.html
* https://washraf.gitbooks.io/the-docker-ecosystem/content/Chapter%201/Section%203/union_file_system.html
* https://medium.com/@paccattam/drooling-over-docker-2-understanding-union-file-systems-2e9bf204177c
