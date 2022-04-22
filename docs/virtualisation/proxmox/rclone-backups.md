---
title: "💾 Faire un disque de backups proxmox avec un drive monté sur rclone"
description: "💾 Faire un disque de backups proxmox avec un drive monté sur rclone"
lead: "💾 Faire un disque de backups proxmox avec un drive monté sur rclone"
tags:
  - proxmox
  - stockage
  - drive
  - rclone
---

## Utilisation d'un drive en disque de backup sur un PVE


![Promox](https://docs.pressynou.ch/img/docs/rclone-backups/1.png)

# Installation et configuration Rclone

Update des packages

`apt update` 

On install rclone

`apt install rclone`  

On configuré rclone

`rclone config`  

[Tuto pour configuré rclone](https://docs.pressynou.ch/docs/outils/rclone)

# Configuration du service rclone

On crée vers où sera monté le drive
`mkdir /mnt/backups`  

Voici la commande qui permet de monté le drive
`rclone mount --vfs-cache-mode writes nomdudrive: /mnt/backups`  

On édit le service du drive
`nano /etc/systemd/system/drive.service`  


    [Unit]
	Description=Drive de backups
	After=syslog.target network-online.target

	[Service]
	#Type=oneshot
	RemainAfterExit=yes
	ExecStart=rclone mount --vfs-cache-mode writes 	nomdudrive:emplacment/que/tu/veux/sur/le/drive /mnt/backups	
	ExecStop=fusermount -uz /mnt/backups

	[Install]
	WantedBy=multi-user.target

On démarre le service rclone:
`systemctl start drive.service`

On fait en sorte qu'il démarre automatiquement à chaque redémarrage:
`systemctl enable drive.service` 

On regarde si tout marche
`systemctl status drive.service`

# Ajout du drive sur proxmox

![Promox](https://docs.pressynou.ch/img/docs/rclone-backups/2.png)

![Promox](https://docs.pressynou.ch/img/docs/rclone-backups/3.png)


Et voilà, drive monté, on peux maintenant backup sur le drive. *Attention, il va y avoir du cache le temps de l'envoie, et faite gaffe au limite d'envoie des services*

![Promox](https://docs.pressynou.ch/img/docs/rclone-backups/4.png)