## About this project
Use this to run pihole in combination with unbound as multi-container docker application using docker-compose.

## Requirements to get this running:

* docker and docker-compose
* git

## Getting started:

* clone this repo with `git clone https://github.com/jubidev/pihole-unbound.git`
* cd into the project folder `cd pihole-unbound`
* start it (must be from inside project folder) `docker-compose up -d`
* stop it (also from inside project folder) `docker-compose down`

## Tools, hints, howtos:

* pihole is available at http://{ip}:180 <- port 180
* list containers: `docker container ls`
* change password (when apps are running): ` docker container exec -it {CONTAINER_ID_PIHOLE} pihole -a -p`
* follow unbound logs: `docker container logs {CONTAINER_ID_UNBOUND} --follow`
* modify verbosity in unbound.conf and restart apps to get more logs (higher number -> more logs)

## Update pihole:

Instead of running the pihole command 'pihole -up', the actual docker image should be updated.
Follow these steps to perform an update:

* `docker-compose down` to stop the application (make sure to have a reachable dns server to resolve the pull/update requests)
* `docker pull pihole/pihole:latest` pulls the latest pihole image
* `docker-compose up -d` start again