# Set base OS image
FROM balenalib/raspberrypi3-debian:buster-build-20200420

# Update package index and install dependencies
RUN install_packages \
    python3 \
    python3-pip \
    python3-dev \
    build-essential \
    libopenjp2-7-dev \
    zlib1g-dev \
    libatlas-base-dev \
    wget \
    libboost-python1.62.0 \
    curl \
    vim \
    libcurl4-openssl-dev

# Required for OpenCV
RUN install_packages \
    libhdf5-dev libhdf5-serial-dev \
    libjpeg-dev libtiff5-dev libjasper-dev libpng-dev \
    libavcodec-dev libavformat-dev libswscale-dev libv4l-dev \
    libqt4-test libqtgui4 libqtwebkit4 libgtk2.0-dev libfontconfig1-dev libcairo2-dev libgdk-pixbuf2.0-dev libpango1.0-dev libgtk-3-dev \
    libilmbase-dev libopenexr-dev

# Cleanup
RUN rm -rf /var/lib/apt/lists/* \
    && apt-get -y autoremove

# Install OpenVINO Toolkit
RUN mkdir -p /opt/intel/openvino && \
    cd /opt/intel/openvino && \
    wget -c https://download.01.org/opencv/2020/openvinotoolkit/2020.1/l_openvino_toolkit_runtime_raspbian_p_2020.1.023.tgz && \
    tar xf l_openvino_toolkit_runtime_raspbian_p*.tgz --strip 1 -C /opt/intel/openvino

# Add USB rules
RUN usermod -a -G users "$(whoami)"
RUN /bin/bash -c "source /opt/intel/openvino/bin/setupvars.sh && \
    sh /opt/intel/openvino/install_dependencies/install_NCS_udev_rules.sh"

# Install OpenCV
RUN pip3 install --upgrade pip
RUN pip3 install --upgrade setuptools
RUN pip3 install opencv-contrib-python==4.1.0.25
