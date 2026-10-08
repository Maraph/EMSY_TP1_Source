# TP1 - Installation Linux sur une VM - V0.4

## Groupe 

4. Matéo (MCN) 		- Thomas (TBT)

## But 

Cette manipulation a pour but d'installer une distribution linux [Sparky Linux](https://sparkylinux.org/) dans une machine virtuelle VMware 
Workstation Player, à l’aide d’une image disque (ISO).

## Materiels à disposition 

- VMware Workstation Player - V17
- Image disque (ISO) : sparkylinux-6.4-x86_64-minimalcli.iso

## Création d’une machine virtuelle 

**A.** Lancez VMware Workstation Player (logiciel)  

**B.** Sélectionnez **Create a New Virtual Machine** 

**C-A.** Placez le fichier `.iso` dans une repertoire connu : 

`C:\VosInitiales\VM\ISO`

**C-B.** Indiquez le chemin d’accès de l’image iso comme indiqué sous l’image ci-dessous :

![install image disk](/Images/Install_ISO.jpg) 

**D-A.** Choisissez un nom d'OS : `Linux - Debian 11.x` 

![OS name choice](Images/OS_Choice.jpg) 

**D-B.** Nommez la machine virtuelle : `SparkyLinux-VosInitiales` 

**E.** Creez un disque virtuel -> capcité : **20GB** 

> Remarque 1 : Cocher **store virtual disk a single file**

![Virtual disk](/Images/VirtualDisk.jpg) 

> Remarque 2 : Ci-dessous, la configuration de la VM 

![Virtual disk](/Images/VM_Config.jpg) 

**F.** Lancez la machine virtuelle : **Play virtual machine** 

## Lancement de l'image ISO (Linux - Live CD) 

**G.** Lancement du live CD : 

![Virtual disk](/Images/G.jpg) 

Shell Linux : 

![Virtual disk](/Images/shell.jpg) 

> **ATTENTION** : par défaut, le clavier est configuré est **Clavier Americain**

Q1. disposition du clavier américain ?

qwerty

Q2. disposition du clavier suisse-romand ?

qwertz

Q3. disposition du le clavier français ? 

azerty

**H.** Déplacez-vous à la **racine du système** en utilisant la commande suivante : `cd` 

Q4. cd /

**I.** Affichez le contenu de la racine avec la commande : `ls –l`	

![Virtual disk](/Images/I.jpg) 


Q5. Que signifie l'option `-l` avec la commande `ls` 

montrer la liste des fichiers avec leurs autorisations et d'autres informations

Q6. Décrypter la ligne où se trouve le répertoire **home**    

![Virtual disk](/Images/Q6.jpg) 

d = Est un directory  
r = Peut etre lu par le créateur  
w = Peut écris par le créateur  
x = Peut être éxécuté par le créateur  
r = Peut etre lu par un groupe  
"-" = Ne peut pas etre écrit par un groupe  
x = Peut être éxécuté par un groupe  
r = Peut etre lu par tout le restes des utilisateurs  
"-" = Peut etre écrit par tout le restes des utilisateurs  
x = Peut être éxécuté par tout le restes des utilisateurs  

**J.** Créez un répertoire de travail nommé « EMSY_VosInitiales» 

Q7. dans quel dossier racine allez-vous le placer (justifiez votre réponse) 

Le répertoire home car il est indépendant a chaque utilisateur et   
j'aurais les droits d'écriture / lecture

Q8. Quelle commande allez-vous utiliser pour faire ceci ?  

cd home  
sudo mkdir EMSY_MCN_TBT

**K.** Dans ce répertoire, créez un fichier texte que vous nommerez `TESTSLO_XXX_XXX` et éditez celui en écrivant un texte, exemple : "TP linux by XXX et XXX".
	   Utiliser la commande `vi`

sudo vi TESTSLO_MCN_TBT

Q9. Pouvez-vous éditez un fichier uniquement avec la commande `vi` 

oui

Q10. Si vous éteignez la machine virtuelle et que vous la rallumez, est-ce que le répertoire créé ci-dessus existe toujours (justifiez votre réponse) ? 

non car il est sauvgardé dans la RAM et non la ROM 

**L.** Tapez la commande `ls -l /dev/sda` 

![Virtual disk](/Images/Q10.jpg) 

Q11. Que signifie **sda** ? 

c'est le premier disque dure 

Q12. Quelle différence y a-t-il entre le répertoire de la question Q6 et celui du point L (justifiez votre réponse) ?

Le repertoire home ne sauvgarde rien qui n'est pas dans un user  
tandis que le /dev/sda lui saugardera tout dans la rom car nous ecrivons  
directement sur le disque.

## Installation de SparkyLinux sur la VM

**M.** Installez SparkyLinux

![Virtual disk](/Images/M.jpg) 

Q13. Quelle est la taille de disque minimum recommandée pour installer la distribution Sparky en mode cli 

