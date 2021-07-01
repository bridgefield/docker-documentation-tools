FROM maven:3-jdk-11 AS build

RUN apt-get update && apt-get install -y --no-install-recommends graphviz fonts-wqy-zenhei && rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/plantuml/plantuml.git

WORKDIR plantuml

RUN mvn package

RUN ls -la /plantuml/target

FROM openjdk:11-buster

RUN apt-get update && apt-get install -y --no-install-recommends graphviz fonts-wqy-zenhei && rm -rf /var/lib/apt/lists/*

RUN mkdir plantuml

COPY --from=build /plantuml/target/*-SNAPSHOT.jar /plantuml/plantuml.jar

RUN ls /plantuml && chmod +x /plantuml/plantuml.jar

ENTRYPOINT ["java", "-Djava.awt.headless=true", "-jar", "/plantuml/plantuml.jar"]
