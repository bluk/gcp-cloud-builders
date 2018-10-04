FROM gcr.io/cloud-builders/git

ARG HUB_VERSION
ARG HUB_SHA256SUM

ARG HUB_CREDENTIAL_HELPER_VERSION
ARG HUB_CREDENTIAL_HELPER_SHA256SUM

RUN apt-get update && \
    apt-get install -y wget && \
    rm -rf /var/lib/apt/lists/* && \
    wget https://github.com/github/hub/releases/download/v${HUB_VERSION}/hub-linux-amd64-${HUB_VERSION}.tgz && \
    echo "${HUB_SHA256SUM} hub-linux-amd64-${HUB_VERSION}.tgz" > checksum && sha256sum -c checksum && \
    tar xzvf hub-linux-amd64-${HUB_VERSION}.tgz && \
    rm hub-linux-amd64-${HUB_VERSION}.tgz && \
    mv hub-linux-amd64-${HUB_VERSION}/bin/hub /usr/bin/ && \
    chmod +x /usr/bin/hub && \
    wget https://github.com/kelseyhightower/hub-credential-helper/releases/download/${HUB_CREDENTIAL_HELPER_VERSION}/hub-credential-helper-linux-amd64-${HUB_CREDENTIAL_HELPER_VERSION}.tgz && \
    echo "${HUB_CREDENTIAL_HELPER_SHA256SUM} hub-credential-helper-linux-amd64-${HUB_CREDENTIAL_HELPER_VERSION}.tgz" > checksum && sha256sum -c checksum && \
    tar xzvf hub-credential-helper-linux-amd64-${HUB_CREDENTIAL_HELPER_VERSION}.tgz && \
    rm hub-credential-helper-linux-amd64-${HUB_CREDENTIAL_HELPER_VERSION}.tgz && \
    mv hub-credential-helper /usr/local/bin/ && \
    alias git=hub

ENTRYPOINT ["/usr/bin/hub"]
