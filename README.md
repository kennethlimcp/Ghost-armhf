# Ghost blog on Armhf

This runs on a [Odroid C1](http://www.hardkernel.com) and monitored using [BMC Truesight](https://www.bmc.com)

Actual blog is running at: http://kennethlimcp.no-ip.org

The original [Dockerfile](https://github.com/docker-library/ghost) is modified and compiled on the **C1** itself using the armhf version of Ubuntu + some other fixes.

Also, blog content is persisted by mounting a volume to the container and is independent of the container itself.

### Steps to update [GHOST](https://ghost.org) version
- run `./update.sh`
- run `docker build --tag kennethlimcp/ghost-armhf:v0.6.x .`
- run ./bin/launch-blog`

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
