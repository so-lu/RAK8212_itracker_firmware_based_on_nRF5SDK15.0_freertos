1. Overview

   This project is RAK8212 itracker firmware based on freertos and nRF52832 SDK 15.0.0, and perform a typical scence for sending and recieving data via NB-IOT. The internet is NB-IOT here, and the RAK8212 could be as the client or server. We use RAK8212 to be as a client and WisLTE as a server. Shown as below 
   
   
   ![](https://github.com/RAKWireless/RAK8212_itracker_firmware_based_on_nRF5SDK15.0_freertos/blob/master/20180827115712.png)
    

    
2. Code and client

    The code is for client, which RAk8212 provide gps location info and sensor data collection like below. In this project, sensor data and gps data update per 15s, then send to server via BG96.
    

    Integrated Quectel BG96 NB-IoT wireless communication Module, with GPS built-in.

    Integrated LIS3DH ultra low-power, high performance 3-axes “nano” accelerometer

    Integrated LIS2MDL ultra-low-power, high-performance 3-axis digital magnetic sensor.

    Integrated BME280 ultra low-power, high linearity, high accuracy sensors for pressure, humidity and temperature

    Integrated OPT3001 that measures the intensity of visible light
   
    Size 43mm x 38mm x 18mm

    Operation temperature -40°C to +85°C

    Power supply 3.5V to 18V (power at solar panel connector P2)

    
   Client connection(gps data is valid only outside building): 
    ![](https://github.com/RAKWireless/RAK8212_itracker_firmware_based_on_nRF5SDK15.0_freertos/blob/master/20180827102432.jpg)

3. Server command 

    Server is WisLTE moudle, which could be connected to PC and send AT commmand via usb by serial port, like below:
    ![](https://github.com/RAKWireless/RAK8212_itracker_firmware_based_on_nRF5SDK15.0_freertos/blob/master/20180827102445.jpg)
    The command may be different for different net operator, so every command detail could be seen on https://www.quectel.com/product/bg96.htm 
    
    WisLTE details is in http://www.rakwireless.com/en/download/Cellular/WisLTE)
    
4. Test environment 

    We use NB-IOT simcard provided by China Telecom, and you could contact your operator.
    ![](https://github.com/RAKWireless/RAK8212_itracker_firmware_based_on_nRF5SDK15.0_freertos/blob/master/20180827102455.jpg)


PS:

1. Project download

   Download the zip file to your folder, then download the nRF52832 SDK 15.0.0 (https://www.nordicsemi.com/eng/Products/Bluetooth-low-energy/nRF52832).
   
2. Program

   Find project path:
   ..\RAK8212_itracker_firmware_based_on_nRF5SDK15.0_freertos\src\nRF5_SDK_15.0.0_a53641a\itracker\ble_peripheral\itracker\pca10040\s132\arm5_no_packs
   
   
   Before download to your board,please ensure the SoftDevice has been programing via nRFgo-studio.
   
3. Version

   nRF52832 SDK:15.0.0
   
   SoftDevice  :6.0.0
   
   FreeRTOS    :10.0.0
   
4. Debug

   A demo task has been supplied for test below:
   
   4.1 collect sensors data per 15s    
   
   4.2 get gps data per 15s (data is valid only in open space)
   
   4.3 send data to server via NB-IOT (please contact your NB-IOT operator)
   
   Considering to the ram and dominant frequency(32kHz), new task size should not be large and the num of tasks should be as less as good.



