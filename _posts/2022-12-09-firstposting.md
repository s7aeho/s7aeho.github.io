---
layout: post
title: TI reference 정리 및 분석
author: lucas
date: 2022-12-12 13:37:00 +0800
categories : [Radar, TI]
tags: [radar, ti, iwr6843, iwr6843isk-ods]
pin: true
---

## **TI reference**
--------------
### **1. overhead mount occupancy**

### **2. DCA1000EVM Command and Data Format**
* The DCA1000EVM follows UDP protocal and supports 14 predefined commands. The configuration and status of the DCA1000EVM are communicated through the configuration port. The data port is used to transfer raw mode/data separated mode data.

#### ***2-1 DCA1000EVM Command Format***
* The DCA1000EVM receives a command from the host through the configuration port, and sends back the 
response in the same port.
The Command Request protocol consists of the following:  

>*    Header  
    a.  Header
    b.  Command code
    c.  Data size
>*    Data
>*   Footer  

![command format1](\image\Ti\DCA1000\dca1000-command-format.png "command format1")  

* The Command Response protocol consists of the following:
>*    Header   
    a.  Header
    b.  Command code
>*    Status
>*    Footer

![command format2](\image\Ti\DCA1000\dca1000-command-format2.png "command format2")

Command supported in the DCA1000EVM are listed in Table 12.


* **Table 12. Supported Commands**

|__Command__|__Command Code__|
|-----------|----------------|
|RESET_FPGA_CMD_CODE|0x01|
|RESET_AR_DEV_CMD_CODE|0x02|
|CONFIG_FPGA_GEN_CMD_CODE|0x03|
|CONFIG_EEPROM_CMD_CODE|0x04|
|RECORD_START_CMD_CODE|0x05|
|RECORD_STOP_CMD_CODE|0x06|
|PLAYBACK_START_CMD_CODE|0x07|
|PLAYBACK_STOP_CMD_CODE|0x08|
|SYSTEM_CONNECT_CMD_CODE|0x09|
|SYSTEM_ERROR_CMD_CODE|0x0A|
|CONFIG_PACKET_DATA_CMD_CODE|0x0B|
|CONFIG_DATA_MODE_AR_DEV_CMD_CODE|0x0C|
|INIT_FPGA_PLAYBACK_CMD_CODE|0x0D|
|READ_FPGA_VERSION_CMD_CODE|0x0E|

#### ***2-2 DCA1000EVM Data Format***
* The DCA1000EVM sends raw mode/data separated mode tata to the host through the data port.
    * `Raw mode data format : the DCA1000EVM sends raw mode data in the following format.`
    ![data format1](\image\Ti\DCA1000\dca1000-data-format1.png "data format1")  
    * `Data separated mode data format: the DCA1000EVM sends data separated mode data in the following format.`
    ![data format2](\image\Ti\DCA1000\dca1000-data-format2.png "data format2")  

#### ***2-3 Stored File Format***
* Raw mode data format: in raw mode, the file is stored in the following format:
    * `Without sequence number:`
    ![Raw mode format1](\image\Ti\DCA1000\dca1000-stored-file-format1.png "Raw mode format1")  
    * `With sequence number:`
    ![Raw mode format2](\image\Ti\DCA1000\dca1000-stored-file-format2.png "Raw mode format2")  
* Data separated mode data format: in data separated mode, the file is stored in the following format:
    * `Without sequence number:`
    ![Data separated mode format1](\image\Ti\DCA1000\dca1000-separated-mode-format1.png  "data separated mode format1")  
    * `With sequence number:`
    ![Data separated mode format2](\image\Ti\DCA1000\dca1000-separated-mode-format2.png "data separated mode format2")  



