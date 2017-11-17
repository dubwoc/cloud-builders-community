FROM ubuntu
RUN apt-get -y update && apt-get -y install ca-certificates unzip
ADD https://releases.hashicorp.com/packer/1.0.0/packer_1.0.0_linux_amd64.zip .
RUN echo 'ed697ace39f8bb7bf6ccd78e21b2075f53c0f23cdfb5276c380a053a7b906853  packer_1.0.0_linux_amd64.zip' | sha256sum && /usr/bin/unzip packer_1.0.0_linux_amd64.zip

FROM ubuntu
COPY --from=0 /var/lib/apt/lists/* /var/lib/apt/lists/
RUN apt-get -y install ca-certificates && rm -rf /var/lib/apt/lists/* && apt-get clean
COPY --from=0 packer /usr/bin/packer
ENTRYPOINT ["/usr/bin/packer"]
