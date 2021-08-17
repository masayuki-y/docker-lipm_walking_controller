# docker-lipm_walking_controller
## Installation & Set up

1. Install nvidia-docker2 & docker-compose
2. Clone this repository with necessary submodules
 ```
 $ git clone --recursive https://github.com/ayuguchi/docker-lipm_walking_controller.git
 $ cd ros/lipm_walking_controller
 $ git submodule update --init cmake/
 ```

3. Build docker
 ```
 $ docker-compose build
 ```

## How to use

1. Run docker
 ```
 $ docker-compose run ros bash
 ```

2. Add a mc_rtc configulation file
 ```
 $ mkdir -p ~/.config/mc_rtc/
 $ nano ~/.config/mc_rtc/mc_rtc.yaml
 ```
 ```
 {
  "MainRobot": "JVRC1",
  "Enabled": ["LIPMWalking"]
 }
 ```
3. Run some software
 ```
 $ roslaunch mc_rtc_ticker display.launch

 (open a new terminal)
 $ docker exec -it ${CONTAINER} bash 
 $ cd /usr/share/hrpsys/samples/JVRC1
 $ ./clear-omninames.sh
 $ choreonoid --start-simulation sim_mc.cnoid
 ```

4. To get more information, please see the following information.

https://jrl-umi3218.github.io/lipm_walking_controller/doxygen/HEAD/build.html#jvrc

https://github.com/stephane-caron/lipm_walking_controller/wiki
