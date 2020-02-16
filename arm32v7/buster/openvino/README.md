# rpi-buster-openvino

## Description

Raspberry Pi Buster OS + OpenCV(4.1.0.25) + OpenVINO(2020.1.023)

## Docker Hub

https://registry.hub.docker.com/r/motojinc25/rpi-buster-openvino

## Using

```bash
$ docker run -it --rm --net=host --privileged -v /dev:/dev motojinc25/rpi-buster-openvino /bin/bash
root@raspberrypi:/# source /opt/intel/openvino/bin/setupvars.sh
[setupvars.sh] 64 bitness for Python 3.7 is requred
[setupvars.sh] OpenVINO environment initialized
root@raspberrypi:/# python3
Python 3.7.3 (default, Dec 20 2019, 18:57:59)
[GCC 8.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import cv2
>>> cv2.__version__
'4.2.0-openvino'
```

