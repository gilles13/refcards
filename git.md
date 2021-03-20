
**Présentation**  
`Git` est un gestionnaire de version (`version control system (VCS)`).
C'est un système qui enregistre l'évolution d'un (ensemble de) fichier(s) au cours du temps, de manière à ce qu'on puisse rappeler une version antérieure à tout moment.

**Vocabulaire**  
|		 anglais 		|		 français		 |		observations		|
|---------------|----------------|--------------------|
|directory 			| répertoire			| où `Git` a été initialisé pour commencer le versioning |
|repository 		| dépôt 					|| 
|remote | distant (hébergé)  ||
|to commit | consigner  ||
|fork | embranchement  ||
|to fetch | aller chercher, rapporter  ||
|to check in | déposer, mettre en dépôt, faire un dépôt  ||
|check out | retrait  ||
|to check out | récupérer, retirer, rapatrier  ||
|stage area | zone d'attente  ||
|stash | remise  ||
|to stash | remiser  ||
|to stage | mettre en attente  ||
|hash | empreinte, signature  ||
|snapshot | instantané  ||
|gist | pastebin service operated by `GitHub`  ||
|Git LFS | Large File Storage (pointeurs vers fichiers)  ||

**Principes**  
`Git` gère les données comme des **instantanés** d'un mini système de fichier. A chaque `commit`, il réalise un instantané du contenu de l'espace de travail, et enregistre une référence à cet instantané. Si les fichiers n'ont pas changé, `Git` ne les stocke pas à nouveau, il pose juste une référence vers le fichier original qu'il a déja enregistré.

*Les états*  
Les fichiers peuvent être dans 2 *états* : suivis ou non.
Lorsqu'ils sont suivis, ils peuvent être :  
  + modifiés :  dans la zone de travail  
  + indexés (dans zone d'index) : avec `git add`  
  + validés : avec `git commit`  

*Les 3 zones*  
le répertoire `Git` (`repository`) contient les méta-données et la BdD des objets du projet.

le répertoire (ou zone) de travail (`working directory`) est une extraction unique d'une `version` du projet.
Elle s'initialise avec `git init`. On parle du `dépôt local`.

la zone d'index ou zone de préparation (`staging area, stage`) stocke les info concernant le prochain instantané.

![](./images/les3etats.png)

**Concepts**  
| concepts | explications |
|----------|--------------|
|master | branche de développement par défaut |
|origin | dépôt amont par défaut |
|HEAD | branche courante, version committé en cours |
|HEAD^ | le commit précédent HEAD (équivalent à HEAD~) |

**Configuration**  
| item à configurer | commande |
|-------------------|----------|
|nom | `git config --global user.name "user name"` |
|email | `git config --global user.email "my@email"` |
|editeur | `git config --global core.editor vim` |
|GH user | `git config --global github.user <user>` |
|GH token | `git config --global github.token <token>` |
|couleurs différences | `git config --global color.diff auto` |
|couleurs status | `git config --global color.status auto` |
|couleurs branches | `git config --global color.branch auto` |
|voir les réglages | `git config --list` |
|aide sur la config | `git help config` |


**Commandes de base**  
| action				|			commande		|
|---------------|-----------------|
|initialiser un dépôt git | `git init` |
|afficher le statut d'un répertoire suivi | `git status` |
|ajouter un fichier au suivi | `git add <fichier>` |
|effacer un fichier (yc dans espace de travail) | `git rm <fichier>` |
|déclarer une modif sur un fichier | `git commit -m "message"` |
|rapatrier une branche | `git checkout` |
|créer une nouvelle branche | `git -b <branche>` |
|cloner un projet GH | `git clone <url>` |
|créer une copie de MASTER | `git branch <branche>` |
|basculer vers BRANCHE | `git checkout <branche>` |
|basculer une branche vers MASTER | `git checkout master` |
|afficher les branches d'un dépôt | `git branch -a` |

**Différences**  
|action | commande |
|-------|----------|
|afficher le journal des modif | `git log` |
|inspecter les modif non indexées | `git diff` |
|inspecter les modif indexées | `git diff --staged` |
|inspecter les modif indexées ou non | `git diff HEAD` |
|inspecter les modif dans une GUI | `git difftools` |

**Annuler**  
|action | commande |
|-------|----------|
|reset | `git reset` |
|revert | `git revert` |

**Remote server**  
|action | commande |
|-------|----------|
|afficher les dépôts distants | `git remote -v` |
|connecter son dépôt local | `git remote add origin <url>` |
|pousser les modifs | `git push -u origin <branche>` |
|mettre à jour le dépôt local | `git pull` |
|récupérer les données d'un dépôt | `git fetch <url>` **ne met pas à jour le dépôt local** |
|tagger un `commit` | `git tag <tag> <commitID>` |

**A savoir**  
La commande `checkout` dans `Git` est différente de celle de `Subversion`.  
Sur `Git`, `checkout` est utilisée pour `switcher` entre les branches d'un dépôt.  
`clone` sert à rapatrier (`fetch`) un dépôt.  

Il est possible de combiner `branch` et `checkout` *via* la cmde `git checkout -b <branche>`.  

On ne valide que les fichiers **préalablement indexés**.
Cette restriction est levée par la cmde `git commit -a -m "MESSAGE"`  

**Références**  
[http://marklodato.github.io/visual-git-guide/index-fr.html](http://marklodato.github.io/visual-git-guide/index-fr.html)  
[https://git-scm.com/book/fr/v2](https://git-scm.com/book/fr/v2)  
[http://gitref.org/](http://gitref.org/)  
[https://try.github.com/levels/1/challenges/1](https://try.github.com/levels/1/challenges/1)  

