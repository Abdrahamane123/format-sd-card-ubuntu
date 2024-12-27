# Format SD Card on Ubuntu
Insérez la carte SD dans votre PC Ubuntu.
Ouvrez un terminal et tapez :

lsblk

Identifiez le nom de votre carte SD (par exemple, /dev/sdb). Ne vous fiez pas aux partitions comme /dev/sdb1 ou /dev/sdb2.
Votre carte SD est listée comme mmcblk0, avec des partitions comme par exemple dans mon cas :

    mmcblk0p1 (512 Mo, montée sur /media/dev/system-boot).
    mmcblk0p2 (57.7 Go, montée sur /media/dev/writable).

Si vous voulez supprimer ces partitions et créer une seule partition, voici comment procéder :
1. Méthode avec fdisk

    Démontez les partitions actuelles :

sudo umount /dev/mmcblk0p1
sudo umount /dev/mmcblk0p2

Lancez fdisk pour la carte SD :

sudo fdisk /dev/mmcblk0

Supprimez toutes les partitions :

    Tapez d pour supprimer une partition. Répétez pour chaque partition.
    Vérifiez avec p pour lister les partitions restantes.

Créez une nouvelle partition unique :

    Tapez n pour créer une nouvelle partition.
    Choisissez primaire et acceptez les valeurs par défaut pour utiliser tout l'espace.

Sauvegardez les modifications :

    Tapez w pour écrire les modifications et quitter.

Formatez la nouvelle partition :

    sudo mkfs.vfat -F 32 /dev/mmcblk0p1

2. Méthode avec gparted (interface graphique)

Installez gparted si ce n'est pas déjà fait :

	sudo apt install gparted

Lancez gparted :

	sudo gparted

Dans l'interface :

    Sélectionnez mmcblk0 (votre carte SD).
    Supprimez toutes les partitions (clic droit > Supprimer).
    Appliquez les modifications (clic sur l'icône en forme de coche).
    Créez une nouvelle partition unique en FAT32.

Montez la partition :

    Après formatage, la partition sera prête à être utilisée.
