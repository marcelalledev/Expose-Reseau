# Expose-Reseau
Une explication claire et concrète de ce qui se passe lorsque vous tapez une URL dans un navigateur : adressage IP, DNS, TCP/UDP et fonctionnement réel d’Internet.
```markdown
# Page de garde
RÉPUBLIQUE DU BÉNIN 
\*\*\*\*\*\*\* 
MINISTÈRE **DE L'ENSEIGNEMENT SUPÉRIEUR ET DE LA RECHERCHE SCIENTIFIQUE** 
\*\*\*\*\*\* 
**ÉCOLE SUPÉRIEURE DE COMMERCE ET D'ADMINISTRATION D'ENTREPRISE** 
\*\*\*\*\*\* 
**[ANNÉE D'ÉTUDE :]** Licence 1 
[**MATIÈRE** :] Fondamentaux réseaux et systèmes 
**[THÈME :]** 
**L'ADRESSAGE IP ET LES DIFFERENTES PROTOCOLES RESEAUX** 
**[Présenter par :]** ALLE Marcel 
**[Sous la supervision :]**Mr KEKE  M. Turibio 
**Février 2026**
---
# SOMMAIRE
[INTRODUCTION](#introduction) 
[I. ADRESSAGE IP : IDENTIFIER LES MACHINES](#adressage-ip-identifier-les-machines) 
 [A. Rôle d'une adresse IP](#rôle-dune-adresse-ip) 
 [B. IPv4 vs IPv6](#ipv4-vs-ipv6) 
 [C. IP publique vs IP privée](#ip-publique-vs-ip-privée) 
[II. PROTOCOLES RÉSEAU : Organiser la communication](#protocoles-réseau--organiser-la-communication) 
 [A. Rôle des protocoles](#rôle-des-protocoles) 
 [B. Protocole IP](#protocole-ip) 
 [C. Protocole TCP](#protocole-tcp) 
 [D. Protocole UDP](#protocole-udp) 
 [E. Protocoles essentiels (DNS, DHCP, ARP, ICMP)](#protocoles-essentiels-dns-dhcp-arp-icmp) 
[III – FONCTIONNEMENT GLOBAL D'UNE COMMUNICATION](#iii--fonctionnement-global-dune-communication) 
 [A. Étapes d'une communication](#étapes-dune-communication) 
 [B. Encapsulation](#encapsulation) 
 [C. Rôle des équipements (routeur, switch)](#rôle-des-équipements-routeur-switch) 
[CONCLUSION](#conclusion) 
[WEBOGRAPHIE](#webographie)
---
# INTRODUCTION
Imaginez la scène : vous tapez « google.com » dans votre navigateur. En quelques millisecondes, la page s'affiche. Pourtant, entre votre ordinateur et le serveur de Google, des milliers de kilomètres sont parcourus, des dizaines d'équipements sont sollicités. Comment votre message arrive‑t‑il exactement au bon endroit, sans se perdre ?
C'est là qu'interviennent deux piliers fondamentaux d'Internet : l'adressage IP, qui donne une identité à chaque machine, et les protocoles réseau, qui organisent les échanges.
Dans un premier temps, nous verrons comment les machines sont identifiées grâce à l'adressage IP. Ensuite, nous étudierons les principaux protocoles qui permettent une communication fiable ou rapide. Enfin, nous mettrons en lumière le fonctionnement global d'une communication, du navigateur au serveur.
---
# I. ADRESSAGE IP : IDENTIFIER LES MACHINES
## A. Rôle d'une adresse IP
Une adresse IP (Internet Protocol) est un identifiant unique attribué à chaque appareil connecté à un réseau (ordinateur, smartphone, imprimante, objet connecté...).
On peut la comparer à un numéro de téléphone : elle permet à la fois d'identifier la machine et de savoir où la joindre sur le réseau. Sans elle, les données ne pourraient pas être acheminées correctement.

## B. IPv4 vs IPv6
Il existe deux versions principales du protocole IP.
- **IPv4** (Internet Protocol version 4) : elle utilise des adresses de 32 bits, écrites sous forme de quatre nombres décimaux séparés par des points (exemple : 192.168.1.1). Cela donne environ 4,3 milliards d'adresses. À l'époque de sa création, cela semblait immense, mais avec l'explosion du nombre d'appareils connectés, le pool d'adresses IPv4 s'est épuisé.
- **IPv6** (Internet Protocol version 6) : conçue pour pallier cette pénurie, elle utilise des adresses de 128 bits, écrites en hexadécimal (exemple : 2001:0db8:85a3::8a2e:0370:7334). Le nombre d'adresses est tellement grand qu'il permet d'attribuer une adresse unique à chaque objet connecté pendant des décennies. IPv6 apporte aussi des améliorations en matière de sécurité et de simplification des en-têtes.
Aujourd'hui, les deux versions coexistent, mais la transition vers IPv6 est indispensable pour accompagner la croissance d'Internet.

## C. IP publique vs IP privée
Toutes les adresses IP ne sont pas utilisées de la même manière.
- **Adresse IP privée** : elle est utilisée au sein d'un réseau local (maison, entreprise, école). Elle n'est pas routable sur Internet. Les plages les plus courantes sont 192.168.x.x, 10.x.x.x ou 172.16.x.x. Plusieurs machines peuvent utiliser les mêmes plages privées dans des réseaux différents sans conflit.
- **Adresse IP publique** : elle est attribuée par un fournisseur d'accès à Internet (FAI) et est unique sur Internet. Elle permet à un équipement d'être directement joignable depuis le réseau mondial.
Un point important : une même machine peut avoir plusieurs adresses IP selon le contexte. Par exemple, votre ordinateur possède une adresse privée dans votre réseau domestique, mais derrière la box, c'est l'adresse publique de la box qui est visible sur Internet. Le routeur (ou la box) fait le lien entre les deux grâce à une technique appelée NAT (Network Address Translation).

---
# II. PROTOCOLES RÉSEAU : Organiser la communication
![](media/image6.jpeg){width="2.4743449256342958in" height="2.3461548556430447in"}
![](media/image7.jpg){width="3.044873140857393in" height="1.826923665791776in"}
## A. Rôle des protocoles
Avoir des adresses ne suffit pas. Pour communiquer, les machines doivent respecter des règles communes : ce sont les protocoles. Ils définissent le format des données, les modalités d'envoi, la gestion des erreurs, etc. Sans eux, chaque équipement parlerait un langage différent et l'échange serait impossible.
## B. Protocole IP
Le protocole IP (Internet Protocol) est le pilier de l'acheminement. Il s'occupe de faire circuler les paquets de données d'une machine à une autre en se basant sur les adresses IP.
Sa caractéristique principale est qu'il fonctionne sans connexion et sans garantie : il envoie les paquets, mais ne vérifie pas s'ils arrivent, ni dans quel ordre. On dit qu'il assure un service de « meilleur effort ».
## C. Protocole TCP
TCP (Transmission Control Protocol) vient compléter IP pour apporter la fiabilité. Il établit une connexion logique entre l'émetteur et le récepteur avant d'envoyer les données.
Il numérote chaque paquet, vérifie leur arrivée, et demande un réenvoi si certains sont perdus ou erronés. Il garantit également que les données sont reconstituées dans l'ordre original.
C'est le protocole utilisé par la navigation web, les courriels, le transfert de fichiers (FTP), etc.
## D. Protocole UDP
UDP (User Datagram Protocol) est l'alternative à TCP. Il n'établit pas de connexion préalable et ne vérifie rien. Il envoie les paquets sans se soucier des pertes ni de l'ordre.
En contrepartie, il est beaucoup plus rapide et introduit une latence très faible.
UDP est privilégié pour les applications où la rapidité prime sur la fiabilité : streaming vidéo, visioconférence, jeux en ligne, téléphonie sur IP (VoIP).

## E. Protocoles essentiels (DNS, DHCP, ARP, ICMP)
Quelques protocoles viennent compléter le fonctionnement des réseaux :
- **DNS** (Domain Name System) : il fait le lien entre les noms de domaine (google.com) et les adresses IP. Grâce à lui, nous n'avons pas à retenir des suites de chiffres.
- **DHCP** (Dynamic Host Configuration Protocol) : il attribue automatiquement une adresse IP, un masque de sous-réseau et d'autres paramètres à une machine qui se connecte à un réseau. Cela évite une configuration manuelle.
- **ARP** (Address Resolution Protocol) : il permet de trouver l'adresse physique (MAC) d'un équipement à partir de son adresse IP au sein d'un même réseau local.
- **ICMP** (Internet Control Message Protocol) : il sert à transmettre des messages d'erreur ou d'information. La commande « ping » utilise ICMP pour tester la connectivité avec une machine distante.
---
# III – FONCTIONNEMENT GLOBAL D'UNE COMMUNICATION

## A. Étapes d'une communication
Prenons l'exemple d'un utilisateur qui souhaite consulter le site google.com.
- L'utilisateur tape l'URL dans le navigateur.
- Le système interroge un serveur DNS pour obtenir l'adresse IP de google.com.
- Une fois l'IP connue, le navigateur utilise TCP pour établir une connexion avec le serveur (c'est le « three-way handshake » : SYN, SYN-ACK, ACK).
- La requête HTTP est découpée en petits paquets par TCP.
- Chaque paquet reçoit un en-tête IP (avec adresses source et destination) et est envoyé sur le réseau.
- Les paquets traversent des routeurs qui, grâce à des tables de routage, les dirigent vers le serveur.
- Le serveur reçoit les paquets, les réassemble, traite la requête et renvoie une réponse selon le même processus.
- Le navigateur affiche la page.
## B. Encapsulation

Chaque fois que des données circulent, elles sont « emballées » par les différentes couches protocolaires. C'est ce qu'on appelle l'encapsulation.
- Les données utilisateur sont d'abord encapsulées dans un segment TCP (ou UDP).
- Ce segment est encapsulé dans un paquet IP (ajout de l'en-tête IP).
- Le paquet IP est encapsulé dans une trame (ajout d'un en-tête Ethernet avec adresses MAC).
On peut comparer cela à un colis : les données sont l'objet, le segment TCP est le carton, l'en-tête IP est l'étiquette de destination, et la trame Ethernet est le bordereau d'expédition local.
## C. Rôle des équipements (routeur, switch)

- **Switch (commutateur)** : il opère au niveau local. Il lit les adresses MAC contenues dans les trames et aiguille les données uniquement vers le destinataire concerné au sein du même réseau.
- **Routeur** : il relie des réseaux différents. Il lit les adresses IP et décide, grâce à une table de routage, vers quel réseau il doit faire suivre chaque paquet. C'est lui qui permet la communication entre votre réseau domestique et Internet.
---
# CONCLUSION
Nous avons parcouru les fondements de la communication réseau.
L'adressage IP donne une identité unique à chaque machine, qu'il s'agisse d'une adresse privée dans un réseau local ou d'une adresse publique sur Internet.
Les protocoles, quant à eux, organisent les échanges : IP achemine, TCP assure la fiabilité, UDP privilégie la rapidité, et des services comme DNS, DHCP, ARP et ICMP facilitent le fonctionnement quotidien.
Comprendre ces mécanismes permet de mieux appréhender les enjeux actuels : la transition vers IPv6 pour répondre à la croissance du nombre d'appareils, la sécurisation des communications (avec IPSec, TLS, etc.), et l'explosion des objets connectés (IoT) qui imposent de nouveaux défis en termes d'adressage et de protocoles.
---
# WEBOGRAPHIE
**Sources et documents de référence**
- IETF – RFC Editor 
  https://www.rfc-editor.org/
- AFRINIC – Informations sur l'adressage IP 
  https://www.afrinic.net/fr/about-us/ip-resources
- AFRINIC – Recherche WHOIS 
  https://www.afrinic.net/fr/services/whois-query ;
  Interface publique pour consulter à qui appartient une adresse IP publique.
- AFNIC – Comprendre le DNS (vidéo pédagogique) 
  https://www.afnic.fr/observatoire-ressources/actualites/lafnic-met-en-ligne-une-video-sur-les-coulisses-des-noms-de-domaine/
- Cisco Networking Academy – Introduction to Networks 
  https://www.netacad.com/courses/networking/introduction-networks
- Computer Networking : A Top-Down Approach (site compagnon) 
  http://gaia.cs.umass.edu/kurose_ross/index.php
- Cloudflare – Qu'est-ce qu'une adresse IP ? 
  https://www.cloudflare.com/fr-fr/learning/dns/glossary/what-is-my-ip-address/
```
