# Change the location of images and container storing

```sh
$ sudo docker -d \
  -H unix://var/run/docker.sock \ 
  -H tcp://127.0.0.1:2375 --graph="/data/docker"
```
# GETTING INSIDE A CONTAINER

```sh
$ docker exec -it <ID> /bin/bash
$ docker attach <ID>
```