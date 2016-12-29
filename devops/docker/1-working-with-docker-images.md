# ANATOMY OF DOCKERFILE

Each instruction of a dockerfile creates an image layer that helps future builds (build only layers that diverge from previously layers).

# BUILDING AND RUNNING AN IMAGE

```sh
$ git clone https://github.com/spkane/docker-node-hello.git

$ docker build -t example/docker-node-hello:latest .

$ docker run -d -p 8080:8080 example/docker-node-hello:latest
```