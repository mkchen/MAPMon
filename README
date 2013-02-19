/*
 * MAP-E CE Monitoring Scripts (MAPMon)
 * Version: 1.0
 * Author:  Maoke Chen (fibrib@gmail.com)
 */

This set of scripts is designed for monitoring the NAPT and TCP port sharing 
behaviour of the MAP CE. The author doesn't guarantee it is able to well work 
for the commercial use in the product networking environment. 

Throughout this document, the "monitor" refers to the UNIX/Linux host 
where MAPMon is to execute. 

1. Requirements

Following conditions should be satisfied as the prerequisite of running the 
MAPMon scripts: 
 - tcpdump is installed in the CE
 - ssh daemon is running on the CE
 - root access through ssh is available on the CE
 - gawk, R, ImageMagick is installed on the monitor
 - outband connection (e.g., native IPv6 connection without going through the 
  MAP functionality) is available between the CE and the monitor. 

2. Installation 

Not needed but copy the following scripts in a specified working directory: 
 - stat_lan 
 - stat_wan
 - plotit

Ensure that all the scripts having the permission to execute. 

3. Usage

3.1 Configure the script

In the stat_lan script, it is needed to configure the CE address for the ssh 
and the private address pool used by the CE for the LAN it serves as router. 
Modify the following two lines according to your environment: 

 CE=2403:9200:fffe::65
 LANPRV=192.168.1/24

In the stat_wan script, CE address and the end user IPv6 prefix are to be 
configured. Modify the following lines according to your environment: 

 CE=2403:9200:fffe::65
 RULE6P=2403:9200:fffe:fff4::/62

In the plotit script, modify the directories for the input and output files: 

 IDIR=/home/M/development
 ODIR=/var/www/html/data

Temporary files are stored in the /tmp directory until the script is finished. 
Please encure that the caller of the plotit script can write in both $IDIR and
$ODIR. 

3.2 Run the script for tcpdump 

  ./stat_wan
  ./stat_lan

It is surely needed to apply the root password of the CE. 

3.3 Call plotit to draw plots 

The usage of the plotit script is as follows: 

    plotit ssid [-d {all|day|hour}] [yyyy-mm-dd [HH:MM]]

where, 
  ssid 
	the session id of this run, which is useful to distinguish user 
	accesses to the plotit tools through, e.g., a web page. It is 
	encourage to apply random session id for this purpose and, when
	calling from a cgi script, to keep the session id identical unless 
	the browser is restarted. 
  -d {all|day|hour}
	the duration of the observation display. default is "hour", e.g., 
 	3600 seconds. There are some other available option but may less 
	used: 
	. 4 hours
	. 15 minutes
	. 5 minutes
	. 1 minute
	"-d all" means display all the records since the record was started. 
  [yyyy-mm-dd [HH:MM]] 
	the starting time of the display. If empty, the script draw for the 
	data until now. 

4. Output

  xxxx.s.png
	the graph for the session behaviours within the specified duration 
	since the specified date or until now. Session behaviours include: 
	. number of all sessions requested in the private LAN that the CE 
	  serves; 
	. number of all sessions actually established between the CE and 
	  the destinations
	. number of port in use for the public address of the CE
	. number of actually connected destination addresses, for comparison. 
  xxxx.a.png
	the graph for the address behaviours within the specified duration 
	since the specified date or until now. Address behaviours include: 
	. number of destination addresses the hosts in LAN are to connect
	. number of actually connected destination addresses
	. number of force port recycle happening in a second
	. number of hosts in the LAN actively making these connections. 

Any questions/comments/recommendations are welcome to send to the author's 
mail address. 

(c) Maoke Chen, FreeBit Co. Ltd. 2013
