FROM ubuntu:18.04

RUN apt-get -y update && \
    apt-get -y install ca-certificates && \
    apt-get -y install jq && \
    rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["/usr/bin/jq"]
