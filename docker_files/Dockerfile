FROM ubuntu:18.04
MAINTAINER jave3737@pm.me

# INSTALL DEPENDENCIES
################################################################################
ENV DEBIAN_FRONTEND noninteractive
ENV PATH="/root/.local/bin:${PATH}"
ENV ZEPHYR_BASE="/root/zephyrproject/zephyr"
RUN apt-get update && \
    apt-get -y install --no-install-recommends apt-utils dialog git cmake ninja-build gperf \
    ccache dfu-util device-tree-compiler wget \
    python3-dev python3-pip python3-setuptools python3-tk python3-wheel xz-utils file \
    make gcc gcc-multilib g++-multilib libsdl2-dev \
    gnupg gnupg1 gnupg2 software-properties-common vim neovim
RUN wget -O - https://apt.kitware.com/keys/kitware-archive-latest.asc 2>/dev/null | apt-key add -
RUN apt-add-repository 'deb https://apt.kitware.com/ubuntu/ bionic main'
RUN apt -y install cmake

################################################################################
# INSTALL AND PREPARE WEST
################################################################################
# install west
RUN pip3 install --user -U west && \
    west --version

# get zephyr source code
RUN west init ~/zephyrproject && \
    cd ~/zephyrproject && \
    west update && \
    west zephyr-export

# install additional python dependencies
RUN pip3 install --user -r ~/zephyrproject/zephyr/scripts/requirements.txt

################################################################################
# INSTALL THE TOOLCHAIN
################################################################################
RUN cd ~ && \
    wget https://github.com/zephyrproject-rtos/sdk-ng/releases/download/v0.11.4/zephyr-sdk-0.11.4-setup.run && \
    chmod +x zephyr-sdk-0.11.4-setup.run && \
    ./zephyr-sdk-0.11.4-setup.run -- -d ~/zephyr-sdk-0.11.4

################################################################################
# INSTALL FLASH TOOL
################################################################################
RUN wget https://www.nordicsemi.com/-/media/Software-and-other-downloads/Desktop-software/nRF-command-line-tools/sw/Versions-10-x-x/10-11-1/nRFCommandLineTools10111Linuxamd64tar.gz -O ~/nrf_flash_tool.tar.gz && \
   mkdir ~/nrf_flash_tool && \
   tar -xzvf ~/nrf_flash_tool.tar.gz -C ~/nrf_flash_tool && \
   dpkg -i --force-overwrite ~/nrf_flash_tool/*.deb

################################################################################
# UPDATE USER SETTINGS
################################################################################
# make a shell script that completely copies over the vim environment into the docker one
RUN echo "set bell-style none" >> /etc/inputrc


