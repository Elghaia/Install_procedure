
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

![[fichier_etc.png]]

- Indiquer les configuration du service dans le fichier dhcpd.conf 
(*Chaque ligne doit se terminer par ;*)

```bash

sudo nano /etc/dhcp/dhcpd.conf

```

![[fichier_dhcpd.png]]
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
![[status.png]]
# Vérifier la configuration sur la machine client

```bash

ip a

```
![[verif1.png]]
# Réservation d'une adresse IP pour un client

- Récupérer l'adresse MAC du client : 
	```bash
	ip link show
	```
	
![[Pasted image 20241103205406.png]]

- Modifier le fichier dhcpd.conf

```bash

sudo nano /etc/dhcp/dhcpd.conf

```

![[config_resa.png]]

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
![[ipverif.png]]

(si besoin utiliser la commande sudo dhcpcd -k enp0s8 pour liberer  l'adresse IP actuelle)
