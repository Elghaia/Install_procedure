## 1. Installation du serveur DNS

1. **Installer le paquet `bind9`** sur le serveur :
    ```bash
    sudo apt update
    sudo apt install bind9 bind9utils bind9-doc
    ```

2. **Vérifier l'installation** :
    Après l'installation, le service `bind9` devrait être en cours d'exécution. Vérifiez son statut avec la commande suivante :
    ```bash
    sudo systemctl status bind9
    ```

## 2. Configurer le serveur DNS


1. Configurez l'accès au serveur DNS, les requêtes récursives et les serveurs DNS de transfert dans **`/etc/bind/named.conf.options`** :<br>

Ouvrez le fichier de configuration  :
   ```bash
    sudo nano /etc/bind/named.conf.options
   ```
Ajoutez les lignes suivantes pour configurer les options nécessaires (à adapter selon votre réseau) :
![conf_options](https://github.com/user-attachments/assets/e2d10b1b-cb6f-4bb5-843a-f1e14300d4c4)
Sauvegardez et quittez 

2. Définissez l'emplacement des fichiers de zones de recherche directe et inverse de votre domaine en spécifiant le fichier de zone correspondant dans **`/etc/bind/named.conf.local`** :<br>

Ouvrez le fichier de configuration :
  ```bash
  sudo nano /etc/bind/named.conf.local
  ```
Ajoutez les lignes suivantes pour inclure la zone `wilders.lan`:
    ![conf_local](https://github.com/user-attachments/assets/75d4c912-0ead-41bb-ad9c-2659a137985d)
Sauvegardez et quittez 

3. Configurer le serveur pour écouter sur IPv4 dans **`/etc/default/named** :<br>
   
Ouvrez le fichier et mettez à jour le paramètre pour que le service DNS écoute uniquement sur IPv4 :
  ```bash   
  `OPTIONS="-u bind -4"`
  ```
Sauvegardez et quittez 

## 3. Configurer la zone DNS 

Creer les fichiers de zone qui contiennent les enregistrements DNS pour la zone `wilders.lan`

1 - **Créer le fichier de zone de recherche directe**

Copiez le fichier d'exemple **`db.local`** présent dans le répertoire **`/etc/bind`** pour créer votre fichier de zone de recherche directe.<br>
  ```bash   
  cp /etc/bind/db.local forward.wilder.lan
  ``` 
Modifiez-le pour ajouter les informations de votre serveur DNS, les enregistrements **A** pour vos serveurs et un enregistrement **CNAME** pour le serveur FTP (à adaptez à votre réseau) :<br>
  ```bash   
  sudo nano /etc/bind/forward.wilder.lan
  ```
   ![forward](https://github.com/user-attachments/assets/26e91e72-4e9b-4a5e-9fed-f7030200268e)


2 - **Créer le fichier de zone de recherche inverse** :

- Copiez le fichier d'exemple **`db.127`** (présent dans **`/etc/bind`**) pour créer votre fichier de zone de recherche inverse.<br>
Ce fichier contiendra les enregistrements inverses pour les adresses IP de votre réseau.
    ```bash   
  cp /etc/bind/db.127 reverse.wilder.lan
  sudo nano /etc/bind/reverse.wilder.lan
    ``` 
![reverse](https://github.com/user-attachments/assets/ce9ca839-1b91-480e-b060-d6b641b38f33)

## 4. Vérification de la configuration

1. **Vérifier la syntaxe des fichiers de configuration** :
    Avant de redémarrer le service BIND, vérifiez la syntaxe des fichiers de configuration avec la commande suivante :
    ```bash
    sudo named-checkconf
    sudo named-checkzone wilders.lan /etc/bind/forward.wilder.lan
    sudo named-checkzone wilders.lan /etc/bind/reverse.wilder.lan
    ```
    
2. **Redémarrer le service BIND** :
    Si aucune erreur n’est signalée, redémarrez le service BIND pour appliquer les modifications :
    ```bash
    sudo systemctl restart bind9
    ```
    

3. **Activer BIND au démarrage** :
    Pour que BIND démarre automatiquement lors du boot, utilisez la commande :
    ```bash
    sudo systemctl enable bind9
    ```

## 5. Tester la configuration sur le serveur

Utilisez la commande `dig` ou `nslookup` depuis le client pour tester la résolution DNS ; nslookup est simple et rapide pour vérifier les DNS, tandis que dig est plus complet et donne plus de détails.<br>
Si la commande dig n'est pas trouvée, installez le paquet dnsutils qui contient l'outil dig : **sudo apt install dnsutils -y**

1. Sur la machine cliente Ubuntu, ouvrez le fichier **/etc/resolv.conf** et modifiez l'entrée du serveur DNS pour qu'il pointe vers votre serveur DNS :<br>

  ![resolve conf](https://github.com/user-attachments/assets/f1c3e13d-443f-49f2-ad34-844e434be2b0)

2. Tester avec la commande dig en recherche inverse :<br>
  ![dig](https://github.com/user-attachments/assets/31f101bc-73b1-43dc-88a3-564ecc963242)
 
3. Tester avec la commande nslookup :<br>
  ![nslookup](https://github.com/user-attachments/assets/af268b32-93da-41be-bc05-6eb74616305b)







