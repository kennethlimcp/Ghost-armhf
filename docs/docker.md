### configuring Docker daemon

#### limit logs files from the default `json-file` driver


```sh
$ sudo service docker stop
$ sudo nano /etc/default/docker
--> append in the line DOCKER_OPTS="--log-driver=json-file --log-opt max-file=1 --log-opt max-size=10m"
```
