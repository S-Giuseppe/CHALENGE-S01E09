# CHALENGE S01E09

**Exercice :**

#### Pour les adresses IP et masques de sous-réseau suivants :

1. 192.168.13.67/24
2. 172.16.0.1 – 255.255.255.0
3. 172.16.27.32/23
4. 10.7.5.1 – 255.255.128.0
5. 10.42.0.82/12

#### Calculez avec la méthode de votre choix (idéalement essayez d’utiliser les deux) :

* L’adresse de réseau
* L’adresse de broadcast
* Le nombre d’adresses utilisables par des machines
* La plage d’adresses disponibles

#### Puis vérifiez vos calculs avec une calculatrice en ligne

## 1. 192.168.13.67/24

Adresse IP en Binaire: 

**1100 0000.1010 1000.0000 1101.0100 0011**

Je détermine le masque sous réseau:  
/24 (en CIDR) étant 24 bits réseau (soit 8 bits pour l’hôte), cela donne en notation binaire :

**1111 1111.1111 1111.1111 1111.0000 0000**

Soit:

**255.255.255.0**

#### - Calcul avec metode ET, OU, NOT Logique

Pour trouver l'Adresse Réseau, je fait :  

* Un ET Logique :

|Adresse IP (en binaire)|1100 0000.1010 1000.0000 1101.0100 0011|
| :--------------- |:---------------:|
|**Masque sous réseau**|**1111 1111.1111 1111.1111 1111.0000 0000**|
|**Adresse réseau**|**1100 0000.1010 1000.0000 1101.0000 0000**|

Soit: **192.168.13.0**

Pour trouver l'Adresse Broadcast je fais:  

* Un NOT Logique:  

|Masque sous réseau|1111 1111.1111 1111.1111 1111.0000 0000|
| :--------------- |:---------------:|
|**En NOT Logique**|**0000 0000.0000 0000.0000 0000.1111 1111**|  

* Puis un OU Logique, entre le NOT Logique et l'Adresse Réseau:  

|**NOT Logique**|**0000 0000.0000 0000.0000 0000.1111 1111**|
| :--------------- |:---------------:|
|**Adresse réseau**|**1100 0000.1010 1000.0000 1101.0000 0000**|
|**OU Logique**|**1100 0000.1010 1000.0000 1101.1111 1111**|  

Soit: **192.168.13.255**  

#### - Calcul avec la méthode du "Nombre Magique"  

Adresse IP : **192.168.13.67**  
Masque s/réseau : **255.255.255.0**

Ici l'octet significatif sur le masque de sous réseau va être le 4eme, soit 0.  

Donc mon calcul est 256-0 = **256** (Nombre Magique)  

Les multiples de mon nombre magique sont :  
**0**, **256**.  

* Pour trouver l'Adresse Réseau:

Je remplace donc le 4eme octet de l'adresse IP par le multiple du nombre magique inférieur ou égal à la valeur de l'octet dans l'adresse, soit par **0**.  

Adresse Réseau : **192.168.13.0**

* Pour trouver l'Adresse Broadcast:

Je remplace donc le 4eme octet de l'adresse IP par le multiple du nombre magique suivant, moins 1, soit 256-1 = **255**

Adresse Broadcast : **192.168.13.255**

### Calcul du nombre d'adresses utilisables et la plage d'adresses disponibles

* Pour le nombre d'adresses utilisables:

Je prends le nombre de bits de l'hote dans mon adresses du masque sous reseau, soit **8**.  
Calcul : 2^8 = 256 adresses utilisables, moins les 2 réservées à l'adresse réseau et broadcast = 256-2= **254** adresses utilisables par des machines.  

* Pour la plage d'adresses disponibles:

Elle est donc comprise entre **192.168.13.1** et **192.168.13.254**. 

## 2. 172.16.0.1 – 255.255.255.0

Adresse IP en Binaire:  

**1010 1100.0001 0000.0000 0000.0000 0001**  

Ici nous avons déjà le masque sous réseau:  

255.255.255.0

Soit en binaire :  
  
**1111 1111.1111 1111.1111 1111.0000 0000**  
  
Son CIDR est **/24**, soit 24 bits réseau (donc 8 bits pour l’hôte).  
  
#### - Calcul avec metode ET, OU, NOT Logique


Pour trouver l'Adresse Réseau, je fait :  

* Un ET Logique :  

|Adresse IP (en binaire)|1010 1100.0001 0000.0000 0000.0000 0001|
| :--------------- |:---------------:|
|**Masque sous réseau**|**1111 1111.1111 1111.1111 1111.0000 0000**|
|**Adresse réseau**|**1010 1100.0001 0000.0000 0000.0000 0000**|  
  
