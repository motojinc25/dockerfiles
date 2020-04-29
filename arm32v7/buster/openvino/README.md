# arm32v7-buster-openvino

## Description

[OpenVINO™ toolkit](https://01.org/openvinotoolkit) Docker image for Raspbian OS

- ARMv7 32-bit(arm32v7) Raspbian Buster Base Image : [balenalib/raspberrypi3-debian:buster-build-20200420](https://hub.docker.com/layers/balenalib/raspberrypi3-debian/buster-build-20200420/images/sha256-9b8e5e469a9dec4dad0af58c2dccba50c518c74590f5cfa9cf77f19a516f6535?context=explore)
- OpenCV 4.1.0.25
- OpenVINO™ toolkit 2020.1.23

## Docker Hub

https://registry.hub.docker.com/repository/docker/motojinc25/arm32v7-buster-openvino

## Using

```bash
# To download the .bin file with weights
$ wget https://download.01.org/opencv/2019/open_model_zoo/R3/20190905_163000_models_bin/face-detection-retail-0004/FP16/face-detection-retail-0004.bin

# To download the .xml file with the network topology
$ wget https://download.01.org/opencv/2019/open_model_zoo/R3/20190905_163000_models_bin/face-detection-retail-0004/FP16/face-detection-retail-0004.xml

# Run arm32v7-buster-openvino container
$ docker run -it --rm --net=host --privileged -v /dev:/dev motojinc25/rpi-buster-openvino:latest /bin/bash

# Connected Neural Compute Stick and Test OpenVINO toolket
root@raspberrypi:/# lsusb | grep VPU
Bus 001 Device 010: ID 03e7:2150 Intel Myriad VPU [Movidius Neural Compute Stick]
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
>>> from openvino.inference_engine import IENetwork, IEPlugin
>>> MODEL_FILE = 'face-detection-retail-0004.xml'
>>> WEIGHTS_FILE = 'face-detection-retail-0004.bin'
>>> net = IENetwork(model=MODEL_FILE, weights=WEIGHTS_FILE)
>>> plugin = IEPlugin(device="MYRIAD")
>>> plugin.load(network=net)
<openvino.inference_engine.ie_api.ExecutableNetwork object at 0x00000000>
```

## Reference

- [Install OpenVINO™ toolkit for Raspbian* OS](https://docs.openvinotoolkit.org/2020.1/_docs_install_guides_installing_openvino_raspbian.html)
