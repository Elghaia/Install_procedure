Étape 1 : Installer le rôle DHCP
Ouvrir le Gestionnaire de serveur :

Cliquez sur l’icône du Gestionnaire de serveur dans la barre des tâches ou accédez-y via le menu Démarrer.
Ajouter des rôles et des fonctionnalités :

Dans le Gestionnaire de serveur, cliquez sur "Gérer" puis sur "Ajouter des rôles et des fonctionnalités".
Assistant Ajout de rôles et de fonctionnalités :


Cliquez sur "Suivant" jusqu'à atteindre l'écran des rôles.
Cochez "Serveur DHCP" et cliquez sur "Suivant".
Suivez les instructions et installez le rôle. Une fois installé, vous aurez la possibilité de configurer le DHCP.
Étape 2 : Configurer le service DHCP
Ouvrir la console DHCP :

Dans le Gestionnaire de serveur, cliquez sur "Outils" puis sur "DHCP".
Créer une nouvelle portée :

Dans la console DHCP, faites un clic droit sur "IPv4" et sélectionnez "Nouvelle portée...".
Suivez l'assistant :
Nom de la portée : Donnez un nom à votre portée (ex. : "Plage DHCP 172.20.0.0").
Plage d'adresses IP : Indiquez la plage 172.20.0.100 à 172.20.0.200.
Masque de sous-réseau : Utilisez 255.255.255.0.
Configurez les autres options (comme le temps d'attribution, etc.) selon vos besoins.
Configurer les options DHCP :

Après avoir créé la portée, vous pouvez configurer les options comme le routeur (passerelle) et le DNS. Faites un clic droit sur la portée, sélectionnez "Configurer les options" et remplissez les informations nécessaires.
Étape 3 : Attribution statique d’une adresse IP
Trouver l'adresse MAC de la machine cliente :

Sur la machine cliente, ouvrez l’invite de commande et tapez ipconfig /all. Recherchez l'adresse MAC (format : xx-xx-xx-xx-xx-xx) de l'interface réseau.
Ajouter une réservation dans DHCP :

Retournez à la console DHCP sur le serveur.
Dans le nœud de la portée que vous venez de créer, faites un clic droit sur "Réservations" et sélectionnez "Nouvelle réservation...".
Remplissez les informations :
Nom : Un nom pour la réservation.
Adresse IP : 172.20.0.10.
Adresse MAC : L'adresse MAC de la machine cliente.
Cliquez sur "Ajouter" pour enregistrer la réservation.
Étape 4 : Activer la portée
Activer la portée :
Faites un clic droit sur la portée que vous avez créée et sélectionnez "Activer".
Étape 5 : Vérification
Vérifier l'attribution :
Sur la machine cliente, vous pouvez exécuter ipconfig /renew dans l'invite de commande pour demander une adresse IP au serveur DHCP.
Vérifiez que la machine cliente reçoit l'adresse 172.20.0.10.
