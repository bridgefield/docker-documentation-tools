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

ENTRYPOINT ["mkdocs"]
