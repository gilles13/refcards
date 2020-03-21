---
papersize: a4
documentclass: article
classoption: landscape
geometry: margin=.5cm
output:
  pdf_document:
    latex_engine: xelatex
header-includes:
    - \usepackage{multicol}
    - \usepackage[yyyymmdd]{datetime}
    - \newcommand{\hideFromPandoc}[1]{#1}
    - \hideFromPandoc{
        \let\Begin\begin
        \let\End\end
      }
---

\pagenumbering{gobble}

\Begin{multicols}{3}

![](./images/Git-Logo-2Color.png){ width=20% }
![](./images/null.png){ width=5% }

\scriptsize

![byncsa](./images/cc-by-nc-sa_icon_120_42.png){ width=4% }  [Gilles FIDANI](gilles.fidani@protonmail.com)  
Update : \today

\footnotesize

**Présentation**  
`Git` est un gestionnaire de version (`version control system (VCS)`).
C'est un système qui enregistre l'évolution d'un (ensemble de) fichier(s) au cours du temps, de manière à ce qu'on puisse rappeler une version antérieure à tout moment.

**Vocabulaire**  
directory \dotfill répertoire  
$\hookrightarrow$ où `Git` a été initialisé pour commencer le versioning  
repository \dotfill dépôt  
remote \dotfill distant (hébergé)  
to commit \dotfill consigner  
fork \dotfill embranchement  
to fetch \dotfill aller chercher, rapporter  
to check in \dotfill déposer, mettre en dépôt, faire un dépôt  
check out \dotfill retrait  
to check out \dotfill récupérer, retirer, rapatrier  
stage area \dotfill zone d'attente  
stash \dotfill remise  
to stash \dotfill remiser  
to stage \dotfill mettre en attente  
hash \dotfill empreinte, signature  
snapshot \dotfill instantané  
gist \dotfill pastebin service operated by `GitHub`  
Git LFS \dotfill Large File Storage (pointeurs vers fichiers)  

**Principes**  
`Git` gère les données comme des **instantanés** d'un mini système de fichier. A chaque `commit`, il réalise un instantané du contenu de l'espace de travail, et enregistre une référence à cet instantané. Si les fichiers n'ont pas changé, `Git` ne les stocke pas à nouveau, il pose juste une référence vers le fichier original qu'il a déja enregistré.

*Les états*  
Les fichiers peuvent être dans 2 *états* : suivis ou non.
Lorsqu'ils sont suivis, ils peuvent être :  
  + modifiés \dotfill dans la zone de travail  
  + indexés (dans zone d'index) \dotfill avec `git add`  
  + validés \dotfill avec `git commit`  

*Les 3 zones*  
le répertoire `Git` (`repository`) contient les méta-données et la BdD des objets du projet.

le répertoire (ou zone) de travail (`working directory`) est une extraction unique d'une `version` du projet.
Elle s'initialise avec `git init`. On parle du `dépôt local`.

la zone d'index ou zone de préparation (`staging area, stage`) stocke les info concernant le prochain instantané.

\vfill
\columnbreak

![](./images/les3etats.png)
![](./images/null.png){ width=1% }

**Concepts**  
master \dotfill branche de développement par défaut  
origin \dotfill dépôt amont par défaut  
HEAD \dotfill branche courante, version committé en cours  
HEAD\textasciicircum \dotfill le commit précédent HEAD  
$\hookrightarrow$ équivalent à HEAD\textasciitilde  

**Configuration**  
nom \dotfill `git config --global user.name "user name"`  
email \dotfill `git config --global user.email "my@email"`  
editeur \dotfill `git config --global core.editor vim`  
GH user \dotfill `git config --global github.user <user>`  
GH token \dotfill `git config --global github.token <token>`  
couleurs différences \dotfill `git config --global color.diff auto`  
couleurs status \dotfill `git config --global color.status auto`  
couleurs branches \dotfill `git config --global color.branch auto`  
voir les réglages \dotfill `git config --list`  
aide sur la config \dotfill `git help config`  

**Commandes de base**  
initialiser un dépôt git \dotfill `git init`  
afficher le statut d'un répertoire suivi \dotfill `git status`  
ajouter un fichier au suivi \dotfill `git add <fichier>`  
effacer un fichier (yc dans espace de travail) \dotfill `git rm <fichier>`  
déclarer une modif sur un fichier \dotfill `git commit -m "message"`  
rapatrier une branche \dotfill `git checkout`  
créer une nouvelle branche \dotfill `git -b <branche>`  
cloner un projet GH \dotfill `git clone <url>`  
créer une copie de MASTER \dotfill `git branch <branche>`  
basculer vers BRANCHE \dotfill `git checkout <branche>`  
basculer une branche vers MASTER \dotfill `git checkout master`  
afficher les branches d'un dépôt \dotfill `git branch -a`  

\vfill
\columnbreak

**Différences**  
afficher le journal des modif \dotfill `git log`  
inspecter les modif non indexées \dotfill `git diff`  
inspecter les modif indexées \dotfill `git diff --staged`  
inspecter les modif indexées ou non \dotfill `git diff HEAD`  
inspecter les modif dans une GUI \dotfill `git difftools`  

**Annuler**  
reset \dotfill `git reset`  
revert \dotfill `git revert`  

**Remote server**  
afficher les dépôts distants \dotfill `git remote -v`  
connecter son dépôt local \dotfill `git remote add origin <url>`  
pousser les modifs \dotfill `git push -u origin <branche>`  
mettre à jour le dépôt local \dotfill `git pull`  
récupérer les données d'un dépôt \dotfill `git fetch <url>`  
$\hookrightarrow$ ne met pas à jour le dépôt local  
tagger un `commit` \dotfill `git tag <tag> <commitID>`  

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

\End{multicols}
