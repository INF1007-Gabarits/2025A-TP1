# TP1 : Exercices d'introduction a Python

:alarm_clock: Date de remise : **Le 8 février à 23:59**

:mailbox_with_mail: **À remettre sur GitHub Classroom** (vous devez utiliser les commandes git vues au TP0)

## Introduction

Bienvenue dans cette série de cinq exercices pour votre TP1!

Lors de ces exercices, vous allez devoir écrire des programmes qui permettront d'interagir avec l'utilisateur en lisant des données entrées au clavier. 

En Python, cela se fait à l'aide de la fonction `input()`.

### Lire une donnée

La fonction `input()` permet de lire ce que l'utilisateur écrit au clavier. 

Par exemple:

```python
nom = input("Entrez votre nom: ")
```
La valeur retournée par `input()` est toujours une chaîne de caractères (texte), même si l'utilisateur entre un nombre. 

### Convertir une donnée

Pour effectuer des calculs, il est souvent nécessaire de convertir la chaîne de caractères entrée par l'utilisateur en un nombre.

Par exemple:

```python
age = int(input()) # Pour convertir en nombre entier
distance = float(input()) # avec décimales
```

Dans cet exemple, si l'utilisateur entre une valeur invalide (c'est-à-dire du texte au lieu d'un nombre), Python génère une **erreur**, ce qu'on ne veut pas. 

### Gérer les erreurs avec `try/except`

Afin d'éviter que le programme s'arrête en cas d'erreur, on peut utiliser des blocs `try/except`. 

Par exemple:

```python
try:
    age = int(input())
except ValueError:
    print("Erreur - donnees invalides.")
```

Dans cet exemple:
- Si l’utilisateur entre un nombre valide, la conversion fonctionne normalement
- Si l’utilisateur entre une valeur qui ne peut pas être convertie en entier, une erreur (`ValueError`) se produit
- Le programme affiche alors le message d’erreur au lieu de s’arrêter brutalement.

Dans ce TP, **toutes les entrées doivent être validées à l'aide de blocs `try/except`**. 

### Gestion de contraintes d'entrée

On peut également vouloir imposer d'autres contraintes d'entrée de données à l'utilisateur (ex: doit être un nombre positif, ne peut pas être égal à zéro, etc.). Ces contraintes peuvent être vérifiées après la conversion. 

Par exemple: 

```python
if age < 0:
    print("Erreur - donnees invalides.")

```

**Consignes générales :**
- Respectez **exactement** les formats d'entrée et de sortie demandées (majuscule/minuscule, orthographe, ponctuation, espaces, etc.)
- Aucune erreur Python ne doit apparaître à l’écran lors de l’exécution. Toute entrée invalide (type incorrect ou valeur hors contraintes) doit être gérée à l’aide de blocs `try / except`, comme présenté ci-dessus, et mener à l’affichage du message d’erreur demandé.
- Chaque exercice est indépendant
- Le niveau de difficulté est progressif

## Exercices

L'automne dernier, l'équipe de football masculin des Carabins a remporté le championnat universitaire canadien et a ramené le trophée de la Coupe Vanier à Montréal pour la troisième fois de son histoire. De plus, l'équipe de soccer féminin des Carabins a décroché un troisième titre national et a obtenu le trophée Gladys-Bean. Dans le cadre d'une semaine de célébration, le service des sports des Carabins souhaite automatiser quelques calculs liés aux statistiques de participation, à l'estimation de temps de trajet, à l'accessibilité et à la planification de billets. Ces exercices vous permettront de pratiquer les entrées/sorties, les opérations mathématiques, les conditions, les arrondis, le formatage et de petites boucles de recherche.

## 01. Bilan de visionnage Carabins

Écrivez un programme qui salue l'utilisateur puis calcule son temps total de visionnage des matchs des Carabins.

**Le programme doit demander à l'utilisateur :**
1) Son nom complet
2) Le nombre de matchs de football visionnés (entier)
3) La durée moyenne par match de football (en minutes, entier)
4) Le nombre de matchs de soccer visionnés (entier)
5) La durée moyenne par match de soccer (en minutes, entier)

