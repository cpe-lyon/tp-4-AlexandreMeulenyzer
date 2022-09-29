# TP 4 - Gestion des paquets

## Exercice 1. Commandes de base  

1/ J'ai utilisé la commande : 
```bash 
sudo apt update & upgrade
```
pour mettre a jour ma machine ubuntu.

2/
```bash 
alias maj="sudo apt upgrade"
```
pour le gardé au prochain démmarage, il faut écrire la commande dans le fichier /User/.bashrc
3/
```bash 
2022-09-26 06:43:18 status half-configured initramfs-tools:all 0.140ubuntu13
2022-09-26 06:44:00 status installed initramfs-tools:all 0.140ubuntu13
2022-09-26 06:44:00 trigproc linux-image-5.15.0-48-generic:amd64 5.15.0-48.54 <none>
2022-09-26 06:44:00 status half-configured linux-image-5.15.0-48-generic:amd64 5.15.0-48.54
2022-09-26 06:44:42 status installed linux-image-5.15.0-48-generic:amd64 5.15.0-48.54
```

4/
```bash
xxd/jammy-updates,jammy-security,now 2:8.2.3995-1ubuntu2.1 amd64 [installed,automatic]
xz-utils/jammy,now 5.2.5-2ubuntu1 amd64 [installed,automatic]
zerofree/jammy,now 1.1.1-1build3 amd64 [installed,automatic]
zlib1g/jammy-updates,now 1:1.2.11.dfsg-2ubuntu9.1 amd64 [installed,automatic]zstd/jammy,now 1.4.8+dfsg-3build1 amd64 [installed,automatic]
```

5/
```bash

User@localhost:~$ apt list --installed | wc -l

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

615
```
```bash
User@localhost:~$ dpkg -l | wc -l
622
```
nous n'utiliseront pas dpkg.log car il faudrait compté a la main tout les packet déjà installé sur notre machine.

6/
```bash
User@localhost:~$ apt list | wc -l

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

68953
```

7/   
Glances : Glances est un outil de surveillance pour GNU/Linux ou BSD.  

tldr :Les pages TLDR sont un effort communautaire pour simplifier les pages de manuel avec des exemples pratiques  

Hollywood : Simule un centre de contrôle affichant des logs qui défilent, des lignes de commandes et du binaire, pour simulé une session de hacking bien cliché.  

8/
```bash
sudo apt install sudoku
```

## Exercice 2.
GNU Core Utilities est le paquet dans lequel nous retrouvons ls
```bash
User@localhost:~$ dpkg -S /bin/ls
coreutils: /bin/ls
```
Script : 
```bash
#!/bin/bash

which -a $1 | xargs dpkg -S 2> /dev/null
```
 ## Exercice 3.

```bash
(dpkg -l "coreutils" | grep "^i") && echo "installé" || echo "non installé"
ii  coreutils      8.32-4.1ubuntu1 amd64        GNU core utilities
installé
```

 ## Exercice 5.

![aptitude](./Capture%20d%E2%80%99%C3%A9cran%202022-09-29%20082339.jpg)


emacs : Emacs est une famille d'éditeurs de texte disposant d'un ensemble extensible de fonctionnalités
![Lynx](Capture%20d’écran%202022-09-29%20083842.jpg)

Lynx : Lynx est un navigateurs web en mode texte utilisable via une console ou un terminal
![Lynx](Capture%20d’écran%202022-09-29%20083712.jpg)

 ## Exercice 6.
```bash
User@localhost:~$ ls /etc/apt/sources.list.d/
linuxuprising-ubuntu-java-jammy.list
```
Le dépot de la team Linux Uprising à bien été enregistré

## Exercice 7. Installation d’un logiciel à partir du code source

```bash
                                        &&
                                    & &&& &
                                    & &&/&\&
                                     & &&&&&
                                   &&&&&&&
                                  &&&&&&&~/
                                 &&&/&&&\|
                                & &/~&&& \|
                             &&&&_&/&~&& //~
                             & &&&&  |/_\/|\
                              &   &\/~   &|        &
                                  & \/_/_&/& _/|&&&
                                     /~|/ /&&&&&&&
                                       /&&/&&&&&&
                                        &~|/~ &&
                                         /~/~/_/                    
                                       //~ /_/ /   /_/_/___/_/   
                                       /_/_/    
                         :___________./~~~\.___________:
                          \                           / 
                           \_________________________/ 
                           (_)                     (_)

```

Et si dessous, nous pouvons voir graçe a checkinstall que cbonsai est bien installé
```bash
*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@localhost ]
1 -  Summary: [ cbonsai ]
2 -  Name:    [ cbonsai ]
3 -  Version: [ 20220929 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ cbonsai ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Recommends: [  ]
12 - Suggests: [  ]
13 - Provides: [ cbonsai ]
14 - Conflicts: [  ]
15 - Replaces: [  ]
```

## Exercice 8. Création de dépôt personnalisé.

Création d'un packet Debian:
```bash
User@localhost:/home/$$ dpkg-deb --build origine-commande
dpkg-deb: building package 'origine-commande' in 'origine-commande.deb'.
```
Création du dépôt personnel avec reprepro:




Signature du dépôt avec GPG:  
Après toutes les étapes suivie de l'exercice, le dépot est bien et belle configurée 
```bash
User@localhost:/home/$/repo-cpe$ sudo apt update
Get:1 file:/home/$/repo-cpe cosmic InRelease [2,466 B]
Get:1 file:/home/$/repo-cpe cosmic InRelease [2,466 B]
Hit:2 https://ppa.launchpadcontent.net/linuxuprising/java/ubuntu jammy InRelease
Hit:3 http://us.archive.ubuntu.com/ubuntu jammy InRelease
Hit:4 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:5 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease
Hit:6 http://us.archive.ubuntu.com/ubuntu jammy-security InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.
W: file:/home/$/repo-cpe/dists/cosmic/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
```

