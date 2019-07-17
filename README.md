# exoplatform/jdk Docker image <!-- omit in toc -->

## Supported tags and respective `Dockerfile` links <!-- omit in toc -->

| JDK version                          | Docker tags                                                                     | Dockerfile                                                                     |
| ------------------------------------ | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| openjdk-8( 8u222b10 ) + Ubuntu 18.04 | `openjdk-8`, `openjdk-8-ubuntu`, `openjdk-8-ubuntu-18`, `openjdk-8-ubuntu-1804` | *[( openjdk-8/ubuntu/18.04/Dockerfile )](./openjdk-8/ubuntu/18.04/Dockerfile)* |
| 8 ( 8u201 ) + Ubuntu 18.04           | `8`, `8-ubuntu`, `8-ubuntu-18`, `8-ubuntu-1804`, `latest`                       | *[( 8/ubuntu/18.04/Dockerfile )](./8/ubuntu/18.04/Dockerfile)*                 |
| 8 ( 8u201 ) + Ubuntu 16.04           | `8-ubuntu-1604`, `8-ubuntu-16`                                                  | *[( 8/ubuntu/16.04/Dockerfile )](./8/ubuntu/16.04/Dockerfile)*                 |

- [Quick reference](#Quick-reference)
- [How to use this image](#How-to-use-this-image)

---

## Quick reference

- **Where to get help**

[the eXo Community Docker space](https://community.exoplatform.com/portal/g/:spaces:docker/docker), [the eXo Community Docker forum](https://community.exoplatform.com/portal/g/:spaces:docker/docker/forum)

- **Supported Docker versions**

[the latest release](https://github.com/docker/docker-ce/releases/latest) (on a best-effort basis)

## How to use this image

Some possible use cases :

- extend this image to add your java application

```dockerfile
FROM exoplatform/jdk
...
# add all your stuff
```

```bash
# build your personalized Docker image
docker build -t myorga/my-app .

# run your application in a container
docker run --rm myorga/my-app
```

- start an UberJAR java application

```bash
docker run --rm -v /path/to/my/uberjar-app.jar:/uberjar-app.jar exoplatform/jdk -jar /uberjar-app.jar
```

- start the jvm with

```bash
# show the help
$ docker run --rm exoplatform/jdk

Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)
where options include:
    -d32    use a 32-bit data model if available
    -d64    use a 64-bit data model if available
    -server   to select the "server" VM
                  The default VM is server,
                  because you are running on a server-class machine.
...

# show the version
$ docker run --rm exoplatform/jdk -version

java version "1.8.0_171"
Java(TM) SE Runtime Environment (build 1.8.0_171-b11)
Java HotSpot(TM) 64-Bit Server VM (build 25.171-b11, mixed mode)
```
