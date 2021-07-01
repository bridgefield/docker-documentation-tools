FROM ubuntu:20.04

RUN apt-get update \
    && apt-get install python3 python3-dev python3-pip build-essential libyaml-dev git -y \
    && rm -rf /var/lib/apt/lists/*

RUN pip3 install mkdocs

ENTRYPOINT ["mkdocs"]