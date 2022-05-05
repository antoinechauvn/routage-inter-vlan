# routage-inter-vlan

### Qu'est-ce que le routage inter-vlan ?
```
Le routage inter-VLAN est un processus qui permet de transférer du trafic réseau d'un VLAN à un autre à l'aide
d'un périphérique de couche 3 comme un routeur.
```

Il y’a 3 manières différentes pour faire du routage inter-vlan: 

* 1 Interface pour 1 vlan<br>
Par exemple, les pc’s du vlan 10 envoient le trafic via le routeur pour atteindre le vlan 20. <br>
Le problème avec cette solution, c’est qu’il faut utiliser une interface distincte du routeur pour chaque vlan. Plus il y’a de vlan, et plus il faut bloquer des interfaces sur le routeur. <br>
Avec ce système, le routeur risque de manquer d’interface. Cette solution n’est vraiment pas évolutive.

![image](https://user-images.githubusercontent.com/83721477/167014312-8651a162-475c-4329-b1b7-b36f98914b56.png)

* Router on a Stick<br>
C’est un type de configuration dans lequel une seule interface physique relie le trafic entre plusieurs VLAN sur un réseau.
Le routeur effectue le routage inter-VLAN à l'aide de ses sous-interfaces. Les sous-interfaces sont des interfaces virtuelles multiples associées à une interface physique<br>
Chaque vlan, dois avoir sa propre interface virtuelle.<br>
Chacune de ses sous-interfaces est configurée indépendamment avec une adresse IP.

![image](https://user-images.githubusercontent.com/83721477/167014349-41db353f-78cd-4a3b-a070-2726b53434ad.png)

* SVI<br>
Le routage inter-VLAN est plus évolutif sur un switch de couche 3 que sur un routeur, car un routeur transmet le trafic à travers le trunk configuré avec le switch. Le switch de couche 3 permet de s’acquitter de ce goulot d’étranglement.<br>
Pour permettre aux switchs de couche 3 d’effectuer le routage entre les vlan 10 et 20 il faut créer les interfaces vlan et leurs spécifier une ip qui correspondra à la passerelle par défaut de chaque vlan.

![image](https://user-images.githubusercontent.com/83721477/167014327-17cc8f6d-177e-4d79-b02f-4217600ec277.png)

*Note: Il n'y a qu'une correspondance entre un SVI et un VLAN*
