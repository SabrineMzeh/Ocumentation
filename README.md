# Configuration des machines

##### 1.Installer Apache HTTP Server

Peu importe dans quel but vous utiliserez le serveur, dans la plupart des cas, vous avez besoin d'un serveur HTTP pour exécuter des sites Web, du multimédia, des scripts côté client et bien d'autres choses.

```
[root@localhost ~]#  yum install httpd -y
Modules complémentaires chargés : fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirrors.atosworldline.com
 * extras: ftp.pasteur.fr
 * updates: mirrors.atosworldline.com
Résolution des dépendances
--> Lancement de la transaction de test
---> Le paquet httpd.x86_64 0:2.4.6-93.el7.centos sera installé
Dépendances résolues

================================================================================
 Package            Architecture  Version                     Dépôt       Taille
================================================================================
Installation :
 httpd              x86_64        2.4.6-93.el7.centos         base        2.7 M
Installation pour dépendances :
 apr                x86_64        1.4.8-5.el7                 base        103 k
 apr-util           x86_64        1.5.2-6.el7                 base         92 k
 httpd-tools        x86_64        2.4.6-93.el7.centos         base         92 k
 mailcap            noarch        2.1.41-2.el7                base         31 k

Résumé de la transaction
================================================================================
Installation   1 Paquet (+4 Paquets en dépendance)
Installé :
  httpd.x86_64 0:2.4.6-93.el7.centos

Dépendances installées :
  apr.x86_64 0:1.4.8-5.el7                     apr-util.x86_64 0:1.5.2-6.el7
  httpd-tools.x86_64 0:2.4.6-93.el7.centos     mailcap.noarch 0:2.1.41-2.el7

Terminé !
```

Il faut activer le firewall :

```
[root@localhost ~]# systemctl enable firewalld
[root@localhost ~]# systemctl start firewalld
[root@localhost ~]# systemctl status firewalld
● firewalld.service - firewalld - dynamic firewall daemon
   Loaded: loaded (/usr/lib/systemd/system/firewalld.service; enabled; vendor preset: enabled)
   Active: active (running) since lun. 2020-09-07 14:50:11 CEST; 16min ago
     Docs: man:firewalld(1)
 Main PID: 680 (firewalld)
   CGroup: /system.slice/firewalld.service
           └─680 /usr/bin/python2 -Es /usr/sbin/firewalld --nofork --nopid

sept. 07 14:50:07 localhost.localdomain systemd[1]: Starting firewalld - dyna...
sept. 07 14:50:11 localhost.localdomain systemd[1]: Started firewalld - dynam...
sept. 07 14:50:12 localhost.localdomain firewalld[680]: WARNING: AllowZoneDri...
Hint: Some lines were ellipsized, use -l to show in full.
```

Autoriser le service **http à **travers le pare-feu

```
[root@localhost ~]# firewall-cmd --add-service=http
success
```

Autoriser le port **80 à **travers le pare-feu

```
[root@localhost ~]# firewall-cmd --permanent --add-port=3221/tcp
success
```

Rechargez le pare-feu.

```
[root@localhost ~]# firewall-cmd --reload
success
```

Après avoir fait toutes les choses ci-dessus, il est maintenant temps de redémarrer **le **serveur **HTTP Apache**

```
[root@localhost ~]# systemctl restart httpd.service
```

Ajoutez maintenant le service Apache à l'ensemble du système pour démarrer automatiquement au démarrage du système

```
[root@localhost ~]# systemctl enable httpd.service
Created symlink from /etc/systemd/system/multi-user.target.wants/httpd.service to /usr/lib/systemd/system/httpd.service.
```

##### 2. Installer PHP

PHP est un langage de script côté serveur pour les services Web.Il est également fréquemment utilisé comme langage de programmation à usage général

```
[root@localhost ~]# yum install php -y
Modules complémentaires chargés : fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirrors.atosworldline.com
 * extras: ftp.pasteur.fr
 * updates: mirrors.atosworldline.com
Résolution des dépendances
--> Lancement de la transaction de test
---> Le paquet php.x86_64 0:5.4.16-48.el7 sera installé
--> Traitement de la dépendance : php-common(x86-64) = 5.4.16-48.el7 pour le paquet : php-5.4.16-48.el7.x86_64
--> Traitement de la dépendance : php-cli(x86-64) = 5.4.16-48.el7 pour le paquet : php-5.4.16-48.el7.x86_64
--> Lancement de la transaction de test
---> Le paquet php-cli.x86_64 0:5.4.16-48.el7 sera installé
---> Le paquet php-common.x86_64 0:5.4.16-48.el7 sera installé
--> Traitement de la dépendance : libzip.so.2()(64bit) pour le paquet : php-common-5.4.16-48.el7.x86_64
--> Lancement de la transaction de test
---> Le paquet libzip.x86_64 0:0.10.1-8.el7 sera installé
--> Résolution des dépendances terminée
Installé :
  php.x86_64 0:5.4.16-48.el7

Dépendances installées :
  libzip.x86_64 0:0.10.1-8.el7             php-cli.x86_64 0:5.4.16-48.el7
  php-common.x86_64 0:5.4.16-48.el7

Terminé !
```

Après avoir installé php, assurez-vous de redémarrer le service Apache pour rendre PHP dans le navigateur Web.

```
[root@localhost ~]# systemctl restart httpd.service
```

##### 3.Installer la base de données MariaDB

**MariaDB **est un fork de **MySQL**. RedHat Enterprise Linux et ses dérivés sont passés de MySQL à MariaDB. C'est le système de gestion de base de données primaire. C'est encore l'un de ces outils qu'il est nécessaire d'avoir et vous en aurez besoin tôt ou tard, quel que soit le type de serveur que vous définissez

