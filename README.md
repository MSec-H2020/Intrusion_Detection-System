# Intrusion_Detection-System_Module
# Requirements
The provided software module was customized for the following IoT gateway test devices:

* OpenBlocks IoT BX1 Gateway Device 
     Raspberry-Pi  
     Firmware: installed version: 1.0.14-1 / OBSBX1 3.10.17-17
     Hardware: Intel Atom Processor (500MHz, 1024KB) 
     Software: Debian GNU/Linux - version 3.10.17-poky-edison 

# User Guides 
The following manufacturer guides are useful for installing and operating the OpenBlocks IoT gateways:  

* https://openblocks.plathome.co.jp/common/pdf/obsiot_developer_guide.pdf 
* https://openblocks.plathome.co.jp/common/pdf/obsiot_webui_setup_guide.pdf

# Download & Installation  

Download “installer.sh” file onto your Openblocks IoT gateway device and execute as follows:  

IoT-1# 	ls -l
total 52320
-rw-r--r--    1 	root root	    41404017	Mar 25 2021 	installer.sh

IoT-1# 	 ./installer.sh 

This will install all the customized files onto your IoT device. 

IoT-1# 	ls -l 
total 52344
-rwxr-xr-x	 1 	spp  spp	   1103 	Jan  1 2020 hardening.sh
drwxr-xr-x  4 	root root	   4096 	Mar 09 2021 installer
-rw-r--r--  1 	root root 41404017	Mar 25 2021 installer.sh
-rwxr-xr-x	 1 	spp  spp	    149 	Jan  1 2020 start_ids.sh
-rwxr-xr-x	 1 	spp  spp	    169 	Jan  1 2020 start_ips.sh
drwxr-xr-x  2 	root root	   4096 	Jan  1 2020 update 
-rw-r--r--  1 	root root	   1435 	Jan  1 2020 updater.py
-rw-r--r--  1 	root root	    227 	Nov 16 2020 version.yaml



# Verify Installation & Running 

* For Intrusion Detection System based security feature: 

IoT-1# 	ps aux | grep suricata

root???? 12551 98.6 14.2 157264 140196 ??????? Rs?? 19:57?? 0:20 suricata -v -i ppp0 -c /etc/suricata/suricata.yaml -D --pidfile /var/run/suricata_ips.pid

root ????12648? 0.0? 0.0?? 4972?? 728 ttyMFD2? S+?? 19:57?? 0:00 grep suricata

If command results in only “grep suricata” process, then use ./start_ips.sh command to start the /var/run/suricata_ips.pid process. 

* For default running of IDS security feature 

Once everything is configured and tested, then Add following commands in the default boot config file to enable security by default
For Protections Mode: 
    ./start_ips.sh
or
For Monitoring mode only 
    ./start_ids.sh 

The above commands will enable both Visualization Tool (Filebeat) and IDS/IPS security features to start whenever the IoT device gets booted. 

