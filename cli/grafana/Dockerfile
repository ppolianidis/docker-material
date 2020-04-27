ARG BUILDER_VERSION=${BUILDER_VERSION:-3.10.3}
ARG VERSION=${VERSION:-3.11.6}
FROM alpine:${BUILDER_VERSION} as builder

ENV GRAFANA_VERSION=6.6.2
RUN mkdir /tmp/grafana \
  && wget -P /tmp/ https://dl.grafana.com/oss/release/grafana-${GRAFANA_VERSION}.linux-amd64.tar.gz \
  && tar xfz /tmp/grafana-${GRAFANA_VERSION}.linux-amd64.tar.gz --strip-components=1 -C /tmp/grafana

FROM alpine:${VERSION}

LABEL maintainer="ppolianidis@gmail.com" \
      version="1.0"

ENV PATH=/usr/share/grafana/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin \
    GF_PATHS_CONFIG="/etc/grafana/grafana.ini" \
    GF_PATHS_DATA="/var/lib/grafana" \
    GF_PATHS_HOME="/usr/share/grafana" \
    GF_PATHS_LOGS="/var/log/grafana" \
    GF_PATHS_PLUGINS="/var/lib/grafana/plugins" \
    GF_PATHS_PROVISIONING="/etc/grafana/provisioning"

WORKDIR $GF_PATHS_HOME    

RUN set -ex \
    && addgroup -S grafana \
    && adduser -S -G grafana grafana \
    && apk add --no-cache libc6-compat ca-certificates su-exec bash

COPY --from=builder /tmp/grafana "$GF_PATHS_HOME"
COPY ./run.sh /run.sh
COPY ./grafana.ini $GF_PATHS_CONFIG
COPY ./datasources.yml /etc/grafana/provisioning/datasources/
COPY ./dashboards.yml /etc/grafana/provisioning/dashboards/
COPY ./node-exporter-dashboard.json /var/lib/grafana/dashboards/

RUN mkdir -p "$GF_PATHS_PROVISIONING/datasources" \
        "$GF_PATHS_PROVISIONING/dashboards" \
        "$GF_PATHS_PROVISIONING/notifiers" \
        "$GF_PATHS_LOGS" \
        "$GF_PATHS_PLUGINS" \
        "$GF_PATHS_DATA" \
    && chown -R grafana:grafana "$GF_PATHS_DATA" "$GF_PATHS_LOGS" "$GF_PATHS_PLUGINS" "$GF_PATHS_PROVISIONING"

EXPOSE 3000

ENTRYPOINT ["/bin/sh"]
CMD ["-c", "/run.sh"]
