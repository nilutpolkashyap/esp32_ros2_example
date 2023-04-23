# _Sample project_

(See the README.md file in the upper level 'examples' directory for more information about examples.)

This is the simplest buildable example. The example is used by command `idf.py create-project`
that copies the project to user specified path and set it's name. For more information follow the [docs page](https://docs.espressif.com/projects/esp-idf/en/latest/api-guides/build-system.html#start-a-new-project)



## How to use example
We encourage the users to use the example as a template for the new projects.
A recommended way is to follow the instructions on a [docs page](https://docs.espressif.com/projects/esp-idf/en/latest/api-guides/build-system.html#start-a-new-project).

## Example folder contents

The project **sample_project** contains one source file in C language [main.c](main/main.c). The file is located in folder [main](main).

ESP-IDF projects are built using CMake. The project build configuration is contained in `CMakeLists.txt`
files that provide set of directives and instructions describing the project's source files and targets
(executable, library, or both). 

## New Project in ESP-IDF
I created a new project in ESP-IDF using the 'getting-started/sample_project" template. 

**Used 'micro_ros_espidf_component' as component. 

### Initial project folder structure:
```
├── CMakeLists.txt
├── components
|   └── micro_ros_espidf_component
├── main
│   ├── CMakeLists.txt
│   ├── component.mk
│   └── main.c
└── README.md                  This is the file you are currently reading
```

### Building the project:
```
idf.py set-target esp32
idf.py build
```

## Working with 'micro_ros_espidf_component/examples/int32_publisher'

### Steps:
- Copied the code from 'int32_publisher/main/main.c' into 'esp32_ros2_example/main/main.c'
- Copied 'Kconfig.projbuild' file inside 'esp32_ros2_example/main' directory
- **'idf.py menuconfig'** and then changed Wifi SSID and password inside 'micro-ROS settings'

### Folder structure
```
├── CMakeLists.txt
├── components
|   └── micro_ros_espidf_component
├── main
│   ├── CMakeLists.txt
    ├── component.mk
    ├── Kconfig.projbuild
│   └── main.c
└── README.md                  
```

### Building and flashing the project:
```
idf.py build
idf.py flash -p <MY_PORT>
idf.py monitor -p <MY_PORT>
```
Successfully built and flashed into the EPS32

### Output Recived (Success)
```
I (2884) wifi_station_netif: got ip:192.168.43.84
I (2884) wifi_station_netif: connected to ap SSID:my_ssid password:mypassword
```

## Working with 'micro_ros_espidf_component/examples/int32_publisher'