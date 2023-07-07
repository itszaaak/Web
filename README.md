# Sommaire  
1. [Frontend](#Frontend)
   - [Theorie](#table-des-matières-frontend)  
   - [Projets](#Projets-frontend)
  
2. [Backend](#Backend)  
   - [Theorie](#table-des-matières-backend)  
   - [Projets](#Projets-backend)

# Frontend
### Table des matières frontend
1. [Introduction](#introduction)
2. [Structures Web](#structures-web)
    2.1 [Client](#client)
    2.2 [Server](#server)
    2.3 [Passerelle](#passerelle)
    2.4 [Cache](#cache)
    2.5 [Proxy](#proxy)
    2.6 [Reverse Proxy](#reverse-proxy)
    2.7 [CDN](#cdn)
3. [Hypermedia](#hypermedia)
4. [Adressage](#adressage)
    4.1 [L'url](#lurl)
    4.2 [DNS](#dns)
5. [HTTP](#http)
6. [Côté client](#côté-client)




## Introduction

WEB et NET sont deux choses totalement différentes. Le "net" fait référence au réseau physique de câbles qui nous relie, tandis que le "Web" est plutôt un maillage de ressources interconnectées par l'hypermedia. L'objectif du Web est de fournir un système d'information global à grande échelle, décentralisé, tolérant aux pannes, extensible et évolutif. Cet objectif permet notamment la mise en place d'un client générique grâce à l'utilisation d'une représentation homogène (HTML) et l'utilisation d'un protocole uniforme (HTTP). Chaque ressource dans le Web possède une adresse unique et uniforme.

En revanche, le "net" est organisé en cinq couches distinctes indépendantes les unes des autres pour garantir une meilleure isolation :

1. Couche physique : RTC, ADSL, 100BASE-TX
2. Couche liaison : Ethernet, ATM, Wi-Fi, IPoAC (troll)
3. Couche réseau : IP, ICMP, BGP, X25
4. Couche transport : TCP, UDP
5. Couche application : HTTP, DNS, XMPP (chat), SMTP

Pour ce qui est du Web, les protocoles utilisés sont : HTTP, DNS, TCP, IP.

## Structures Web
### Client
Le client du serveur joue un rôle essentiel dans l'envoi des requêtes au serveur pour manipuler les ressources via leur représentation spécifique. Il maintient l'état de l'application, car chaque utilisateur a un état différent, et cela se reflète lorsqu'ils interagissent avec l'application en se déplaçant à travers les graphes de ressources. Le serveur ne stocke pas l'état spécifique à chaque utilisateur, mais fournit plutôt les ressources et les fonctionnalités nécessaires pour que le client puisse gérer son propre état. Les clients du serveur comprennent les navigateurs web, qui permettent d'accéder aux ressources du Web et d'envoyer des requêtes, ainsi que les robots (crawler/scrapers) qui parcourent automatiquement les sites web pour extraire des données. Les agrégateurs sont également des clients du serveur, collectant des informations provenant de différentes sources via des flux RSS structurés (tels que XML) et effectuant des analyses sur ces données.

### Server
Le client du serveur joue un rôle crucial dans le processus de communication. Il envoie des requêtes au serveur pour manipuler les ressources via leur représentation spécifique, tout en maintenant l'état de l'application du côté du client. Le client peut créer, détruire et gérer les ressources, en générant des représentations adéquates et en utilisant l'adressage URL pour accéder à l'information. Le serveur peut être statique ou dynamique, fournissant des fichiers HTML, CSS et JavaScript en lecture simple ou générant dynamiquement des représentations à partir d'un programme. Des exemples de serveurs incluent Apache, Nginx, mod_php, Node.js et Tomcat.

### Passerelle
Les passerelles étaient utilisées dans le passé pour la conversion de protocoles, par exemple, pour transférer des fichiers via FTP afin de les afficher sur le Web. Cependant, ces passerelles sont devenues obsolètes avec l'évolution des technologies. Elles différaient des serveurs d'applications car elles étaient très générales et ne comportaient pas de logique métier spécifique. Un exemple de passerelle était "mod_proxy_FTP".

### Cache
Le cache joue un rôle essentiel dans la mémorisation des requêtes. Lorsqu'il reçoit une requête identique à une précédente, il peut envoyer directement la réponse sans passer par le serveur, ce qui est particulièrement utile dans des situations telles que le retour en arrière dans une page web. Le cache peut être de deux types : local, intégré au navigateur, ou intermédiaire, placé entre le client et le serveur. Dans ce dernier cas, le client communique directement avec le cache, qui peut répondre si la réponse est déjà disponible. La mise en place d'un cache permet d'améliorer les performances en évitant les requêtes répétées au serveur, tout en rendant le système plus tolérant aux pannes du serveur. Un exemple de cache bien connu est "Varnish". En ce qui concerne les proxies, ils peuvent être configurés de deux manières : explicite, où le client les configure directement, ou transparente, où le client ne les voit pas car leur fonctionnement est géré automatiquement par le réseau.

### Proxy
Les proxies côté client jouent un rôle essentiel dans divers aspects. Ils permettent le partage de connexion d'accès entre différentes machines au sein d'un même réseau, comme dans le cas des réseaux universitaires. De plus, les proxies peuvent être utilisés pour filtrer l'accès à des sites spécifiques, car ils examinent les requêtes et peuvent bloquer certaines d'entre elles. Ils offrent également des fonctionnalités d'optimisation des applications pour les appareils mobiles, telles que la compression des données. Les proxies peuvent également masquer la source de la connexion en attribuant une adresse IP au proxy, ce qui donne l'impression au serveur que la communication se fait avec le proxy plutôt qu'avec le client réel. Des exemples courants de proxies incluent Squid et Polipo.

### Reverse Proxy
Le reverse proxy, également connu sous le nom de proxy côté serveur, offre plusieurs fonctionnalités essentielles. Tout d'abord, il permet la répartition de la surcharge sur plusieurs machines serveurs, garantissant ainsi des performances optimales tout en maintenant une seule URL pour les clients. De plus, le reverse proxy peut servir de portail d'intégration, permettant d'attribuer des rôles spécifiques à différentes machines pour un traitement efficace des requêtes. Par exemple, une machine peut être dédiée à l'affichage du contenu HTML tandis qu'une autre se charge des images. En outre, il agit comme un relais ou une passerelle vers d'autres serveurs, permettant de rediriger le trafic vers des serveurs spécifiques en fonction des besoins. Des exemples populaires de reverse proxies incluent Haproxy et Apache
### CDN
Le Content Delivery Network (CDN) est un réseau de serveurs en miroir synchronisés qui sont répartis géographiquement, généralement un par continent. Les serveurs CDN sont spécialement conçus pour servir du contenu statique, tels que des images ou du texte HTML, afin de soulager la charge des serveurs d'application. Les CDN peuvent être publics, comme Amazon AWS et Azure, ou privés, comme ceux utilisés par Facebook. Le rôle des CDN est d'accepter davantage de données et d'utilisateurs afin de réduire la charge sur les serveurs des applications principales, améliorant ainsi les performances et la disponibilité du contenu.

## Hypermedia

Une ressource forme un bloc d'information unitaire. Ces blocs sont structurés par des liens, ce qui crée un système de graphes non linéaires navigables par découverte, c'est-à-dire qu'il n'est pas nécessaire de connaître leur existence au préalable. Ce système de graphes s'avère utile car il est très évolutif et permet la transclusion ou l'inclusion d'autres blocs dans un même bloc.

## Adressage 
Tout bloc d'information est identifieé par une adresse unique, un peu comme l'adresse de chez vous. Ce adressage s'appelle uri ou uniform ressource identifier. Dans l'uri on retrouve le urn ou uniform ressource name et le url ou uniform ressource loacaor, l'url est plus interessant pour le web

### L'url
L'identifiant de ressource est unique dans l'espace, et cet espace est défini par le système de noms de domaine (DNS). De plus, cet identifiant peut être unique dans le temps, avec le serveur qui gère cette notion. L'identifiant est dereferençable, ce qui signifie qu'il contient suffisamment d'informations pour se connecter au serveur et récupérer le fichier associé. Il existe une structure sous-jacente qui permet cette opération. L'identifiant de ressource est défini par le serveur lui-même, sans nécessiter de gestion centrale. En d'autres termes, chaque individu peut gérer ses propres identifiants de ressource sans avoir à demander la permission à une autorité centrale. Cependant, l'identifiant peut être opaque pour le client, ce qui signifie qu'il n'a pas nécessairement une compréhension sémantique de ce qui se passe, contrairement au serveur qui peut interpréter l'identifiant de manière significative.

La structure d'une URL suit une représentation uniforme par protocole. Elle se compose de plusieurs parties distinctes. Tout d'abord, le "scheme" spécifie le protocole utilisé pour communiquer avec le serveur, déterminant ainsi la manière dont le client va interagir avec le serveur. Ensuite, le "hostname" (et le port, facultatif) indique où se trouve le serveur, soit par une adresse IP soit par un nom de domaine, garantissant l'unicité de l'adresse. Le "path" identifie la ressource localement sur le serveur, mais cette information est opaque pour le client. Le "path" peut être suivi d'une "query string" après le point d'interrogation, qui constitue le seul moyen pour l'utilisateur de construire les URL en ajoutant des paramètres à la demande. Le "fragment", qui apparaît après le dièse (#), représente une sous-ressource ou une partie spécifique du document, tel qu'un lien interne sur la même page ou une page spécifique dans un document PDF. Le client attribue une signification au fragment, qui dépend du type de représentation utilisée.

Le client n'a pas besoin de comprendre autre chose que la structure de l'URL lorsqu'il interagit avec le serveur. Cela permet un découplage entre le client et le serveur, ce qui signifie qu'il est possible d'utiliser un client unique pour accéder à différents serveurs. Par exemple, un navigateur web peut être utilisé pour accéder à divers sites web sans avoir besoin d'un client spécifique pour chaque site. Cela facilite l'expérience de l'utilisateur, car il peut utiliser une interface familière pour interagir avec différentes ressources sur le web.

### design d'url

Les URL doivent être stables et ne pas changer, ce qui implique certaines pratiques à suivre. Il ne faut pas inclure le nom de la technologie dans l'URL, car cela permet de changer de technologie sans casser les URL existantes. Les liens entrants sont un facteur important pour le classement dans les résultats de recherche de Google, donc si les URL sont modifiées, cela peut entraîner une diminution des liens vers le site. Il est préférable de ne pas inclure d'extension dans l'URL, car cela ne permet pas d'envoyer au client la représentation du fichier souhaitée (par exemple, un PNG ou un nouveau format). Les URL servent à identifier la ressource, mais pas à spécifier sa représentation. Le navigateur peut déterminer le type de fichier (par exemple, s'il s'agit d'une image JPEG) à partir des métadonnées associées à l'URL.

La réflexion a priori est importante pour s'assurer que suffisamment d'informations sont disponibles pour retrouver la ressource souhaitée sur le serveur. L'URL est un espace d'adressage abstrait distinct de la représentation physique, ce qui permet une indépendance par rapport aux informations variables. Cela ressemble à une encapsulation des informations.

Dans la conception des URL, certaines pratiques sont à éviter. Il est préférable d'éviter d'inclure le nom du propriétaire, la technologie utilisée, le format ou l'extension du fichier, l'accès (public ou privé), le titre, la catégorie ou la structure de l'organisation dans l'URL. Il est préférable de rediriger vers un lien canonique pour éviter de casser les URL existantes. Les changements de statut peuvent être gérés en utilisant des redirections appropriées. L'URL doit être courte, facile à retenir, à écrire, à décrire et à dicter, ce qui a un aspect marketing important. Idéalement, elle devrait être facilement manipulable à la main, bien que cela ne soit pas toujours nécessaire. Si l'URL est devinable, cela peut constituer une faille de sécurité potentielle. Lorsque des liens sont partagés avec les clients, il est important de leur fournir des liens à suivre ou à découvrir.

## DNS

Le système de noms de domaine (DNS) joue un rôle important dans la résolution des noms d'hôtes en adresses IP. Les URL sont déréférençables, ce qui signifie qu'elles permettent de se connecter au serveur sur le réseau. L'identification des machines sur le réseau se fait généralement par adresse IP, ce qui peut être difficile à retenir et dépendant de l'architecture réseau et du fournisseur d'accès. Si l'adresse IP change, cela peut entraîner une cassure de l'URL et poser des problèmes de répartition de charge.

Le DNS agit comme un niveau d'indirection en attribuant un nom à une machine et en effectuant la résolution entre le nom d'hôte et l'adresse IP pour établir la connexion. Cela rend les noms de domaine plus faciles à retenir que les adresses IP. De plus, le DNS est indépendant du réseau, ce qui signifie que même en changeant d'opérateur, les liens ne sont pas cassés car on peut associer une nouvelle adresse IP à un nom de domaine existant. Le système DNS est hiérarchique, avec des serveurs racines pour les domaines de premier niveau, puis une délégation aux serveurs responsables des domaines spécifiques. Lorsque nous achetons un nom de domaine, nous avons la possibilité de construire différentes structures possibles. De plus, le DNS est cachable, ce qui permet d'améliorer les performances en évitant des requêtes répétitives pour la même résolution de nom.

## HTTP

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

## Côté client

Dans le développement d'une application web, il est courant de séparer l'application en trois grandes couches : le stockage des données sur le serveur, le traitement des données et la présentation des données pour l'interaction avec le client. Ces trois composants sont maintenus distincts, en utilisant des principes tels que l'encapsulation et l'extensibilité indépendante. Selon les besoins, le traitement des données peut être effectué entièrement sur le serveur (client léger) ou entièrement dans le client (client lourd). Il est également possible d'opter pour une approche mixte, où le client et le serveur partagent le traitement des données. Les avantages du web client plus léger sont nombreux : le protocole HTTP offre une tolérance aux pannes, des performances élevées et une sécurité renforcée grâce à HTTPS. Les navigateurs sont devenus des plateformes génériques, permettant l'exécution de code JavaScript à la demande, sans nécessité de déploiement ni de mises à jour, et offrant une indépendance du terminal. Les technologies web sont libres, bien documentées et faciles à mettre en place, favorisant la composition de services et l'intégration de fonctionnalités telles que les cartes Google Maps. Du côté client, les données sont représentées en HTML, la présentation est gérée par CSS, et le traitement des données est effectué en JavaScript.


## Projets frontend
1.[Coffeebean.com](https://github.com/itszaaak/CoffeeBean.com)

# Backend
### Table des matières backend

1. [Côté server](#côté-server)  
   1.1 [CGI](#cgi)  
   1.2 [Langage embarqué](#langage-embarqué)  
   1.3 [FastCGI](#fastcgi)  
   1.4 [Server d'application et application autonome](#server-dapplication-et-application-autonome)  
   1.5 [Cookies et sessions](#cookies-et-sessions)  
2. [MVC](#mvc)  
   2.1 [Contrôleur](#contrôleur)  
   2.2 [Modèle](#modèle)  
   2.3 [Vue](#vue)  
   2.4 [Renderer et MVCR](#renderer-et-mvcr)  
3.[Internationalisation](#Internationalisation)  
4.[Gestion d'accès aux ressources](#gestion-daccès-aux-ressources)  
   4.1 [TLS](#tls-transport-layer-security)  
   4.2 [Certificat TLS](#certificat-tls)  
   4.3 [Sécurité des mots de passe](#sécurité-des-mots-de-passe)  
5. [Projets backend](#projets-backend)  



## Côté server

La génération des représentations des ressources va au-delà de l'affichage de fichiers HTML statiques. Elle permet de créer dynamiquement des représentations adaptées aux besoins des clients. Cela inclut l'utilisation de code côté serveur pour effectuer des tâches telles que l'interrogation de services, les calculs, la manipulation des ressources, etc. Cette approche offre une plus grande flexibilité et permet de créer des applications web personnalisées. L'architecture à n-tiers est souvent utilisée, avec des couches distinctes pour traiter les requêtes et générer les réponses, ce qui facilite la maintenance et l'évolutivité du système.
### CGI
Le CGI (Common Gateway Interface) est un ancien outil permettant la communication entre le serveur et un programme autonome pour générer des réponses côté serveur. Il fonctionne en exécutant un programme`(sous processus)` spécifié par la configuration du serveur en fonction de la requête reçue. Le programme CGI analyse les paramètres de la requête, génère les en-têtes et le corps de la réponse, puis communique avec le serveur via des variables d'environnement. La réponse est renvoyée au client par le serveur. Bien que le CGI soit facile à tester et à déployer, il présente des problèmes de performances avec un grand nombre de requêtes concourantes. De plus, il ne permet pas de partager l'état entre les requêtes. En conséquence, le CGI a été remplacé par des technologies plus performantes.

### language  embarqué
Le langage embarqué a été développé pour améliorer les performances des CGI. Au lieu de lancer un sous-processus à chaque requête, l'interpréteur est directement intégré au serveur web. Cela permet d'exécuter le programme de manière plus efficace, d'accéder aux variables directement et d'utiliser des bibliothèques spécialisées. Cependant, cela peut entraîner un manque d'isolation, car si l'interpréteur plante, le serveur web peut également être affecté.

### FastCGI
FastCGI est une alternative au CGI qui utilise un démon en permanence pour exécuter les programmes. Le serveur web communique avec le démon via des sockets, ce qui améliore les performances en évitant la création de sous-processus à chaque requête. FastCGI offre des avantages tels que la réutilisation du démon, la répartition de charge et une plus grande indépendance du langage utilisé. Cependant, il nécessite de redémarrer le démon en cas de modification du code.

### Server d'application et application autonome
Le serveur d'application est un conteneur dans lequel on déploie des applications spécifiques à un langage donné. Il facilite l'accès aux paramètres et permet une communication via HTTP. Les applications autonomes, quant à elles, embarquent un serveur web et peuvent être déployées individuellement. Les deux approches ont leurs avantages et inconvénients en termes de performance, isolation et gestion

###  cookies et sessions
Les cookies jouent un rôle important dans le protocole HTTP, qui est sans état. Habituellement, les URL ne dépendent pas des actions précédentes de l'utilisateur, ce qui facilite la navigation sur les pages et les applications. Cependant, dans certains cas, comme avec Facebook, une couche d'état supplémentaire est nécessaire dans l'application, ce qui empêche l'exploitation du cache. Pour maintenir cet état, les informations nécessaires sont stockées par le client et renvoyées à chaque requête. Les cookies sont des entêtes spécifiques du protocole HTTP qui permettent de stocker des informations spécifiques à une application. Contrairement aux en-têtes génériques du protocole, ces informations ne peuvent pas être gérées par un client générique. Les cookies sont envoyés par le serveur sous la forme d'une paire clé-valeur avec des métadonnées. Ils sont stockés par le client et renvoyés à chaque requête. Il est important de noter que les cookies ne sont pas des fichiers, mais des entêtes incluses dans les requêtes. Ils sont utilisés pour des cas tels que les préférences utilisateur, et contiennent des métadonnées pour définir leur validité, tels que le domaine, le chemin et la durée de validité. Les cookies peuvent également être sécurisés en étant transmis uniquement via HTTPS et en interdisant l'accès via des API JavaScript. Ils sont essentiels pour maintenir un état côté client sans avoir à dépendre de l'URL, bien que leur utilisation avec le cache puisse être ambiguë.

Les sessions et les cookies sont des éléments importants pour la gestion de l'état dans les applications web. Les cookies sont des entêtes spécifiques qui permettent de stocker des informations côté client, tandis que les sessions sont des structures de données stockées côté serveur. Les cookies sont utilisés pour envoyer des préférences ou des informations spécifiques de l'application entre le client et le serveur. Ils sont stockés par le client et renvoyés à chaque requête. Les sessions sont maintenues par un cookie unique et permettent de stocker des informations côté serveur, comme un panier d'achat ou des préférences utilisateur. Cependant, l'utilisation des sessions peut poser des problèmes d'équilibrage de charge et de persistance des données. De plus, les cookies tiers provenant d'autres serveurs peuvent poser des problèmes de sécurité et de vie privée. Il est essentiel de prendre en compte ces aspects pour garantir un fonctionnement sécurisé et efficace des applications web.

## MVC
Le modèle MVC est une architecture couramment utilisée pour développer des applications côté serveur. Elle se compose de trois composants : le modèle qui représente les données et les règles métier, la vue qui se charge de la présentation des données, et le contrôleur qui gère les interactions entre le modèle et la vue. Lorsqu'une requête HTTP est reçue, le processus de routage détermine le contrôleur à utiliser. Le contrôleur instancie alors le modèle, extrait les données nécessaires et les envoie à la vue. La vue génère la représentation visuelle des données, puis le contrôleur génère la réponse HTTP complète. Il existe d'autres variantes du modèle MVC, ainsi que des micro-frameworks et des frameworks complets comme Spring ou Spring Boot.

### Contrôleur
Le contrôleur joue un rôle d'orchestration entre le modèle et la vue. Il analyse l'URL et les en-têtes de la requête pour déterminer quel modèle instancier. En fonction du verbe HTTP utilisé, il choisit l'opération à effectuer sur cette instance du modèle. Le contrôleur extrait les informations pertinentes du modèle et, en fonction des en-têtes de la requête, sélectionne la vue appropriée. Il génère la réponse en instanciant la vue et en définissant le code de statut approprié. En général, les vues et les modèles ne génèrent pas directement d'erreurs, mais lèvent des exceptions. Ces exceptions sont capturées par le contrôleur, qui renvoie un code de statut correspondant. Selon les frameworks, le contrôleur peut être implémenté de différentes manières : en utilisant des appels de fonctions, des annotations, des fichiers de configuration XML, ou en suivant une convention spécifique. Certains frameworks, comme Spark, offrent une grande flexibilité mais nécessitent également un travail manuel plus important dans la gestion du contrôleur.

### modèle
Le modèle contient les données et la logique métier, et il encapsule l'accès aux données via le DAO (Data Access Object) pour interagir avec la couche de persistance. L'idée est que le modèle n'a pas de dépendance directe sur le contrôleur ou la vue, il ne s'agit que de la logique métier qui n'a pas conscience de son exposition dans le contexte web. L'impédance de mismatch est une différence conceptuelle entre le modèle objet et le modèle relationnel des bases de données, ce qui peut entraîner des frictions lorsqu'on souhaite mapper des objets dans une base de données relationnelle. Pour pallier cela, on utilise le DAO, qui encapsule l'accès aux données et gère les requêtes vers la base de données. On peut manipuler explicitement le DAO ou l'encapsuler dans le modèle par délégation ou héritage. Les DTO (Data Transfer Objects) sont des structures de données utilisées pour transférer les données entre le DAO et la couche métier. Pour éviter les failles de sécurité comme les injections SQL, il est recommandé d'utiliser des Prepared Statements ou des ORM (Object-Relational Mapping). Les ORM sont des frameworks ou systèmes qui facilitent la création des requêtes SQL en se basant sur une description de classe, et ils permettent de réduire les frictions liées à l'impédance de mismatch. Cependant, l'utilisation d'ORM peut être plus complexe pour des cas plus avancés, nécessitant parfois l'écriture manuelle de requêtes.

### Vue
La vue est une fonction ou une méthode d'une classe qui prend en paramètre des données brutes indépendantes du métier et renvoie une représentation sous forme d'octets. Elle peut également utiliser des view models, qui sont des structures de données spécifiques pour extraire les données nécessaires. On utilise souvent des systèmes de templates pour la génération de la vue. Un template est un système qui permet de générer du texte à partir d'un patron ou modèle. Il existe différents types de systèmes de templates, tels que les templates illimités (comme PHP) qui utilisent le langage hôte complet, et les systèmes de templates spécifiques qui sont indépendants du langage hôte mais adaptés à la génération du document. Les templates peuvent être utilisés en mode pull, où la vue récupère les données directement du modèle, ou en mode push, où le contrôleur ou la vue injecte les données dans le template. Les systèmes de templates utilisent souvent des flux de conversion tels que les pipelines, les callbacks ou les reverse callbacks pour gérer le processus de génération. Les callbacks sont couramment utilisés lorsque le langage hôte fait du pull, et les templates sont souvent des fichiers du langage hôte (comme les fichiers PHP). Les modèles en pipeline utilisent un patron externe compilé et interprété à la demande, et ils sont souvent utilisés en mode push. Ils permettent de séparer la logique métier de la présentation et offrent la possibilité de changer de patron de template sans difficulté. Cela facilite la collaboration entre développeurs et designers, car chaque partie peut se concentrer sur son domaine spécifique.

### Renderer et MVCR
Le rendu (render) est une étape importante dans le processus de génération de la vue. Les templates ne prennent en charge que les chaînes de caractères, mais nous avons souvent besoin de manipuler des objets métier complexes. Nous ne voulons pas passer directement ces objets à la vue, donc le contrôleur construit un modèle de vue à partir du modèle métier en utilisant des structures simples telles que des listes ou des dictionnaires. Les valeurs que nous voulons afficher dans la vue sont généralement des valeurs primitives, comme des chaînes de caractères ou des types primitifs. Pour convertir ces valeurs primitives en chaînes de caractères pour la vue, nous utilisons le concept de rendu (render). Le rendu est effectué soit dans le contrôleur lors de la création du modèle de vue, soit implicitement en appelant la méthode toString sur les objets. Le rendu des types primitifs et le formatage peuvent être gérés par le contrôleur ou par le moteur de template. Cela facilite également la prise en charge de l'internationalisation (i18n) et permet une adaptation facile de l'application à différentes langues ou régions.

## Internationalisation

L'internationalisation (i18n) est essentielle pour rendre une application adaptée à différentes langues et cultures. Étant donné que Internet est utilisé à l'échelle mondiale, il est nécessaire de prendre en compte les différentes langues et symboles utilisés. Cela implique d'avoir différentes représentations et rendus pour différentes langues, ce qui nécessite l'utilisation de templates spécifiques à chaque langue. Le contrôleur joue un rôle crucial dans le choix des templates appropriés en fonction de la langue demandée.

Pour rendre une application compatible avec plusieurs langues, il est important de prendre en compte les locales POSIX. Cela garantit que l'application est compatible avec différentes langues en prenant en compte les préférences culturelles telles que l'ordre d'écriture, l'ordre alphabétique, le formatage des nombres, le formatage des dates, le formatage des devises et les règles typographiques.

L'internationalisation (i18n) vise à rendre une application adaptable et prenant en compte les paramètres de langue dans son comportement. Cela implique de rendre le code paramétrable et de prendre en compte les locales, qui doivent être indépendantes du système initial. La localisation (l10n) consiste à traduire les chaînes de caractères et à adapter le style en fonction des locales. Il est important de réaliser l'internationalisation avant de procéder à la localisation.

En ce qui concerne l'encodage des caractères, il existe différents jeux de caractères qui correspondent aux correspondances entre caractères et codes numériques. L'encodage représente ces codes numériques sous forme binaire. Lorsque des textes sont transférés dans le web ou stockés dans des bases de données, il est important de savoir quel encodage a été utilisé.

L'Unicode est un jeu de caractères qui représente tous les symboles de toutes les langues. Il existe différents encodages pour l'Unicode, tels que UTF-8, UTF-16 et UTF-32, qui utilisent des octets pour représenter les caractères. Il peut y avoir des problèmes liés à l'ordre des octets, notamment avec l'endianness (ordre des octets) lors de la lecture des encodages multi-octets.

Il est important de spécifier l'encodage des caractères dans les métadonnées ou les négociations de contenu lors du transfert de fichiers ou des requêtes HTTP. De plus, la gestion de la longueur des chaînes de caractères peut être complexe en raison des caractères diacritiques, des emoji et des variantes d'emoji.

## Gestion acces aux ressources
L'identification consiste à associer une identité ou un identifiant à un utilisateur. Cela permet de reconnaître et d'étiqueter une personne qui utilise le service, sans nécessairement être liée à un compte spécifique. Par exemple, pour des systèmes de recommandation basés sur les recherches récentes, un identifiant peut être utilisé sans avoir besoin d'être authentifié.

Les moyens d'identification peuvent inclure la fourniture de l'identifiant via les en-têtes HTTP, l'utilisation de cookies avec un identifiant unique pour suivre l'agent utilisateur, l'utilisation de certificats cryptographiques ou même une identification implicite basée sur le comportement de l'utilisateur.

L'authentification vise à garantir l'identité de l'utilisateur. Elle repose sur le partage d'un secret, tel qu'un mot de passe ou un jeton d'authentification. Dans certains cas, l'authentification peut également se faire par le biais de tiers de confiance, tels que les connexions via un compte Twitter ou Facebook. En général, l'authentification est liée à un compte sur le site.

L'autorisation concerne le contrôle d'accès et définit ce que l'utilisateur est autorisé à faire. Cela se fait généralement à l'aide de listes de contrôle d'accès (ACL) qui spécifient les permissions accordées à chaque identité. Il peut s'agir de triplets en HTTP (méthode-URL-identité), de contrôle d'accès basé sur les rôles (RBAC) utilisant des groupes ou des rôles, d'attributs spécifiques à l'application ou de règles métier. Selon la technologie utilisée, l'autorisation peut être mise en place via HTTP sans nécessiter de code spécifique, ce qui peut être pratique au niveau des serveurs frontal ou des reverse proxies.

### TLS

TLS (Transport Layer Security) est un protocole utilisé pour sécuriser les communications sur un réseau. Il combine le chiffrement asymétrique, les signatures numériques et l'utilisation de certificats pour garantir la confidentialité, l'intégrité et l'authenticité des données transmises. TLS est couramment utilisé pour sécuriser les connexions HTTPS, et il permet aux utilisateurs de vérifier l'authenticité des clés publiques grâce à l'utilisation de certificats délivrés par des Autorités de Certification de confiance.

### TLS CERTIFICATE
Le certificat TLS permet au client de chiffrer le contenu à l'aide de la clé publique du serveur, garantissant ainsi la confidentialité des données transmises. Le certificat, qui contient la clé publique du serveur, est signé par une autorité de certification de confiance. La vérification du certificat entre le serveur et le client est cruciale pour garantir l'authenticité du serveur. Cependant, TLS peut rencontrer des problèmes avec les intermédiaires tels que les reverse proxies ou les caches, et la confiance dans les certificats repose sur la chaîne de validation et les autorités de certification. Les certificats auto-signés peuvent poser des problèmes et les mécanismes de contrôle parental et les CDN peuvent entraîner des problèmes de contenu mixte et de traçabilité.

### petit point securité
Pour garantir la sécurité des mots de passe, ils ne sont jamais stockés en clair dans une base de données. Au lieu de cela, ils sont hachés et salés. Lors de la vérification d'un mot de passe, on ne cherche pas directement s'il est présent dans la base de données, mais plutôt si le mot de passe haché et salé fourni par l'utilisateur, combiné à son propre sel personnel, correspond à un mot de passe haché et salé dans la base de données. Cette méthode renforce la confidentialité des mots de passe et rend plus difficile la récupération des mots de passe d'origine à partir de la base de données.

**NB : **  hachés = fonction d'hachage type sha256, salés = string aleatoire a rajouter au mot de passe avant hachage

## projets backend  
//soon
