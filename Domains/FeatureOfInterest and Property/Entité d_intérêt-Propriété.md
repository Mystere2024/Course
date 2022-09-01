Feature of Interest and Properties
# Name
Description des entités d'intérêt et de leurs propriétés
# Description
Ce modelet décrit les entités d'intérêt et leurs propriétés (caractéristiques ou qualités). Il s'agit du patron d’ontologie au cœur de l'ontologie CoSWoT. Une propriété est intrinsèque à une entité d’intérêt et ne peut pas exister sans son entité d'intérêt. Une propriété a une valeur associée, qui est alors considérée unique dans le contexte où elle est exprimée (contexte temporel et spatial).
# Motivating Scenario
## Exemple Batiment
Une pièce est une entité d'intérêt dans le domaine de la domotique. Une pièce a par exemple une température intérieure de l’air ambiant dans la pièce, et un taux de CO2 de l’air ambiant dans la pièce. Un mur a une conductivité thermique constante, un radiateur a une consigne (hors gel, réduit, confort 1, manuel, … ) et une puissance, une fenêtre a un état (ouvert, fermé).
## Exemple Agriculture
Les entités dans le domaine de l’agriculture peuvent être des phénomènes naturels (pluie, vent, parcelle cultivée, plant de tomate) mais aussi des dispositifs mécaniques ou électroniques (tracteurs, système d’arrosage, …)

Une parcelle a comme propriété une surface, une géométrie, une localisation, un type de sol, ....

une plante cultivée a comme propriété une préconisation de date de semence, un nom de cultivar, un rendement max, ...

une culture (un ensemble de plantes cultivé sur une parcelle) a comme propriété un stade de développement, une date de semence,  un rendement, …

un système d’arrosage a comme propriété un débit d’eau, une fréquence d’arrosage, une durée d'arrosage, …

# Competency Questions 
### CQQ1 : Quelles sont les propriétés d’une entité d’intérêt ?
La liste des propriétés associées à une entité d’intérêt.

Exemple : La pièce 429 a une température de l’air ambiant, une luminosité, un taux d’humidité de l’air ambiant, taux de CO2 de l’air ambiant. 
### CQQ2 : Quelles sont les propriétés de type température ?
La liste des instances de la classe température (sous classe de property).

Exemple : Room418Temperature,Room420Temperature, CuisineTemperature…
### CQQ3 : Quelle est la capacité d’une salle ?
La valeur de la propriété capacité de l’entité d’intérêt salle.

la capacité d’une salle permet de connaitre le nombre maximum de personnes autorisées dans la salle.


# Term Glossary
Deux ontologies ont été identifiées SOSA/SSN et SAREF. Nous avons choisi de réutiliser les éléments de l’ontologie SOSA/SSN. 
## SOSA/SSN
### **Feature Of Interest** 
IRI: http://www.w3.org/ns/sosa/FeatureOfInterest

**étiquette française**: entité d'intérêt

The thing whose property is being estimated or calculated in the course of an Observation to arrive at a Result, or whose property is being manipulated by an Actuator, or which is being sampled or transformed in an act of Sampling.

Example	When measuring the height of a tree, the height is the observed ObservableProperty, 20m may be the Result of the Observation, and the tree is the FeatureOfInterest. A window is a FeatureOfInterest for an automatic window control Actuator.
### **Observable Property** 
IRI: <http://www.w3.org/ns/sosa/ObservableProperty>

**etiquette française:** propriété observable

An observable quality (property, characteristic) of a FeatureOfInterest. Example	The height of a tree, the depth of a water body, or the temperature of a surface are examples of observable properties, while the value of a classic car is not (directly) observable but asserted.
### **Property**
IRI: http://www.w3.org/ns/ssn/Property

**étiquette française:** propriété

