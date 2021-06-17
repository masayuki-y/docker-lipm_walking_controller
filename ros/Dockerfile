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
#       wget \
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
    && apt install -y python-eigen python3-eigen libcopra-dev libmc-rtc-dev mc-rtc-utils python3-mc-rtc  jvrc-choreonoid ros-melodic-mc-rtc-*

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
WORKDIR /root/lib
RUN git clone --recursive https://github.com/jrl-umi3218/mc_openrtm.git ~/devel/src/mc_openrtm \
    && mkdir -p ~/devel/src/mc_openrtm/build \
    && cd ~/devel/src/mc_openrtm/build \
    && cmake ../ -DCMAKE_BUILD_TYPE=RelWithDebInfo \
    && make -j$(nproc) \
    && make install

#Install LIPMWalking controller
WORKDIR /root/
ADD ./lipm_walking_controller /root/lipm_walking_controller
#RUN git clone --recursive https://github.com/jrl-umi3218/lipm_walking_controller.git ~/devel/src/lipm_walking_controller \
RUN cd ./lipm_walking_controller \
    && mkdir -p build \
    && cd build \
#    && mkdir -p ~/devel/src/lipm_walking_controller/build \
#    && cd ~/devel/src/lipm_walking_controller/build \
    && cmake ../ -DCMAKE_BUILD_TYPE=RelWithDebInfo \
    && make -j$(nproc) \
    && make install

# Add thomas-schiex's PPA to install blender
# RUN add-apt-repository -y ppa:thomas-schiex/blender \
#    && apt-get update -y \
#    && apt-get -qq install -y blender

# Install wget command to install blender2.78
WORKDIR /root/
RUN apt-get update \
    && apt-get install -y wget

# Install Blender_ver_2.78
WORKDIR /root/
RUN mkdir -p blender_2_78 \
    && cd  blender_2_78 \
    && wget https://download.blender.org/release/Blender2.78/blender-2.78c-linux-glibc219-x86_64.tar.bz2  \
    && tar -jxvf blender-2.78c-linux-glibc219-x86_64.tar.bz2 blender-2.78c-linux-glibc219-x86_64 \
    && mv blender-2.78c-linux-glibc219-x86_64 $root/blender2.78 \
    && mv $root/blender2.78 /opt/ \
    && ln -s /opt/blender2.78/blender /usr/bin/blender

#    && cd ~/blender_2_78/blender-2.78c-linux-glibc219-x86_64 \
#    && apt -y build-dep blender \
#    && apt -y install \
#    libx11-dev \
#    libxi-dev \
#    libsndfile1-dev \
#    libopenexr-dev \
#    libjpeg-dev \
#    libopenal-dev \
#    libalut-dev \
#    libglu1-mesa-dev \
#    libsdl-dev \
#    libfreetype6-dev \
#    libavdevice-dev \
#    libavformat-dev \
#    libavutil-dev \
#    libavcodec-dev \
#    libswscale-dev \
#    libx264-dev \
#    libxvidcore-dev \
#    libmp3lame-dev \
#    libspnav-dev



# Install Blender addon by zip
WORKDIR /root/
RUN mkdir -p addons \
    && cd addons \
    && wget https://gite.lirmm.fr/multi-contact/robot_script/-/archive/master/robot_script-master.zip

# Install Blender addon with git clone
WORKDIR /root/
RUN mkdir -p .config/blender/2.78 \
    && mkdir -p .config/blender/2.78/scripts/addons \
    && cd .config/blender/2.78/scripts/addons \
    && git clone --recursive https://gite.lirmm.fr/multi-contact/robot_script.git \
    && cd ~/.config/blender/2.78/scripts/addons/robot_script \
    && cp -r blender_addons/io_qconvex/  /root/.config/blender/2.78/scripts/addons

# Install Blender moedel
WORKDIR /root/
RUN mkdir blender_model \
    && cd blender_model \
    && wget  https://jrl-umi3218.github.io/mc_rtc/tutorials/advanced/data/blender_model_final.blend

# wget shelf moedel as wrl from github
WORKDIR /root/
RUN mkdir shelf_model \
    && cd shelf_model \
    && git clone https://github.com/masayuki-y/Test-model-file-with-wget.git \
    && cd Test-model-file-with-wget \
    && git checkout add_wrl_files \
    && apt -y install emacs \
    && git pull

