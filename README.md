# jmx_prometheus_standalone_docker
Docker image using ubuntu/jre to run jmx_prometheus_standalone


## Build 

```
docker build -t jmxexporter:latest -f docker/Dockerfile .
```

## Compose

```
services:
  jmxnode1:
    image: jmxexporter:latest
    volumes:
      - ./config.yml:/config.yml
    ports:
      - 8000:8000
```
