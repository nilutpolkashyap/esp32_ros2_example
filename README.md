# 

## New Project in ESP-IDF
I created a new project in ESP-IDF using the 'getting-started/sample_project" template. 

**Used **'micro_ros_espidf_component'** as component. 

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
Commit : https://github.com/nilutpolkashyap/esp32_ros2_example/commit/1ca1df4b936e613afcd0ff83152ab82c29210fae

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

Commit : https://github.com/nilutpolkashyap/esp32_ros2_example/commit/19253bae383c29af977ed0321aa9b75ebaef46a0

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

## Working with 'micro_ros_espidf_component/examples/int32_publisher_custom_transport'

### Steps:
- Make changes to 'colcon.meta' file inside 'components/micro_ros_espidf_component'
```
cd components/micro_ros_espidf_component/
sed -i 's/DRMW_UXRCE_TRANSPORT=udp/DRMW_UXRCE_TRANSPORT=custom/' colcon.meta
```
- Type **'idf.py clean-microros'** inside the project to clean and rebuild all the micro-ROS library
- Copied the code from 'int32_publisher_custom_transport/main/main.c' into 'esp32_ros2_example/main/main.c'
- Copied 'Kconfig.projbuild' file inside 'esp32_ros2_example/main' directory
- Copied 'esp32_serial_transport.h' and 'esp32_serial_transport.c' files inside 'esp32_ros2_example/main' directory
- Updated 'main/CMakeLists.txt' to include 'esp32_serial_transport.c'
- Copied 'app-colcon.meta' and 'colcon.meta' files from 'int32_publisher_custom_transport' inside 'esp32_ros2_example' directory
- Type **'idf.py menuconfig'** and then changed 'micro-ROS network interface select' to 'Micro XRCE-DDS over UART' option inside 'micro-ROS settings'
- In **idf.py menuconfig**, changed both **UART TX pin** and **UART RX pin** to **'0'** inside 'micro-ROS settings -> UART settings'

### Folder structure
```
├── CMakeLists.txt
├── components
|   └── micro_ros_espidf_component
├── main
│   ├── CMakeLists.txt
    ├── component.mk
    ├── esp32_serial_transport.c
    ├── esp32_serial_transport.h
    ├── Kconfig.projbuild
│   └── main.c
├── app-colcon.meta
└── README.md                  
```

Commit : https://github.com/nilutpolkashyap/esp32_ros2_example/commit/83998dedf83ea90b99eb060f44d2a6cd30a54f18

### Building and flash the project:
```
idf.py build
idf.py flash -p <MY_PORT>
```