Soit: **172.16.0.0**

Pour trouver l'Adresse Broadcast je fais:  

* Un NOT Logique:  

|Masque sous réseau|1111 1111.1111 1111.1111 1111.0000 0000|
| :--------------- |:---------------:|
|**En NOT Logique**|**0000 0000.0000 0000.0000 0000.1111 1111**|  

* Puis un OU Logique, entre le NOT Logique et l'Adresse Réseau:  

|**NOT Logique**|**0000 0000.0000 0000.0000 0000.1111 1111**|
| :--------------- |:---------------:|
|**Adresse réseau**|**1010 1100.0001 0000.0000 0000.0000 0000**|
|**OU Logique**|**1010 1100.0001 0000.0000 0000.1111 1111**|  

Soit: **172.16.0.255**

#### - Calcul avec la méthode du "Nombre Magique"  

Adresse IP : **172.16.0.1**  
Masque s/réseau : **255.255.255.0**  

Ici l'octet significatif sur le masque de sous réseau va être le 4eme, soit 0.  

Donc mon calcul est 256-0 = **256** (Nombre Magique)  

Les multiples de mon nombre magique sont :  
**0**, **256**.  

* Pour trouver l'Adresse Réseau:

Je remplace donc le 4eme octet de l'adresse IP par le multiple du nombre magique inférieur ou égal à la valeur de l'octet dans l'adresse, soit par **0**.  

Adresse Réseau : **172.16.0.0**

* Pour trouver l'Adresse Broadcast:

Je remplace donc le 4eme octet de l'adresse IP par le multiple du nombre magique suivant, moins 1, soit 256-1 = **255**

Adresse Broadcast : **172.16.0.255**

### Calcul du nombre d'adresses utilisables et la plage d'adresses disponibles

* Pour le nombre d'adresses utilisables:

Je prends le nombre de bits de l'hote dans mon adresses du masque sous reseau, soit **8**.  
Calcul : 2^8 = 256 adresses utilisables, moins les 2 réservées à l'adresse réseau et broadcast = 256-2= **254** adresses utilisables par des machines.  

* Pour la plage d'adresses disponibles:

Elle est donc comprise entre **172.16.0.1** et **172.16.0.254**.  

## 3. 172.16.27.32/23. 

Adresse IP en Binaire: 

**1010 1100.0001 0000.0001 1011.0010 0000**

Je détermine le masque sous réseau:  
/23 (en CIDR) étant 23 bits réseau (soit 9 bits pour l’hôte), cela donne en notation binaire :

**1111 1111.1111 1111.1111 1110.0000 0000**

Soit:

**255.255.254.0**

#### - Calcul avec metode ET, OU, NOT Logique 

Pour trouver l'Adresse Réseau, je fait :  

* Un ET Logique :

|Adresse IP (en binaire)|1010 1100.0001 0000.0001 1011.0010 0000|
| :--------------- |:---------------:|
|**Masque sous réseau**|**1111 1111.1111 1111.1111 1110.0000 0000**|
|**Adresse réseau**|**1010 1100.0001 0000.0001 1010.0000 0000**|

Soit: **172.16.26.0**

Pour trouver l'Adresse Broadcast je fais:  

* Un NOT Logique:  

|Masque sous réseau|1111 1111.1111 1111.1111 1110.0000 0000|
| :--------------- |:---------------:|
|**En NOT Logique**|**0000 0000.0000 0000.0000 0001.1111 1111**|  

* Puis un OU Logique, entre le NOT Logique et l'Adresse Réseau:  

|**NOT Logique**|**0000 0000.0000 0000.0000 0001.1111 1111**|
| :--------------- |:---------------:|
|**Adresse réseau**|**1010 1100.0001 0000.0001 1010.0000 0000**|
|**OU Logique**|**1010 1100.0001 0000.0001 1011.1111 1111**|  

Soit: **172.16.27.255**  

#### - Calcul avec la méthode du "Nombre Magique"  

Adresse IP : **172.16.27.32**  
Masque s/réseau : **255.255.254.0**

Ici l'octet significatif sur le masque de sous réseau va être le 3eme, soit 254.  

Donc mon calcul est 256-254 = **2** (Nombre Magique)  

Les multiples de mon nombre magique sont :  
**0**, **2**,**4**, **6**, **8**,**...**, **24**, **26**, **28**, **30**,**...**, **254**, **256**.  