A quality of an entity. An aspect of an entity that is intrinsic to and cannot exist without the entity.
#
# OWL Description
## Diagramme
Lien: <https://app.diagrams.net/#G1YLwbnZobNIHKCXJfScjohD-5jGThZfpf>

![](Aspose.Words.ec963108-8202-4837-a1d7-eaf0de5264c8.001.png)


## Recommendations
Une entité d’intérêt possède plusieurs caractéristiques qui sont représentées par les propriétés (à travers la relation hasProperty).

Une instance de propriété est nécessairement rattachée à une instance d’entité d’intérêt (par la relation isPropertyOf, cardinalité minimum=1), et est spécifique à celle-ci (isPropertyOf est une relation fonctionnelle). 

Les instances de propriétés sont regroupées dans des sous-classes qui peuvent qualifier le phénomène observé (Température, stade d’évolution) ou sujet d’actuation (luminosité, humidité) entre autres. Ce typage permettrait d’identifier les propriétés de même nature pour des besoins de raisonnement par exemple. 

La relation entre les entités d’intérêt et leur échantillons ainsi que les propriétés d’échantillons sont formalisés dans le modelet sample. 

Le processus permettant l’assignation d’une valeur à une propriété est décrit dans le modelet Evaluation. 

Le concept de valeur simple d’une propriété est détaillé dans le modelet “Valeur Simple”.

Les états des entités d’intérêt sont des propriétés (coswot:State) ayant des valeurs qualitatives. Elles sont définies dans le modelet “Etat”. 

## Spécification dans l’ontologie


**sosa:FeatureOfInterest** a rdfs:Class ; a owl:Class ;

`  `rdfs:label "Feature Of Interest"@en ;

`  `rdfs:label "Entité d'Intérêt"@fr ;

`  `rdfs:isDefinedBy sosa: ;

`  `rdfs:comment "The thing whose property is being observed through a Sensor or whose property estimated/calculated in the course of an Evaluation to get a Value or whose property is being manipulated by an Actuator, or which is being sampled or transformed in an act of Sampling."@en ;

`  `rdfs:comment "Une entité dont la propriété est en cours d'Observation par un Capteur ou dont la propriété estimée/calculée par une Evaluation afin d'obtenir une valeur ou dont la propriété est manipulée par un actionneur, ou qui est en cours d'Echantillonage ou transformée par un Echantillonage."@fr ;

`  `skos:definition "The thing whose property is being observed through a Sensor or whose property estimated/calculated in the course of an Evaluation to get a Value or whose property is being manipulated by an Actuator, or which is being sampled or transformed in an act of Sampling."@en ;

`  `skos:example "When measuring the height of a tree, the height is the observed Property, 20m may be the Result of the Observation, and the tree is the FeatureOfInterest. A window is a FeatureOfInterest for an automatic window control Actuator."@en ;



**ssn:Property** a owl:Class ;

`  `rdfs:label "Property"@en ;

`  `rdfs:label "Propriété"@fr ;

`  `rdfs:isDefinedBy sosa: ;

`  `rdfs:comment "A characteristic of a feature of interest that is interinsic to, and can not exist without the feature of interest."@en ;

`  `rdfs:comment "Une charactéristique intrinsèque de l'entité d'intérêt, qui ne peut exister indépendamment d'elle."@fr ;

`  `skos:definition "Une charactéristique intrinsèque de l'entité d'intérêt, qui ne peut exister indépendamment d'elle."@en ;



#Add observableProperty and ActionableProperty

#Axioms in sensor sosa:observes

Ensemble de données (Dataset)

T-Box : terminologie

**coswot:TemperatureProperty** a owl:Class ;  

`  `rdfs:label "Temperature"@en ;

`  `rdfs:label "Température"@fr ;

`  `rdfs:subClassOf ssnsosa:Property ;

`  `rdfs:isDefinedBy coswot: ;

`  `rdfs:comment "The temperature of a Feature of Interest."@en ;

`  `rdfs:comment "La température d'une Entité d'intérêt."@fr ;

