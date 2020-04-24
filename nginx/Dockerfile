FROM ubuntu:latest

RUN apt-get update && \
    apt-get install -y nginx curl

COPY nginx.conf /etc/nginx/nginx.conf

ENTRYPOINT ["/bin/sh"]
CMD ["-c", "nginx -c /etc/nginx/nginx.conf -g \"daemon off;\""]
