1. Project download

   Download the 8 zip file to your folder and uncompress together, then generate the project folder.
2. Program

   Find project path:
   ..\RAK8212_itracker_firmware_based_on_nRF5SDK15.0_freertos\src\nRF5_SDK_15.0.0_a53641a\itracker\ble_peripheral\itracker\pca10040\s132\arm5_no_packs
   
   Do not need any setting and compile drectly.
   
   Before download to your board,please ensure the SoftDevice has been programing via nRFgo-studio.
3. Version

   nRF52832 SDK:15.0.0
   
   SoftDevice  :6.0.0
   
   FreeRTOS    :10.0.0
   
4. Debug

   A demo task has been supplied for test below:
   
   4.1 collect sensors data per 10s    
   
   4.2 get gps data per 10s (data is valid only in open space)
   
   4.3 send data to server via NB-IOT per 10s (please contact your NB-IOT operator)
   
   Considering to the ram and dominant frequency(32kHz), new task size should not be large and the num of tasks should be as less as good.


PS:
Program the firmware of RAK8212

RAKWireless provides a whole firmware which is an example for RAK8212 module on their Github page: https://github.com/RAKWireless/RAK8212_itracker_firmware_based_on_nRF5SDK15.0_freertos.

This firmware is based on the newest nRF5 SDK 15.0.0 and Softdevice S132 v6.0.0. It includes a Softdevice S132 V6.0.0, a bootloader supported OTA-DFU, and an application for RAK8212 module. You can use this firmware directly on RAK8212 module to send “hello world” to your server via NB-IOT(refer to demo task).

Before our starting, we should install nRFgo Studio on our PC. It is a programing tool provided by Nordic. Surely, you can use any other programing tools too. https://www.nordicsemi.com/eng/Products/2.4GHz-RF/nRFgo-Studio/(language)/eng-GB

Program the firmware provided by RAKWireless to RAK8212 module directly

Firstly, let’s download the firmware from RAKWireless page(https://github.com/RAKWireless/RAK8212_itracker_firmware_based_on_nRF5SDK15.0_freertos), and compile drectly. Secondly, let’s select a programing method.

SWD interface

If there is no firmware on your RAK8212 module, you must select this method for programing. You can also select this method surely even if there is already a firmware on your RAK8212 module.

According to the picture above, we connect RAK8212 module with PC via ARM Emulator, and open nRFgo Studio on our PC. Then we select “nRF5x programing” in the Device Manager panel, and the following UI will be shown in front of us: 

We can click the “Erase all” button to erase the firmware which had been programed into our RAK8212 module before, and it doesn’t matter that we start to program without erasing the old firmware. Now, let’s program the firmware: Click the “Browse” button and select the firmware file which is a .hex file; image

Click the “program” button to start; image
