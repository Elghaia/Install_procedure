#### Étape 1 : Installer le rôle DNS
Ouvrir le Gestionnaire de serveur :

Dans le Gestionnaire de serveur, cliquez sur "Gérer" puis sur "Ajouter des rôles et des fonctionnalités" :

![addrole](https://github.com/user-attachments/assets/4359d6e3-4faa-4896-86e4-1c3afdf8b4ef)

Choisissez l'option "Installation basée sur un rôle ou une fonctionnalité" et poursuivez.

![type](https://github.com/user-attachments/assets/b49a1aed-297f-46df-8b29-2116c6353008)


Poursuivez directement, car le serveur local est déjà sélectionné.

![serveur](https://github.com/user-attachments/assets/401b9e03-f352-48b9-aa80-f581ab82fef8)


Dans la liste des rôles, cochez "DNS Server" et au sein de la fenêtre qui s'affiche, vérifiez que l'option "Inclure les outils de gestion" soit cochée.

![dns service](https://github.com/user-attachments/assets/c6b8bec6-09c5-4473-84b4-36ca4d168321)

Cliquez sur "Suivant" et installez le rôle.

![end](https://github.com/user-attachments/assets/a974b279-499d-43c0-bd9e-0d72748a87b7)


#### Étape 2 : Configurer la zone wilder.lan 

Dans le Gestionnaire de serveur, cliquez sur "Outils" puis sur "DNS".

![tool](https://github.com/user-attachments/assets/9b00208f-66c1-469b-afc7-88956914f78b)


Dans la console DNS manager qui s'affiche, faites un clic droit sur "Zone de recherche direct" (ou Forward lookup zone si server en anglais) et sélectionnez "Nouvelle zone".

![add new](https://github.com/user-attachments/assets/e181c122-1476-4946-abbc-3724f668ad87)

![new zone](https://github.com/user-attachments/assets/879c41e3-cfc5-4ae7-8888-15733a1ef296)

Après l’écran de bienvenue, vous devriez avoir l’écran suivant : laissez l'option **"Zone primaire"** 
**Cette option indique que le serveur DNS que vous configurez est autoritaire pour cette zone** puis cliquez sur Suivant.

![primary zone](https://github.com/user-attachments/assets/8e135f33-b6f4-4fc6-838f-15bf16b4bd0a)


Entrez le nom de la zone : wilder.lan et cliquez sur Suivant.

![zone name](https://github.com/user-attachments/assets/8ed447c2-4095-41f2-9c81-c4802015a0b6)

Laissez le nom par défeaut :

![new file](https://github.com/user-attachments/assets/dc609dfb-d890-4caa-8482-46656db7ddd3)

L'Active Directory n'étant pas encore mis en place , laissez l'option par défaut ne pas mettre à jour dynamiquement:

![sans AD](https://github.com/user-attachments/assets/cc39143b-3c66-4c69-bc0b-1e4e56aea62c)

Cliquez sur Finish et vous le verrez apparaitre dans le DNS manager :

![affichage](https://github.com/user-attachments/assets/6d0bd0fb-2237-44a1-ad4c-407fd72d9728)


#### Étape 3 : Ajouter des enregistrements

**Ajouter un enregistrement A pour serveur.wilder.lan**

Dans la console DNS, faites un clic droit sur wilder.lan et choisissez Nouvel enregistrement hôte (A ou AAAA).

![new A](https://github.com/user-attachments/assets/0bd67411-f385-4e40-a243-9859528ca87d)

Entrez Nom : serveur (ce qui donne serveur.wilder.lan).
Entrez l'adresse IP fixe réservée à cette machine : 172.20.0.2 

![newhost](https://github.com/user-attachments/assets/73d67d75-6378-4703-b590-ff7ad6ce8a81)
Cliquez sur Ajouter.

**Ajouter un enregistrement A pour client.wilders.lan**

Dans la console DNS, faites un clic droit sur wilders.lan et choisissez Nouvel enregistrement hôte (A ou AAAA).

![new A](https://github.com/user-attachments/assets/0bd67411-f385-4e40-a243-9859528ca87d)

Entrez Nom : client (ce qui donne serveur.wilder.lan).
Entrez l'adresse IP fixe réservée à cette machine : 172.20.0.10

![clienthost](https://github.com/user-attachments/assets/2d0c80e9-2b82-46dc-842d-0bb627535cf9)

Cliquez sur Ajouter.

**Ajouter un enregistrement CNAME pour dns.wilders.lan**
Faites un clic droit sur wilders.lan et choisissez Nouvel alias (CNAME).

![cnam](https://github.com/user-attachments/assets/4dcb4873-e27a-40be-a00b-068ac7885353)

Entrez Nom : dns (ce qui donne dns.wilder.lan).
Dans Nom canonique, entrez server.wilder.lan pour que dns.wilder.lan redirige vers server.wilders.lan.

![cnamhost](https://github.com/user-attachments/assets/4f531b81-c433-40c0-97cc-903e60300020)

Cliquez sur OK.

#### Étape 4 : Configurer la zone inversé

Dans la console DNS manager , faites un clic droit sur "Zone de recherche indirect" (ou Reverse lookup zone si server en anglais) et sélectionnez "Nouvelle zone".

Laisser l'option primary zone et entrez votre adresse ip 

![reverse_prim](https://github.com/user-attachments/assets/0baa17e8-9f3a-4277-bd53-e1afe0c6df32)

Sélectionner IPV4

![reverse_name](https://github.com/user-attachments/assets/677f924f-8c12-4471-babf-383e80d7d57c)

Sélectionner Networik id et entrez votre IP

![reverse_ip](https://github.com/user-attachments/assets/90587b33-ec68-4e90-a078-0cfb9fd723f2)

Poursuivez avec les autres paramètres par défaut

#### Étape 5 : Tester le serveur DNS

**Utilisez nslookup pour vérifier les enregistrements :**

nslookup serveur.wilder.lan
nslookup client.wilder.lan
nslookup dns.wilder.lan


#### Étape 4 : Tester le serveur DNS

**Utilisez nslookup pour vérifier les enregistrements :**

- nslookup serveur.wilder.lan
- nslookup client.wilder.lan
- nslookup dns.wilder.lan

Lancer les commandes depuis le serveur.

Configurez le client Windows pour qu'il utilise le serveur DNS en IPv4 :

Ouvrez le Panneau de configuration.
Allez dans Réseau et Internet > Centre Réseau et partage > Modifier les paramètres de la carte.
Faites un clic droit sur l'interface Ethernet et choisissez Propriétés.
Sélectionnez Protocole Internet version 4 (TCP/IPv4) et cliquez sur Propriétés.
Cochez Utiliser l'adresse de serveur DNS suivante.
Dans Serveur DNS préféré, entrez 172.20.0.2 (adresse du serveur DNS de votre réseau).
Cliquez sur OK pour appliquer les modifications.

![dnsclient](https://github.com/user-attachments/assets/fe24284c-6ece-47a1-a272-bbb2be0206bb)


Lancer les commandes depuis le client.

Le resultat doit renvoyer ca :

![resultat](https://github.com/user-attachments/assets/530bb4b5-3e7f-44c6-9204-a141b7bda93f)



