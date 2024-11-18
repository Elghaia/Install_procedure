# Installer Active Directory sur Windows Server 2022


1. Ouvrir le Gestionnaire de serveur 

2. Dans le Gestionnaire de serveur, cliquez sur "Gérer" puis sur "Ajouter des rôles et des fonctionnalités" :

![addrole](https://github.com/user-attachments/assets/4359d6e3-4faa-4896-86e4-1c3afdf8b4ef)

3. Choisir « Installation basée sur un rôle ou une fonctionnalité » .

 ![type](https://github.com/user-attachments/assets/b49a1aed-297f-46df-8b29-2116c6353008)

4. Poursuivez directement, car le serveur local est déjà sélectionné.

![serveur](https://github.com/user-attachments/assets/401b9e03-f352-48b9-aa80-f581ab82fef8)


5. Cocher le rôle « Services AD DS » pour Active Directory Domain Services et vérifiez que l'option "Inclure les outils de gestion" soit cochée 
   
![adds](https://github.com/user-attachments/assets/fa96315d-0cf9-4cb6-9910-2d9b79e2c5af)

Remarque : les rôles DNS et DHCP seront ajoutés plus tard.

6. L’écran suivant permet d’ajouter des fonctionnalités, ne rien faire et cliquer sur Suivant.

7. Vérifier le résumé de l’installation et cliquer sur « Installer » pour démarrer l’opération.


8. En laissant l’écran ouvert, à la fin du processus, on peut lire « Configuration requise. Installation réussie sur SERVEUR » et surtout la ligne « Promouvoir ce serveur en contrôleur de domaine » : c’est sur cette phrase qu’il faut cliquer pour convertir le serveur en contrôleur de domaine du réseau.

![controleurdedomaine](https://github.com/user-attachments/assets/fba16670-79b4-4d4a-9bae-1b508740cb60)


9. Comme il s'agit d'un nouveau domaine, choisissez "Ajouter une nouvelle forêt" et indiquez le nom de domaine.

![forest](https://github.com/user-attachments/assets/465a13ed-bf0d-4b11-be6d-155fc86bb875)


10. Laisser coché l’ajout de la fonctionnalité Serveur DNS pour ajouter ce rôle et indiquer un mot de passe de récupération des services d’annuaire (DSRM). Ce mot de passe ne doit absolument pas être perdu.


11. Un message d’erreur en jaune vient alerter de la délégation du serveur DNS. Il n’y a rien à faire à ce stade, cliquer simplement sur Suivant pour continuer.


12. Nous avons précédemment choisi un nom de domaine complet (FQDN), il faut maintenant indiquer l’équivalent NetBIOS pour les anciens appareils qui ne gèrent pas les noms de domaines qualifiés. Par exemple, pour « domaine.local » on pourra choisir le NetBIOS « DOMAINE » .
![netbios](https://github.com/user-attachments/assets/f359ddb4-cc5a-4c5d-9738-af0db832ab92)


13. Valider l’emplacement de la base de données AD DS, des journaux d’historique et pour SYSVOL. Laisser les dossiers proposés par défaut (NTDS et SYSVOL dans C:\Windows).

![path](https://github.com/user-attachments/assets/4a721da3-17ca-47b1-91bb-bac205c8ccd3)


14. Un récapitulatif résume la configuration qui va être appliquée. Cliquer sur Suivant pour continuer.

15. Une dernière vérification est effectuée, des notifications sont affichées mais cliquer sur Installer pour démarrer le processus.

![pre](https://github.com/user-attachments/assets/ccae16e9-7aca-460e-8b58-b84959fce579)


16. L’opération dure quelques minutes et le redémarrage de Windows prendra plus de temps que d’habitude, le temps de configurer le contrôleur de domaine.

17. La connexion à Windows doit maintenant se faire sur le domaine pour utiliser le compte Administrateur du domaine. Utiliser le mot de passe du compte Administrateur créé lors de l’installation de Windows Server 2016.

18. ![Capture d’écran 2024-11-17 163624](https://github.com/user-attachments/assets/b572b919-70a6-48da-9897-977145c19a67)

