# Qu’est que HTTP/2 ?

HTTP/2 est une révision majeure du protocole HTTP (Hypertext Transfert Protocol), qui est le protocole de couche applicative utilisé dans le web. 

# Origines

Avant d’en venir à HTTP/2, comprenons d’où vient HTTP et ses différentes versions. Il est nécessaire de voir toutes les versions de HTTP avant HTTP/2 afin de comprendre l’évolution de ce protocole. HTTP a été créé en 1990, en même temps que le langage HTML et que les adresses web, ce fut le début du world wide web (www).

Cette première version de HTTP, HTTP/0.9, proposait uniquement de faire des requêtes GET et ne prenait en charge que des fichiers HTML.

Il est ensuite suivi de HTTP/1 qui fut décrite en 1996 par la RFC 1945, qui apportait plusieurs innovations: 
Introduction des en-têtes HTTP, ce qui permettait de préciser le type de méthodes (GET, POST, …) ainsi que le type de contenu (HTML, …).
Il est donc possible de faire d’autre type de requête, comme des requêtes POST, HEAD, … 
HTTP/1 permet, en plus de l’HTML, de prendre en charge des contenus comme des scripts (fichier js, …), …  

Puis vient HTTP/1.1 (1997), qui fut la première version standardisée de HTTP. Elle a été décrite en 1997 par la RFC 2068 puis en 1999 par la RFC 2616. Voici quelques innovations apportés par cette version:
Il est dorénavant possible d’avoir plusieurs requêtes par connexion TCP (ce qui n’était pas le cas auparavant).
Possibilité d’envoyer plusieurs requêtes avant de recevoir une réponse, contrôle de cache.
 …

En 2012 commence le développement  de HTTP/2.

# Création  de HTTP/2

Google a développé un protocole de remplacement à HTTP/1.1 nommé SPDY (speedy) qui avait pour objectif d’augmenter la vitesse par rapport à celui-ci. Celui-ci proposait d’envoyer des requêtes et réponses de manières asynchrones sur la même connexion TCP. En 2012, le projet initial de HTTP/2 est développé et se base directement sur SPDY, car on cherchait également à réduire la latence avec cette version de HTTP.  En 2015, l’IESG (Internet Engineering Steering Group) qui est chargé des standards d’internet approuve la norme HTTP/2. Par la suite, le navigateur Google Chrome annonce l'abandon progressif de SPDY au profit d’HTTP/2.

# Objectif


Le principale objectif de HTTP/2 est de réduire la latence. En effet, les pages web d’aujourd’hui ont grandement évolué par rapport à celles qu’on trouvait au début de HTTP/1.1, celles-ci devant générer des centaines de requêtes. Hors, HTTP/1.1 ne supporte qu’une requête par connexion.Pour corriger ce problème, HTTP/2 autorise lui qu’une connexion par site mais il permet de transmettre plusieurs requêtes par messages (pipeline). 

# Spécification:

En mai 2015, la spécification HTTP/2 fut publiée via la RFC 7540 (les rfcs sont les spécifications techniques d’internet). Celle-ci précisait que …


# Changement par rapport à HTTP/1.1

Une connexion TCP multiplexé: Comme précisé au dessus, HTTP/2 ne permet qu’une connexion TCP car celle-ci prend beaucoup de temps à s’établir, mais permet de faire une requête sur cette même connexion.
Compression d’en-tête HTTP: Contrairement à HTTP/1.1, HTTP/2 compresse les en-têtes, grâce à un algorithme nommé HPACK. De plus, il ne place un en-tête que s' il y a un changement d’état par rapport à la requête précédente, réduisant ainsi la répétition.
Serveur Push: Au lieu de lire la page HTML et de déterminer les ressources nécessaires à partir de celle-ci (exemple: page de style css), le serveur se charge de les envoyés directement, évitant ainsi d'attendre que le serveur lise la page HTML

