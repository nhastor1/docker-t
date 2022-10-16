FROM ubuntu:22.04 AS stage1
RUN apt-get -y update
RUN apt-get -y install git
RUN git clone https://github.com/kkenan/basic-microservices.git

FROM maven:3-openjdk-8-slim AS stage2
COPY --from=stage1 basic-microservices/spring-boot-app/src /usr/src/app/src
COPY --from=stage1 basic-microservices/spring-boot-app/pom.xml /usr/src/app
RUN mvn -f /usr/src/app/pom.xml clean package

FROM openjdk:8-jdk-alpine AS stage3
COPY --from=stage2 /usr/src/app/target/spring-boot-app-1.0-SNAPSHOT.jar /usr/app/spring-boot-app-1.0-SNAPSHOT.jar
COPY my-conf.yml /usr/app/my-conf.yml
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/usr/app/spring-boot-app-1.0-SNAPSHOT.jar", "--spring.config.location=/usr/app/my-conf.yml"]