# arm32v7-buster-sensehat

## Description

[Sense HAT](https://www.raspberrypi.org/products/sense-hat/) Docker image for Raspbian OS

- ARMv7 32-bit(arm32v7) Raspbian Buster Base Image : [balenalib/raspberrypi3-debian:buster-build-20200518](https://hub.docker.com/layers/balenalib/raspberrypi3-debian/buster-build-20200518/images/sha256-5daaf7d747e81e312821b9204013c9c77c086611aa08f132b5df958e077a1ede?context=explore)
- Sense-HAT 2.2.0

## GitHub

https://github.com/motoJinC25/dockerfiles/tree/master/arm32v7/buster/sensehat

## Docker Hub

https://registry.hub.docker.com/repository/docker/motojinc25/arm32v7-buster-sensehat

## Using

```bash
# Run arm32v7-buster-sensehat container
$ docker run -it --rm --privileged motojinc25/arm32v7-buster-sensehat:latest /bin/bash

# Test Sense HAT
root@raspberrypi:/# python3
Python 3.7.3 (default, Dec 20 2019, 18:57:59)
[GCC 8.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> from sense_hat import SenseHat
>>> sense = SenseHat()
>>> sense.show_message("Hello world")
```

## Reference

- [Getting started with the Sense HAT](https://projects.raspberrypi.org/en/projects/getting-started-with-the-sense-hat)
