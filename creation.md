# Créer les comptes utilisateurs du domaine


1. Aller dans Server manager → Tools → Active Directory Users and Computers

2. Dérouler « wilder.lan » et Users pour voir la liste des utilisateurs et des groupes qui existent déjà, par défaut dans Windows Server 2022. On notera que figure déjà le compte « Administrateur » que l’on utilise déjà.

3. Faire un clic droit sur le nom du domaine ==> Nouveau ==> Unité d’organisation. 
![Capture d'écran 2024-11-18 232339](https://github.com/user-attachments/assets/376e005e-51f1-484b-b1fd-60c8e66fd137)

4. Donner un nom à cette UO / OU, par exemple le nom de l’entreprise. ici wilder_students




5. Ce nouveau « dossier » s’ajoute au même niveau que Users.

6. Faire un clic droit sur la nouvelle UO (Wilder_students) ==> Nouveau ==> group.

Renseigner nom ![Capture d'écran 2024-11-17 171158](https://github.com/user-attachments/assets/0f816dd5-03fe-452e-ade2-a628d58016dc)

![Capture d'écran 2024-11-17 171248](https://github.com/user-attachments/assets/594926b8-4709-49e6-b006-946fdf3e87bc)

7. Faire un clic droit sur la nouvelle UO (Wilders_students)==> Nouveau ==> User.
Entrez les informations de l'utilisateur : Prénom, Nom, Nom d’ouverture de session

![Capture d'écran 2024-11-17 171631](https://github.com/user-attachments/assets/464d7609-239d-424b-bc19-e487184f8656)
![Capture d'écran 2024-11-17 171730](https://github.com/user-attachments/assets/ff99bb25-0cb5-4b7d-8d8e-bc6f579292f2)
![Capture d'écran 2024-11-17 171800](https://github.com/user-attachments/assets/91eb0b6a-256d-4c73-a310-54cdbc09cfe9)



8. Faire un clic droit sur le nouvel utilisateur et Add to group

![Capture d'écran 2024-11-17 171849](https://github.com/user-attachments/assets/43828130-7ead-492f-920a-af457652b86b)

9. Ecrire le nom du groupe (Wilders_students) et faire Check Names puis OK
![Capture d'écran 2024-11-17 171938](https://github.com/user-attachments/assets/8efe37c1-eae7-4bd7-af97-0ac0e47b0a38)
![Capture d'écran 2024-11-17 172022](https://github.com/user-attachments/assets/f9c66ac1-1f3c-4b11-ad9f-37d77fe80ead)



