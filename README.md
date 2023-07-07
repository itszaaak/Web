# Web
## Sommaire  
1. [Frontend](#Frontend)  
   - [Theorie](#table-des-matières)  
   - [Projets](#Projets-frontend)
  
2. [Backend](#Backend)  

## Frontend
## Table des matières
- [Introduction](#introduction)
- [Structures Web](#structures-web)
  - [Client](#client)
  - [Server](#server)
  - [Passerelle](#passerelle)
  - [Cache](#cache)
  - [Proxy](#proxy)
  - [Reverse Proxy](#reverse-proxy)
  - [CDN](#cdn)
- [Hypermedia](#hypermedia)
- [Adressage](#adressage)
    - [L'url](#lurl)
    - [DNS](#dns)
- [HTTP](#http)
- [Côté client](#côté-client)



### Introduction

WEB et NET sont deux choses totalement différentes. Le "net" fait référence au réseau physique de câbles qui nous relie, tandis que le "Web" est plutôt un maillage de ressources interconnectées par l'hypermedia. L'objectif du Web est de fournir un système d'information global à grande échelle, décentralisé, tolérant aux pannes, extensible et évolutif. Cet objectif permet notamment la mise en place d'un client générique grâce à l'utilisation d'une représentation homogène (HTML) et l'utilisation d'un protocole uniforme (HTTP). Chaque ressource dans le Web possède une adresse unique et uniforme.

En revanche, le "net" est organisé en cinq couches distinctes indépendantes les unes des autres pour garantir une meilleure isolation :

1. Couche physique : RTC, ADSL, 100BASE-TX
2. Couche liaison : Ethernet, ATM, Wi-Fi, IPoAC (troll)
3. Couche réseau : IP, ICMP, BGP, X25
4. Couche transport : TCP, UDP
5. Couche application : HTTP, DNS, XMPP (chat), SMTP

Pour ce qui est du Web, les protocoles utilisés sont : HTTP, DNS, TCP, IP.

### Structures Web
#### Client
Le client du serveur joue un rôle essentiel dans l'envoi des requêtes au serveur pour manipuler les ressources via leur représentation spécifique. Il maintient l'état de l'application, car chaque utilisateur a un état différent, et cela se reflète lorsqu'ils interagissent avec l'application en se déplaçant à travers les graphes de ressources. Le serveur ne stocke pas l'état spécifique à chaque utilisateur, mais fournit plutôt les ressources et les fonctionnalités nécessaires pour que le client puisse gérer son propre état. Les clients du serveur comprennent les navigateurs web, qui permettent d'accéder aux ressources du Web et d'envoyer des requêtes, ainsi que les robots (crawler/scrapers) qui parcourent automatiquement les sites web pour extraire des données. Les agrégateurs sont également des clients du serveur, collectant des informations provenant de différentes sources via des flux RSS structurés (tels que XML) et effectuant des analyses sur ces données.

#### Server
Le client du serveur joue un rôle crucial dans le processus de communication. Il envoie des requêtes au serveur pour manipuler les ressources via leur représentation spécifique, tout en maintenant l'état de l'application du côté du client. Le client peut créer, détruire et gérer les ressources, en générant des représentations adéquates et en utilisant l'adressage URL pour accéder à l'information. Le serveur peut être statique ou dynamique, fournissant des fichiers HTML, CSS et JavaScript en lecture simple ou générant dynamiquement des représentations à partir d'un programme. Des exemples de serveurs incluent Apache, Nginx, mod_php, Node.js et Tomcat.

#### Passerelle
Les passerelles étaient utilisées dans le passé pour la conversion de protocoles, par exemple, pour transférer des fichiers via FTP afin de les afficher sur le Web. Cependant, ces passerelles sont devenues obsolètes avec l'évolution des technologies. Elles différaient des serveurs d'applications car elles étaient très générales et ne comportaient pas de logique métier spécifique. Un exemple de passerelle était "mod_proxy_FTP".

#### Cache
Le cache joue un rôle essentiel dans la mémorisation des requêtes. Lorsqu'il reçoit une requête identique à une précédente, il peut envoyer directement la réponse sans passer par le serveur, ce qui est particulièrement utile dans des situations telles que le retour en arrière dans une page web. Le cache peut être de deux types : local, intégré au navigateur, ou intermédiaire, placé entre le client et le serveur. Dans ce dernier cas, le client communique directement avec le cache, qui peut répondre si la réponse est déjà disponible. La mise en place d'un cache permet d'améliorer les performances en évitant les requêtes répétées au serveur, tout en rendant le système plus tolérant aux pannes du serveur. Un exemple de cache bien connu est "Varnish". En ce qui concerne les proxies, ils peuvent être configurés de deux manières : explicite, où le client les configure directement, ou transparente, où le client ne les voit pas car leur fonctionnement est géré automatiquement par le réseau.

#### Proxy
Les proxies côté client jouent un rôle essentiel dans divers aspects. Ils permettent le partage de connexion d'accès entre différentes machines au sein d'un même réseau, comme dans le cas des réseaux universitaires. De plus, les proxies peuvent être utilisés pour filtrer l'accès à des sites spécifiques, car ils examinent les requêtes et peuvent bloquer certaines d'entre elles. Ils offrent également des fonctionnalités d'optimisation des applications pour les appareils mobiles, telles que la compression des données. Les proxies peuvent également masquer la source de la connexion en attribuant une adresse IP au proxy, ce qui donne l'impression au serveur que la communication se fait avec le proxy plutôt qu'avec le client réel. Des exemples courants de proxies incluent Squid et Polipo.

#### Reverse Proxy
Le reverse proxy, également connu sous le nom de proxy côté serveur, offre plusieurs fonctionnalités essentielles. Tout d'abord, il permet la répartition de la surcharge sur plusieurs machines serveurs, garantissant ainsi des performances optimales tout en maintenant une seule URL pour les clients. De plus, le reverse proxy peut servir de portail d'intégration, permettant d'attribuer des rôles spécifiques à différentes machines pour un traitement efficace des requêtes. Par exemple, une machine peut être dédiée à l'affichage du contenu HTML tandis qu'une autre se charge des images. En outre, il agit comme un relais ou une passerelle vers d'autres serveurs, permettant de rediriger le trafic vers des serveurs spécifiques en fonction des besoins. Des exemples populaires de reverse proxies incluent Haproxy et Apache
#### CDN
Le Content Delivery Network (CDN) est un réseau de serveurs en miroir synchronisés qui sont répartis géographiquement, généralement un par continent. Les serveurs CDN sont spécialement conçus pour servir du contenu statique, tels que des images ou du texte HTML, afin de soulager la charge des serveurs d'application. Les CDN peuvent être publics, comme Amazon AWS et Azure, ou privés, comme ceux utilisés par Facebook. Le rôle des CDN est d'accepter davantage de données et d'utilisateurs afin de réduire la charge sur les serveurs des applications principales, améliorant ainsi les performances et la disponibilité du contenu.

### Hypermedia

Une ressource forme un bloc d'information unitaire. Ces blocs sont structurés par des liens, ce qui crée un système de graphes non linéaires navigables par découverte, c'est-à-dire qu'il n'est pas nécessaire de connaître leur existence au préalable. Ce système de graphes s'avère utile car il est très évolutif et permet la transclusion ou l'inclusion d'autres blocs dans un même bloc.

### Adressage 
Tout bloc d'information est identifieé par une adresse unique, un peu comme l'adresse de chez vous. Ce adressage s'appelle uri ou uniform ressource identifier. Dans l'uri on retrouve le urn ou uniform ressource name et le url ou uniform ressource loacaor, l'url est plus interessant pour le web

#### L'url
L'identifiant de ressource est unique dans l'espace, et cet espace est défini par le système de noms de domaine (DNS). De plus, cet identifiant peut être unique dans le temps, avec le serveur qui gère cette notion. L'identifiant est dereferençable, ce qui signifie qu'il contient suffisamment d'informations pour se connecter au serveur et récupérer le fichier associé. Il existe une structure sous-jacente qui permet cette opération. L'identifiant de ressource est défini par le serveur lui-même, sans nécessiter de gestion centrale. En d'autres termes, chaque individu peut gérer ses propres identifiants de ressource sans avoir à demander la permission à une autorité centrale. Cependant, l'identifiant peut être opaque pour le client, ce qui signifie qu'il n'a pas nécessairement une compréhension sémantique de ce qui se passe, contrairement au serveur qui peut interpréter l'identifiant de manière significative.

La structure d'une URL suit une représentation uniforme par protocole. Elle se compose de plusieurs parties distinctes. Tout d'abord, le "scheme" spécifie le protocole utilisé pour communiquer avec le serveur, déterminant ainsi la manière dont le client va interagir avec le serveur. Ensuite, le "hostname" (et le port, facultatif) indique où se trouve le serveur, soit par une adresse IP soit par un nom de domaine, garantissant l'unicité de l'adresse. Le "path" identifie la ressource localement sur le serveur, mais cette information est opaque pour le client. Le "path" peut être suivi d'une "query string" après le point d'interrogation, qui constitue le seul moyen pour l'utilisateur de construire les URL en ajoutant des paramètres à la demande. Le "fragment", qui apparaît après le dièse (#), représente une sous-ressource ou une partie spécifique du document, tel qu'un lien interne sur la même page ou une page spécifique dans un document PDF. Le client attribue une signification au fragment, qui dépend du type de représentation utilisée.

Le client n'a pas besoin de comprendre autre chose que la structure de l'URL lorsqu'il interagit avec le serveur. Cela permet un découplage entre le client et le serveur, ce qui signifie qu'il est possible d'utiliser un client unique pour accéder à différents serveurs. Par exemple, un navigateur web peut être utilisé pour accéder à divers sites web sans avoir besoin d'un client spécifique pour chaque site. Cela facilite l'expérience de l'utilisateur, car il peut utiliser une interface familière pour interagir avec différentes ressources sur le web.

#### design d'url

Les URL doivent être stables et ne pas changer, ce qui implique certaines pratiques à suivre. Il ne faut pas inclure le nom de la technologie dans l'URL, car cela permet de changer de technologie sans casser les URL existantes. Les liens entrants sont un facteur important pour le classement dans les résultats de recherche de Google, donc si les URL sont modifiées, cela peut entraîner une diminution des liens vers le site. Il est préférable de ne pas inclure d'extension dans l'URL, car cela ne permet pas d'envoyer au client la représentation du fichier souhaitée (par exemple, un PNG ou un nouveau format). Les URL servent à identifier la ressource, mais pas à spécifier sa représentation. Le navigateur peut déterminer le type de fichier (par exemple, s'il s'agit d'une image JPEG) à partir des métadonnées associées à l'URL.

La réflexion a priori est importante pour s'assurer que suffisamment d'informations sont disponibles pour retrouver la ressource souhaitée sur le serveur. L'URL est un espace d'adressage abstrait distinct de la représentation physique, ce qui permet une indépendance par rapport aux informations variables. Cela ressemble à une encapsulation des informations.

Dans la conception des URL, certaines pratiques sont à éviter. Il est préférable d'éviter d'inclure le nom du propriétaire, la technologie utilisée, le format ou l'extension du fichier, l'accès (public ou privé), le titre, la catégorie ou la structure de l'organisation dans l'URL. Il est préférable de rediriger vers un lien canonique pour éviter de casser les URL existantes. Les changements de statut peuvent être gérés en utilisant des redirections appropriées. L'URL doit être courte, facile à retenir, à écrire, à décrire et à dicter, ce qui a un aspect marketing important. Idéalement, elle devrait être facilement manipulable à la main, bien que cela ne soit pas toujours nécessaire. Si l'URL est devinable, cela peut constituer une faille de sécurité potentielle. Lorsque des liens sont partagés avec les clients, il est important de leur fournir des liens à suivre ou à découvrir.

### DNS

Le système de noms de domaine (DNS) joue un rôle important dans la résolution des noms d'hôtes en adresses IP. Les URL sont déréférençables, ce qui signifie qu'elles permettent de se connecter au serveur sur le réseau. L'identification des machines sur le réseau se fait généralement par adresse IP, ce qui peut être difficile à retenir et dépendant de l'architecture réseau et du fournisseur d'accès. Si l'adresse IP change, cela peut entraîner une cassure de l'URL et poser des problèmes de répartition de charge.

Le DNS agit comme un niveau d'indirection en attribuant un nom à une machine et en effectuant la résolution entre le nom d'hôte et l'adresse IP pour établir la connexion. Cela rend les noms de domaine plus faciles à retenir que les adresses IP. De plus, le DNS est indépendant du réseau, ce qui signifie que même en changeant d'opérateur, les liens ne sont pas cassés car on peut associer une nouvelle adresse IP à un nom de domaine existant. Le système DNS est hiérarchique, avec des serveurs racines pour les domaines de premier niveau, puis une délégation aux serveurs responsables des domaines spécifiques. Lorsque nous achetons un nom de domaine, nous avons la possibilité de construire différentes structures possibles. De plus, le DNS est cachable, ce qui permet d'améliorer les performances en évitant des requêtes répétitives pour la même résolution de nom.

### HTTP

L'HyperText Transfer Protocol (HTTP) est un protocole utilisé pour manipuler les représentations des ressources sur le Web. Le client envoie une requête pour obtenir une représentation de la ressource, puis le serveur traite la requête et renvoie la représentation de la ressource demandée. HTTP/2 est une version du protocole qui utilise un format binaire pour des performances améliorées, tout en maintenant la même sémantique.

Les messages HTTP sont composés de différentes parties. La "start line" contient la version et le type de message. Les en-têtes suivent, avec des paires clé-valeur, puis une ligne vide sépare les en-têtes du corps du message.

La "start line" comprend le verbe, l'identifiant et la version. Par exemple, "GET/foo HTTP/1.1".

Différents verbes HTTP sont utilisés pour manipuler les ressources. Par exemple, "POST" est utilisé pour créer une ressource, tel qu'un commentaire dans un forum. "GET" (et "HEAD") est utilisé pour lire une ressource, tandis que "PUT" et "PATCH" sont utilisés pour mettre à jour une ressource, avec des différences entre la mise à jour absolue ("PUT") et la mise à jour différencielle/incrementale ("PATCH"). "DELETE" est utilisé pour supprimer une ressource.

Les propriétés importantes de HTTP comprennent l'indempotence (exécution multiple de la même requête donnant le même résultat) et l'absence d'effets de bord (modifications de ressources ou non). Ces propriétés sont essentielles pour la tolérance aux pannes et le bon fonctionnement du cache.

Les codes de statut HTTP fournissent des informations sur le statut de la requête, avec différentes catégories pour l'évolution du protocole. Par exemple, les codes commençant par "1xx" sont des informations générales sur le protocole, tandis que les codes commençant par "2xx" indiquent une réussite de la requête.

HTTP est conçu pour être extensible et permettre une évolution du client. Il facilite la création des navigateurs en vérifiant les codes de statut et offre une meilleure évolutivité

**Propietes Verbes :**
| Verbe HTTP | Indépendance | Sans Effets de Bord |
| ---------- | ----------- | ------------------ |
| GET        | Oui         | Oui                |
| HEAD       | Oui         | Oui                |
| PUT        | Oui         | Non                |
| DELETE     | Oui         | Non                |
| POST       | Non         | Non                |
| PATCH      | Non         | Non                |

**Codes status :**
| Code de Statut | Signification                                    |
| ------------- | ------------------------------------------------ |
| 1xx           | Informations générales sur le protocole          |
| 2xx           | Réussite de la requête                           |
| 3xx           | Redirection, ressource disponible ailleurs       |
| 4xx           | Erreur du client                                 |
| 5xx           | Erreur du serveur                                |

### Cote Client

Dans le développement d'une application web, il est courant de séparer l'application en trois grandes couches : le stockage des données sur le serveur, le traitement des données et la présentation des données pour l'interaction avec le client. Ces trois composants sont maintenus distincts, en utilisant des principes tels que l'encapsulation et l'extensibilité indépendante. Selon les besoins, le traitement des données peut être effectué entièrement sur le serveur (client léger) ou entièrement dans le client (client lourd). Il est également possible d'opter pour une approche mixte, où le client et le serveur partagent le traitement des données. Les avantages du web client plus léger sont nombreux : le protocole HTTP offre une tolérance aux pannes, des performances élevées et une sécurité renforcée grâce à HTTPS. Les navigateurs sont devenus des plateformes génériques, permettant l'exécution de code JavaScript à la demande, sans nécessité de déploiement ni de mises à jour, et offrant une indépendance du terminal. Les technologies web sont libres, bien documentées et faciles à mettre en place, favorisant la composition de services et l'intégration de fonctionnalités telles que les cartes Google Maps. Du côté client, les données sont représentées en HTML, la présentation est gérée par CSS, et le traitement des données est effectué en JavaScript.


### Projets frontend
1.[Coffeebean.com](https://github.com/itszaaak/CoffeeBean.com)

## Backend
//soon
