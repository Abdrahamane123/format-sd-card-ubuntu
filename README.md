# Format SD Card on Ubuntu

This repository contains a step-by-step guide to format an SD card on Ubuntu, ensuring only one partition.

## Steps

1. Identify the SD card using `lsblk`.
Votre carte SD est listée comme mmcblk0, avec deux partitions par exemple:

    mmcblk0p1 (512 Mo, montée sur /media/dev/system-boot).
    mmcblk0p2 (57.7 Go, montée sur /media/dev/writable).
 
2. Lancez fdisk pour la carte SD :

sudo fdisk /dev/mmcblk0

3. Supprimez toutes les partitions :

    Tapez d pour supprimer une partition. Répétez pour chaque partition.
    Vérifiez avec p pour lister les partitions restantes.

4. Créez une nouvelle partition unique :

    Tapez n pour créer une nouvelle partition.
    Choisissez primaire et acceptez les valeurs par défaut pour utiliser tout l'espace.

5. Sauvegardez les modifications :

    Tapez w pour écrire les modifications et quitter.

6. Formatez la nouvelle partition :

    sudo mkfs.vfat -F 32 /dev/mmcblk0p1

Méthode avec gparted (interface graphique)

1. Installez gparted si ce n'est pas déjà fait :

sudo apt install gparted

2. Lancez gparted :

    sudo gparted

3. Dans l'interface :
        Sélectionnez mmcblk0 (votre carte SD).
        Supprimez toutes les partitions (clic droit > Supprimer).
        Appliquez les modifications (clic sur l'icône en forme de coche).
        Créez une nouvelle partition unique en FAT32.

4. Montez la partition :
        Après formatage, la partition sera prête à être utilisée.

Ces étapes garantiront qu’il ne reste qu’une seule partition sur votre carte SD.
