# docker-t

## Requirements

 - docker app

## Description

This is an example of creating docker images. Just clone this repository, open the folder in the command line and run the command `docker compose up` and all images will be built and run.

If you want to change the configuration of `docker-compose` you can edit `.env` file or you can run the command `docker compose --env-file YOUR_FILE up` with YOUR_FILE be configuration file for docker-compose instead of .env. Also, you can edit spring-boot-app configuration by editing `my-conf.yml`.

*Note: Configuration files(.env and my-conf.yml) should not be on git repository, but this is just an example so I keep them on git.*