# Original file:
# https://github.com/GoogleCloudPlatform/cloud-builders-community/blob/883a80728295fb51e41a1e3301f9c7831b01b7e0/packer/Dockerfile
#
# Copyright 2017 Google, Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
FROM ubuntu:18.04

ARG PACKER_VERSION
ARG PACKER_VERSION_SHA256SUM

RUN apt-get -y update && \
    apt-get -y install ca-certificates && \
    apt-get -y install unzip && \
    rm -rf /var/lib/apt/lists/*

COPY packer_${PACKER_VERSION}_linux_amd64.zip .
RUN echo "${PACKER_VERSION_SHA256SUM} packer_${PACKER_VERSION}_linux_amd64.zip" > checksum && sha256sum -c checksum && \
    /usr/bin/unzip packer_${PACKER_VERSION}_linux_amd64.zip

FROM ubuntu:18.04
RUN apt-get -y update && \
    apt-get -y install ca-certificates software-properties-common git && \
    apt-add-repository --yes --update ppa:ansible/ansible && \
    apt-get -y install ansible && \
    rm -rf /var/lib/apt/lists/*

COPY --from=0 packer /usr/local/bin/packer

ENTRYPOINT ["/usr/local/bin/packer"]
