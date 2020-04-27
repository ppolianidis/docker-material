### Prometheus

Set the correct IP of node-exporter (or if port is exposed, the IP of your server) in `conf/prometheus.yml`

To build and start the container use:
```
docker build -t prometheus:latest .
docker run -dit --name prometheus -p 9090:9090 prometheus
```