![image]([https://user-images.githubusercontent.com/71312671/163960230-f5a4070d-5254-40a6-9b6f-455aa8fa6922.png](https://i.goopics.net/ujhh9w.png))

source: https://www.infoq.com/fr/articles/http2-les-details/

Protocole binaire: les commandes sont transmises dans un format binaire, (zéro et un). Il existe deux types de messages: données et en-têtes. Ceci permet une meilleure sécurité, compression et facilite le multiplexage.


# Avantages de HTTP/2

Performance: le multiplexage permet de transmettre plus de données en même temps, ce qui va considérablement augmenter la vitesse. En effet, il n’est plus nécessaire d’établir une connexion (connexions prenant beaucoup de temps à s’établir) à chaque fois qu’une requête est envoyée. De plus, les requêtes prioritaires ne sont plus bloquées par des requêtes d’importance mineures.

![image]([[https://user-images.githubusercontent.com/71312671/163960230-f5a4070d-5254-40a6-9b6f-455aa8fa6922.png](https://i.goopics.net/ujhh9w.png](https://i.goopics.net/jpngdt.png))


source: https://www.disko.fr/wp-content/uploads/2016/07/Image5.png

Performances du web mobiles: le multiplexage et la compression d’en-tête permet de diminuer la latence sur les réseaux mobiles.
Diminution des coûts: l’augmentation du débit obtenue avec HTTP/2 permettra aux services de télécommunication de réduire leur dépense, réduisant ainsi les tarifs proposés par les fournisseurs.
Sécurité: L'algorithme HPACK (pris en charge par HTTP/2) permet de contrer les menaces de sécurité. En effet, il permet d'éviter les attaques CRIME, qui cherchent à divulguer les cookies secrets.

# Inconvénients de HTTP/2:

Implémentation complexe: en effet, les étapes de multiplexages et de démultiplexeurs sont exigeantes pour le code client et le code serveurs.
Étant donnée l’utilisation commune de serveur reverse-proxy (serveur frontal), et celui-ci communiquant avec le serveur applicatif en HTTP/2. Il faut donc que HTTP/2 soit mis en place de bout en bout et donc que les protocoles s’y prêtent.

# Place de HTTP/2 aujourd’hui:

En 2022, 47% des sites webs les plus connus utilisent HTTP/2. 97% des navigateurs pouvaient déjà le prendre en charge HTTP/2 fin 2015. 

# Et après ?

HTTP/3 est la version de HTTP qui a suivi HTTP/2, qui ne fonctionne plus sous TCP mais sur UDP. Il est basé sur le protocole QUIC de google, qui fonctionne également sous UDP et utilise le multiplexage. Cette version a été publiée dans la RFC 9114 en juin 2022. HTTP/3 est pris en charge par 75% des navigateurs, 25% des sites webs l’utilisent.

# Conclusion

Le web ne cesse d’évoluer ces dernières années, à mesure que les utilisateurs et les sites se font de plus en plus nombreux. Le protocole applicatif HTTP se doit donc d’évoluer pour répondre à l'expansion du web. HTTP/2 est une grande évolution de ce protocole qui permettra aux utilisateurs d’internet d’avoir une meilleure expérience avec un web plus rapide, moins coûteux et sécurisé. 






# Sources:

https://en.wikipedia.org/wiki/HTTP/2

https://developer.mozilla.org/fr/docs/Web/HTTP/Basics_of_HTTP/Evolution_of_HTTP

https://fr.wikipedia.org/wiki/Internet_Engineering_Steering_Group

https://web.dev/performance-http2/

https://stileex.xyz/pourquoi-internet-rapide-http2/

https://boowiki.info/art/hypertext-transfer-protocol/http-2.html#Obiettivi

https://blog.dareboost.com/fr/2016/11/http2-changements-bonnes-pratiques-http1-front-end/

https://kinsta.com/fr/apprendre/http2/#main_benefits_of_http2

https://fr.wikipedia.org/wiki/Hypertext_Transfer_Protocol

https://cheapsslsecurity.com/p/http2-vs-http1/

https://www.disko.fr/reflexions/technique/quest-ce-que-le-http2/#:~:text=Les%20principaux%20avantages%20du%20HTTP2,et%20les%20cookies%20sont%20similaires

https://blog.cloudflare.com/hpack-the-silent-killer-feature-of-http-2/

https://zestedesavoir.com/billets/3726/le-probleme-de-http-2/

https://w3techs.com/technologies/details/ce-http3

