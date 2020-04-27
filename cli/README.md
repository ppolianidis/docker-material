### Expose port

```
docker run -p <host_port>:<container_port>/protocol <image_name>:<image_tag>
docker run -p 8080:80 -dit <image_name>:<image_tag>
docker run -p 8080:80/tcp -dit <image_id>
```

### Mount volume
```
docker run -v source_path:dest_path -dit <image_name>:<image_tag>
docker run -v source_path:dest_path -dit <image_id>
```

### Use Args, Env Vars
```
docker run -e MYVAR=foo -dit <image_name>:<image_tag>
```

### Set Entrypoint
```
docker run --entrypoint=<path_to_binary> -dit <image_name>:<image_tag>
```

### Execute into a container
```
docker exec -it <container_name or id> command
```

### Change user
```
docker exec --user root -it <container_name or id> command
```

### Create a container
```
docker create <image_name>:<image:tag>
```

### List containers
```
docker ps
docker ps -a
```

### Start Container
```
docker start <container_name or id>
```

### Stop Container
```
docker stop <container_name or id> #SIGTERM SIGTERM, and then SIGKILL after grace period
docker kill <container_name or id> #SIGKILL, or specified signal
```

### Delete Container
```
docker rm <container_name or id>
```

### List images
```
docker images
```

### Delete Images
```
docker rmi <image_name>:<image_tag>
docker rmi <image_id>
```

### Checking container logs
```
docker logs <container_name or ID>
docker logs <container_name or ID> -f
```

### System Prune
```
docker system prune
docker system prune -fa
```

### Tagging images
```
docker tag <image_name>:<image_tag> <another_name>:<another_tag>
```

### Docker Registry (docker pull and docker push)
```
docker pull <registry>/<image_name>:<image_tag>
docker push <registry>/<image_name>:<image_tag>
```
