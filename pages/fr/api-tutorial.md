Documentation de l'API
======================

Cette page décrit le comportement de l'API gratuite et ouverte de ce site.

Authentification
----------------

De façon à pouvoir exécuter des opérations d'écriture, vous devez d'abord être authentifié et obtenir une clé d'API dans les paramètres de votre profil.

Cette clé doit être fournie à chaque appel dans l'entête HTTP `X-API-KEY`.

Autorisations
-------------

Les appels d'API sont soumis aux même permissions que l'interface web.

Par exemple, vous devez être membre de l'organisation pour modifier l'un de ses jeux de données.

Pagination
----------

Certaines méthodes sont paginées et suivent le même modèle de pagination. La liste d'objets est encapsulée dans un objet `Page`.

Vous n'avez pas à calculer vous-même les pages précédentes et suivantes puisque les URL sont disponible dans la réponse dans les attributs `previous_page` et `next_page`. Ils seront définis à `null` si il n'y a pas de page précédente et/ou suivante.

Exemple:

    {
                    "data": [{...}, {...}],
                    "page": 1,
                    "page_size": 20,
                    "total": 10,
                    "next_page": "https://data.public.lu/api/endpoint/?page=2",
                    "previous_page": null
                }


## Exemples 

Tous les exemples utilisent [httpie](http://httpie.org) et [jq](http://stedolan.github.io/jq/) pour faciliter la lisibilité. Vous n'êtes pas contraint d'utiliser ces bibliothèques pour votre code, ce sont juste des outils pour mieux comprendre l'API.

### Vérifier que httpie fonctionne

Une fois httpie installé, vous pouvez vérifier qu'il fonctionne comme convenu en tapant cette commande dans votre terminal :

    $ http 'https://data.public.lu/api/1/organizations/?page_size=1'

Cela doit retourner une réponse de ce style :

    
                HTTP/1.1 200 OK
                Access-Control-Allow-Credentials: true
                ... LOTS OF HEADERS ...
                
                {
                    "data": [
                        {
                
                            ... LOTS OF DATA ...
                
                            "name": "Stelareum",
                            "page": "https://data.public.lu/organizations/stelareum/",
                            "slug": "stelareum",
                            "uri": "https://data.public.lu/api/1/organizations/5cb1d1ed0f7fb0438df74602/",
                            "url": "https://www.stelareum.io/"
                        }
                    ],
                    "next_page": "https://data.public.lu/api/1/organizations/?page=2&page_size=1",
                    "page": 1,
                    "page_size": 1,
                    "previous_page": null,
                    "total": "10"
                }
                

C'est très verbeux et nous n'avons pas besoin de toute cette information pour l'instant. C'est la raison pour laquelle nous utilisons jq.

### Vérifier que jq fonctionne

Une fois jq installé, vous pouvez vérifier qu'il fonctionne en tapant cette commande dans votre terminal :

    $ http 'https://data.public.lu/api/1/organizations/?page_size=1' | jq '.data[].name'

Cela doit retourner une réponse de ce style :

    "Stelareum"

C'est bien mieux ! Maintenant que tout fonctionne bien, réduisons un peu la taille de notre ligne de commande :

    $ export API="https://data.public.lu/api/1/"

La commande précédente est maintenant équivalente à la commande plus lisible (ne pas oublier les apostrophes) :

    $ http $API'organizations/?page_size=1' | jq '.data[].name'

C'est un bon début, maintenant plongeons dans l'API en elle-même. Nous ne le savons pas encore mais nous avons déjà récupéré notre première organisation.

### Parcourir et récupérer des données

Vous pouvez récupérer une liste d'organisations (filtrée ou non) ou une organisation unitaire. Lorsque vous récupérez un point d'accès, le nombre d'éléments par page par défaut est de 20. Récupérons les 20 premières organisations via l'API :

    $ http $API'organizations/' | jq '.data[].name'

    
                "Stelareum"
                "Département des Travaux Publics - MMTP"
                "NEXXTLAB S.A."
                "Legato Team"
                "Legato Team  uni.lu"
                "Service National de la Jeunesse"
                "OpenAgenda"
                "toto"
                "Autorité luxembourgeoise indépendante de l'audiovisuel"
                "Centre de gestion informatique de l'éducation"
                
                

C'est une bonne chose d'avoir cette liste mais que se passe-t-il si nous souhaitons parcourir les organisations retournées ? Récupérons les 5 premières URI d'organisations.

    $ http $API'organizations/?page_size=5' | jq '.data[].uri'

    
                "https://data.public.lu/api/1/organizations/5cb1d1ed0f7fb0438df74602/"
                "https://data.public.lu/api/1/organizations/5c403e1528c4b2621cd384e9/"
                "https://data.public.lu/api/1/organizations/5b5b26157676667aa7f57afe/"
                "https://data.public.lu/api/1/organizations/5953ebee111e9b2a8e7133bd/"
                "https://data.public.lu/api/1/organizations/5953d44c111e9b2a5fcb4b59/"
                
                

Maintenant, nous sommes capables de récupérer une organisation seulement via l'URI retournée.

    $ http $API'organizations/5cb1d1ed0f7fb0438df74602/' | jq '.'

Cela fait beaucoup de données à parcourir. Affinons ces données, si nous voulons seulement extraire les métriques :

    $ http $API'organizations/5cb1d1ed0f7fb0438df74602/' | jq '.metrics'

    
                {
                 "datasets": 0,
                 "members": 1,
                 "views": 0,
                 "followers": 0,
                 "reuses": 0,
                 "dataset_views": 0,
                 "reuse_views": 0,
                 "resource_downloads": 0,
                 
                }
                

Ou peut-être juste le nom des membres de cette organisation :

    $ http $API'organizations/5cb1d1ed0f7fb0438df74602/' | jq '.members[].user.last_name'

    
                "Crypto"
                
                

Il est vraiment de votre ressort de récupérer les données pertinentes pour votre projet. N'hésitez pas à consulter le [tutoriel de jq](http://stedolan.github.io/jq/tutorial/) et [son manuel](http://stedolan.github.io/jq/manual/) si vous voulez parcourir l'API via la ligne de commande plus en détail.

### Modifier et supprimer des données

Attention, vous entrez dans une zone de danger. Les modifications et suppressions de données via l'API sont définitives et nous ne proposons pas de bac à sable pour faire des tests avant de les exécuter (pour l'instant). Soyez conscient de ces responsabilités avant d'utiliser vos super pouvoirs.

