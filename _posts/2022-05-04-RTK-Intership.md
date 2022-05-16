---
layout: post
authors: [cisse_tsyen]
title: 'RTK Internship'
image: /img/2022-05-04-RTK-Internship/DiagramRTK.png
tags: [IoT, RTK, cloud, testing]
category: IoT
comments: true
---
- [What is GNSS?](#What-is-GNSS)
- [What is RTK?](#What-is-RTK)
- [What is FLEPOS?](#What-is-FLEPOS)
- [NEO-M8P-2 RTK module + antenna](NEO-M8P-2-RTK-module-antenna)
- [How to connect correction data to the RTK-module (Windows)](#How-to-connect-correction-data-to-the-RTK-Module-Windows)
- [How to connect correction data to the RTK-module (Linux)](#How-to-connect-correction-data-to-the-RTK-Module-Linux)
- [Extra: Sending it to the cloud](Extra-Sending-it-to-the-cloud)

## What is GNSS?
#### EXPLAIN

## What is RTK?
#### EXPLAIN
## What is FLEPOS?
#### EXPLAIN
#### flepos mounpoint
table from word document!!!


## NEO-M8P-2 RTK module + antenna
#### EXPLAIN


## How to connect correction data to the RTK-Module (Windows)
#### Step 1:
Register for FLEPOS as in the section above. 
Once you are registered and have your login information you can get started.

#### Step 2:
Install [RTKLIB](http://www.rtklib.com/)

#### Step 3:
Once you have installed RTKLIB you can open the rtklaunch.exe. 
This is going to open a menu where you can run different applications.
Then you click on the RTKNAVI button, RTKNAVI allows us to connect to RTCM feeds from different providers. 
Here you click on the "I" button
{:refdef: style="text-align: center;"}
<img src="{{ '/img/2022-05-04-RTK-Internship/rtknavi.JPG' | prepend: site.baseurl }}" alt="rtknavi" class="image center" style="margin:0px auto; max-width:100%">
{: refdef}

In the Input Streams window click on the check box of the base station, here you indicate NTRIP Client (NTRIP stands for Networked Transport of RTCM via Internet Protocol ) from the dropdown window and choose RTCM3 as format. 
Then press the 3 small dots under Opt.

{:refdef: style="text-align: center;"}
<img src="{{ '/img/2022-05-04-RTK-Internship/InputStream.JPG' | prepend: site.baseurl }}" alt="InputStream" class="image center" style="margin:0px auto; max-width:100%">
{: refdef}

Then the NTRIP Client Options window comes up, here you enter the NTRIP Caster Host, port, mountpoint to be determined, User-ID/username, Password. 
Before determining the mountpoint press the button Ntrip..., here is the list of all possible Mountpoints.
Choose the mounpoint that fits your purpose best. 
**Note: NEO-M8P only works with RTCM 3.x.** 
I use FLEPOSVRS32GREC because it can use all GNSS systems and it is one of the two data streams most used by FLEPOS.
To use it copy the name of the Mountpoint you want to use into the Mountpoint box. 
Then you can close the Ntrip browser. 
When all the login information is entered click OK to close the NTRIP Client Options.
{:refdef: style="text-align: center;"}
<img src="{{ '/img/2022-05-04-RTK-Internship/NTRIPClient.JPG' | prepend: site.baseurl }}" alt="NTRIPClient" class="image center" style="margin:0px auto; max-width:100%">
{: refdef}

After this you indicate in the dropdown menu of "Transmit NMEA GPGGA to base station" Latitude and Longitude. 
Here you indicate the lat/long of the base station. 
Because the software of FLEPOS expects an NMEA GGA with the initial position of the GNSS receiver in order to generate a VRS (Virtual Reference Station) or NRS correction stream.
{:refdef: style="text-align: center;"}
<img src="{{ '/img/2022-05-04-RTK-Internship/GPGGA.JPG' | prepend: site.baseurl }}" alt="GPGGA" class="image center" style="margin:0px auto; max-width:100%">
{: refdef}
The Input Streams should be configured, you can close it by pressing OK. 
Then click on start to test the connection to the FLEPOS server.
{:refdef: style="text-align: center;"}
<img src="{{ '/img/2022-05-04-RTK-Internship/rtknaviBars.JPG' | prepend: site.baseurl }}" alt="rtknaviBars" class="image center" style="margin:0px auto; max-width:100%">
{: refdef}

EXPLAIN SERIAL WITH PHOTO OF THE MODULE!!!!!!!!!!!!!!!!!!!


## How to connect correction data to the RTK-Module (Linux)
It is the same principle as before but instead of a GUI in Windows we use a CUI in Linux.
You can find how to build the CUI apps and all associated commands in the [datasheet of RTKLIB](http://www.rtklib.com/prog/manual_2.4.2.pdf) from page 88 to 100
##### To build a specific app like RTKRCV (=RTKNAVI on Windows):
```
sudo git clone https://github.com/rtklibexplorer/RTKLIB.git
cd /home/pi/RTKLIB/app/consapp/rtkrcv/gcc
sudo make
sudo make install
```

##### To build all the apps:
```
sudo git clone https://github.com/rtklibexplorer/RTKLIB.git
cd /home/pi/RTKLIB/app/consapp
sudo make
sudo make install
```
I'm going to use the STR2STR app to ouput the correction data from FLEPOS to the RTK module.
This command is going to start the STR2STR app, set the NTRIP caster (FLEPOS) as an input.
Than its going to send a fix position to the NTRIP caster and set the serial port that is connected with the RTK module as an output.
```
sudo str2str -in ntrip://69845a001:Ordina2022\!@212.204.120.33:2101/FLEPOSVRS32GREC -p 51.05191220718147 4.909250985575229 19.0 -n 1 -out  serial://ttyAMA0:9600:8
```

## Extra: Sending it to the cloud
#### EXPLAIN