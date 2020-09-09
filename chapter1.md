#                                                 Django 

#### Introduction

Django est un framework puissant pour écrire des applications Web Python.L'utilisation d'un framework complet comme Django vous permet de rendre vos applications et sites opérationnels plus rapides sans avoir à vous soucier du code structurel commun pour les relier.Les cadres vous permettent de vous concentrer sur les parties uniques de votre application et de laisser les outils faire le gros du travail.

1. ##### Installez le EPEL Repositories

Le référentiel EPEL contient des packages supplémentaires qui ne sont pas maintenus dans le cadre de la distribution principale, ce qui est assez rare.

```
[root@localhost ~]# sudo yum install epel-release
--> Résolution des dépendances terminée

Dépendances résolues

=============================================================================================================================================
 Package                                Architecture                     Version                        Dépôt                          Taille
=============================================================================================================================================
Mise à jour :
 epel-release                           noarch                           7-12                           epel                            15 k

Résumé de la transaction
=============================================================================================================================================
Mettre à jour  1 Paquet

Taille totale des téléchargements : 15 k
Is this ok [y/d/N]: y
Downloading packages:
Delta RPMs disabled because /usr/bin/applydeltarpm not installed.
epel-release-7-12.noarch.rpm                                                                                          |  15 kB  00:00:00
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Mise à jour  : epel-release-7-12.noarch                                                                                                1/2
  Nettoyage    : epel-release-7-11.noarch                                                                                                2/2
  Vérification : epel-release-7-12.noarch                                                                                                1/2
  Vérification : epel-release-7-11.noarch                                                                                                2/2

Mis à jour :
  epel-release.noarch 0:7-12

Terminé !

```

##### 2.Installez pip et les dépendances nécessaires

  




