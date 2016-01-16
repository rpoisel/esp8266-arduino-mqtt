ESP8266 Arduino CMake configuration
===========================================

This project demonstrates how to use the [ESP8266 CMake build environment](http://www.github.com/rpoisel/esp8266-cmake) to develop an Arduino project using CMake for ESP8266 controllers. A sample project using the [Arduino Client for MQTT](https://github.com/knolleary/pubsubclient) is being developed. 

Please read about the advantages using this build environment [here](http://www.github.com/rpoisel/esp8266-cmake).

# Prerequisites

Installing the required tools (compiler, flasher, SDKs, etc.) is documented at the original [ESP8266 CMake build environment](http://www.github.com/rpoisel/esp8266-cmake) page. 

# Preparing the source code

In order to refer to other projects, [git submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules) are being used in this build environment. Take your time to learn what git submodules are and how they work! It definitely pays on the long run. 

First, clone the sample project source recursively to get both a clone of the project source as well as clones of all referenced git repositories:

```
cd <directory-to-hold-the-source-tree>
git clone --recursive https://github.com/rpoisel/esp8266-arduino-mqtt.git
```

*TODO*: Explanation of the project files/directories layout

# Generating an Eclipse project

# Importing the Eclipse project into the IDE

# Building the project from the command-line

