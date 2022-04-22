---
title: "🗝️ Désactiver You do not have valid subscription"
description: "🗝️ Désactiver You do not have valid subscription"
lead: "🗝️ Désactiver You do not have valid subscription"
tags:
  - proxmox
  - subscription
  - keys
---

Quand on installe Proxmox en communautaire, à chaque connexion, ce message s'affiche.

![Promox subscription](https://docs.pressynou.ch/img/docs/subscription.png)


On ouvre le fichier qui fait que la pop-up s'affiche:

`nano /usr/share/javascript/proxmox-widget-toolkit/proxmoxlib.js`

On cherche la ligne suivante:
`if (data.status !== 'Active') {`

Que l'on remplace part:
`if (data.status == 'Active') {`

