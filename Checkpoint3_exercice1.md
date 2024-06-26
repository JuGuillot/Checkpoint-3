# Partie 1 : Gestion des utilisateurs

## Q.1.1.1

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/20e702f5-f9a8-47ac-9e54-5cbc4587e18f)

J'ai copié l'utilisateur Kelly Rhameur et changé les attributs aisni que les "direct reports" qui ont été transférés à Lionel Lemarchand.

## Q.1.1.2

- Clic droit sur `TSSR.LAN -> New -> Organization Unit`, et rentrer le nom de l'OU `DeactivatedUsers`.
- Clic droit sur Kelly Rhameur ->  `Disable Account`.
- Clic droit sur Kelly Rhameur -> `Move` -> `DeactivatedUsers`

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/cafe75f3-87d0-45cb-a005-4ac2aff66502)

## Q.1.1.3

Cliquer sur `Remove` :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/56465252-03cb-43b6-92af-757feeb9cf67)

Puis `Apply`.

## Q.1.1.4

J'ai créé un dossier nommé `ARCHIVES` dans lequel a été déplacé le dossier personnel de Kelly Rhameur.

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/1fd519e2-f54c-41d3-815c-017af4e7d110)

Puis création d'un dossier personnel pour Lionel Lemarchand et modification des accès pour que lui seul puisse y accéder (parmi les utilisateurs) :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/4cab80ce-e1d7-48c9-a817-ae234515f8ad)

# Partie 2 : Restriction utilisateurs

## Q.1.2.1

Aller dans les `propriétés de Gabriel Guhl -> Account -> Logon Hours` et modifier en conséquence :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/6645da66-34fb-4f82-86c4-7b09e14e26d9)

## Q.1.2.2

Toujours dans `Account` mais ce coup-ci `Log On to` :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/a1d4bb45-a676-4b7a-9775-67da1e36cc37)

## Q.1.2.3

- Aller dans le `Group Policy Management`
- Faire un clic droit sur `Group Policy Objects -> New`, lui donner un nom
- Clique droit puis `Edit` :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/c6c0b530-9325-4e87-ac5a-6580a4ce013a)

Ensuite :
- Clic droit sur `LabUsers -> Link an Existing GPO...` :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/4b57ddc8-4307-48b2-aa91-c6c219b61d86)

# Partie 3 : Lecteurs réseaux

## Q.1.3.1

Tout d'abord, il faut partager les dossiers `E:` et `F:` comme ceci :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/5c0a5320-2c27-4d6f-80d9-98d78adf5e6f)

Faire de même avec `F:`.

Ensuite, créer la GPO :

- Aller dans le `Group Policy Management`
- Faire un clic droit sur `Group Policy Objects -> New`, lui donner un nom
- Clique droit puis `Edit`
- `User Configuration -> Preferences -> Windows Settings -> Drive Maps`
- Clic droit -> `New -> Mapped Drive`

Pour `E:`:

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/582c27c9-b0d0-4fcd-90de-57c9ce1b5633)

Pour `F:` :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/e1085872-7567-4bfc-a2f5-98f99bae8266)

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/8d416c1f-0e05-464e-b7b1-18822b8e7269)

Ensuite :
- Clic droit sur `LabUsers -> Link an Existing GPO...`

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/8736ce25-fd87-4aa9-b85b-223ff4739050)

