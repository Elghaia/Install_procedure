
# Prérequis

- un serveur Debian

- une machine client Ubuntu

- les deux machines sont sur le même réseau interne

- le service DHCP est activé sur la machine cliente

# Mettre à jour le système sur le serveur

- Lancer la commande de mise à jour du système

```bash

sudo apt install && apt upgrade

```

# Installer le serveur DHCP

- Installer le paquet isc-dhcp-server

```bash

sudo apt install isc-dhcp-server

```


# Configurer le serveur DHCP

- Récupérer le nom des interfaces 

```bash

ip a

```

- Ouvrir le fichier de configuration pour préciser sur quel interface le serveur doit être configurer

```bash

sudo nano /etc/default/isc-dhcp-server

```

==>  Décommenter la ligne

```bash

DHCPDv4_CONF=/etc/dhcp/dhcpd.conf

```

==>  Spécifier les interfaces (uniquement IPV4 pour notre cas)

```bash

INTERFACESv4="nomdelinterface"

```

![fichier_etc](https://github.com/user-attachments/assets/01ffbfe2-f488-4ee7-b48f-90b1f04cb3aa)

- Indiquer les configuration du service dans le fichier dhcpd.conf 
(*Chaque ligne doit se terminer par ;*)

```bash

sudo nano /etc/dhcp/dhcpd.conf

```
![fichier_dhcpd](https://github.com/user-attachments/assets/7f3b435d-db01-4ccc-8bee-9d0417da8adf)

# Démarrer et activer le serveur DHCP

- Lancement du service dhcp

```bash

systemctl start isc-dhcp-server
systemctl enable isc-dhcp-server

```

- Vérifier le status

```bash

sudo systemctl status isc-dhcp-server

```
![status](https://github.com/user-attachments/assets/7845e56a-e0d2-4584-a89f-dec858c0be5c)

# Vérifier la configuration sur la machine client

```bash

ip a

```

![verif1](https://github.com/user-attachments/assets/d2481365-ccab-4fb8-8e8c-af1a457e3a67)

# Réservation d'une adresse IP pour un client

- Récupérer l'adresse MAC du client : 
	```bash
	ip link show
	```
![Pasted image 20241103205406](https://github.com/user-attachments/assets/4ea9637f-6953-438a-9db0-b80a9e998d5e)


- Modifier le fichier dhcpd.conf

```bash

sudo nano /etc/dhcp/dhcpd.conf

```
![config_resa](https://github.com/user-attachments/assets/8a9a8c7d-6264-48d5-932d-16b7d4790f58)


- Sauvegarder et redémarrer le service

```bash


sudo service isc-dhcp-server restart

```

- Vérifier la configuration du serveur

```bash

sudo dhcpd -t

```

- Vérifier la configuration sur la machine client

```bash

ip a

```
![ipverif](https://github.com/user-attachments/assets/fa6fe8b0-83d6-4b63-98ae-88266e934de8)


(si besoin utiliser la commande sudo dhcpcd -k enp0s8 pour liberer  l'adresse IP actuelle)