# git clone repository
WORKDIR /root/
RUN mkdir github \
    && cd  github\
    && git clone https://github.com/masayuki-y/mc_rtc_tutorial_controller.git \
    && git config --global user.name "masayuki-y" \
    && git config --global user.email "yamada.masayuki.yk6@is.naist.jp" \
#    && git clone https://github.com/masayuki-y/mc_rtc_tutorial_controller.git \
    && git init \
    && cd  /root/github/mc_rtc_tutorial_controller \
    && git fetch --all \
#    && git checkout controll_EF
    && git checkout reach_box



#clone repository and make install
#WORKDIR /root/
#RUN mkdir Mygithub \
#    && cd Mygithub \
#    && git config --global user.email "yamada.masayuki.yk6@is.naist.jp" \
#    && git clone  https://61ca76807ac5b994e1d5ad3adab0ceb2fe22f166:@github.com/masayuki-y/mc_rtc_tutorial_controller.git \
#    && git clone https://61ca76807ac5b994e1d5ad3adab0ceb2fe22f166:x-oauth-basic@github.com/masayuki-y/mc_rtc_tutorial_controller.git \
#    && git clone https://github.com/masayuki-y/mc_rtc_tutorial_controller.git \
#    && git checkout EF_controller


#Install mc_hrp4j
#WORKDIR /root/
#ADD ./mc_hrp4j /root/mc_hrp4j
#RUN cd ./mc_hrp4j \
#    && mkdir -p build \
#    && cd build \
#    && cmake .. \
#    && make -j$(nproc) \
#    && make install
WORKDIR /root/catkin_ws
CMD [ "bash" ]

WORKDIR /root/
ARG GITHUB_USER
ARG GITHUB_TOKEN
RUN touch /root/.netrc \
    && echo machine github.com >> /root/.netrc \
    && echo login $GITHUB_USER >> /root/.netrc \
    && echo passowrd $GITHUB_TOKEN >> /root/.netrc

#WORKDIR /root/catkin_ws/src/
#RUN git clone https://gite.lirmm.fr/mc-hrp4/hrp4j_description.git　\
#    && catkin build -j4 \
#    && source devel/setup.bash \
#    && cd \
#    && mkdir gitlab \
#    && git clone https://gite.lirmm.fr/mc-hrp4/mc_hrp4j.git \
#    && cd mc_hrp4j \
#    && mkdir build \
#    && cd build \
#    && cmake .. \
#    && make \
#    && sudo make install \
#    && rm /root/.netrc


#git clone & catkin build hrp4j_description
#WORKDIR /root/catkin_ws/src
#RUN git clone https://gite.lirmm.fr/mc-hrp4/hrp4j_description.git \
#    && cd .. \
#    && catkin build -j4 \
#    && source devel/setup.bash

#git clone & catkin build hrp4j_description
#WORKDIR /root/catkin_ws/src
#ARG GITHUB_USER
#ARG GITHUB_TOKEN
#RUN git clone https://gite.lirmm.fr/mc-hrp4/hrp4j_description.git \
#    && cd .. \
#    && catkin build -j4 \
#    && source devel/setup.bash

#git clone mc_hrp4j
#WORKDIR /root/
#ARG GITHUB_USER
#ARG GITHUB_TOKEN
#RUN mkdir gitlab \
#    && git clone https://gite.lirmm.fr/mc-hrp4/mc_hrp4j.git \
#    && cd mc_hrp4j \
#    && mkdir build \
#    && cd build \
#    && cmake .. \
#    && make \
#    && sudo make install

#Add a mc_rtc configulation file
WORKDIR /root/
RUN mkdir -p ~/.config/mc_rtc/ \
    && touch ~/.config/mc_rtc/mc_rtc.yaml

# Made controller
WORKDIR /root/
RUN mc_rtc_new_controller my_first_controller MyFirstController \
    && cd my_first_controller \
    && mkdir -p build \
    && cd  \
    && cd github/mc_rtc_tutorial_controller


#set up for using catkin build
WORKDIR /root/
RUN apt install -y python-catkin-tools


WORKDIR  /root/github/mc_rtc_tutorial_controller/reach_box
RUN  cd src \
     && cp -r .  /root/my_first_controller/src

WORKDIR /root/.config/mc_rtc
RUN cp /root/github/mc_rtc_tutorial_controller/reach_box/mc_rtc.yaml .


#WORKDIR /root
#RUN mkdir ModelFiles \
#    && cd ModelFiles \
#    && git clone https://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:x-oauth-basic@github.com/masayuki-y/Model-files.git



WORKDIR /root
