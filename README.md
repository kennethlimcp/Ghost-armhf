# Ghost blog on Armhf

This runs on a [Odroid C1](http://www.hardkernel.com) and monitored using [Boundary](https://boundary.com)

Actual blog is running at: http://kennethlimcp.no-ip.org

The original [Dockerfile](https://github.com/docker-library/ghost) is modified and compiled on the **C1** itself using the armhf version of Ubuntu + some other fixes.

Also, blog content is persisted by mounting a volume to the container and is independent of the container itself.

### Steps to update [GHOST](https://ghost.org) version
- run `./update.sh`
- run `docker build --tag kennethlimcp/ghost-armhf:v0.6.x .`
- run `docker stop ghostblog; docker rm ghostblog; docker run -d --name ghostblog -p 80:2368 -e "NODE_ENV=production" -v /home/odroid/blog:/var/lib/ghost ghost`

The eventual plan is for the container to sit behind NGINX and spin up a new container running the latest GHOST before stopping the old one. This will be a 0-downtime deployment goodness! :)
