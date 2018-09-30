#  Copyright 2018 Bryant Luk
#
#  Licensed under the Apache License, Version 2.0 (the "License");
#  you may not use this file except in compliance with the License.
#  You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
#  Unless required by applicable law or agreed to in writing, software
#  distributed under the License is distributed on an "AS IS" BASIS,
#  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#  See the License for the specific language governing permissions and
#  limitations under the License.

FROM ubuntu:18.04

ARG TERRAFORM_VERSION
ARG TERRAFORM_VERSION_SHA256SUM

RUN apt-get -y update && \
    apt-get -y install ca-certificates unzip && \
    rm -rf /var/lib/apt/lists/*

COPY terraform_${TERRAFORM_VERSION}_linux_amd64.zip .

RUN echo "${TERRAFORM_VERSION_SHA256SUM} terraform_${TERRAFORM_VERSION}_linux_amd64.zip" > checksum && sha256sum -c checksum && \
    /usr/bin/unzip terraform_${TERRAFORM_VERSION}_linux_amd64.zip

FROM ubuntu:18.04
RUN apt-get -y update && \
    apt-get -y install ca-certificates && \
    rm -rf /var/lib/apt/lists/*

COPY --from=0 terraform /usr/local/bin/terraform

ENTRYPOINT ["/usr/local/bin/terraform"]