`  `skos:definition "The temperature of a Feature of Interest."@en ;

`  `skos:definition "La température d'une Entité d'intérêt."@fr ;

`  `skos:example "La température d'une pièce, du sol, d'un processeur.."@fr.

**coswot:HumidityProperty** a owl:Class ;

`  `rdfs:label "Humidity"@en ;

`  `rdfs:label "Humidité"@fr ;

`  `rdfs:subClassOf sosa:Property ;

`  `rdfs:isDefinedBy coswot: ;

`  `rdfs:comment "The humidity Property of a Feature of Interest."@en ;

`  `rdfs:comment "L'humidité d'une Entité d'intérêt."@fr ;

`  `skos:definition "The humidity Property of a Feature of Interest."@en ;

`  `skos:definition "L'humidité d'une Entité d'intérêt."@fr ;

`  `skos:example "l'humidité d'une pièce, du sol.."@fr .

**coswot:CarbonDioxideConcentrationProperty** a owl:Class ;

`  `rdfs:label "Carbon dioxide concentration property"@en ;

`  `rdfs:label "Niveau de CO2"@fr ;

`  `rdfs:subClassOf sosa:Property ;

`  `rdfs:isDefinedBy coswot: ;

`  `rdfs:comment "The CO2 level of a Feature of Interest."@en ;

`  `rdfs:comment "Le niveau de gaz carbonique d'une entité d'intérêt."@fr ;

`  `skos:definition "The CO2 level of a Feature of Interest."@en ;

`  `skos:definition "Le niveau de gaz carbonique d'une entité d'intérêt"@fr ;

`  `skos:example "Le niveau de CO2 dans une pièce, une serre agricole.."@fr.



#Add property AreaProperty

A-Box : description des instances

##Meeting Room 418

**:418Meetingtemperature** a coswot:Temperature ;

`                `coswot:hasPropertyValue "21.6"^^xsd:Decimal.

**:418MeetingHumidity** a coswot:Humidity.

`                `coswot:hasPropertyValue "0.6"^^xsd:Decimal.

**:418Meetingluminosity** a coswot:Luminosity,

`                `coswot:hasPropertyValue "800"^^xsd:Decimal.

**:418Meetingco2** a coswot:CO2,

`                `coswot:hasPropertyValue "0.7"^^xsd:Decimal.

**:418Meeting** a sosa:FeatureOfInterest ;

`  `rdfs:label "meeting room 418"@en, "sale de réunion 418"@fr ;

`  `rdfs:comment "Meeting room 418 at 4th floor of Espace Fauriel, Mines Saint-Étienne" @en ;

`  `rdfs:comment "Salle de réunion 418 au 4ème étage de l'espace Fauriel, Mines Saint-Étienne" @fr ;

`  `sosa:hasProperty :418#temperature, :418#humidity, :418#co2, :418#luminosity.

# Queries
### Prefixes
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>

PREFIX owl: <http://www.w3.org/2002/07/owl#>

PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

PREFIX sosa: <http://www.w3.org/ns/sosa/>

PREFIX coswot:  <https://coswot.gitlab.io/FeatureOfInterestOntology#>

PREFIX  : <http://www.semanticweb.org/FatmaZohra/FeatureOfInterestBuilding#>

### CQQ1 : Quelles sont les propriétés d’une entité d’intérêt ?
SELECT  ?property 

WHERE { :Office429 sosa:hasProperty ?property .}

![Une image contenant texte

Description générée automatiquement](Aspose.Words.ec963108-8202-4837-a1d7-eaf0de5264c8.002.png)
### CQQ2: Quelles sont les propriétés de type température ?

SELECT ?property

WHERE { ?property a :Temperature .}

![Une image contenant texte

Description générée automatiquement](Aspose.Words.ec963108-8202-4837-a1d7-eaf0de5264c8.003.png)
###














