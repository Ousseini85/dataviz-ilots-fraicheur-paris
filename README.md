# dataviz-ilots-fraicheur-paris


# Les îlots de fraîcheur à Paris : répartition, accessibilité et disponibilité

## 1. Description du projet

Ce projet DataViz consiste à analyser la répartition géographique des équipements de fraîcheur dans la ville de Paris, afin de mieux comprendre leur implantation, leur diversité, leur tarification et la disponibilité des informations relatives à leurs horaires d'ouverture.

À partir des données ouvertes de la Ville de Paris, le projet mobilise plusieurs outils de traitement et de visualisation de données : **SQL** pour l'exploration et la préparation des données, **Tableau** pour la création des visualisations et **K-Means** pour réaliser une première analyse exploratoire de regroupement géographique.

L'objectif est de transformer un jeu de données brutes en indicateurs et représentations visuelles facilitant la compréhension de l'offre d'équipements de fraîcheur à Paris.

## 2. Contexte et problématique

Les périodes de fortes chaleurs constituent un enjeu important pour les grandes villes, notamment en raison des différences d'exposition à la chaleur entre les quartiers et de la nécessité de disposer de lieux permettant de se rafraîchir.

Dans ce contexte, les équipements de fraîcheur jouent un rôle essentiel : brumisateurs, piscines, ombrières, lieux de culte et autres équipements accessibles au public peuvent contribuer au confort des habitants et des visiteurs.

La Ville de Paris met à disposition des données ouvertes recensant différents équipements et leurs caractéristiques.

**Problématique :**

Comment les équipements de fraîcheur sont-ils répartis sur le territoire parisien, quelle est leur diversité et dans quelle mesure les informations disponibles permettent-elles d'évaluer leur accessibilité et leur disponibilité ?

## 3. Présentation des données

Le jeu de données utilisé provient de l'Open Data de la Ville de Paris.

Il contient initialement :
- 535 lignes de données ;
- 19 colonnes ;
- 12 catégories d'équipements ;
- Des informations relatives aux identifiants, aux noms, aux types d'équipements, aux adresses, aux codes postaux, à la tarification, aux statuts d'ouverture et aux horaires ;
- Des coordonnées géographiques permettant de localiser les équipements.

Les données couvrent les 20 arrondissements parisiens.

## 4. Démarche et méthodologie

### 4.1. Exploration et préparation des données avec SQL

Une première phase a été consacrée à l'exploration et au contrôle de la qualité des données.

Les principales opérations réalisées sont :
- Vérification du nombre de lignes et des identifiants distincts ;
- Identification des doublons et des valeurs manquantes ;
- Analyse de la répartition des équipements par catégorie ;
- Extraction de l'arrondissement à partir du code postal ;
- Normalisation des informations relatives à la tarification ;
- Création d'un indicateur permettant de distinguer les équipements disposant d'au moins un horaire renseigné de ceux pour lesquels les horaires sont absents ;
- Extraction des coordonnées géographiques pour l'analyse spatiale.

Deux identifiants étant présents en double, le jeu de données comporte 535 lignes pour 533 identifiants distincts. Les doublons ont été conservés dans l'analyse.

### 4.2. Analyse et visualisation avec Tableau

Les données préparées ont ensuite été exploitées dans Tableau afin de construire plusieurs visualisations :

- Répartition des équipements par type ;
- Localisation géographique des équipements sur une carte de Paris ;
- Répartition selon la tarification : gratuit, payant ou non renseigné ;
- Analyse de la répartition territoriale ;
- Indicateurs clés sur le nombre d'équipements et la part des équipements gratuits ;
- Analyse de la disponibilité des informations relatives aux horaires.

Ces visualisations permettent de synthétiser les principales caractéristiques du jeu de données et de faciliter leur interprétation.

### 4.3. Analyse exploratoire avec K-Means

Une approche de Machine Learning non supervisé a également été mise en œuvre à l'aide de l'algorithme K-Means.

L'analyse repose uniquement sur les coordonnées géographiques (latitude et longitude), afin de regrouper les équipements selon leur proximité spatiale.

Le modèle a été exécuté avec :
- 535 observations ;
- 2 variables géographiques ;
- 3 clusters (K = 3) ;
- Une initialisation K-Means++ ;
- Un maximum de 300 itérations.

Cette approche permet de faire ressortir trois regroupements géographiques et de compléter la lecture de la carte réalisée dans Tableau.

## 5. Principaux résultats et enseignements

L'analyse fait ressortir plusieurs éléments :

**Une offre diversifiée**

Le jeu de données recense 12 catégories d'équipements. Les ombrières pérennes, les lieux de culte et les brumisateurs figurent parmi les catégories les plus représentées.

