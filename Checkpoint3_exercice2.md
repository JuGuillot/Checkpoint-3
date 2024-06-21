# Partie 1 : Gestion des utilisateurs

## Q.2.1.1 

Création de l'utilisateur "julien" avec `adduser` et vérification avec `cat /etc/passwd` :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/56dc3012-c9d2-4213-b2d7-90168cfd3f85)

## Q.2.1.2

Le mettre dans le groupe `root` pour qu'il puisse avoir les super privilèges et aussi lui donner les droits de se connecter en SSH dans `/etc/ssd/sshd_config`.

## Q.2.2.1

Faire un `nano /etc/ssd/sshd_config` et modifier comme suit :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/db978e48-2ccd-495e-aa98-4afb89e201a8)

## Q.2.2.2

Rajouter la ligne `AllowUsers julien` :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/f3a096db-20f8-4b6b-84ea-9cf39a6cd3e1)

L'accès est bien possible pour l'utilisateur `julien` :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/a5106017-f1a8-41ce-8936-8f5920fc67bf)

## Q.2.2.3

Création de la clé depuis le client et envoi de cette clé au serveur :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/6384c70f-064b-4c51-8708-256c014d229f)

Modification de `/etc/ssd/sshd_config` pour désactiver la connexion par mot de passe :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/0c2c0ac2-15c8-4f9c-80ee-7d4b0cd3cb30)

