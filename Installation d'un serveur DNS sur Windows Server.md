#### Étape 1 : Installer le rôle DNS
Ouvrir le Gestionnaire de serveur :

Dans le Gestionnaire de serveur, cliquez sur "Gérer" puis sur "Ajouter des rôles et des fonctionnalités" :
![addrole](https://github.com/user-attachments/assets/4359d6e3-4faa-4896-86e4-1c3afdf8b4ef)

Choisissez l'option "Installation basée sur un rôle ou une fonctionnalité" et poursuivez.
![type](https://github.com/user-attachments/assets/b49a1aed-297f-46df-8b29-2116c6353008)


Poursuivez directement, car le serveur local est déjà sélectionné.

![serverselection](https://github.com/user-attachments/assets/544193d9-7cf7-4ad5-bb1e-dc27eec00931)

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


Entrez le nom de la zone : wilders.lan et cliquez sur Suivant.

![zone name](https://github.com/user-attachments/assets/8ed447c2-4095-41f2-9c81-c4802015a0b6)

Laissez le nom par défeaut :

![new file](https://github.com/user-attachments/assets/dc609dfb-d890-4caa-8482-46656db7ddd3)

L'Active Directory n'étant pas encore mis en place , laissez l'option par défaut ne pas mettre à jour dynamiquement:

![sans AD](https://github.com/user-attachments/assets/cc39143b-3c66-4c69-bc0b-1e4e56aea62c)

Cliquez sur Finish et vous le verrez apparaitre dans le DNS manager :

![affichage](https://github.com/user-attachments/assets/6d0bd0fb-2237-44a1-ad4c-407fd72d9728)


#### Étape 3 : Ajouter des enregistrements

**Ajouter un enregistrement A pour le serveur DNS**

Dans la console DNS, faites un clic droit sur wilders.lan et choisissez Nouvel enregistrement hôte (A ou AAAA).
![new A](https://github.com/user-attachments/assets/0bd67411-f385-4e40-a243-9859528ca87d)

Entrez Nom : ns1 (ce qui donne ns1.wilders.lan). (Par convention on va choisir ns1 pour un serveur DNS principal)

Dans Adresse IP, entrez l'IP de votre serveur DNS : 172.20.05
Cliquez sur Ajouter.

Ajouter un enregistrement A pour ns1.wilders.lan :

**Ajouter un enregistrement A pour serveur.wilders.lan**

Faites un clic droit sur wilders.lan et sélectionnez Nouvel enregistrement hôte (A ou AAAA).
Entrez Nom : serveur (ce qui donne serveur.wilders.lan).
Entrez l'adresse IP fixe réservée à cette machine : 172.20.0.10 
Cliquez sur Ajouter.

**Ajouter un enregistrement CNAME pour dns.wilders.lan**
Faites un clic droit sur wilders.lan et choisissez Nouvel alias (CNAME).

Entrez Nom : dns (ce qui donne dns.wilders.lan).

Dans Nom canonique, entrez ns1.wilders.lan pour que dns.wilders.lan redirige vers ns1.wilders.lan.

Cliquez sur OK.

#### Étape 4 : Tester le serveur DNS




