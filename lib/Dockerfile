FROM nvidia/cudagl:10.0-devel-ubuntu18.04
ENV DEBIAN_FRONTEND=noninteractive
# Append Japanese apt mirrors for ubuntu for faster download
#RUN echo "deb http://linux.yz.yamagata-u.ac.jp/ubuntu/ xenial main restricted universe multiverse" > /etc/apt/sources.list \
#    && echo "deb http://linux.yz.yamagata-u.ac.jp/ubuntu/ xenial-updates main restricted universe multiverse" >> /etc/apt/sources.list \
#    && echo "deb http://linux.yz.yamagata-u.ac.jp/ubuntu/ xenial-backports main restricted universe multiverse" >> /etc/apt/sources.list \
#    && echo "deb http://linux.yz.yamagata-u.ac.jp/ubuntu/ xenial-security main restricted universe multiverse" >> /etc/apt/sources.list

RUN set -x \
    && apt update \
#    && apt upgrade -y\
    && apt install -y cmake cython doxygen g++ git gfortran libboost-all-dev libeigen3-dev libgeos++-dev libnanomsg-dev libtinyxml2-dev python-coverage python-nose python-numpy python-pip python-setuptools \
#        git \
#        wget \
        apt-utils \
        apt-transport-https \
        software-properties-common \
        nano \
#        libtbb2 \
#        libtbb-dev \
#        libjpeg-dev \
#        libpng-dev \
#        libtiff-dev \
#        libopenblas-dev \
#        libboost-all-dev \
#        libfann-dev \
#        libunwind-dev \
    && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654 \
    && echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list \
    && apt update \
    && apt install -y \
	ros-melodic-desktop-full \
    ros-melodic-eigenpy \
	python-rosdep \
    && rosdep init\
    && rosdep update\
    && echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc\
    && echo "source /root/catkin_ws/devel/setup.bash" >> ~/.bashrc\
    && apt install -y \
        python-rosinstall \
        python-rosinstall-generator \
        python-wstool \
        build-essential \
