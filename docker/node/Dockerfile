FROM ubuntu:22.04 AS stage1
RUN apt-get -y update
RUN apt-get -y install git
RUN git clone https://github.com/kkenan/basic-microservices.git

FROM node:9.9-alpine AS stage2
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app
COPY --from=stage1 ./basic-microservices/node-app ./
RUN npm install
RUN apk update
RUN apk add curl
EXPOSE 8081
CMD [ "node", "index.js" ]