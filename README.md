[![Docker Image CI](https://github.com/apjone/jmx_prometheus_standalone_docker/actions/workflows/docker-image.yml/badge.svg)](https://github.com/apjone/jmx_prometheus_standalone_docker/actions/workflows/docker-image.yml) [![Docker Image Publish](https://github.com/apjone/jmx_prometheus_standalone_docker/actions/workflows/docker-publish.yml/badge.svg)](https://github.com/apjone/jmx_prometheus_standalone_docker/actions/workflows/docker-publish.yml)

# jmx_prometheus_standalone_docker
Docker image using [ubuntu/jre](https://hub.docker.com/r/ubuntu/jre) to run [jmx_prometheus_standalone](https://prometheus.github.io/jmx_exporter/1.5.0/standalone/)


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

## Config.yml example

```
jmxUrl: service:jmx:rmi:///jndi/rmi://<APPLICATION_HOSTNAME_OR_IP>:<APPLICATION_RMI_PORT>/jmxrmi
rules:
- pattern: ".*"
```

# License: MIT

```
MIT License

Copyright (c) 2026 Tony J

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```