**Une majorité d'équipements gratuits**

Sur les 535 lignes analysées :
- 426 équipements sont identifiés comme gratuits ;
- 91 sont identifiés comme payants ;
- 18 ne disposent pas d'une information tarifaire renseignée.

Cela représente environ 79,6 % de lignes classées comme gratuites.

**Une répartition géographique observable**

La cartographie permet de visualiser l'implantation des équipements dans les 20 arrondissements parisiens. Elle facilite l'identification des zones de concentration et des zones où les équipements apparaissent moins nombreux.

**Une disponibilité limitée des informations horaires**

Seules 125 lignes disposent d'au moins un horaire renseigné, contre 410 pour lesquelles aucune information horaire n'est disponible, soit environ 76,6 % de lignes sans horaires renseignés.

Cette absence d'information ne signifie pas nécessairement que les équipements sont fermés ou indisponibles. Elle constitue néanmoins une limite importante pour évaluer leur accessibilité réelle.

**Trois regroupements géographiques identifiés**

L'analyse K-Means met en évidence trois clusters construits à partir des coordonnées géographiques. Ces regroupements apportent un éclairage complémentaire sur la distribution spatiale des équipements.

## 6. Limites de l'analyse et perspectives

Cette étude présente plusieurs limites :

- Les données analysées ne permettent pas nécessairement de recenser l'ensemble des lieux de fraîcheur existants à Paris.
- Les informations relatives aux horaires et aux statuts d'ouverture sont largement incomplètes.
- Le nombre d'équipements par arrondissement ne suffit pas à mesurer l'accessibilité réelle pour les habitants. Il faudrait notamment intégrer les données démographiques.
- Le clustering K-Means repose uniquement sur la proximité géographique et ne mesure ni la qualité des équipements ni leur accessibilité.

Pour approfondir cette étude, plusieurs pistes pourraient être envisagées :
- Croiser les données avec la population de chaque arrondissement ;
- Intégrer des données relatives aux températures et aux îlots de chaleur urbains ;
- Étudier les distances entre les équipements et les zones résidentielles ;
- Enrichir les données relatives aux horaires et aux conditions d'accès.

## 7. Conclusion

Ce projet a permis de mettre en œuvre une démarche complète de DataViz, depuis l'exploration et la préparation des données jusqu'à leur analyse et leur visualisation.

L'utilisation combinée de SQL, Tableau et de l'algorithme K-Means a permis de dégager plusieurs enseignements sur la diversité, la répartition géographique, la tarification et la disponibilité des informations concernant les équipements de fraîcheur à Paris.

Au-delà des visualisations produites, ce travail met également en évidence l'importance de la qualité et de la complétude des données pour construire une analyse pertinente et fiable.

## 8. Outils et technologies

- **Source des données :** Open Data de la Ville de Paris
- **Base de données :** MySQL
- **Préparation et analyse :** SQL
- **Visualisation :** Tableau
- **Machine Learning :** K-Means (clustering non supervisé)
- **Format des données :** CSV



Requêtes et Graphiques 

SQL/

 
/* =====================================================
  1 - CONTROLE DE LA QUALITE DES DONNEES
   ===================================================== */

SELECT * FROM equipements_activites

-- Contrôle qualité : valeurs NULL, doublons, identifiants.

SELECT
    COUNT(*) AS total,
    SUM(`Identifiant DICOM` IS NULL) AS dicom_manquants,
    SUM(`Payant (O/N)` IS NULL) AS tarif_manquant,
    SUM(`Adresse` IS NULL) AS adresse_manquante,
    SUM(`STATUT OUVERTURE` IS NULL) AS statut_manquant,
    SUM(`HORAIRES PERIODE` IS NULL) AS periode_manquante
FROM equipements_activites;

-- Détecter les doublons d identifiants

SELECT
    IDENTIFIANT,
    COUNT(*) AS nombre
FROM equipements_activites
GROUP BY IDENTIFIANT
HAVING COUNT(*) > 1;


/* =====================================================
   02 - TRANSFORMATION ET AJOUT DE COLONNES
   ===================================================== */


-- Répartition des équipements par catégorie
SELECT TYPE,
       COUNT(*) as nombre_equipementS
FROM equipements_activites
GROUP BY TYPE
ORDER BY nombre_equipements DESC ;

-- Transformation SQL
-- Extraire l'arrondissement depuis le code postal
-- ALTER TABLE equipements_activites
-- ADD COLUMN Arrondissement VARCHAR(10);

UPDATE equipements_activites
SET Arrondissement = RIGHT(TRIM(`Code postal`), 2)
WHERE `Code postal` IS NOT NULL;

