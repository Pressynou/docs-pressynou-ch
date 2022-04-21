---
title: "🗝️ Désactiver You do not have valid subscription"
description: "🗝️ Désactiver You do not have valid subscription"
lead: "🗝️ Désactiver You do not have valid subscription"
tags:
  - proxmox
  - subscription
  - key
---

https://docs.pressynou.ch/img/docs/subscription.png

On ouvre le fichier qui fait que la pop-up s'affiche:

`nano /usr/share/javascript/proxmox-widget-toolkit/proxmoxlib.js`
`if (data.status !== 'Active') {`
`if (data.status == 'Active') {`