# Set base OS image
FROM balenalib/raspberrypi3-debian:buster-build-20200518

# Update package index and install dependencies
RUN install_packages \
    python3 \
    python3-pip \
    python3-dev \
    sense-hat

# Needed by iothub_client
RUN install_packages \
    libboost-python1.62.0 \
    libcurl4-openssl-dev

# Cleanup
RUN rm -rf /var/lib/apt/lists/* \
    && apt-get -y autoremove

# Install OpenCV
RUN pip3 install --upgrade pip
RUN pip3 install --upgrade setuptools

