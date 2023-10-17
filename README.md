# exoplatform/jdk Docker image <!-- omit in toc -->
[![Build & publish eXo JDK images](https://github.com/exo-docker/jdk/actions/workflows/build.yml/badge.svg)](https://github.com/exo-docker/jdk/actions/workflows/build.yml)

## Supported tags and respective `Dockerfile` links <!-- omit in toc -->

| JDK version                             | Docker tags                                                                         | Dockerfile                                                                       |
|-----------------------------------------|----------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
| openjdk-21 ( 21 ) + Ubuntu 22.04 | `openjdk-21`, `openjdk-21-ubuntu`, `openjdk-21-ubuntu-22`, `openjdk-21-ubuntu-2204`,`latest`    | *[( openjdk-21/ubuntu/22.04/Dockerfile )](./openjdk-21/ubuntu/22.04/Dockerfile)* |
| openjdk-17 ( 17.0.8 ) + Ubuntu 22.04 | `openjdk-17`, `openjdk-17-ubuntu`, `openjdk-17-ubuntu-22`, `openjdk-17-ubuntu-2204`    | *[( openjdk-17/ubuntu/22.04/Dockerfile )](./openjdk-17/ubuntu/22.04/Dockerfile)* |
| openjdk-14 ( 14.0.2 ) + Ubuntu 22.04 | `openjdk-14`, `openjdk-14-ubuntu`, `openjdk-14-ubuntu-22`, `openjdk-14-ubuntu-2204`             | *[( openjdk-14/ubuntu/22.04/Dockerfile )](./openjdk-14/ubuntu/22.04/Dockerfile)* |
| openjdk-11 ( 11.0.19 ) + Ubuntu 22.04 | `openjdk-11`, `openjdk-11-ubuntu`, `openjdk-11-ubuntu-22`, `openjdk-11-ubuntu-2204`            | *[( openjdk-11/ubuntu/22.04/Dockerfile )](./openjdk-11/ubuntu/22.04/Dockerfile)* |
| openjdk-17 ( 17.0.8 ) + Ubuntu 20.04 | `openjdk-17`, `openjdk-17-ubuntu`, `openjdk-17-ubuntu-20`, `openjdk-17-ubuntu-2004`             | *[( openjdk-17/ubuntu/20.04/Dockerfile )](./openjdk-17/ubuntu/20.04/Dockerfile)* |
| openjdk-14 ( 14.0.2 ) + Ubuntu 20.04 | `openjdk-14`, `openjdk-14-ubuntu`, `openjdk-14-ubuntu-20`, `openjdk-14-ubuntu-2004`             | *[( openjdk-14/ubuntu/20.04/Dockerfile )](./openjdk-14/ubuntu/20.04/Dockerfile)* |
| openjdk-11 ( 11.0.19 ) + Ubuntu 20.04 | `openjdk-11`, `openjdk-11-ubuntu`, `openjdk-11-ubuntu-20`, `openjdk-11-ubuntu-2004`            | *[( openjdk-11/ubuntu/20.04/Dockerfile )](./openjdk-11/ubuntu/20.04/Dockerfile)* |
| 8 ( 8u342 ) + Ubuntu 20.04              | `8`, `8-ubuntu`, `8-ubuntu-20`, `8-ubuntu-2004`                                              | *[( 8/ubuntu/20.04/Dockerfile )](./8/ubuntu/18.04/Dockerfile)*    
| openjdk-11 ( 11.0.19+7 ) + Ubuntu 18.04 | `openjdk-11`, `openjdk-11-ubuntu`, `openjdk-11-ubuntu-18`, `openjdk-11-ubuntu-1804`          | *[( openjdk-11/ubuntu/18.04/Dockerfile )](./openjdk-11/ubuntu/18.04/Dockerfile)* |
| 8 ( 8u201 ) + Ubuntu 18.04              | `8`, `8-ubuntu`, `8-ubuntu-18`, `8-ubuntu-1804`                                              | *[( 8/ubuntu/18.04/Dockerfile )](./8/ubuntu/18.04/Dockerfile)*                   |
| 8 ( 8u201 ) + Ubuntu 16.04              | `8-ubuntu-1604`, `8-ubuntu-16`                                                               | *[( 8/ubuntu/16.04/Dockerfile )](./8/ubuntu/16.04/Dockerfile)*     
| openjdk-8( 8u342b07 ) + Ubuntu 20.04    | `openjdk-8`, `openjdk-8-ubuntu`, `openjdk-8-ubuntu-20`, `openjdk-8-ubuntu-2004`              | *[( openjdk-8/ubuntu/20.04/Dockerfile )](./openjdk-8/ubuntu/20.04/Dockerfile)*   |
| openjdk-8( 8u222b10 ) + Ubuntu 18.04    | `openjdk-8`, `openjdk-8-ubuntu`, `openjdk-8-ubuntu-18`, `openjdk-8-ubuntu-1804`              | *[( openjdk-8/ubuntu/18.04/Dockerfile )](./openjdk-8/ubuntu/18.04/Dockerfile)*   |
| 8 ( 8u201 ) + Ubuntu 18.04              | `8`, `8-ubuntu`, `8-ubuntu-18`, `8-ubuntu-1804`,                                             | *[( 8/ubuntu/18.04/Dockerfile )](./8/ubuntu/18.04/Dockerfile)*                   |
| 8 ( 8u201 ) + Ubuntu 16.04              | `8-ubuntu-1604`, `8-ubuntu-16`                                                               | *[( 8/ubuntu/16.04/Dockerfile )](./8/ubuntu/16.04/Dockerfile)*                   |

- [Quick reference](#quick-reference)
- [How to use this image](#how-to-use-this-image)

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
