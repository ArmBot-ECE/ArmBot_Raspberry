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

Insérer la carte SD dans son PC et la formatter avec un logiciel dédié 
ex : SD Card Formatter (accessible sur windows et mac) 

Télécharger Raspberry Pi OS à l’adresse suivante : 
https://www.raspberrypi.org/downloads/raspberry-pi-os/

Récupérer sur le dépôt https://github.com/ArmBot-ECE/ArmBot_C.git nommé “ArmBot_C-main”
Vérifier que tous les dossiers sont complets 

Ouvrir le dossier téléchargé et rentrer dans le dossier “raspberry_setup”. Puis prendre les 2 fichiers et les placer sur votre bureau :

					wpa_supplicant.conf
					SSH

Une fois les deux fichiers placés sur le bureau, éditer le fichier wpa_supplicant.conf ( Remplacer "MaBoxInternet" par le nom de la box où sera connectée la Rpi, et remplacer "ClefSecurite" par le mot de passe de la box. Pensez à bien garder les doubles quottes.)

					country=fr
					update_config=1
					ctrl_interface=/var/run/wpa_supplicant
					network={
					scan_ssid=1
					ssid="MaBoxInternet"
					psk="ClefSecurite"
					}

Extraire l’image de l’OS téléchargé et écrire cette dernière sur la carte SD 
ex : Win32 Disk Imager (Windows) ou BalenaEtcher (Mac)

Une fois l’opération terminé ouvrir la carte SD sur votre ordinateur et placer   le reste du dossier téléchargé “ArmBot_C-main” sur la carte SD

Éjecter la carte SD du PC, l’insérer dans la Rpi, puis alimenter cette dernière (il faut d'abord brancher le câble HDMI avant d’alimenter la raspberry). L’installation va se lancer seule.

Se connecter à la raspberry (attention le clavier est en qwerty)
						user : pi	password : raspberry

Une fois connecté à la machine tapper la commmande suivante : 
				
					$ sudo raspi-config 

Appuyer entrer sur le choix : 
					Localisation Options 
					
Sélectionner l’option : 
					Keyboard

Choisir l’option suivante : 
					Generic 105-Key (Intl) 
					
Choisir ensuite l’option : 
					other 

Sélectionner le pays “French” puis choisir à nouveau “french” 

Sélectionner le clavier : 
					The default for the keyboard layout 

Choisir ensuite :
					No compose key

Appuyer entrer sur le choix : 
					Localisation Options
					
Choisir “WLAN Country” et choisir “FR France” puis faire “OK”

Appuyer sur “Finish”, une fois que la barre noir apparait en-bas faire “CTRL + L”

Dans un premier temps créer un dossier dans /etc :

					$ sudo mkdir -p /etc/repo
	
Copier le dossier "ArmBot_C-main" dans le dossier suivant :

					$ sudo cp -r /boot/ArmBot_C-main /etc/repo/

Se rendre dans le dossier :

					$ cd /etc/repo/ArmBot_C-main/raspberry_setup/
          
Exécuter la commande suivante : 
 					
					$ sudo ./start.sh ADRESSE_MAC_TELEPHONE

Durant le lancement du script une demande de changement de mot de passe pour l’utilisateur pi est demandé, il faut que le mot de passe possède au moins 8 caractères minimum, chiffres & lettres, minuscules & majuscules, caractères spéciaux (attention il faudra le rentrer 2 fois)  

Si la connexion à réussi alors le téléphone est connecté à la raspberry et la configuration est terminée et la raspberry va redémarrer.
