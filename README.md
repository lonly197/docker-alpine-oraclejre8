# docker-alpine-oraclejre8

[![](https://images.microbadger.com/badges/image/lonly/docker-alpine-oraclejre8.svg)](http://microbadger.com/images/lonly/docker-alpine-oraclejre8)

> This image is based on Alpine Linux image, which is only a 5MB image, and contains
[OracleJRE 8](http://www.oracle.com/technetwork/java/javase/overview/index.html).

## Introduction

Minified Docker image with OracleJRE 8 to run Java applications.

## Build

```sh
$ docker build \
--rm \
-t lonly/docker-alpine-oraclejre8 \
--build-arg VCS_REF=`git rev-parse --short HEAD` \
--build-arg BUILD_DATE=`date -u +"%Y-%m-%dT%H:%M:%SZ"` .
```

## Usage

This image could be a base image for your projects, so you may use it like this:

```Dockerfile
FROM lonly/docker-alpine-oraclejre8

COPY ./my_app /usr/local/bin/my_app
```

```sh
$ docker build -t my_app .
```

There are already several images using this image, so you can refer to them as usage examples:

* [`lonly/docker-zeppelin`](https://hub.docker.com/r/lonly/docker-zeppelin/) ([github](https://github.com/lonly197/docker-zeppelin))

* [`lonly/docker-presto`](https://hub.docker.com/r/lonly/docker-presto/) ([github](https://github.com/lonly197/docker-presto))

## Test

```bash
$ echo 'public class Main { public static void main(String[] args) { System.out.println("Hello World"); } }' > Main.java
$ docker run --rm -v "$(pwd)":/mnt --workdir /mnt lonly/docker-alpine-oraclejre8 sh -c "javac Main.java && java Main"
```