Si vous tentez de modifier une ressource sans le token d'authentification, une erreur 401 sera renvoyée :

    $ http PUT $API'organizations/organization-uri-x/'

    
                HTTP/1.1 401 UNAUTHORIZED
                ... LOTS OF HEADERS ...
                
                {
                    "message": "Unauthorized",
                    "status": 401
                }
                

Vous devez spécifier votre Clé d'API (voir ci-dessus) et utiliser le header HTTP `X-API-KEY`. Si vous tentez de modifier une ressource que vous ne contrôlez pas, une erreur 400 sera retournée :

    $ http PUT $API'organizations/organization-uri-x/' X-API-KEY:your.api.key.here

    
                HTTP/1.1 401 UNAUTHORIZED
                ... LOTS OF HEADERS ...
                
                {
                    "message": "Invalid API Key",
                    "status": 401
                }
                

C'est le message que vous obtiendrez si vous avez spécifié une mauvaise clé d'API. C'est un autre message d'erreur potentiel que vous pouvez rencontrer.

    
                HTTP/1.1 403 FORBIDDEN
                ... LOTS OF HEADERS ...
                
                {
                    "message": "You do not have the permission to modify that object.",
                    "status": 403
                }
                

Cela arrive si vous essayez d'accéder à une ressource que vous ne pouvez éditer avec vos accréditations. Si votre clé est valide vous devriez obtenir quelque chose comme ça:

    
                HTTP/1.1 200 OK
                ... LOTS OF HEADERS ...
                
                {
                    ...
                }
                

Mais ça ne change pas tout ! C'est parfaitement normal, nous avons oublié de spécifier la bonne donnée à envoyer au serveur.

    $ http PUT $API'organizations/organization-uri-x/' X-API-KEY:your.api.key.here name="Lorem ipsum" description="The quick brown fox jumps over the lazy dog." | jq '{name: .name, description: .description}'

    
                {
                  "name": "Lorem ipsum",
                  "description": "The quick brown fox jumps over the lazy dog."
                }
                

La ressource a été modifiée avec vos nouvelles valeurs. Finalement, vous pouvez supprimer une ressource avec le verbe HTTP approprié (attention, aucun retour arrière n'est possible en utilisant l'API pour le moment):

    $ http DELETE $API'organizations/organization-uri-x/' X-API-KEY:your.api.key.here

    
                HTTP/1.0 204 NO CONTENT
                ... LOTS OF HEADERS ...
                
                

Une fois effectué, vous pouvez vérifier que c'est effectif en envoyant un GET sur l'URL précédente:

    $ http GET $API'organizations/organization-uri-x/'

    
                HTTP/1.0 410 GONE
                ... LOTS OF HEADERS ...
                
                {
                    "message": "Organization has been deleted",
                    "status": 410
                }
                
                

Consultez la documentation de référence ci-dessous pour d'autres intéractions avec l'API ou posez-nous vos questions sur le sujet !