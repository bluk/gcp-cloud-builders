FROM ubuntu:18.04

ARG DOCKER_COMPOSE_VERSION

RUN apt-get -y update && \
    apt-get -y install ca-certificates curl && \
    curl -L "https://github.com/docker/compose/releases/download/${DOCKER_COMPOSE_VERSION}/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && \
    rm -rf /var/lib/apt/lists/* && \
    chmod +x /usr/local/bin/docker-compose

ENTRYPOINT ["/usr/local/bin/docker-compose"]
