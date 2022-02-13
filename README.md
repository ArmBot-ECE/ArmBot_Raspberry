# Armbot-Raspberry

## Table of contents
* [Project Goal](#project-goal)
* [Raspberry Configuration Steps](#raspberry-configuration-steps)

## Project Goal

'*Duchenne muscular dystrophy (DMD) is a genetic disorder characterized by progressive muscle degeneration and weakness due to the alterations of a protein called dystrophin that helps keep muscle cells intact*'. 

([Muscular Dystrophy Association](https://www.mda.org/disease/duchenne-muscular-dystrophy) - Duchenne Muscular Dystrophy (DMD) - Diseases (2021, April 29))

Approximatly 4.78 people out of 100,000 poccess the DMD in the world. To help those people improve their autonomy, we decided to create a robotic arm, accessible and customizable. Our goal was to create an arm, controllable with an android app, and under a ~400€ budget, using a 3D printer. 

This project was possible thanks to [Niryo](https://niryo.com/fr/)'s 3D models of the arm, the FabLab of [ECE Paris](https://www.ece.fr/) school and [HandiTech](https://handitech-france.fr/).

**The usage of the arm is under the responsability of the user.**

To learn how to use our arm, please go through our [course](https://rise.articulate.com/share/YxWGhuafWEo22Ty-tBzGM7W94fOSDhKb#/).

You'll find further informations in our GitHub and all the ressources in the following [link](https://drive.google.com/drive/folders/1EEAC_9meE7mFTIsfq7AG75mwahTAs3Wy?usp=sharing).

Finally, dont miss to visit our [YouTube](https://www.youtube.com/channel/UCcuagSu5sPNIdyUf5VJzb_w) page.


## Raspberry Configuration Steps

Insert the SD card in your PC and format it using a dedicated software (f.e. "SD Card Formatter" on macOS and Windows).

Download Raspberry Pi OS on the following link :
https://www.raspberrypi.org/downloads/raspberry-pi-os/

Download the folder named "ArmBot_C-main" on our Github repository :
https://github.com/ArmBot-ECE/ArmBot_C.git 

Open the downloaded folder and using a terminal run the command "raspberry_setup". Then drag and drop the following 2 files from the folder to your desktop :

					wpa_supplicant.conf
					SSH

Once both files are on your Desktop, edit the file named wpa_supplicant.conf.

In there, replace the variable "MaBoxInternet" with the name of the box that the Raspberry Pi will be connecting to. Then replace "ClefSecurite" with your box's password. Make sure you keep the quotes while editing.

					country=fr
					update_config=1
					ctrl_interface=/var/run/wpa_supplicant
					network={
					scan_ssid=1
					ssid="MaBoxInternet"
					psk="ClefSecurite"
					}

Extract the OS image and move it to the SD card using Win32 Disk Imager (on Windows) or BalenaEtcher (on Mac).

Once the operation is done open your SD card and place in it the rest of the "ArmBot_C-main" folder.

Eject the SD card, take it and insert it into the Raspberry Pi. Then plug your HDMI and then the alimentation of the Raspberry and the OS installation will take care of itself. Make sure you plugged the HDMI first and then the power to make it work perfectly.

Once the installation is complete, connect to the Raspberry using the default user (pay attention to the fact that the default keyboard will be in QWERTY).

					login :  pi

					password : raspberry

Once connected to the machine, open a terminal and run the following command :
				
					$ sudo raspi-config 

Press "Enter" on "Localisation Options". 

Select the "Keyboard" option.

Choose then the "other" option and select "French" then once more select "French".

Choose the following option "Generic 105-Key (Intl)" and clic on "OK".

Select the option "The default for the keyboard layout" then clic on "OK".

Choose then "No compose key" and clic on "OK".


If you're still in the same menu as "French Keyboard Configuration", there is no need to execute the following command, if not, do it :

					$ sudo raspi-config 

Press "Enter" on "Localisation Options".

Chopse "WLAN Country" and choose "FR France" then clic on "OK".

Clic on "Finish". Once the black bar displays at the bottom do "CTRL + L".

Firstly create a folder in /etc using the following command :

					$ sudo mkdir -p /etc/repo

Then copy the downloaded folder in the created folder :

					$ sudo cp -r /boot/ArmBot_C-main /etc/repo/

 Move to the following folder :

					$ cd /etc/repo/ArmBot_C-main/raspberry_setup/

Then run the following command :

					$ sudo ./start.sh MY_PHONE_MAC_ADDRESS

While the script runs, you will be asked to change the password for the user "pi". Make sure the password you give is at least 8 characters long, has letters and numbers, upper and lower case, special characters. Keep in mind you'll have to write it twice.

If the connection succeeds then the phone is connected to the Raspberry and the configuration is done. the Raspberry will then reboot.
