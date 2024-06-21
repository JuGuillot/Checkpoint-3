# Partie 1 : Gestion des utilisateurs

## Q.2.1.1 

Création de l'utilisateur "julien" avec `adduser` et vérification avec `cat /etc/passwd` :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/56dc3012-c9d2-4213-b2d7-90168cfd3f85)

## Q.2.1.2

Le mettre dans le groupe `root` pour qu'il puisse avoir les super privilèges et aussi lui donner les droits de se connecter en SSH dans `/etc/ssd/sshd_config`.

# Partie 2 : Configuration de SSH

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

Partie 3 : Analyse du stockage

## Q.2.3.1

Il y a du `ext4`, `ext2` et `SWAP` :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/2d6ab127-ed50-4bad-aaa8-6a5d808146bf)

## Q.2.3.2

Il y a du `RAID1` et du `LVM` :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/037268ca-2f2d-49d0-ba46-a413d76c1646)

## Q.2.3.3

J'ai ajouté un nouveau disque de 8Go à la machine et je l'ai partitionné avec `fdisk /dev/sdb` :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/8a4532b6-81be-4449-9002-5e1a80f962df)

Avec la commande `mdadm --detail /dev/md0`, on a ce résultat :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/8f086fc6-621a-45ba-9875-3cc0b34c7d15)

On fait donc un `mdadm --manage /dev/md0 --add /dev/sdb1`, si on refait `mdadm --detail /dev/md0` on a alors : 

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/25e1d0f7-d61d-4fda-b668-ff8f14e2502a)

Et au bout d'un moment :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/352550ae-9ac8-4ffa-9d31-fd7d06dd96c0)

## Q.2.3.3

Avec la commande `lvdisplay` on peut voir le détail des groupes de volume : 

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/bdc7172d-2c28-4db6-8c1a-c56b7119e28d)

Pour créer un nouveau volume logique LVM de 2 Go, entrer la commande suivante `lvcreate -n Sauvegardes -L 2G cp3-vg` :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/0d085f52-a409-476e-b213-c2c77bea99ac)

Ensuite il faut le formater avec `mkfs.ext4 /dev/cp3-vg/Sauvegardes` :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/79cc289a-e764-4cf2-8fa9-2637ba5a1232)

Pour le montage automatiquement à chaque démarrage dans l'emplacement par défaut `/var/lib/bareos/storage` :

- Il faut monter le volume nouvellement créé sur `/var/lib/bareos/storage` avec la commande `mount /dev/cp3-vg/Sauvegardes /var/lib/bareos/storage`
- Puis éditer le fichier `/etc/fstab` avec `nano /etc/fstab` et rajouter la dernière ligne :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/3b20da6a-39e5-4c20-a314-716f545195db)

Vérifier avec `mount -a` qu'il n'y a pas d'erreurs : 

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/6a1d6e88-ecd8-4740-abe0-b9120ad68f57)

## Q.2.3.4

Pour savoir combien d'espace disponible il reste dans le groupe de volume, utiliser la commande `vgdisplay cp3-vg` :

![image](https://github.com/JuGuillot/Checkpoint-3/assets/161329881/f27a56ed-39dd-4ee7-bd50-cebb12c93ca8)

On peut voir qu'il reste 1.79Go d'espace libre.
