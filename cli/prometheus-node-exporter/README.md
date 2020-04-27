### Prometheus node-exporter

To build and start the container use:
```
docker build -t prometheus-node-exporter:latest .
docker run -dit --name prometheus-node-exporter -p 9100:9100 -v /proc:/usr/proc -v /sys:/usr/sys -v /:/rootfs prometheus-node-exporter
```
