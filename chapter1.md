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
Installé :
  python-devel.x86_64 0:2.7.5-88.el7           python-setuptools.noarch 0:0.9.8-7.el7           python2-pip.noarch 0:8.1.2-12.el7

Dépendances installées :
  python-backports.x86_64 0:1.0-8.el7   python-backports-ssl_match_hostname.noarch 0:3.5.0.1-1.el7   python-ipaddress.noarch 0:1.0.16-2.el7
  python-rpm-macros.noarch 0:3-32.el7   python-srpm-macros.noarch 0:3-32.el7                         python2-rpm-macros.noarch 0:3-32.el7

Terminé !
```

```
[root@localhost ~]# sudo pip3 install --upgrade pip
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

Taille totale des téléchargements : 24 k
Taille d'installation : 39 k
Downloading packages:
(1/2): centos-release-scl-rh-2-3.el7.centos.noarch.rpm                                                                |  12 kB  00:00:00
(2/2): centos-release-scl-2-3.el7.centos.noarch.rpm                                                                   |  12 kB  00:00:00
---------------------------------------------------------------------------------------------------------------------------------------------
                                                                             2/2

Installé :
  centos-release-scl.noarch 0:2-3.el7.centos

Dépendances installées :
  centos-release-scl-rh.noarch 0:2-3.el7.centos

Terminé !
```

Une fois le référentiel activé, installez Python 3.8 avec la commande suivante:

```
sudo yum install rh-python38
```

Une fois Python 3.8 installé, nous sommes prêts à créer un environnement virtuel pour notre application Django.

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

##### Créer un environnement virtuel à l'aide de virtualenv

Dites que vous souhaitez créer un environnement virtuel dédié pour contenir le framework Django:

```
[root@localhost ~]# mkdir my_django_app
[root@localhost ~]# cd my_django_app
[root@localhost my_django_app]# virtualenv djangoenv
created virtual environment CPython2.7.5.final.0-64 in 2436ms
  creator CPython2Posix(dest=/root/my_django_app/djangoenv, clear=False, global=False)
  seeder FromAppData(download=False, pip=bundle, wheel=bundle, setuptools=bundle, via=copy, app_data_dir=/root/.local/share/virtualenv)
    added seed packages: pip==20.2.2, setuptools==44.1.1, wheel==0.35.1
  activators PythonActivator,CShellActivator,FishActivator,PowerShellActivator,BashActivator
```

##### 5.Installez Django dans l'environnement virtuel

Tout d'abord, activez l'environnement virtuel:

```
[root@localhost ~]# source ~/djangoenv/bin/activate
(djangoenv) [root@localhost ~]#
```

Cela signifie que vous êtes entré dans l'environnement virtuel "djangoenv".

Installez Django dans l'environnement virtuel:

```
[root@localhost ~]# python3.7 -m venv venv
(venv) [root@localhost ~]# source venv/bin/activate
(venv) [root@localhost ~]# pip install Django==2.2.*
Collecting Django==2.2.14
  Downloading https://files.pythonhosted.org/packages/f2/6c/f7e0ed3d07952742439be43e7fb5a8b07b065ab927c6493be2a6cea59f33/Django-2.2.14-py3-none-any.whl (7.5MB)
    100% |████████████████████████████████| 7.5MB 2.5MB/s
Requirement already satisfied: pytz in ./venv/lib/python3.7/site-packages (from Django==2.2.14) (2020.1)
Requirement already satisfied: sqlparse>=0.2.2 in ./venv/lib/python3.7/site-packages (from Django==2.2.14) (0.3.1)
Installing collected packages: Django
  Found existing installation: Django 3.1.1
    Uninstalling Django-3.1.1:
      Successfully uninstalled Django-3.1.1
Successfully installed Django-2.2.14
You are using pip version 10.0.1, however version 20.2.3 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
```

Vérifier l'installation

```
(venv) [root@localhost ~]# python -m django --version
2.2.14
```

Une fois le projet django créé, changez le répertoire en djangoproject et migrez les modifications avec la commande suivante:

```
(djangoenv) [root@localhost opt]# cd djangop
(djangoenv) [root@localhost djangop]#  python3 manage.py migrate
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying sessions.0001_initial... OK
```

Ensuite, vous devrez créer un compte utilisateur administrateur pour gérer le projet Django. Vous pouvez le créer avec la commande suivante:

```
(djangoenv) [root@localhost djangop]# python3 manage.py createsuperuser
Username (leave blank to use 'root'): sabrine
Email address: sabrine.mzeh@gmail.com
Password:
Password (again):
The password is too similar to the email address.
This password is too short. It must contain at least 8 characters.
Bypass password validation and create user anyway? [y/N]: y
Superuser created successfully.
```

Par défaut, l'application Django n'est pas accessible depuis les hôtes distants.

Vous devrez donc autoriser Django pour les hôtes externes. Vous pouvez le faire en ajoutant l'adresse IP de votre serveur dans settings.py:

```
 cd /opt/djangop/djangop/settings.py
```

Modifiez la ligne suivante:  
`ALLOWED_HOSTS = ['192.168.1.6']`

Enregistrez et fermez le fichier.Ensuite, démarrez l'application Django avec la commande suivante:

```
djangoenv) [root@localhost djangop]#  python3 manage.py runserver 192.168.1.6:8000
Performing system checks...

System check identified no issues (0 silenced).
September 18, 2020 - 14:19:35
Django version 2.1.15, using settings 'djangop.settings'
Starting development server at http://192.168.1.6:8000/
Quit the server with CONTROL-C.
```

Vous pouvez accéder à l'application Django en visitant l'URL http: //192.168.1.6: 8000





![](/assets/import.png)

