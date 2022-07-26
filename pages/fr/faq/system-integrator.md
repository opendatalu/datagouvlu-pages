
Découvrir l’OpenData en tant qu’intégrateur
===========================================

La plateforme « data.public.lu » vous offre plusieurs moyens plus ou moins avancés d’intégrer les données disponibles en open data sur vos propres sites :

1.  de manière unitaire si vous souhaitez n’afficher qu’un ou quelques jeu(x) de données particulier(s) ;
2.  de manière plus générale si vous souhaitez afficher tous les jeux de données relatifs à un territoire ou à une organisation ;
3.  pour une gestion fine de l’habillage et des données affichées, nous vous recommandons l’API ;
4.  pour avoir votre propre portail fondé sur le moteur de la plateforme.

Ces différents cas d’intégration correspondent généralement à différents profils :

1.  un journaliste traitant d’une problématique donnée va être intéressé par l’inclusion de jeux de données directement au sein de son article ;
2.  une mairie va être intéressée par l’intégration des jeux de données relatifs à son territoire sur son site internet ;
3.  une association pourrait être intéressée par la création d’une page personnalisée compilée à partir de données issues de sources multiples ;
4.  un pays se lançant dans l’open data va chercher à créer son propre portail.

Quel que soit votre besoin ou votre profil, nous sommes là pour vous accompagner dans votre démarche de diffusion de données ouvertes. Ci-dessous, la documentation technique correspondant à chacun des cas évoqués :

1\. Intégration ponctuelle de jeux de données
---------------------------------------------

Chaque jeu de données est intégrable sur n’importe quelle page en ajoutant deux lignes de HTML :

    <div data-udata-dataset-id="IDENTIFIANT DU JEU DE DONNÉES"></div>
    <script src="https://data.public.lu/static/widgets.js" id="udata" async defer onload="udataScript.loadDatasets()"></script>
    

En remplaçant l’`IDENTIFIANT DU JEU DE DONNÉES` par l’identifiant disponible sur sa page dédiée vous devriez voir apparaître sur votre site un cartouche contenant les informations relatives à ce jeux de données de la manière suivante :

Il est possible d’intégrer plusieurs jeux de données à la fois en dupliquant la ligne correspondant à l’élément `<div>` avec un nouvel identifiant. Vous pouvez personnaliser l’apparence du rendu du cartouche grâce à la classe CSS `dataset-card`.

2\. Intégration pour une organisation ou un territoire
------------------------------------------------------

Attention : ce type d’intégration est actuellement en cours de développement et l’API est susceptible de changer. Veuillez nous contacter si vous souhaitez participer aux tests préliminaires.

Le mécanisme pour afficher tous les jeux de données relatifs à une organisation ou un territoire est le même que celui pour l’intégration d’un seul jeu de donnée décrit précédemment.

Cet usage est recommandé si vous êtes responsable de cette organisation ou de ce territoire et souhaitez faire la promotion des jeux de données associés.

### 2.1 Intégration d’une organisation

    <div data-udata-organization="IDENTIFIANT DE L’ORGANISATION"></div>
    <script src="https://www.data.public.lu/static/widgets.js" id="udata" async defer onload="udataScript.loadOrganization()"></script>
    

En remplaçant l’`IDENTIFIANT DE L’ORGANISATION` par l’identifiant disponible sur sa page dédiée vous devriez voir apparaître sur votre site un cartouche contenant les informations relatives aux jeux de données de cette organisation de la manière suivante :

Optionnellement, il est possible d’afficher une barre de recherche pour laisser la possibilité au visiteur de filtrer la liste des jeux de données affichés. Cela est activé en passant l’option `{withSearch: true}` à la méthode `loadOrganization()` ci-dessus.

3\. Intégration d’un portail open data complet
----------------------------------------------

Les outils que nous développons sont disponibles en open-source. Ils sont le fruit d’un effort international pour créer des synergies autour de la donnée ouverte et mutualiser nos efforts de développement. La gouvernance est inclusive et la licence est permissive. Nous participons à l’animation autour du développement de la plateforme car nous souhaitons produire un bien commun réutilisable par tous.

L’intégration d’un portail open data complet demande des compétences en administration système, en développement Python et JavaScript ainsi qu’un temps non négligeable de prise en main de la plateforme. C’est un choix qui doit être mûrement réfléchi et nous vous recommandons de passer directement par « data.public.lu » si vous avez des données issues de territoires francophones.

Si vous souhaitez néanmoins vous lancer dans cette aventure, vous pouvez commencer par analyser le [code source](https://github.com/opendatateam/udata) ainsi que la [documentation dédiée](http://udata.readthedocs.io/en/latest/). Vous pouvez également venir en [discuter avec la communauté](https://gitter.im/opendatateam/udata) (en anglais).


[← Retour à l’accueil de la FAQ](/fr/faq/)