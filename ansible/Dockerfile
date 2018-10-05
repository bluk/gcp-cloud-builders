FROM ubuntu:18.04
RUN apt-get -y update && \
    apt-get -y install ca-certificates software-properties-common git && \
    apt-add-repository --yes --update ppa:ansible/ansible && \
    apt-get -y install ansible && \
    rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["ansible"]
