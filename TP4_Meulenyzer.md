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
 









