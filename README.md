Contribute to Drupal project with Docker
==========================================
https://www.drupal.org/contribute

## How to start?

````bash
docker-compose up -d
````
That command will run group of containers in background mode

## Usefull commands

Check ports map:
````bash
docker-compose port
````

See docker provision logs: 
````bash
docker-compose logs
````

Enter drupal container (to run drush commands, use codesniffer or whatever):
````bash
docker exec -ti <container_name_or_id> bash
````
Drupal folder is in /app/drupal location.

## Requirements

* [Docker](https://docs.docker.com/installation/ubuntulinux/)

````bash
# You can use this command on Ubuntu to install it.
curl -sSL https://get.docker.com/ubuntu/ | sudo sh
````

* [docker-compose](http://docs.docker.com/compose/install/)

````bash
# The easiest way to install on ubuntu is:
curl -L https://github.com/docker/compose/releases/download/1.1.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
````

## Configuration

Edit docker-compose.yml file to change default settings (like Drupal 7/8 version). You will find most of it under [drupal] container specification.
