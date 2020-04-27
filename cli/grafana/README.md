### Grafana

Set the correct IP of Prometheus (or if port is exposed, the IP of your server) in `datasources.yml`

To build and start the container use:
```
docker build -t grafana:latest .
docker run -dit --name granafa -p 3000:3000 grafana
```
