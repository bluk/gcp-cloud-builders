FROM gcr.io/cloud-builders/git

ARG HUB_VERSION
ARG HUB_SHA256SUM

RUN apt-get update && \
    apt-get install -y wget && \
    rm -rf /var/lib/apt/lists/* && \
    wget https://github.com/github/hub/releases/download/v${HUB_VERSION}/hub-linux-amd64-${HUB_VERSION}.tgz && \
    echo "${HUB_SHA256SUM} hub-linux-amd64-${HUB_VERSION}.tgz" > checksum && sha256sum -c checksum && \
    tar xzvf hub-linux-amd64-${HUB_VERSION}.tgz && \
    rm hub-linux-amd64-${HUB_VERSION}.tgz && \
    mv hub-linux-amd64-${HUB_VERSION}/bin/hub /usr/bin/ && \
    chmod +x /usr/bin/hub && \
    alias git=hub

ENTRYPOINT ["/usr/bin/hub"]