-- Normaliser les informations de tarification

-- ALTER TABLE equipements_activites
-- ADD COLUMN Categorie_tarifaire VARCHAR(30);
UPDATE equipements_activites
SET Categorie_tarifaire =
    CASE
        WHEN `Payant (O/N)` = 'Oui' THEN 'Payant'
        WHEN `Payant (O/N)` = 'Non' THEN 'Gratuit'
        ELSE 'Non renseigné'
    END;
-- Gratuité et équipements payants par catégorie
SELECT
    TYPE,
    SUM(`Payant (O/N)` = 'Non') AS Gratuit,
    SUM(`Payant (O/N)` = 'Oui') AS Payant
FROM equipements_activites
GROUP BY TYPE
ORDER BY Gratuit DESC;

-- Créer un indicateur de complétude des horaires

-- ALTER TABLE equipements_activites
-- ADD COLUMN Horaires_renseignes VARCHAR(30);

UPDATE equipements_activites
SET Horaires_renseignes =
    CASE
        WHEN
            NULLIF(TRIM(`HORAIRES LUNDI`), '') IS NOT NULL
            OR NULLIF(TRIM(`HORAIRES MARDI`), '') IS NOT NULL
            OR NULLIF(TRIM(`HORAIRES MERCREDI`), '') IS NOT NULL
            OR NULLIF(TRIM(`HORAIRES JEUDI`), '') IS NOT NULL
            OR NULLIF(TRIM(`HORAIRES VENDREDI`), '') IS NOT NULL
            OR NULLIF(TRIM(`HORAIRES SAMEDI`), '') IS NOT NULL
            OR NULLIF(TRIM(`HORAIRES DIMANCHE`), '') IS NOT NULL
        THEN 'Renseigné'
        ELSE 'Non renseigné'
    END;

SELECT
    Horaires_renseignes,
    COUNT(DISTINCT Identifiant) AS Nombre_equipements
FROM equipements_activites
GROUP BY Horaires_renseignes

-- vérification des modifications
SHOW COLUMNS FROM equipements_activites;

SELECT
    Arrondissement,
    COUNT(*) AS Nombre_lignes,
    COUNT(DISTINCT Identifiant) AS Nombre_equipements
FROM equipements_activites
GROUP BY Arrondissement
ORDER BY Arrondissement;

SELECT
    COUNT(DISTINCT Arrondissement) AS Nombre_arrondissements,
    MIN(Arrondissement) AS Premier_arrondissement,
    MAX(Arrondissement) AS Dernier_arrondissement
FROM equipements_activites
WHERE Arrondissement IS NOT NULL;

SELECT
    Categorie_tarifaire,
    COUNT(*) AS Nombre_equipements
FROM equipements_activites
GROUP BY Categorie_tarifaire
ORDER BY Nombre_equipements DESC;

SELECT
    Horaires_renseignes,
    COUNT(*) AS Nombre_equipements
FROM equipements_activites
GROUP BY Horaires_renseignes;

Création de colonne Latitude et Longitude
SELECT
    CAST(TRIM(SUBSTRING_INDEX(`geo_point_2d`, ',', 1)) AS DECIMAL(10,7)) AS Latitude,
    CAST(TRIM(SUBSTRING_INDEX(`geo_point_2d`, ',', -1)) AS DECIMAL(10,7)) AS Longitude
FROM equipements_activites
WHERE `geo_point_2d` IS NOT NULL
  AND TRIM(`geo_point_2d`) <> '';

  Tableau/
### Tableau de bord global
https://github.com/Ousseini85/dataviz-ilots-fraicheur-paris/blob/main/Tableau%20de%20bord.png

### Répartition par type
[Répartition des équipements par type.png](https://github.com/Ousseini85/dataviz-ilots-fraicheur-paris/blob/main/Re%CC%81partition%20des%20e%CC%81quipements%20par%20type.png)

### Répartition géographique
https://github.com/Ousseini85/dataviz-ilots-fraicheur-paris/blob/main/Re%CC%81partition%20ge%CC%81ographique.png 

### Répartition des équipements selon leur tarification
![Uploading Capture d’écran 2026-11-17 à 14.54.15.png…]()

### KPI Gratuité
![Uploading Capture d’écran 2026-11-17 à 14.55.25.png…]()

### Nombre total d'équipements
![Uploading Capture d’écran 2026-11-17 à 14.57.25.png…]()

### Disponibilité des horaires
![Uploading Capture d’écran 2026-11-17 à 14.59.35.png…]()


Machine_Learning
### Clustering_kmeans
![Uploading chart.png…]()
