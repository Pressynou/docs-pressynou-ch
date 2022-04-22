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
<br>

![Promox](https://docs.pressynou.ch/img/docs/rclone-backups/1.png)

# Installation et configuration Rclone

Update des packages
`apt update`

On install rclone
`apt install rclone`

On configuré rclone
`rclone config`

[Tuto pour configuré rclone](https://docs.pressynou.ch/docs/outils/rclone)


# TRUCH MUCHE SLEWES I LAY MOCH


`mkdir /mnt/backups`  
`rclone mount --vfs-cache-mode writes nomdudrive:emplacment/que/tu/veux/sur/le/drive /mnt/backups`  

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