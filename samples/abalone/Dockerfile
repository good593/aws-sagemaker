# docker build --build-arg REGION=ap-northeast-2 -f Dockerfile -t my_docker:1.0 .
# docker run -it -p 80:80 -v ~/.aws:/root/.aws -v /var/run/docker.sock:/var/run/docker.sock --name my_docker my_docker:1.0 /bin/bash

FROM amazonlinux

RUN yum -y update && \
    yum -y install wget tar gzip iputils jq bash-completion && \
    yum -y install python3 python3-pip && \
    yum clean all

RUN amazon-linux-extras install docker
RUN python3 -m pip install numpy pandas boto3 awscli s3fs

RUN mkdir -p /root/environment
COPY workshop-files /root/environment/workshop-files
COPY abalone.csv /root/environment/abalone.csv

RUN mkdir -p /root/environment/mlops
COPY workshop-files/model /root/environment/mlops

WORKDIR /root/environment

