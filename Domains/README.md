# **Property and Sample**

# Description
Les domains correspondent dans ce repository aux différents modelets de l'ontologie Coswot. Chaque dossier contient les sources (ttl/owl) de l'A-box et la T-box, ainsi qu'un ensemble de requêtes correspondant aux questions de compétences.

# Liste des Modelets
Le tableau suivant énumère la liste des modelets. Chaque modelet est décrit et l'état de progression de sa définition est indiqué: En cours pour les modelets en cours de définition, V X.Y pour les modelets complètement définis mais qui peuvent subir des modifications dans des prochaines versions. Si l'état est vide, le modelet a été spécifié mais pas encore défini. 

| ID | Modelet | Description | Etat | 
|---|---|---|---|
| M1 | Entité d'intérêt et propriétés  |  | V 0.1|
| M2 | Echantillons et propriétés  |  | V 0.1 |
| M3 | Valeur Simple  |  | En cours |
| M4 | Etat  |  | En cours |
| M5 | Evaluation  |  | En cours |
| M6 | Grandeurs physiques  |  | En cours |
| M7 | Bâtiment et topologie  |  | |
| M8 | Procédure  |  | |
| M9 | Capteurs  |  | |
| M10 | Affordances  |  | V 0.1 |
| M11 | Deploiement  |  | |
| M12 | Aggrégation  |  | |
| M13 | Décision  |  | |
| M14 | Personnalisation  |  | |


# Recommendations
- Ecriture et test des modelets:
s'assurer que les fichiers (ttl ou owl/xml) sont bien complets et interprétables/éditables dans Protégé (pour Catherine)
- Test unitaire: un fichier rdf qui implémente les classes définies et A-box test et T-box test.
- Puis modulariser: découper: (a) bout d'ontologie coswot d'un côté, (b) ontologie d'exemple qui définit la T-box et importe l'ontologie coswot, (c) ontologie d'exemple qui définit la A-box et importe la T-box

- Trois approches possibles pour réutiliser les classes existantes dans d'autres ontologies:
    1. import de l'ontologie et utilisation des classes/propriétés
       Avantage: plus clair pour les utilisateurs si ils connaissent l'ontologie importée
        Avantage: l'ontologie coswot résultante définit moins de termes
        Avantage: on n’a pas besoin de redocumenter les entités, ecrire une bonne documentation prend du temps.
        Inconvénient: lorsque finalement on utilise /importe des concepts de deux ontologies comme SOSA et SAREF, ces deux ontologies définissent parfois des concepts similaires (sosa:Observation, saref:Measurement) ou (SAREF:sensor et SOSA:Sensor). On ne sait pas lequel choisir. On fait donc un choix: utiliser SOSA et éviter SAREF. Malheureusement dans un 
    2. on re-déclare les classes dont on a besoin, mais on n'importe pas les ontologies (OK pour ce choix)
        Avantage: on n'importe pas l'entièreté des ontologies externes. On redéfinit seulement ce qu'on souhaite.
        On n'est pas obligé de lier formellement les ontologies importées, mais on les lie "indirectement" via les termes de coswot.
        Inconvénient: il faut à chaque fois choisir de quelle ontologie on récupère les termes.
        Avantage: le but est de démontrer comment nous souhaitons réutiliser ces termes, et on explique comment on compte les utiliser.
    3. est-ce qu'on redéfinit dans le namespace de notre ontologie les concepts que l'on souhaite 
        On peut également créer des ontologies à part qui importent notre ontologie et l'ontologie externe, et définit des alignement formels entre les deux ontologies.