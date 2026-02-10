# ───────────── Builder stage ─────────────
FROM ubuntu:24.04 AS builder

# Minimal dependencies — keeps this stage small
RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
        ca-certificates curl && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /download

# Example: download JMX exporter + your config
RUN curl -L -o jmx_prometheus_javaagent.jar \
    https://github.com/prometheus/jmx_exporter/releases/download/1.5.0/jmx_prometheus_standalone-1.5.0.jar

# ───────────── Final chiseled image ─────────────
FROM ubuntu/jre:21-24.04_stable
COPY --from=builder /download/jmx_prometheus_javaagent.jar /jmxexporter/
COPY ./config.yml /
ENTRYPOINT ["java","-jar", "/jmxexporter/jmx_prometheus_javaagent.jar","8000","/config.yml"]
