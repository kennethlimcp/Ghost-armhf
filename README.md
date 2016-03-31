# Ghost blog on Armhf

### Introduction

This runs on a [Odroid C1](http://www.hardkernel.com) and monitored using [BMC Truesight](https://www.bmc.com)

Actual blog is running at: http://kennethlimcp.no-ip.org

The original [Dockerfile](https://github.com/docker-library/ghost) is modified and compiled on the **C1** itself using the armhf version of Ubuntu + some other fixes.

Currently, the docker image is built through Docker hub automated build to add trust for people to use it safely.

The repo containing the Dockerfile is at https://github.com/kennethlimcp/armhf-ghost


Also, blog content is persisted by mounting a volume to the container and is independent of the container itself.

### Steps to compile manually

```sh
$ git clone http://github.com/kennethlimcp/ghost-on-armhf.git
$ cd ghost-build
$ docker build --tag username/imagename:version .
```


### Steps to launch blog with NGINX as the front-facing application

- run `./bin/nginx-storage`
- run `./bin/blog-nginx`
- run `./bin/nginx`

### Some plans

- Currently the volumes path for the docker containers are hard-coded but I should probably change them to env var soon.
- switch over to a paid domain name
- use [letsencrypt](https://letsencrypt.org/) and turn on `https`
- automate the building of a new ghost version and perform a deploy

There still work to be done to spin up a new container running the latest GHOST before stopping the old one. This will be a 0-downtime deployment goodness! :)