2 [GB]

Q14. A quoi sert la partition swap ? Est-ce que ce principe existe-t-il sur les OS Microsoft Windows ? 

si la mémoire vive est pleine la partition swap sera utilisée comme "RAM supplémentaire"  
oui mais sous forme de fichier et non de portion du disque a proprement parler

Q15. Quel format pourriez-vous utiliser pour la 3ème partition afin qu’elle soit également accessible depuis un OS Microsoft ? 

Fat32

Q16. Durant l’installation, on vous demande deux noms d’utilisateur. A quoi correspondent-ils ? 

le premier est le nom de la machine sur un reseau (host) et le deuxieme est un utilisateur sur cette machine

**N.** Une fois l’installation de Linux terminée, prenez une capture d’écran du démarrage de votre système (GRUB)

![Virtual disk](/Images/N.jpg) 

**O.** Trouvez la ou les lignes de commande permettant de changer le clavier et procédez à la configuiration 

sudo dpkg-reconfigure keyboard-configuration

![Virtual disk](/Images/O.jpg)  
![Virtual disk](/Images/O2.jpg) 
![Virtual disk](/Images/O3.jpg)   

**P.** Tapez la commande : `nano -version`

![Virtual disk](/Images/P.jpg) 

Q17. A quoi sert `nano` ? 

créer / modifier des fichiers texte

**Q.** Testez si l’application `git` est installée sur votre distribution, si ce n’est pas le cas installez un client git. 

Q18. Comment savoir si `git` est déjà installé ? 

"git --version" devrait retourner la version de l'application 

git --version

Q19. Si le client `git` n'est pas installé, quelle(s) commande(s) utilisez-vous pour l’installer ? 

sudo apt-get update  
sudo apt-get install git

Q20. Que veut dire `apt` ? 

Advanced Packaging Tool, un installateur de packets (une app store)

Q21. Est-ce que cette commande (`apt`) peut être utilisée sur toutes les distributions Linux (justifiez votre réponse)? 

non, nous pouvons l'utiliser car nous sommes sur debian tandis que sur archlinux par exemple nous devons utiliser  
un autre installer comme pacman ou archinstaller.

**R.** Créez un sous-répertoire « EMSY_TP1_XXX-YYY » dans le répertoire de votre utilisateur. 
       
**Attention** : Ici on veut que l’utilisateur (vous) ait les droits de lecture, d’écriture et d’exécution.

sudo mkdir EMSY_MCN_TBT

Q22. Quel est le répertoire utilisateur ?  

le répertoire se trouvant dans le répertoire home, dans mon cas newusermateo/

Q23. Quelles sont les commandes pour changer les droits d'utilisateurs (lecture - écriture - execution) ?  

chmod u+wrx File  
chmod g+wrx File  
chmod o+wrx File  
chmod ugo-wrx File  

**S.** Dans ce répertoire, tapez la commande : `git clone https://github.com/votreDepot/EMSY_TP1_Source`

***Remarque*** : Il faut au préalable que vous ayez mis en place à cette adresse un fork du dépôt fourni lors de ce TP.

Q24. Qu’observez-vous dans ce répertoire ?

On ne peut pas faire de git pull
![Virtual disk](/Images/Q24.jpg) 

**T.** Editez le fichier source `.c` avec l’éditeur de texte « nano ». -> Réalisez un petit programme en C (par exemple de type « Hello world »).

![Virtual disk](/Images/T.jpg) 

**U.**	Vérifiez si le compilateur `gcc` est bien installé. Notez la version du logiciel

gcc --version  
![Virtual disk](/Images/U.jpg) 

**U-A.** Tapez les commandes suivantes :
```Shell 
gcc -Wall -o fichier.o -c fichier.c 
gcc -o fichier fichier.o 
```
Remarque : « fichier » est à remplacer par le nom de votre choix

![Virtual disk](/Images/U-A.jpg) 

Q25. Quels sont les fichiers qui ont été générés 

EMSY_TP1 qui est un executable  
EMSY_TP1.o  

![Virtual disk](/Images/Q25.jpg) 

**V.** Entrez la commande suivante : `./fichier`

![Virtual disk](/Images/V.jpg)

Q26. Que se passe-t-il ?

le fichié compilé auparavant se fait executer

## Tips 

> Tip 1 : sortir de la VM -> appuyer simultanément sur `Ctrl` et `Alt` 

> Tip 2 :  
> Pour arrêter un Linux proprement : 	`shutdown`  
> Pour forcer l’arrêt d’un système :	`halt` ou `poweroff`  
> Seul un administrateur peut exécuter ces commandes !

> Tip 3 : [commande vi avec ses options](https://www.linuxtricks.fr/wiki/guide-de-sur-vi-utilisation-de-vi)

> Tip 4 : [éditer un fichier type markdown (.md)](https://ashki23.github.io/markdown-latex.html)

