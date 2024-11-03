### Installation du Serveur DHCP sur Windows Server

#### Étape 1 : Installer le rôle DHCP
Ouvrir le Gestionnaire de serveur :

Dans le Gestionnaire de serveur, cliquez sur "Gérer" puis sur "Ajouter des rôles et des fonctionnalités" :

![addrole](https://github.com/user-attachments/assets/4359d6e3-4faa-4896-86e4-1c3afdf8b4ef)

Choisissez l'option "Installation basée sur un rôle ou une fonctionnalité" et poursuivez.

![type](https://github.com/user-attachments/assets/b49a1aed-297f-46df-8b29-2116c6353008)


Poursuivez directement, car le serveur local est déjà sélectionné.

![serverselection](https://github.com/user-attachments/assets/544193d9-7cf7-4ad5-bb1e-dc27eec00931)


Dans la liste des rôles, cochez "Serveur DHCP" et au sein de la fenêtre qui s'affiche, vérifiez que l'option "Inclure les outils de gestion" soit cochée. Elle permet d'ajouter la console de gestion DHCP sur le serveur. 

![dhcprole](https://github.com/user-attachments/assets/07492a1f-2e1f-48f5-9600-e86ba907586b)
 
Cliquez sur "Ajouter des fonctionnalités".

Cliquez sur "Suivant" et installez le rôle. 

Dans le "Gestionnaire de serveur", il y a un avertissement en haut à droite. Cliquez sur l'icône puis sur "Terminer la configuration DHCP".

![post](https://github.com/user-attachments/assets/0bdeef64-9fed-47c8-9710-539bf1c66000)


#### Étape 2 : Configurer le service DHCP

Dans le Gestionnaire de serveur, cliquez sur "Outils" puis sur "DHCP".
![dhcp](https://github.com/user-attachments/assets/b70d5f94-535c-42b9-840f-e01f92402913)


Dans la console DHCP, faites un clic droit sur "IPv4" et sélectionnez "Nouvelle portée...".

![scope](https://github.com/user-attachments/assets/961780c5-3c8a-43a9-a11a-5033f5fdff61)


Suivez l'assistant :

Nom de la portée : Donnez un nom à votre portée (ex. : "Plage DHCP 172.20.0.0").
Plage d'adresses IP : Indiquez la plage 172.20.0.100 à 172.20.0.200.
Masque de sous-réseau : Utilisez 255.255.255.0.

![plage](https://github.com/user-attachments/assets/acf16185-f68e-42b8-8ea3-5f33fba55e78)

![check](https://github.com/user-attachments/assets/5e680f80-3e6c-481a-9c51-2651a6880892)


#### Étape 3  : Verification que le client a bien une adresse IP dans la plage selectionner

![Capture d'écran 2024-10-29 144025](https://github.com/user-attachments/assets/46a65fc7-2152-4714-b998-6f4b349b3ed1)


### Reservation d'une adresse IP 


#### Étape 1 : Recherchez l'adresse MAC de la machine cliente (format : xx-xx-xx-xx-xx-xx) de l'interface réseau :
  ```powershell
  ipconfig /all.
  ```


#### Étape 2 : Ajouter la réservation dans DHCP :

Retournez à la console DHCP sur le serveur.
Sous l'etendue crée , faites un clic droit sur "Réservations" et sélectionnez "Nouvelle réservation...".
![new](https://github.com/user-attachments/assets/9d176918-6e81-4827-b75b-1101a14586ce)


Remplissez les informations :
Un nom pour la réservation.
Adresse IP de réservation 
L'adresse MAC de la machine cliente.

![Capture d'écran 2024-10-29 144530](https://github.com/user-attachments/assets/c3b0dc23-7628-4fef-abaf-8255e4d7b298)

Cliquez sur "Ajouter" pour enregistrer la réservation.

![resa](https://github.com/user-attachments/assets/4d3ddb10-cb4d-416f-9dab-7e9a64f3b0b3)



#### Étape 3 : Activer la portée :

Faites un clic droit sur la portée que vous avez créée et sélectionnez "Activer".

![active](https://github.com/user-attachments/assets/9753463d-c57f-4f10-9c30-247843dcaf2f)



#### Étape 4 : Vérifier l'attribution 

Sur la machine cliente, vous pouvez exécuter ipconfig /renew dans l'invite de commande pour demander une adresse IP au serveur DHCP.

Vérifiez que la machine cliente reçoit l'adresse 172.20.0.10.
![Capture d'écran 2024-10-29 161058](https://github.com/user-attachments/assets/1ad62cdd-31a9-4d00-81d1-18c54f7f8d92)




