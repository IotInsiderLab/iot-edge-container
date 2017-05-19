# iot-edge-container
A containerized deployment of the [iot-edge](https://github.com/Azure/iot-edge) project from Microsoft.

*Instructions also available in [Chinese](README.zh-cn.md)*

## Building and Running

- Install [Docker](https://www.docker.com/) *(Community Edition is fine)* on the Desktop

  **or**

  run the following command from shell on the Raspberry Pi

  ```
  curl -sSL https://get.docker.com | sh
  ```
  *Note: You may need to use sudo if you get errors about permissions*

- Clone this repository locally with the following command

  ```
  git clone git@github.com:IotInsiderLab/iot-edge-container.git
  ```

- [Create an IoTHub](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-create-through-portal) in the Azure Portal

- From the [Portal](https://portal.azure.com/) for your IoTHub use DeviceExplorer to create the 5 devices shown below

  ![](docs/DeviceExplorer.png)

- Edit the simulated_device_cloud_upload_lin.json file in your favorite text editor

  - replace ```<insert iothub name here>``` with the name of your IoTHub
  - replace ```<insert primary key here>``` for each of the 5 DockerDevices with the primary key for that device found in Device Explorer

- From your favorite command shell change to the local folder where you cloned this respository and run the following commands.

  ```
  docker build -t iot-edge -f Dockerfile-x86 .
  docker run -ti iot-edge
  ```

- From the shell in the container run the following command
  ```
  cd iot-edge/build
  samples/simulated_device_cloud_upload/simulated_device_cloud_upload_sample ../samples/simulated_device_cloud_upload/src/simulated_device_cloud_upload_lin.json
  ```
