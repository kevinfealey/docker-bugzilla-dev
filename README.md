Docker Bugzilla
===============

Configure a running Bugzilla system using Docker

**Note: the only differences between this project and the original are the port-forwarding scheme used in docker-compose.yml and the timeout allowance to start up MySQL before configuring it.**

## Features

* Running latest Centos
* Preconfigured with initial data and test product
* Running Apache2 and MySQL Community Server 5.6
* Code resides in `/var/www/html/bugzilla` and can be updated,
  diffed, and branched using standard git commands

## How to install Docker

Visit [Docker][docker] and get Docker up and running on your system. Optionally
you could install [Docker Compose](docker-compose)
to help with setting up a new container.

## How to build Bugzilla Docker image

To build a fresh image, just change to the directory containing the checked out
files and run the below command:

```bash
$ docker build --no-cache -t bugzilla/bugzilla-dev .
```
## How to start Bugzilla Docker image

To start a new container (or rerun your last container) you simply do:

```bash
$ docker-compose up -d
```

This will stay in the foreground and you will see the output from `supervisord`. You
can use the `-d` option to run the container in the background.

To stop, start or remove the container that was created from the last run, you can do:

```bash
$ docker-compose stop
$ docker-compose start
$ docker-compose rm
```

## How to access the Bugzilla container

If you are using Linux, you can simply point your browser to
`http://localhost:8081/bugzilla` to see the the Bugzilla home page.

The Administrator login is `admin` and the password is `password`.
You can use the Administrator account to creat other users, add products or
components, etc.

You can also login to the container using `docker exec -it bugzilla-dev su - bugzilla` command.
You can run multiple containers but you will need to give each one a different name/hostname
as well as non-conflicting ports numbers for httpd and vnc.

## TODO

* Enable SSL support.

[docker]: https://docs.docker.com/installation/
[docker-compose]: https://docs.docker.com/compose/install/
