FROM ubuntu:22.04 AS stage1
ARG git_repo
RUN apt-get -y update
RUN apt-get -y install git
RUN git clone ${git_repo} repo

FROM maven:3-openjdk-8-slim AS stage2
COPY --from=stage1 repo/spring-boot-app/src /usr/src/app/src
COPY --from=stage1 repo/spring-boot-app/pom.xml /usr/src/app
RUN mvn -f /usr/src/app/pom.xml clean package

FROM openjdk:8-jdk-alpine AS stage3
ARG jar_file_name
ARG conf_file
COPY --from=stage2 /usr/src/app/target/$jar_file_name /usr/app/app.jar
COPY ${conf_file} /usr/app/my-conf.yml
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/usr/app/app.jar", "--spring.config.location=/usr/app/my-conf.yml"]