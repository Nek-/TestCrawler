Stratégie de déploiement
========================

Dev
---

### Le projet
* Crawler du site [Notcambule](http://notcambule.fr)
* Calcul de décimales de π

### Intégration continue
Ecriture de [tests](https://github.com/Nek-/TestCrawler/tree/master/spec/AwesomeCrawler) 

Mise en place des services suivants :

* **Travis** ([![Build Status](https://travis-ci.org/Nek-/TestCrawler.svg?branch=master)](https://travis-ci.org/Nek-/TestCrawler)) pour l'exécution de notre suite de test
* **Scrutinizer** ([![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/Nek-/TestCrawler/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/Nek-/TestCrawler/?branch=master)) pour la code quality

Le déploiment se fait après le merge de la pull request. Ce dernier doit être fait uniquement si la PR affiche que tous les status sont « green », c'est à dire que l'intégration continue a fonctionné.

OPS
---

### Provisioning

* **[User data](https://github.com/Nek-/TestCrawler/blob/master/doc/script.sh)** qui prépare les instances 
* **Amazon S3** que l'on utilise notamment pour récuperer notre fichier de conf apache

### Déploiement du code

* Fabric (couplé à [fabric-aws](https://github.com/EverythingMe/fabric-aws))
* Déploiement automatique à l'aide de d'un [outil de déploiement](https://github.com/valanz/deploy) que nous avons développé pour l'occasion, et accessible sur: ec2-52-23-196-233.compute-1.amazonaws.com


### Montée en charge
* Load balancer mis en place.
* Auto scaling mis en place.

URLs existantes sur le projet:

* http://balance-toi-881187321.us-east-1.elb.amazonaws.com
* http://balance-toi-881187321.us-east-1.elb.amazonaws.com/pi.php

Process en prod
---------------

1. Créer une branche
2. Écrire le code
3. Pousser sur github
4. Créer une pull-request
5. Attendre la validation de la PR (affichée sur le bouton merge)
6. Merger la PR

Le déploiement s'effectue automatiquement.
