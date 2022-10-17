# docker-t

## Prerequisites

 - installed git
 - installed docker

## Steps

 - open console 
 - clone repository `git clone https://github.com/nhastor1/docker-t.git`
 - change directory `cd docker-t`
 - run `docker compose up`

## Description

This is an example of creating docker images. 

If you want to change the configuration of `docker-compose` you can edit `.env` file or you can run the command `docker compose --env-file YOUR_FILE up` with YOUR_FILE be configuration file for docker-compose instead of .env. Also, you can edit spring-boot-app configuration by editing `my-conf.yml`.

*Note: Configuration files (.env and my-conf.yml) should not be on git repository, but this is just an example so I kept them on git.*