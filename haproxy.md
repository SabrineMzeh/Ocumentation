## Haproxy load balancer

[**HAProxy**](http://www.haproxy.org/) est une solution gratuite, très rapide et fiable offrant une haute disponibilité, un équilibrage de charge et un proxy pour les applications TCP et HTTP.Il est particulièrement adapté aux sites Web à très fort trafic et alimente un certain nombre de sites parmi les plus visités au monde.

##### 1.**installer Haproxy**

Exécutez la commande ci-dessous pour installer haproxy:

```
[root@localhost ~]# sudo yum install haproxy
Modules complémentaires chargés : fastestmirror
Loading mirror speeds from cached hostfile
 * base: centos.crazyfrogs.org
 * epel: mirror.hostnet.nl
 * extras: mirrors.atosworldline.com
 * updates: centos.crazyfrogs.org
Résolution des dépendances
--> Lancement de la transaction de test
---> Le paquet haproxy.x86_64 0:1.5.18-9.el7 sera installé
--> Résolution des dépendances terminée

Dépendances résolues

=============================================================================================================================================
 Package                          Architecture                    Version                                Dépôt                         Taille
=============================================================================================================================================
Installation :
 haproxy                          x86_64                          1.5.18-9.el7                           base                          834 k

Résumé de la transaction
=============================================================================================================================================
Installation   1 Paquet

Taille totale des téléchargements : 834 k
Taille d'installation : 2.6 M
Is this ok [y/d/N]: y
Downloading packages:
haproxy-1.5.18-9.el7.x86_64.rpm                                                                                       | 834 kB  00:00:01
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installation : haproxy-1.5.18-9.el7.x86_64                                                                                             1/1
  Vérification : haproxy-1.5.18-9.el7.x86_64                                                                                             1/1

Installé :
  haproxy.x86_64 0:1.5.18-9.el7

Terminé !
```



