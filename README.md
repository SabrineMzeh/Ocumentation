# Configuration des machines

1. ##### Installez Apache HTTP Server

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

##### 2. Install PHP

PHP est un langage de script côté serveur pour les services Web.Il est également fréquemment utilisé comme langage de programmation à usage général



