---
layout: post
title: "Getting the ISpindel Started"
date: 2018-03-18
---

As brewing beer is one of my passions, I was thinking about tuning/extending my equipment. After upgrading to 50 liters is no option due to space issues, I decided to build the [iSpindel](https://github.com/universam1/iSpindel). The iSpindel can be used for recording the fermentation of beer. After reading the instructions, I ordered the [DIY iSpindel](https://www.3d-mechatronics.de/de/ispindel-diy-set_151.html) set.

After receiving the electric components, I realised that I might have overestimated my soldering skills. Last tim I might have been soldering similar tiny parts goes back to 2002 during my apprenticeship. However, my joy for that project voted down my concerns.  

The soldering [manual at 3d-mechatronics](https://dl.dropbox.com/s/s95dsfn3c269hm1/DIY_Spindel_Anleitung_DE.pdf) is ok and briefly describes all steps that need to be performed. Whereas desoldering the diode was already fiddly desoldering the LED seemed to be almost impossible. However, somehow I managed to remove the LED from the gyro sensor. In addition, the temperature sensor has very small soldering joints. In contrast to the description on the vendors page, I could not solve the soldering in 15 minutes but more than an hour with interruptions. 

I was quite happy when I was finished and plugged in the power cable to charge the battery. Also a red light was glowing. Thus, I though that everything is ok. However, after charging turning on the iSpindel, nothing happened. I looked at the soldering joints, but could not detect any errors. I tried to detect the error with some measuring device but failed. After some further testing I somehow managed to start a short-circuit and some component started to burn. 

After that failure, I decided to get the spare parts and start the soldering from scratch. In addition, I bought a new soldering iron, as mine was not working properly. This time, the soldering went smoother, however the desoldering of the LED still is painful. This time after charging the battery not only a red led was showing up but also a blue one. In addition turning the switch off only the red light remained. That seemed to be some kind of success. After the battery was charged I switched on the iSpindel and the Wemos was blinking. 

The next step to finish the iSpindel project was to install the firmware. I followed the instruction on the [German Hobbybrauerforum](https://hobbybrauer.de/forum/viewtopic.php?f=58&t=13374), but could not succeed. The main issue is that the vendor of the chip only provides a driver for Windows but not for Mac (In the meantime there seems to be again some driver for Mac). Fortunately, I was able to find an old Windows machine. Here it was easy to flash the chip and install the firmware as described in the [documentation](https://github.com/universam1/iSpindel/blob/master/docs/Firmware.md):

  * Download and install driver: [CH341SER](https://github.com/HobbyComponents/CH340-Drivers/tree/master/CH341SER) 
  * Download most recent [firmware](https://github.com/universam1/iSpindel/raw/master/bin/)
  * Connect iSpindel to PC via USB (using the USB plug where the battery is NOT connected)
  * Switch on the iSpindel
  * Download and start [NodeMCU-Flasher](https://github.com/nodemcu/nodemcu-flasher/raw/master/Win32/Release/ESP8266Flasher.exe)
  * Select the correct COM port (check in Administrative Tools (Verwaltung in German) which port is selected for the CH340)
  * Within the Flasher also select the downloaded firmware (and disable the selection of the pre-enabled firmware)
  * Start the flashing!
  
Using the Windows machine that step works smoothly. After that step you can disconnect the iSpindel. I switched the iSpindel off and on again and then you can search for the WLAN named iSpindel and connect to you iSpindel. What a relief when I was able to connect to my iSpindel, after all these hurdles. Whereas from the interface I saw some value for the termperature there was a value of 0 for the gyrosensor. After asking in the hobbybrauerforum I got the answer to check again the soldering joints between the Wemos and the gyrosensor (see image). 

![gyrosensor](https://raw.githubusercontent.com/riedlma/riedlma.github.io/master/_posts/2018-03-18/iSpindel-bleading-wrong.png "iSpindel, bad soldering between Wemos and gyrosensor")

I desoldered the gyrosensor and tried my very best to solder as best as possible. Luckily, after connecting to the iSpindel again the gyrosensor was working! 

Ok the next thing you need to know is that you also need balancing weights to weight the iSpindel in such a way that is has the perfect angle within the liquid. According to the forum a degree of 20% or 25% is advised. As weights you can use the ones that are also used to balance the wheels of cars (just ask at the next garage for several 5g weights or order them at ebay). 





 
