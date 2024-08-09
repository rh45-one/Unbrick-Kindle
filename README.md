# How I fixed a bricked Kindle after a failed jailbreak attempt.<br>

#### Disclaimer: I am not responsible if any further damage occurs to your device while following this guide. Follow it at your own risk.<br>

### Please, do not share this guide without mentioning its author and including a link to my GitHub profile.<br>

## What happened?
I was recently gifted a family member’s old Kindle Paperwhite (6th Generation).
After reading about Kindle jailbreaks for a while, I figured it was time to try it out on my own device. Unfortunately, it turned out my Kindle’s firmware version (5.12.2.2) was not supported yet. <br>

During the preparation for the install, an unknown error popped.<br>

I then decided to perform a factory reset (through the option in the device settings) to remove my relative’s Amazon account and books.<br>
Before performing the factory reset, I was supposed to delete all jailbreak-related files from the Kindle (which I didn’t do). I believe this is what bricked the device.<br>

After the reset, the kindle entered a boot loop that lasted approximately 5 minutes, after which I was greeted by an error screen which provided no useful information:<br>

" Repair needed<br>
—-—-—-—-—-—-—-—-—-—-—-—-—-<br>
!<br>
Your Kindle Needs Repairing.<br>
Please contact Kindle Customer Service at http://www.amazon.com/devicesupport<br>
Repair Code:2<br>
Version:371510038<br>
DSN: ##CENSORED## "<br>
<br>
## Required tools:
The following tools and skills are required throughout this guide:<br>

•	Serial to USB TTY board - I built mine simply by adding a 1.8V LDO Rectifier to a 5v Serial to USB TTY (running an FTDI chip FT232RL) for about 7€ with the help of the following guide: https://ebookrepairs.com/kindle-tips/how-can-i-connect-a-serial-port-to-a-kindle/)<br>

•	Soldering Iron and tin (a basic one with a fine tip will do)<br>

•	Basic soldering skills - although the job requires precision, it really wasn’t challenge (despite having barely any soldering experience myself)<br>

•	Computer with any OS - I used Ubuntu for its “screen” serial monitor, but any serial monitor program for Windows or MacOS will work.<br>

•	Micro USB to USB-A cable – It must have data transmission capabilities. Avoid using a thin, cheap, unreliable one.<br>
<br>
## Steps: 

1.	Take the Kindle apart, solder 3 wires to the board’s serial pads and connect the other ends to the corresponding pins on the serial monitor as shown [here](https://raw.githubusercontent.com/OhShoot01/Unbrick-Kindle/main/soldered_connections.png).
#### Note: Instead of using the ground pad, the ground line can be soldered to a heat shield.
 <br>
2.	Connect the serial adapter to a computer and open the serial monitor program. Set the baud rate to 115200 and start the connection. 

3.	You should also connect the Kindle to the computer using the charging cable.

4.	Power on the device and carefully watch the console. At some point it will slow down. Soon after that, you will see a line that reads “Press [ENTER] for recovery menu…”. Quickly press ENTER on your keyboard. [The following menu will then be displayed](https://raw.githubusercontent.com/OhShoot01/Unbrick-Kindle/main/serial_menu.png)<br>
    Type “e” and hit enter. You should do this before the 10 second countdown reaches 0. Otherwise, the menu will close and you will have to start over.

6.	A new message like “FAT mounted” should appear with only two options: “done” and “reboot”. Leave the console as it is. 
Open your computer’s file explorer and navigate to the internal Kindle storage.

7.	Create a text (.txt) document named DO_FACTORY_RESTORE. Now delete the .txt extension.
The inside of the file should remain empty, you must not write anything in it.

8.	Go back to the console and select “reboot”. After a few automatic reboots, you will be greeted by the first step of the kindle setup (language selection). Complete this step. 
The kindle will enter the boot loop once again. When it stops, it will display the same “Needs Repair” screen.

9.	Repeat step 3 (enter recovery menu and select “e” option).

10.	Drag and drop the latest firmware available for your specific device. 
You can find and download this from Amazon’s website. (https://www.amazon.com/gp/help/customer/display.html?nodeId=GKMQC26VQQMM8XSW).

11.	Once the “.bin” update file has been copied to the Kindle, go back to the console and select “done”.
If the recovery menu doesn’t show up again, you will have to repeat step 3 to enter it.
Select option “u” this time. The update will now begin.

   

#### Once this has been completed, you will be greeted by the Wi-Fi set-up menu. You may now finish to configuring your device. 

