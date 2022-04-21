---
title: "🗝️ Désactiver You do not have valid subscription"
description: "🗝️ Désactiver You do not have valid subscription"
lead: "🗝️ Désactiver You do not have valid subscription"
date: 2020-10-06T08:49:31+00:00
author:
  name: Pressynou
  avatar: https://cdn.discordapp.com/attachments/945027218155929703/945713566214914138/profilephoto.jpg
icon: database
tags:
  - proxmox
  - subscription
  - key
---

https://docs.pressynou.ch/img/tuto/docs/subscription.png

On ouvre le fichier qui fait que la pop-up s'affiche:

`nano /usr/share/javascript/proxmox-widget-toolkit/proxmoxlib.js`
`if (data.status !== 'Active') {`
`if (data.status == 'Active') {`