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

Dans un premier temps créer un dossier dans /etc :

					$ sudo mkdir -p /etc/repo
	
Aller dans le dossier suivant :

					$ sudo cp -r /boot/ArmBot_C-main /etc/repo/

Se rendre dans le dossier :

					$ cd /etc/repo/ArmBot_C-main/raspberry_setup/
          
Exécuter la commande suivante : 
 					
					$ sudo ./start.sh ADRESSE_MAC_TELEPHONE

Durant le lancement du script une demande de changement de mot de passe pour l’utilisateur pi est demandé, il faut que le mot de passe possède au moins 8 caractères minimum, chiffres & lettres, minuscules & majuscules, caractères spéciaux (attention il faudra le rentrer 2 fois)  

Si la connexion à réussi alors le téléphone est connecté à la raspberry et la configuration est terminée et la raspberry va redémarrer.
