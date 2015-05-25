#Git Workflow

Ce Workflow (Flux de travail) n'est pas exclusif. Il s'agit d'un guide fonctionnel pour effectuer les taches courantes de contribution au projet :

* modification du projet en local, 
* verification des modifications, 
* enregistrement des modifications en local, 
* envoi des modifs sur un depot perso distant, 
* proposition des modifs depuis son depot perso distant vers le depot global distant du projet.

--------------------------------------
##Verification des modifications
Verification (positionnement) de la branche courante (ici "master" mais cela pourrait etre un autre branche!)

`$ git checkout master`

##Verification format fichiers (espace / cr ....)
###en ligne de commande
`$ git diff –check`
### en gui (gitk)
 * gitk --> Menu --> File --> git gui
 * Sélection dans la liste fichier non indexé des fichiers modifié devant être commité, si ya du brun dans le source, en avant pour une relecture du format du code, ensuite effectuez un rafraîchissement sous gitk ([Ctrl]-[F5])
 * gitk --> diff-path

##C&C (Commente & Commit ... ton code aussi!)
###en ligne de commande
 * Premierement, ajouter dans le "staging area" les fichiers faisant partie du prochain commit

`$ git add "mes_fichiers"`

 * Commit en commantant

`$ git commit -m "mon message de commit"`

### en gui (gitk)
 * gitk , Menu --> git gui
 * git gui / commenter
 * git gui → Menu → commiter - ([Ctrl]-[Return])

## Vérification du resultat
###en ligne de commande
 * Afficher l'etat du depot :

`$ git status`

 * Afficher l'historique des commits :

`$ git log`

### en gui (gitk)
gitk , menu / file / reload (ctrl-f5) :

 * point jaune dans gitk , master gras et nom du commit (OK !!!), 
 * point rouge si pas bon (KO !!!!) truc pas commité?.


##Préparation de la sortie de ton ordi !
###en ligne de commande
 * Verif (positionnement) de branche!

`$ git checkout master`

 * Rafraîchissement du code ! "upstream" est une configuration perso' pointant vers le depot global distant du projet. "upstream" peut etre différent suivant les configurations de chacun. 

`$ git fetch upstream`

 * Fait rebase. Cela vas faire "monter" ses commit perso au dessus de l'état raffraîchit du projet (afin de garder un historique lineaire)

`$ git rebase upstream/master`

####Réponse possible du rebase :

* __Cannot rebase: You have unstaged changes. Please commit or stash them.__
 
(KO) Nop ! point rouge dans gitk, il existe des modifs non commité (ou non annulé)

*  __First, rewinding head to replay your work on top of it...__
 
(OK) Yep! point jaune dans gitk , master gras et nom du commit

## C'est le bon moment de vérifier si tout fonctionne encore ...
Les modifications des autres participants aux projets on été récupérer ... peu etre cela vas t'il influencer la qualité du code que tu viens de modifier ... c'est le bon moment de faire un check up (build / re-tests .... )

## Pousse sur le serveur git a toi
("origin" est une configuration perso' pointant sur le depot perso' distant du projet)

__"--force" est parfois requis, attention son utilisation peut etre violente!__

`$ git push origin master`

__Login et mot de passe demandé__

## Proposition des modif vers le serveur global
 * Sur el web, connexion sur git, depuis ton depot perso distant, click sur button __"pull request"__, recommente ... et hop!
