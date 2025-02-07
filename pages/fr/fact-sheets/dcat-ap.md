# Fiche d’information : DCAT-AP, le standard pour les métadonnées des Portails Open Data
Le standard DCAT-AP permet la réutilisation des métadonnées des portails open data en Europe. Via ce standard, les principaux portails open data sont interopérables et peuvent de manière tout à fait automatisée échanger leurs métadonnées, les synchroniser, les fédérer. Ce standard permet de décrire les métadonnées des jeux de données publiés sur les portails open data.

## Données et métadonnées

Avant de commencer, il nous semble intéressant de rappeler la différence entre données et métadonnées. Les métadonnées sont des données à propos de données, comme le nom d’un jeu de données, sa date de publication ou encore la licence sous laquelle ces contenus sont publiés.

Sur le portail open data, vous trouverez les métadonnées dans l’onglet « Métadonnées » de chaque jeu de donnée.

![](https://data.public.lu/fr/pages/fact-sheets/data-quality-metadata.png)

## Des métadonnées lisibles par machine

Si l’on veut échanger ces métadonnées non seulement avec des humains mais aussi avec des machines, il est nécessaire d’avoir un langage commun et standardisé pour transmettre ces informations.

C’est ce que l’on fait sur data.public.lu avec une API spécifique qui implémente le standard DCAT-AP.

On peut par exemple interroger le catalogue du portail open data à cette URL :

<https://data.public.lu/catalog.rdf>

Si vous consultez cette URL via votre navigateur, n’hésitez pas à afficher le code source de la page pour afficher son contenu (par exemple via le clic droit sur la page puis « afficher le code source de la page »).

Via ce web service, nous pouvons récupérer toutes les métadonnées de tous les jeux de données présents sur data.public.lu. Les données n’y sont pas présentes, seules les URLs des données y sont référencées.

Vous constatez ici que les métadonnées sont structurées en XML. DCAT-AP est basé sur RDF, qui est un modèle abstrait qui a plusieurs sérialisations, c’est-à-dire plusieurs représentations concrètes dans des langages informatiques spécifiques, une d’entre elles étant en XML. Vous pouvez accéder aux autres sérialisations proposées par le portail open data en changeant l’extension à la fin de l’URL. Vous pouvez par exemple utiliser l’extension .json pour obtenir une sérialisation au format JSON-LD, ou .ttl ou .nt pour les formats textuels Turtle ou N-triples). Pour une liste des formats disponibles, vous pouvez consulter la [documentation de la plateforme udata](https://udata.readthedocs.io/en/stable/rdf/).

Ce web service est paginé, il ne rend par défaut que les 100 premiers datasets. Vous pouvez atteindre les autres pages en utilisant les paramètres page, pour le numéro de la page et page_size pour le nombre de jeux de données par page. Par exemple pour afficher la 2e page, vous pouvez interroger l’URL suivante :

<https://data.public.lu/api/1/site/catalog.rdf?page=2&page_size=100>

De la même manière, il est possible d’obtenir les métadonnées d’un jeu de données particulier ou de tous les jeux de données liés à une organisation particulière.

Pour les métadonnées des datasets d’une organisation, l’URL est de la forme :

[https://data.public.lu/api/1/organizations/{id}/catalog.rdf](https://data.public.lu/api/1/organizations/%7bid%7d/catalog.rdf)

où {id} est l’identifiant d’une organisation, que l’on peut trouver dans l’URL de cette organisation sur le portail.

Par exemple : <https://data.public.lu/api/1/organizations/open-data-letzebuerg/catalog.rdf>

Pour les métadonnées d’un seul dataset, l’URL est de la forme :

[https://data.public.lu/api/1/datasets/{id}/rdf](https://data.public.lu/api/1/datasets/%7bid%7d/rdf)

où {id} est l’identifiant du dataset, que l’on peut retrouver dans son URL sur le portail.

Par exemple : <https://data.public.lu/api/1/datasets/digital-accessibility-monitoring-report-2020-2021/rdf>

## Un vocabulaire spécifique : DCAT-AP

[DCAT-AP](https://semiceu.github.io/DCAT-AP/releases/3.0.0/) (DCAT Application Profile for data portals in Europe) est un standard défini par le [SEMIC](https://interoperable-europe.ec.europa.eu/collection/semic-support-centre) (european SEMantic Interoperability Community) pour les métadonnées des portails open data. Il s’agit d’une extension du standard [DCAT](https://www.w3.org/TR/vocab-dcat-3/) (Data Catalogue Vocabulary) défini par le W3C.

### Les buts

Si chaque portail open data adoptait son propre schéma de données pour l’échange de métadonnées, il serait très compliqué de réaliser ces échanges en pratique. Le standard DCAT-AP a justement été défini dans le but de soutenir l’interopérabilité entre les portails open data en Europe.

Avec DCAT-AP, on peut :

- Récupérer les métadonnées d’un portail open data.
- Fédérer des portails open data, par exemple entre le portail luxembourgeois et le portail européen, ou entre le portail d’un établissement public ou d’une commune et le portail national.
- Pouvoir réaliser des recherches sur de multiples portails.

Le portail open data luxembourgeois fournissant une API au format DCAT-AP, ses données sont fédérées dans le portail européen data.europa.eu.

### Le schéma

Au moment d’écrire ces lignes, la dernière version de DCAT-AP est la version 3.0 (N’hésitez pas à vous référer à la [dernière version de DCAT-AP](https://github.com/SEMICeu/DCAT-AP/releases).) Nous vous recommandons de prendre connaissance du schéma de données de [DCAT-AP 3](https://semiceu.github.io/DCAT-AP/releases/3.0.0/#application-profile-diagram).

Le graphique ci-dessous présente le schéma de données de DCAT-AP 3.0.

Les principaux concepts sont les suivants :

- **Dataset** : représente un jeu de données sur le portail open data. Un Dataset a notamment un titre, une description, un auteur, une licence, etc.
- **Distribution** : sur le portail open data on va plutôt parler de Ressource ou de Fichier. Un Dataset est lié à une ou plusieurs distributions, chacune représentant un Fichier disponible sur le portail Open data ou à une URL donnée. Une distribution a nécessairement une URL, et peut avoir des métadonnées supplémentaires, comme le format de données, la description, etc.
- **Catalogue** : représente le portail open data lui-même, est lié à l’ensemble des jeux de données du portail.

DCAT-AP va plus loin que DCAT, dans la mesure où il précise le caractère obligatoire, recommandé ou optionnel des classes et propriétés à implémenter. Ces informations sont précisées sur le schéma ci-dessus et sont importantes pour les personnes responsables de l’implémentation de portails open data.

### Compatibilité

Les principales plateformes open source pour la création de portails open data comme [CKAN](https://ckan.org/) ou [udata](https://udata.readthedocs.io) supportent le standard DCAT-AP. Idem pour les portails de données géographiques comme GeoNetwork.

Il est possible de vérifier la compatibilité d’une implémentation de DCAT-AP grâce à son validateur :

[DCAT-AP validator](https://www.itb.ec.europa.eu/shacl/dcat-ap/upload)

La démarche de validation et la configuration du validateur sont détaillées dans la documentation de DCAT-AP, notamment dans la section [« Validation of DCAT-AP »](https://semiceu.github.io/DCAT-AP/releases/3.0.0/#validation-of-dcat-ap)

### Les extensions de DCAT-AP

DCAT-AP est un format extensible. En effet, il est difficile de prévoir a priori un schéma de données qui puisse répondre à tous les besoins. Certaines extensions ont été définies pour venir compléter DCAT-AP sur des cas d’utilisation spécifiques :

- [StatDCAT-AP](https://joinup.ec.europa.eu/collection/semic-support-centre/solution/statdcat-application-profile-data-portals-europe) : pour le domaine des statistiques
- [GeoDCAT-AP](https://semiceu.github.io/GeoDCAT-AP/releases/) : pour les données géographiques

Plusieurs pays européens ont créé leur propre extension de DCAT-AP comme la [Belgique](http://dcat.be/) ou l’[Allemagne](https://www.dcat-ap.de/), ...

## En conclusion

Vous souhaitez créer un nouveau portail open data au Luxembourg et le fédérer avec le portail open data Luxembourgeois, cela se passera très certainement via le standard DCAT-AP. De même si vous souhaitez récupérer toutes les métadonnées du portail open data Luxembourgeois, la connaissance de DCAT-AP vous sera très utile.

## En savoir plus

- [DCAT and DCAT-AP training - Webinar 1: General introduction](https://www.youtube.com/watch?v=_JB93__aj_M)
- [DCAT and DCAT-AP training - Basic user](https://www.youtube.com/watch?v=Za1XgjisosM)
- [DCAT and DCAT-AP training Webinar 3: Advanced user](https://www.youtube.com/watch?v=etUu24hNgz4)
- [DCAT-AP API endpoints for data.public.lu](https://data.public.lu/fr/datasets/dcat-ap-api-endpoints-for-data-public-lu/)
