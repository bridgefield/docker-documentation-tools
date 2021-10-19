FROM maven:3-jdk-11 AS build

RUN apt-get update --quiet \
    && apt-get install --quiet --no-install-recommends --assume-yes \
        graphviz \
        fonts-wqy-zenhei\
    && rm -rf /var/lib/apt/lists/*

ARG PLANTUML_VERSION=master

RUN git clone -b $PLANTUML_VERSION https://github.com/plantuml/plantuml.git

RUN cd /plantuml && mvn package

FROM debian:11-slim

RUN apt-get update --quiet \
    && apt-get install --quiet --no-install-recommends --assume-yes \
        python3 \
        python3-pip \
        libyaml-0-2 \
        build-essential \
        python3-dev \
        libyaml-dev \
    && pip3 install mkdocs mkdocs-build-plantuml-plugin \
    && apt-get remove --assume-yes \
        python3-dev \
        build-essential \
        libyaml-dev \
    && apt-get autoremove --assume-yes \
    && rm -rf /var/lib/apt/lists/*

# deps for plantuml
RUN apt-get update --quiet \
    && apt-get install --quiet --no-install-recommends --assume-yes \
        default-jre-headless \
        graphviz \
        fonts-wqy-zenhei \
    && rm -rf /var/lib/apt/lists/*

COPY --from=build /plantuml/target/*-SNAPSHOT.jar /usr/share/plantuml/plantuml.jar

COPY plantuml /usr/bin/

ENTRYPOINT ["mkdocs"]