#        ros-melodic-image-transport \
    && rm -rf /var/lib/apt/lists/* 

# Make sure you have required tools
RUN apt-get update -y \
    && apt-get -qq install -y apt-transport-https lsb-release ca-certificates gnupg \
    # Add our key
    && apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key 892EA6EE273707C6495A6FB6220D644C64666806 \
    # Add our repository (head versions)
    && sh -c 'echo "deb https://dl.bintray.com/gergondet/multi-contact-release $(lsb_release -sc) main" | tee /etc/apt/sources.list.d/multi-contact.list' \
    # Update packages list
    && apt-get -qq update -y \
    # Install required dependencies, Choreonoid, JVRC1 sample project and mc_rtc tools
    # && apt install -y libeigen3-dev doxygen libboost-all-dev libmc-rtc-dev libcopra-dev mc-openrtm jvrc-choreonoid mc-rtc-utils ros-melodic-mc-rtc-tools
    && apt install -y python-eigen python3-eigen libcopra-dev libmc-rtc-dev mc-rtc-utils python3-mc-rtc mc-openrtm jvrc-choreonoid ros-melodic-mc-rtc-*

# Install JRL dependencies
#WORKDIR /root/lib
##RUN git clone --recursive https://github.com/jrl-umi3218/Eigen3ToPython \\
#ayumi:~/Software/Eigen3ToPython/build$ cmake .. -DCMAKE_BUILD_TYPE=Release
#ayumi:~/Software/Eigen3ToPython/build$ make -j4
#ayumi:~/Software/Eigen3ToPython/build$ sudo make install

#RUN git clone --recursive https://github.com/jrl-umi3218/mc_rtc.git \ 
#~/devel/src/mc_rtc \
#    && cd mc_rtc/ \
#    && mkdir -p build \
#    && cd build \
#    && cmake .. -DCMAKE_BUILD_TYPE=Release \
#    && make -j$(nproc) \
#    && make install
##    && ./build_and_install.sh
# Make sure you have required tools
#RUN apt update \
#    && sudo apt install apt-transport-https lsb-release ca-certificates gnupg \
#    # Add our key
#    && apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key 892EA6EE273707C6495A6FB6220D644C64666806 \
#    # Add our repository
#    && sh -c 'echo "deb https://dl.bintray.com/gergondet/multi-contact-release $(lsb_release -sc) main" | tee /etc/apt/sources.list.d/multi-contact.list'
## Update packages list
#sudo apt update
## Install packages
#sudo apt install libmc-rtc-dev mc-rtc-utils python3-mc-rtc
## Assuming you have a ROS distribution mirror setup
#sudo apt install ros-melodic-mc-rtc-plugin

#Install eigen-quadprog
#WORKDIR /root/lib
#RUN git clone --recursive https://github.com/jrl-umi3218/eigen-quadprog.git \#~/devel/src/eigen-quadprog \
#    && mkdir -p ~/devel/src/eigen-quadprog/build \
#    && cd ~/devel/src/eigen-quadprog/build \
#    && cmake ../ -DCMAKE_BUILD_TYPE=RelWithDebInfo \
#    && make -j${nproc} \
#    && make install
# Make sure you have required tools
#RUN apt update \
#    && apt install apt-transport-https lsb-release \
#    # Add our key
#    && apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key 892EA6EE273707C6495A6FB6220D644C64666806 \
#    # Add our repository (stable versions)
#    && sh -c 'echo "deb https://dl.bintray.com/gergondet/multi-contact-release $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/multi-contact.list' \
#    # Use this to setup the HEAD version
#    # sudo sh -c 'echo "deb https://dl.bintray.com/gergondet/multi-contact-head $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/multi-contact.list'
#    # Update packages list
#    && apt update \
#    # Install packages
#    && apt install libeigen-quadprog-dev

#Install copra
#WORKDIR /root/lib
#RUN git clone --recursive https://github.com/jrl-umi3218/copra.git \#~/devel/src/copra \
#    && mkdir -p ~/devel/src/copra/build \
#    && cd ~/devel/src/copra/build \
#    && cmake ../ -DCMAKE_BUILD_TYPE=RelWithDebInfo \
#    && make -j$(nproc) \
#    && make install

#WORKDIR /root/
RUN apt-get update -y \
    && apt-get install -y f2c gettext liblapack-dev libomniorb4-dev libyaml-dev omniidl omniidl-python 

#Install OpenRTM
#WORKDIR /root/lib
#RUN wget https://github.com/OpenRTM/OpenRTM-aist/releases/download/svn/RELEASE_1_1_2/OpenRTM-aist_1.1.2_ubuntu`lsb_release -rs`_amd64_package.tar.gz \
#    && tar xvzf OpenRTM-aist_1.1.2_ubuntu`lsb_release -rs`_amd64_package.tar.gz \
#    && cd OpenRTM-aist_1.1.2_ubuntu`lsb_release -rs`_amd64_package \
#    && dpkg -i *.deb

#WORKDIR /root/lib
#RUN wget https://github.com/OpenRTM/OpenRTM-aist-Python/releases/download/svn%252FRELEASE_1_1_2/OpenRTM-aist-Python_1.1.2_ubuntu`lsb_release -rs`_amd64_package.tar.gz \
#    && tar zxvf OpenRTM-aist-Python_1.1.2_ubuntu`lsb_release -rs`_amd64_package.tar.gz \
#    && cd OpenRTM-aist-Python_1.1.2_ubuntu`lsb_release -rs`_amd64_package \
#    && dpkg -i *.deb

#Install OpenHRP3
#WORKDIR /root/lib
#RUN git clone --recursive https://github.com/fkanehiro/openhrp3.git ~/devel/src/openhrp3 \
#    && mkdir -p ~/devel/src/openhrp3/build \
#    && cd ~/devel/src/openhrp3/util \
#    && ./installPackages.sh packages.list.ubuntu.`lsb_release -rs` \
#    && cd ../build \
#    && cmake .. -DCMAKE_BUILD_TYPE=RelWithDebInfo \
#    && make -j$(nproc) \
#    && make install

#Install hrpsys-base
#WORKDIR /root/lib
#RUN git clone --recursive https://github.com/fkanehiro/hrpsys-base.git ~/devel/src/hrpsys-base \
#    && mkdir -p ~/devel/src/hrpsys-base/build \
#    && cd ~/devel/src/hrpsys-base/build \
#    && cmake .. -DCMAKE_BUILD_TYPE=RelWithDebInfo \
#    && make -j{nproc} \
#    && make install

#Install Choreonoid
#WORKDIR /root/lib
#RUN git clone --recursive https://github.com/s-nakaoka/choreonoid.git ~/devel/src/choreonoid \
#    && mkdir -p ~/devel/src/choreonoid/build \
#    && cd ~/devel/src/choreonoid/build \
#    && cmake .. -DCMAKE_BUILD_TYPE=RelWithDebInfo \
#    && make -j$(nproc) \
#    && make install

#Install mc_openrtm
#WORKDIR /root/lib
#RUN git clone --recursive https://github.com/jrl-umi3218/mc_openrtm.git ~/devel/src/mc_openrtm \
#    && mkdir -p ~/devel/src/mc_openrtm/build \
#    && cd ~/devel/src/mc_openrtm/build \
#    && cmake ../ -DCMAKE_BUILD_TYPE=RelWithDebInfo \
#    && make -j$(nproc) \
#    && make install

#Install LIPMWalking controller
#WORKDIR /root/
#RUN git clone --recursive https://github.com/jrl-umi3218/lipm_walking_controller.git ~/devel/src/lipm_walking_controller \
#    && mkdir -p ~/devel/src/lipm_walking_controller/build \
#    && cd ~/devel/src/lipm_walking_controller/build \
#    && cmake ../ -DCMAKE_BUILD_TYPE=RelWithDebInfo \
#    && make -j$(nproc) \
#    && make install
WORKDIR /root/catkin_ws
CMD [ "bash" ]