**Contraintes de validation des entrées:**
- Tous les nombres doivent être des entiers
- Nombre de matchs >= 0
- Durée moyenne > 0

En cas d'erreur, afficher exactement :

```text
Erreur - donnees invalides.
```

Sinon, afficher exactement 4 lignes (formatage obligatoire) :

```text
Bonjour NOM
Football (Carabins): A match(s), HhMM de visionnage
Soccer (Carabins): B match(s), HhMM de visionnage
Total: HhMM
```

Notes :
- Convertissez correctement les minutes en heures et minutes.
- Les minutes doivent être affichées sur 2 chiffres (ex: 11h00, 1h05).

## 02. Ambiance autour du stade

Lors de la semaine de célébration des Carabins, le service des sports souhaite illustrer l'ambiance autour du stade avec un diagramme similaire à celui-ci :
![Ambiance autour du stade](https://t4.ftcdn.net/jpg/03/33/23/41/360_F_333234186_rWQQpvHnOnia4l9RIYHQ3UsK5GeHAEOr.jpg)

où les lignes verticales représentent le niveau d'intensité de l'ambiance et chaque colonne représente une section du stade.

La zone autour du stade des Carabins est divisée en 8 sections, nommées A, B, C, D, E, F, G et H.

Vous devez lire le nombre de personnes présentes dans les 8 sections autour du stade,
calculer un niveau d’ambiance pour chaque section, puis afficher ces niveaux sous forme de grille verticale.

### Entrées

Votre programme doit lire **8 nombres entiers**, un par ligne, correspondant au nombre
de personnes dans les sections **A à H**, dans cet ordre.

Contraintes :
- chaque valeur doit être un entier
- chaque valeur doit être ≥ 0

En cas d’entrée invalide (non entier ou valeur négative), afficher exactement :
```
Erreur - donnees invalides.
```

### Intensité brute de chaque section

À chaque section est associé un facteur d’ambiance. Voici les valeurs que vous devez utiliser pour chaque section: 

| Section | A    | B    | C    | D    | E    | F    | G    | H    |
| ------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Facteur | 1.30 | 1.15 | 1.05 | 0.95 | 0.95 | 1.05 | 1.15 | 1.30 |

Pour chaque section, calculez l’intensité brute :
```
intensité = nombre de personnes × facteur
```

### Normalisation des intensités

Les intensités doivent être converties en niveaux de 0 à 10.

Soit maxI la plus grande intensité brute:

- Si maxI == 0, alors tous les niveaux valent 0
- Sinon :
```
niveau = int((intensite / maxI) * 10 + 0.5)
```

L’ajout de `+ 0.5` avant la conversion avec `int()` sert à arrondir la décimale à l'entier le plus proche (par exemple, 3.2 est arrondi à 3, 3.7 est arrondi à 4, 3.5 est arrondi à 4).

Le niveau final doit être compris entre 0 et 10.

**Affichage:**

Vous devez afficher une grille verticale selon les directives suivantes :
- Lignes : Les niveaux d'intensité (de 10 à 1)
- Colonnes : sections A à H
- Afficher `❚` si le niveau d'intensité de la section est ≥ niveau de la ligne
- Sinon, afficher `.`
- La première colonne affiche les niveaux d'intensité (10 à 1), suivi d'un espace et d'une ligne verticale | 
- La dernière ligne affiche les labels des sections (A à H)
- Les cellules sont séparées par un espace

Exemple de format exact : 
```
10 | ❚ ❚ . . . . ❚ ❚
 9 | ❚ ❚ . . . . ❚ ❚
 8 | ❚ ❚ ❚ . . ❚ ❚ ❚
 7 | ❚ ❚ ❚ . . ❚ ❚ ❚
 6 | ❚ ❚ ❚ ❚ ❚ ❚ ❚ ❚
 5 | ❚ ❚ ❚ ❚ ❚ ❚ ❚ ❚
 4 | ❚ ❚ ❚ ❚ ❚ ❚ ❚ ❚
 3 | ❚ ❚ ❚ ❚ ❚ ❚ ❚ ❚
 2 | ❚ ❚ ❚ ❚ ❚ ❚ ❚ ❚
 1 | ❚ ❚ ❚ ❚ ❚ ❚ ❚ ❚
     A B C D E F G H
```

## 03. Choisir le meilleur trajet vers le CEPSUM

Écrivez un programme qui compare trois options pour arriver au CEPSUM (marche, navette, métro), en incluant un temps de contrôle à l'entrée du CEPSUM pour la vérification des billets. 

**Le programme doit prendre en entrée :**
- Distance jusqu'au CEPSUM (km, float)
- Temps d'attente de la navette (minutes, float)
- Temps du trajet en métro (minutes, float)
- Temps de contrôle a l'entrée du CEPSUM (minutes, float)

**Hypothèses :**
- vitesse de marche = 5 km/h
- vitesse de navette = 18 km/h

**Calculs (en minutes) :**
- `marche = distance * 60 / 5 + controle`
- `navette = attente + distance * 60 / 18 + controle`
- `metro = metro + controle`

Pour la comparaison, vous devez arrondir chaque temps à la minute supérieure (ceil).

**En sortie, le programme doit faire les affichages suivants:**

- Si une seule option est la plus rapide:

```
Option la plus rapide : X.
```

où X est l'option la plus rapide (`marcher`, `navette` ou `metro`)

- Si 2 options sont ex-aequo et minimales :

```
Egalite : X et Y.
```
où X et Y sont les deux options les plus rapides, avec l'ordre d'affichage suivant : marcher, navette, metro

- Si 3 options sont ex-aequo :

```
Egalite : marcher, navette et metro.
```

- En cas de données invalides (valeurs négatives), afficher exactement :

```text
Erreur - donnees invalides.
```

## 04. Vérification d'une rampe d'accessibilité

Écrivez un programme qui calcule la pente (%) et l'angle (degrés) d'une rampe, puis verifie si elle respecte une pente maximale de 8%.

**Entrées :**
- Hauteur à franchir (en centimetres, float)
- Longueur horizontale (en metres, float)

**Contraintes à respecter:**
- Hauteur >= 0
- Longueur > 0

En cas de données invalides, afficher :

```text
Erreur - donnees invalides.
```

**Calculs :**
- `hauteur_m = hauteur_cm / 100`
- `pente (%) = (hauteur_m / longueur_m) * 100`
- `angle (deg) = atan(hauteur_m / longueur_m)`, converti en degrés

**Sortie**

L'affichage en sortie doit suivre le format suivant:

```text
Pente: PP.PP%
Angle: AA.AA deg
Conforme: OUI|NON
```

Si la rampe ne respecte PAS une pente maximale de 8%, affichez une 4e ligne : 

```text
Depassement: DD.DD%
```

## 05. Planification d'achat de billets

Écrivez un programme qui choisit la combinaison la moins dispendieuse pour acheter au moins `n` billets pour les événements des Carabins.

**Les options pour acheter des billets sont les suivantes:**
- Forfait de 24 billets : 66.00$
- Forfait de 12 billets : 36.00$
- Forfait de 5 billets  : 15.75$
- Billet unitaire       :  3.60$

**Rabais étudiant :**
- Si statut etudiant = 0, appliquer 12% de réduction sur les forfaits uniquement
- Les billets unitaires ne sont jamais réduits

**Objectifs :**
- Couvrir au moins `n` billets
- Minimiser le coût total
- En cas d'égalité sur le coût : choisir la solution avec le plus petit nombre de billets total (surplus minimal), puis le plus petit nombre de billets unitaires

En cas de données invalides :

```text
Erreur - donnees invalides.
```

Sinon, afficher exactement 6 lignes :

```text
Forfaits de 24 billets - A
Forfaits de 12 billets - B
Forfaits de 5 billets - C
Billets unitaires - D
Total billets - T
Prix total - PPP.PP$
```

## Fichiers du projet

- README.md : consignes et informations générales
- `exo1.py` : exercice 01
- `exo2.py` : exercice 02
- `exo3.py` : exercice 03
- `exo4.py` : exercice 04
- `exo5.py` : exercice 05
- `test.py` : script de tests automatisés

**Vous devez compléter les exercices à l'intérieur des fichiers `exo1.py` à `exo5.py`.**

**Vous pouvez exécuter le fichier `test.py` pour vérifier vos réponses.**

## Directives pour la remise

Vous devez remettre votre travail avant 23:59 le 8 février.

Votre travail doit être remis en utilisant les commandes git vues au TP0, sur votre répertoire GitHub créé avec GitHub Classroom. Nous corrigerons votre dernier commit avant la date limite. 

## Barème de correction

| Exercice                                                   | Critère       | Description                                        | Points   |
| ---------------------------------------------------------- | ------------- | -------------------------------------------------- | -------- |
| **Exercice 1 – Bilan de visionnage Carabins**              |               |                                                    | **/3.5** |
| 1.1                                                        | Entrées       | Lecture du nom et des 4 valeurs numériques         | 0.5      |
| 1.2                                                        | Validation    | Validation des données et message d’erreur exact   | 1.0      |
| 1.3                                                        | Calculs       | Calcul correct des durées football et soccer       | 0.75     |
| 1.4                                                        | Formatage     | Conversion minutes → HhMM (minutes sur 2 chiffres) | 0.75     |
| 1.5                                                        | Sortie        | Affichage exact des 4 lignes demandées             | 0.5      |
| **Exercice 2 – Ambiance autour du stade**                  |               |                                                    | **/5.0** |
| 2.1                                                        | Entrées       | Lecture et validation des 8 sections (entiers ≥ 0) | 1.0      |
| 2.2                                                        | Calculs       | Calcul des intensités brutes avec facteurs         | 0.75     |
| 2.3                                                        | Normalisation | Gestion de maxI et du cas maxI = 0                 | 0.75     |
| 2.4                                                        | Arrondi       | Arrondi half-up et bornage des niveaux (0–10)      | 1.0      |
| 2.5                                                        | Affichage     | Grille correcte (symboles, alignement, labels)     | 1.5      |
| **Exercice 3 – Choisir le meilleur trajet vers le CEPSUM** |               |                                                    | **/3.5** |
| 3.1                                                        | Entrées       | Lecture et validation des 4 entrées (floats ≥ 0)   | 1.0      |
| 3.2                                                        | Calculs       | Calcul correct des temps (marche, navette, métro)  | 1.0      |
| 3.3                                                        | Arrondi       | Application correcte du `ceil`                     | 0.5      |
| 3.4                                                        | Décision      | Comparaison correcte et gestion des égalités       | 1.0      |
| **Exercice 4 – Vérification d’une rampe d’accessibilité**  |               |                                                    | **/3.5** |
| 4.1                                                        | Entrées       | Lecture et validation des données                  | 0.75     |
| 4.2                                                        | Calculs       | Calcul correct de la pente (%)                     | 0.75     |
| 4.3                                                        | Calculs       | Calcul correct de l’angle (degrés)                 | 0.75     |
| 4.4                                                        | Sortie        | Affichage exact et dépassement si non conforme     | 1.25     |
| **Exercice 5 – Planification d’achat de billets**          |               |                                                    | **/4.5** |
| 5.1                                                        | Entrées       | Lecture et validation de `n` et du statut étudiant | 1.0      |
| 5.2                                                        | Tarification  | Application correcte des prix et réductions        | 1.0      |
| 5.3                                                        | Couverture    | Combinaison couvrant au moins `n` billets          | 1.0      |
| 5.4                                                        | Optimisation  | Prix minimal, surplus minimal, billets unitaires   | 1.0      |
| 5.5                                                        | Sortie        | Affichage exact des 6 lignes demandées             | 0.5      |
| **Total**                                                  |               |                                                    | **/20**  |
