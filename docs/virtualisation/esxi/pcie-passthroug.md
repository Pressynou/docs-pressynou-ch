---
title: "PCI(e) passthrough"
description: "Komment faire PCI(e) passthrough sur ESXi"
date: 2020-10-06T08:49:31+00:00
author:
  name: Pressynou
  avatar: https://cdn.discordapp.com/attachments/945027218155929703/945713566214914138/profilephoto.jpg
tags:
  - esxi
  - gpu
  - passtrough
icon: cpu
---


### Config Périph pcie

Passé le périph pci en relais  https://cdn.discordapp.com/attachments/749999414067724319/942541227985883136/unknown.png

### Ajout périph pci

https://media.discordapp.net/attachments/749999414067724319/942541495209193492/unknown.png


### Changer params vm 

Dans les params avancés de la VM il faut ajouté:

`hypervisor.cpuid.v0 = FALSE`

Puis passé a l'install des drivers dans windows