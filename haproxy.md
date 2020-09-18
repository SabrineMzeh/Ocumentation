## Haproxy load balancer

[**HAProxy**](http://www.haproxy.org/) est une solution gratuite, très rapide et fiable offrant une haute disponibilité, un équilibrage de charge et un proxy pour les applications TCP et HTTP.Il est particulièrement adapté aux sites Web à très fort trafic et alimente un certain nombre de sites parmi les plus visités au monde.

##### 1.**installer Haproxy**

Exécutez la commande ci-dessous pour installer haproxy:

```
[root@localhost ~]# sudo yum install haproxy
Modules complémentaires chargés : fastestmirror
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

Taille totale des téléchargements : 834 k
Taille d'installation : 2.6 M
Is this ok [y/d/N]: y
Downloading packages:
haproxy-1.5.18-9.el7.x86_64.rpm                                                                                       | 834 kB  00:00:01
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installation : haproxy-1.5.18-9.el7.x86_64                                                                                             1/1
  Vérification : haproxy-1.5.18-9.el7.x86_64                                                                                             1/1

Installé :
  haproxy.x86_64 0:1.5.18-9.el7

Terminé !
```

##### 2.configuration de **load balancer**

Nous allons créer un fichier de configuration **/etc/haproxy/haproxy.cfg **contenant les paramètres et configurations nécessaires.

Et on ajoute cette partie :

```
[root@localhost ~]# cat /etc/haproxy/haproxy.cfg

global
   log /dev/log local0
   log /dev/log local1 notice
   chroot /var/lib/haproxy
   stats socket /run/haproxy/admin.sock mode 660 level admin
    stats timeout 30s
    user haproxy
    group haproxy
    daemon

defaults
     log global
     mode http
     option httplog
     option dontlognull
     timeout connect 5000
     timeout client 50000
     timeout server 50000

frontend http_front
     bind *:80
     stats uri /haproxy?stats
     default_backend http_back

backend http_back
     balance roundrobin
     server my_server private_IP:80 check
     server my_server private_IP:80 check
```

Ensuite,redémarrez Haproxy en utilisant la commande ci-dessous:

```
[root@localhost ~]# sudo systemctl restart haproxy
[root@localhost ~]# sudo systemctl enable haproxy
Created symlink from /etc/systemd/system/multi-user.target.wants/haproxy.service to /usr/lib/systemd/system/haproxy.service.
```



