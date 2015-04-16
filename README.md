Contribute to Drupal project with Docker
==========================================
https://www.drupal.org/contribute

## How to start?

````bash
docker-compose up -d
````
That command will run group of containers in background mode. That's all you need.
If you are using [jwilder/nginx-proxy](https://github.com/jwilder/nginx-proxy) container your site will be available under drupal.dev domain.
If you are not using nginx-proxy - start using it. It's really small and cool container which help you sharing port 80 across containers.
If you don't want to install anything else - check port expanded by drupal container.



## Usefull commands

Check ports exposed by containers:

````bash
docker-compose port
````

See logs for containers: 

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
If you want to use blackfire profiling tool you will have replace DEV_MODULE value from XDEBUG to BLACKFIRE

## Known issues
If you don't have /drupal folder, new one will be created for you and git will clone drupal core into that folder. But it will be done from inside of container. So all files will be owned by root, not your host user. You have to recursively change ownership of /drupal folder and assign it to your user:

````
chown -R <username> drupal
````

Do it from Docker host (don't do that while you are inside a container) and be in the parent to drupal directory in that time.

If you are using PHPStorm, disable 'safe write' setting (PHPStorm likes to mess up with file ownership).

