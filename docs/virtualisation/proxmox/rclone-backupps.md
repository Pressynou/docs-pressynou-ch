---
title: "Faire un disque de backups proxmox avec un drive monté sur rclone"
description: "Faire un disque de backups proxmox avec un drive monté sur rclone"
lead: "Faire un disque de backups proxmox avec un drive monté sur rclone"
date: 2020-10-06T08:49:31+00:00
author:
  name: Pressynou
  avatar: https://cdn.discordapp.com/attachments/945027218155929703/945713566214914138/profilephoto.jpg
icon: database
tags:
  - proxmox
  - stockage
  - drive
  - rclone
---
💾

## Utilisation d'un drive en disque de backup sur un PVE

On install rclone


![Promox](https://docs.pressynou.ch/virtualisation/proxmox/rclone-backups/af.png)

`apt updateee` Update des packages  
`apt install rclone`  

`rclone config`

### 

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