# Django

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

Taille totale des téléchargements : 15 k
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

Mis à jour :
  epel-release.noarch 0:7-12

Terminé !
```

##### 2.Installez pip et les dépendances nécessaires

Utilisez les commandes ci-dessous pour installer la dernière version de pip 

```
[root@localhost ~]# sudo yum install python-devel python-setuptools python-pip

--> Résolution des dépendances terminée

Dépendances résolues

=============================================================================================================================================
 Package                                               Architecture             Version                         Dépôt                  Taille
=============================================================================================================================================
Installation :
 python-devel                                          x86_64                   2.7.5-88.el7                    base                   398 k
 python-setuptools                                     noarch                   0.9.8-7.el7                     base                   397 k
 python2-pip                                           noarch                   8.1.2-12.el7                    epel                   1.7 M
Installation pour dépendances :
 python-backports                                      x86_64                   1.0-8.el7                       base                   5.8 k
 python-backports-ssl_match_hostname                   noarch                   3.5.0.1-1.el7                   base                    13 k
 python-ipaddress                                      noarch                   1.0.16-2.el7                    base                    34 k
 python-rpm-macros                                     noarch                   3-32.el7                        base                   8.8 k
 python-srpm-macros                                    noarch                   3-32.el7                        base                   8.4 k
 python2-rpm-macros                                    noarch                   3-32.el7                        base                   7.7 k

Résumé de la transaction
=============================================================================================================================================
Installation   3 Paquets (+6 Paquets en dépendance)
Installé :
  python-devel.x86_64 0:2.7.5-88.el7           python-setuptools.noarch 0:0.9.8-7.el7           python2-pip.noarch 0:8.1.2-12.el7

Dépendances installées :
  python-backports.x86_64 0:1.0-8.el7   python-backports-ssl_match_hostname.noarch 0:3.5.0.1-1.el7   python-ipaddress.noarch 0:1.0.16-2.el7
  python-rpm-macros.noarch 0:3-32.el7   python-srpm-macros.noarch 0:3-32.el7                         python2-rpm-macros.noarch 0:3-32.el7

Terminé !
```

```
[root@localhost ~]# sudo pip install --upgrade pip
Collecting pip
  Downloading https://files.pythonhosted.org/packages/4e/5f/528232275f6509b1fff703c9280e58951a81abe24640905de621c9f81839/pip-20.2.3-py2.py3-none-any.whl (1.5MB)
    100% |████████████████████████████████| 1.5MB 355kB/s
Installing collected packages: pip
  Found existing installation: pip 8.1.2
    Uninstalling pip-8.1.2:
      Successfully uninstalled pip-8.1.2
Successfully installed pip-20.2.3
```

##### 3.Installez de Python 3

Nous installerons Python 3.7

```
[root@localhost ~]# sudo yum install centos-release-scl -y

Dépendances résolues

=============================================================================================================================================
 Package                                   Architecture               Version                               Dépôt                      Taille
=============================================================================================================================================
Installation :
 centos-release-scl                        noarch                     2-3.el7.centos                        extras                      12 k
Installation pour dépendances :
 centos-release-scl-rh                     noarch                     2-3.el7.centos                        extras                      12 k

Résumé de la transaction
=============================================================================================================================================
Installation   1 Paquet (+1 Paquet en dépendance)

Taille totale des téléchargements : 24 k
Taille d'installation : 39 k
Downloading packages:
(1/2): centos-release-scl-rh-2-3.el7.centos.noarch.rpm                                                                |  12 kB  00:00:00
(2/2): centos-release-scl-2-3.el7.centos.noarch.rpm                                                                   |  12 kB  00:00:00
---------------------------------------------------------------------------------------------------------------------------------------------
                                                                             2/2

Installé :
  centos-release-scl.noarch 0:2-3.el7.centos

Dépendances installées :
  centos-release-scl-rh.noarch 0:2-3.el7.centos

Terminé !
```

Une fois le référentiel activé, installez Python 3.7 avec la commande suivante:

```
sudo yum install rh-python37
```

Une fois Python 3.6 installé, nous sommes prêts à créer un environnement virtuel pour notre application Django.

##### 4. Création d'un environnement virtuel

##### 

  
Vous pouvez utiliser pip pour installer virtualenv:

```
[root@localhost ~]# sudo pip install virtualenv
DEPRECATION: Python 2.7 reached the end of its life on January 1st, 2020. Please upgrade your Python as Python 2.7 is no longer maintained. pip 21.0 will drop support for Python 2.7 in January 2021. More details about Python 2 support in pip can be found at https://pip.pypa.io/en/latest/development/release-process/#python-2-support pip 21.0 will remove support for this functionality.
Collecting virtualenv
  Downloading virtualenv-20.0.31-py2.py3-none-any.whl (4.9 MB)
     |████████████████████████████████| 4.9 MB 71 kB/s
Collecting six<2,>=1.9.0
  Downloading six-1.15.0-py2.py3-none-any.whl (10 kB)
Collecting importlib-resources>=1.0; python_version < "3.7"
  Downloading importlib_resources-3.0.0-py2.py3-none-any.whl (23 kB)
Collecting filelock<4,>=3.0.0
  Downloading filelock-3.0.12.tar.gz (8.5 kB)
Collecting pathlib2<3,>=2.3.3; python_version < "3.4" and sys_platform != "win32"
  Downloading pathlib2-2.3.5-py2.py3-none-any.whl (18 kB)
Collecting distlib<1,>=0.3.1
  Downloading distlib-0.3.1-py2.py3-none-any.whl (335 kB)
     |████████████████████████████████| 335 kB 95 kB/s
Collecting appdirs<2,>=1.4.3
  Downloading appdirs-1.4.4-py2.py3-none-any.whl (9.6 kB)
Collecting importlib-metadata<2,>=0.12; python_version < "3.8"
  Downloading importlib_metadata-1.7.0-py2.py3-none-any.whl (31 kB)
Collecting singledispatch; python_version < "3.4"
  Downloading singledispatch-3.4.0.3-py2.py3-none-any.whl (12 kB)
Collecting zipp>=0.4; python_version < "3.8"
  Downloading zipp-1.2.0-py2.py3-none-any.whl (4.8 kB)
Collecting contextlib2; python_version < "3"
  Downloading contextlib2-0.6.0.post1-py2.py3-none-any.whl (9.8 kB)
Collecting typing; python_version < "3.5"
  Downloading typing-3.7.4.3-py2-none-any.whl (26 kB)
Collecting scandir; python_version < "3.5"
  Downloading scandir-1.10.0.tar.gz (33 kB)
Collecting configparser>=3.5; python_version < "3"
  Downloading configparser-4.0.2-py2.py3-none-any.whl (22 kB)
Using legacy 'setup.py install' for filelock, since package 'wheel' is not installed.
Using legacy 'setup.py install' for scandir, since package 'wheel' is not installed.
Installing collected packages: six, singledispatch, contextlib2, zipp, scandir, pathlib2, typing, importlib-resources, filelock, distlib, appdirs, configparser, importlib-metadata, virtualenv
    Running setup.py install for scandir ... done
    Running setup.py install for filelock ... done
Successfully installed appdirs-1.4.4 configparser-4.0.2 contextlib2-0.6.0.post1 distlib-0.3.1 filelock-3.0.12 importlib-metadata-1.7.0 importlib-resources-3.0.0 pathlib2-2.3.5 scandir-1.10.0 singledispatch-3.4.0.3 six-1.15.0 typing-3.7.4.3 virtualenv-20.0.31 zipp-1.2.0

```