```
[root@localhost ~]# yum install mariadb-server mariadb -y
Modules complémentaires chargés : fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirrors.atosworldline.com
 * extras: ftp.pasteur.fr
 * updates: mirrors.atosworldline.com
Résolution des dépendances
--> Lancement de la transaction de test
---> Le paquet mariadb.x86_64 1:5.5.65-1.el7 sera installé
--> Lancement de la transaction de test
---> Le paquet perl.x86_64 4:5.16.3-295.el7 sera installé
-
================================================================================
 Package                      Architecture
                                          Version               Dépôt     Taille
================================================================================
 00:00
(16/37): perl-PlRPC-0.2020-14.el7.noarch.rpm               |  36 kB   00:00
(17/37): perl-Pod-Escapes-1.04-295.el7.noarch.rpm          |  51 kB   00:00
(18/37): perl-Pod-Perldoc-3.20-4.el7.noarch.rpm            |  87 kB   00:00
(19/37): perl-Pod-Simple-3.28-4.el7.noarch.rpm             | 216 kB   00:00
(20/37): perl-Pod-Usage-1.63-3.el7.noarch.rpm              |  27 kB   00:00
(21/37): perl-Scalar-List-Utils-1.27-248.el7.x86_64.rpm    |  36 kB   00:00
(22/37): perl-Socket-2.010-5.el7.x86_64.rpm                |  49 kB   00:00
(23/37): perl-Storable-2.45-3.el7.x86_64.rpm               |  77 kB   00:00
(24/37): perl-Text-ParseWords-3.29-4.el7.noarch.rpm        |  14 kB   00:00
(25/37): perl-Time-HiRes-1.9725-3.el7.x86_64.rpm           |  45 kB   00:00
(26/37): perl-Time-Local-1.2300-2.el7.noarch.rpm           |  24 kB   00:00
(27/37): perl-constant-1.27-2.el7.noarch.rpm               |  19 kB   00:00
(28/37): mariadb-server-5.5.65-1.el7.x86_64.rpm            |  11 MB   00:08
(29/37): perl-macros-5.16.3-295.el7.x86_64.rpm             |  44 kB   00:00
(30/37): perl-parent-0.225-244.el7.noarch.rpm              |  12 kB   00:00
(31/37): perl-podlators-2.5.1-3.el7.noarch.rpm             | 112 kB   00:00
(32/37): perl-threads-1.87-4.el7.x86_64.rpm                |  49 kB   00:00
(33/37): perl-threads-shared-1.43-6.el7.x86_64.rpm         |  39 kB   00:00
(34/37): perl-libs-5.16.3-295.el7.x86_64.rpm               | 689 kB   00:01
(35/37): mariadb-5.5.65-1.el7.x86_64.rpm                   | 8.7 MB   00:13
(36/37): perl-5.16.3-295.el7.x86_64.rpm                    | 8.0 MB   00:15
(37/37): perl-Exporter-5.68-3.el7.noarch.rpm               |  28 kB   00:00
--------------------------------------------------------------------------------
Total                                              956 kB/s |  33 MB  00:35
Running transaction check
Running transaction test
Transaction test succeeded

Installé :
  mariadb.x86_64 1:5.5.65-1.el7       mariadb-server.x86_64 1:5.5.65-1.el7

Terminé !
```

Démarrez et configurez MariaDB pour démarrer automatiquement au démarrage.

```
[root@localhost ~]# systemctl start mariadb.service
[root@localhost ~]# systemctl enable mariadb.service
Created symlink from /etc/systemd/system/multi-user.target.wants/mariadb.service to /usr/lib/systemd/system/mariadb.service.
```

Autoriser le service mysql \(**mariadb**\) à travers le pare-feu.

```
[root@localhost ~]# firewall-cmd --add-service=mysql
success
```

##### 4. Installer GCC :

**GCC **signifie **GNU Compiler Collection **est un système de compilation développé par GNU Project qui prend en charge divers langages de programmation.

```
[root@localhost ~]# yum install gcc
Modules complémentaires chargés : fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirrors.atosworldline.com
 * extras: ftp.pasteur.fr
 * updates: mirrors.atosworldline.com
Résolution des dépendances
--> Lancement de la transaction de test
---> Le paquet gcc.x86_64 0:4.8.5-39.el7 sera installé
Installé :
  gcc.x86_64 0:4.8.5-39.el7

Dépendances installées :
  cpp.x86_64 0:4.8.5-39.el7
  glibc-devel.x86_64 0:2.17-307.el7.1
  glibc-headers.x86_64 0:2.17-307.el7.1
  kernel-headers.x86_64 0:3.10.0-1127.19.1.el7
  libmpc.x86_64 0:1.0.1-3.el7
  mpfr.x86_64 0:3.1.1-4.el7

Terminé !
```

Vérifiez la version de **gcc **installé.

```
[root@localhost ~]# gcc --version
gcc (GCC) 4.8.5 20150623 (Red Hat 4.8.5-39)
```

##### 5.Tester Perfermance

installer un outil stress

```
[root@localhost ~]# yum install stress -y

Dépendances résolues

=============================================================================================================================================
 Package                         Architecture                    Version                                 Dépôt                         Taille
=============================================================================================================================================
Installation :
 stress                          x86_64                          1.0.4-16.el7                            epel                           39 k

Résumé de la transaction
=============================================================================================================================================
Installation   1 Paquet
                                                                                           1/1
Installé :
  stress.x86_64 0:1.0.4-16.el7

Terminé !

```



# Ocumentation
