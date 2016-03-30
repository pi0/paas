[![Docker Repository on Quay](https://quay.io/repository/pooya/laas/status "Docker Repository on Quay")](https://quay.io/repository/pooya/laas)
[![](https://badge.imagelayers.io/pooya/laas:latest.svg)](https://imagelayers.io/?images=pooya/laas:latest 'Get your own badge on imagelayers.io')

# Laas ( Laravel As A Service )
Painless and Automated Laravel Docker instances Hosting and Deployment.

## What is Laravel
Laravel is a free, open-source PHP web framework, created by Taylor Otwell and intended for the development of web applications following the model–view–controller (MVC) architectural pattern. [Laravel](https://laravel.com)

## What is Docker
Docker allows you to package an application with all of its dependencies into a standardized unit for software development. [Docker](https://www.docker.com)

# What is Laas
Laas is developed under inspiration of [Laravel Forge](https://forge.laravel.com) Project, which allows you deploy and host your laravel projects wihout any configuraion. Laas is Free, Self Hosted and More powerful.

## What is Butterfly
Butterfly is a xterm compatible terminal that runs in your browser. [See Here](https://github.com/paradoxxxzero/butterfly)


# Features
- Production ready And fully dockerized environment for hosting Laravel applications
- All Data is independent of container, just delete and create an new one any time you want
- Powered by **Nginx**, **PHP-FPM** on **Debian** Jessie
- **Webhooks** are ready ! Just push and commit your changes and your site is up!
- PHP **Mongo** extension compiled
- **SSH-Keys** are auto-generated for git access
- Very **Light**, no database running inside container
- Easy Shell Access Using [**Butterfly**](https://github.com/paradoxxxzero/butterfly)

# Quick Start

+ To run a test Instance
```bash
docker run --rm -p 2739:80 -itv /tmp/lass_test:/var/www quay.io/pooya/laas http://github.com/bestmomo/laravel5-exampe
```
Your container is Ready on `http://host_ip:2739`
    
+ To run a instance that starts at host boot time:
```bash
docker run --name <Name> --restart=always -itdv <DataStorage>:/var/www quay.io/pooya/laas <YourLaravelProjectGitURL>
```

+ Simple Docker file with database

```yaml
version: '2'
services:
  laravel:
    image: quay.io/pooya/laas
    command: https://github.com/some/repo.git
    volumes:
      - ./data/www:/var/www
    environment:
      -  VIRTUAL_HOST=my.subdomain.tld
    links:
      - db:db
    restart: always
    network_mode: "bridge"
  db:
    image: mariadb
    volumes:
      - ./data/mariadb:/var/lib/mysql
    environment:
      - MYSQL_ROOT_PASSWORD=<MYSQL_PASSWORD>
    restart: always
    network_mode: "bridge"
```





