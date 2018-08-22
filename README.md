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



