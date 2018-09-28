UPDATE:2018.9.28

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

The update of this version includes below:

1. Add dfu feature of long-distance via NB-IOT or 4G/3G/2G. We test on GSM with China Mobile, you should use your operator. Here the RAK8212 moudle is as TCP Listener for recieving update bin file, and remote server is as a client to send cmd and file. Must use the Transparent Access Mode of BG96.


2. Integrate the dfu task in application, and provide the bootloader code for assist in dfu

3. Use the dual_bank type dfu of nRF52832, and the app firmware is about 87k now. So the max size of your firmware is better less than 120k

4. You should do some preparatory work when develop your firmware below:

   4.1 Generate bootloader setting and download to the flash at 0x7F000 (with the firmware you want to update) with nrfutil
   
   4.2 When you compile and can get the hex file of firmware, so generate the bin file and dat file with nrfutil
   
   4.3 Because the signature is debuging now, the code just support update directly.
   
   4.4 RTT Viewer is used for displaying log, and if speed is fast ,it will halt. But don't worry, check your program whether is running normally or not.
   
   The guide of use nrfutil of nordic is below: 
   
   https://infocenter.nordicsemi.com/index.jsp?topic=%2Fcom.nordic.infocenter.tools%2Fdita%2Ftools%2Ftools.html

5. DFU PROCESS
   
   5.1 Build the tcp connect with Transparent Access Mode
   
   5.2 Remote client send cmd ("update") to RAK8212
   
   5.3 RAK8212 will response "please send dat file" (this is for signature verify, just ignore for this version)
   
   5.4 Remote client cmd("bin") to RAK8212, and 8212 enter recieve bin file mode 
   
   5.5 Remote client wait for at least 30s and begin send bin file 
   
   5.6 RAK8212 recieve bin 1500 byte/packet and when complete, it will reset from boot
   
   5.7 Your new firmware will successfully run.
   
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++


UPDATE:2018.8.31

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++


The update of this version includes below:

1. open NRF log to debug expediently

2. add a BLE demo task. if want to test, please download the nrf connect app to your phone from below:

https://www.nordicsemi.com/eng/Products/Nordic-mobile-Apps/nRF-Connect-for-Mobile

3. the nodic ble advertising is really different from ohters. First, it advertise in fast mode, when time-out,to slow mode.If no connect, 
enter idle mode and deep sleep mode to save power. When wake up,it will lead to a reset...... so consider the situation when creat your ble task.


++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++


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
    
    WisLTE details is in http://www.rakwireless.com/en/download/Cellular/WisLTE
    
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
   
   4.4 use J-link RTT Viewer to watch client running log like below:
   
   ![](https://github.com/RAKWireless/RAK8212_itracker_firmware_based_on_nRF5SDK15.0_freertos/blob/master/20180827122232.png)
 
 
   ![](https://github.com/RAKWireless/RAK8212_itracker_firmware_based_on_nRF5SDK15.0_freertos/blob/master/20180827122253.jpg)
   



