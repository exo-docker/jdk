# exoplatform/jdk Docker image <!-- omit in toc -->
[![Build & publish eXo JDK images](https://github.com/exo-docker/jdk/actions/workflows/build.yml/badge.svg)](https://github.com/exo-docker/jdk/actions/workflows/build.yml)

## Supported tags and respective `Dockerfile` links <!-- omit in toc -->

| JDK version                            | Docker tags                                                                                                                                        | Dockerfile                           |
| -------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------ |
| **openjdk-25 + Ubuntu 26.04**          | `25-ubuntu-26`, `25-ubuntu-2604`, `openjdk-25-ubuntu-26`, `openjdk-25-ubuntu-2604`                                                                 | `openjdk-25/ubuntu/26.04/Dockerfile` |
| **openjdk-25 + Ubuntu 24.04 (latest)** | `latest`, `25`, `25-ubuntu`, `25-ubuntu-24`, `25-ubuntu-2404`, `openjdk-25`, `openjdk-25-ubuntu`, `openjdk-25-ubuntu-24`, `openjdk-25-ubuntu-2404` | `openjdk-25/ubuntu/24.04/Dockerfile` |
| **openjdk-21 + Ubuntu 26.04**          | `21-ubuntu-26`, `21-ubuntu-2604`, `openjdk-21-ubuntu-26`, `openjdk-21-ubuntu-2604`                                                                 | `openjdk-21/ubuntu/26.04/Dockerfile` |
| **openjdk-21 + Ubuntu 24.04**          | `21`, `21-ubuntu`, `21-ubuntu-24`, `21-ubuntu-2404`, `openjdk-21`, `openjdk-21-ubuntu`, `openjdk-21-ubuntu-24`, `openjdk-21-ubuntu-2404`           | `openjdk-21/ubuntu/24.04/Dockerfile` |
| **openjdk-21 + Ubuntu 22.04**          | `21-ubuntu-22`, `21-ubuntu-2204`, `openjdk-21-ubuntu-22`, `openjdk-21-ubuntu-2204`                                                                 | `openjdk-21/ubuntu/22.04/Dockerfile` |
| **openjdk-17 + Ubuntu 24.04**          | `17`, `17-ubuntu`, `17-ubuntu-24`, `17-ubuntu-2404`, `openjdk-17`, `openjdk-17-ubuntu`, `openjdk-17-ubuntu-24`, `openjdk-17-ubuntu-2404`           | `openjdk-17/ubuntu/24.04/Dockerfile` |
| **openjdk-17 + Ubuntu 22.04**          | `17-ubuntu-22`, `17-ubuntu-2204`, `openjdk-17-ubuntu-22`, `openjdk-17-ubuntu-2204`                                                                 | `openjdk-17/ubuntu/22.04/Dockerfile` |
| **openjdk-17 + Ubuntu 20.04**          | `17-ubuntu-20`, `17-ubuntu-2004`, `openjdk-17-ubuntu-20`, `openjdk-17-ubuntu-2004`                                                                 | `openjdk-17/ubuntu/20.04/Dockerfile` |
| **openjdk-11 + Ubuntu 22.04**          | `11`, `11-ubuntu`, `11-ubuntu-22`, `11-ubuntu-2204`, `openjdk-11`, `openjdk-11-ubuntu`, `openjdk-11-ubuntu-22`, `openjdk-11-ubuntu-2204`           | `openjdk-11/ubuntu/22.04/Dockerfile` |
| **openjdk-11 + Ubuntu 20.04**          | `11-ubuntu-20`, `11-ubuntu-2004`, `openjdk-11-ubuntu-20`, `openjdk-11-ubuntu-2004`                                                                 | `openjdk-11/ubuntu/20.04/Dockerfile` |
| **openjdk-8 + Ubuntu 22.04**           | `8`, `8-ubuntu`, `8-ubuntu-22`, `8-ubuntu-2204`, `openjdk-8`, `openjdk-8-ubuntu`, `openjdk-8-ubuntu-22`, `openjdk-8-ubuntu-2204`                   | `openjdk-8/ubuntu/22.04/Dockerfile`  |
| **openjdk-8 + Ubuntu 20.04**           | `8-ubuntu-20`, `8-ubuntu-2004`, `openjdk-8-ubuntu-20`, `openjdk-8-ubuntu-2004`                                                                     | `openjdk-8/ubuntu/20.04/Dockerfile`  |

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
