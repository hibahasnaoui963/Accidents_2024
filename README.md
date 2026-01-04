# Prédiction de la gravité des accidents de la route (France 2024)

## Présentation du projet
Ce projet d'analyse de données traite de la sécurité routière en France pour l'année 2024. L'objectif principal est de construire un modèle de **Machine Learning** capable de prédire la gravité d'un accident (Léger vs Grave) à partir de caractéristiques environnementales et socio-démographiques.

##  Source des Données
Les données utilisées proviennent de la plateforme **Open Data du gouvernement français**. Elles concernent les accidents corporels de la circulation routière pour l'année 2024.

Ce dépôt illustre une démarche complète de Data Science, de la fusion de données brutes à l'interprétation de modèles statistiques.

---

##  Structure du projet (Pipeline)
Le projet est découpé en trois notebooks structurés selon la méthodologie CRISP-DM :

* **Lien du jeu de données :** [Bases de données annuelles des accidents corporels (2024)](https://www.data.gouv.fr/fr/datasets/bases-de-donnees-annuelles-des-accidents-corporels-de-la-circulation-routiere-annee-2024/)
* **Fichiers nécessaires :** * `caracteristiques-2024.csv`
    * `usagers-2024.csv`

> **Note :** Une fois téléchargés, ces fichiers doivent être placés dans le dossier `data/` à la racine du projet.
### 1. Préparation des données [`01_import_prep.ipynb`]
* **Fusion des tables** : Croisement des fichiers "Caractéristiques" et "Usagers".
* **Nettoyage** : Traitement des valeurs manquantes (seuil de suppression à 20%) pour assurer la qualité du dataset.
* **Targeting** : Création de la variable cible binaire `target` (0: Léger, 1: Grave) à partir de la variable `grav`.

### 2. Analyse exploratoire - EDA [`02_analyse_exploratoire.ipynb`]
* **Visualisation** : Analyse de l'impact du sexe et de la luminosité sur le taux de gravité.
* **Validation Statistique** : Réalisation d'un **Test du $\chi^2$ d'indépendance** confirmant un lien significatif entre le genre et la gravité (p-value < 0,05).

### 3. Modélisation [`03_modelisation.ipynb`]
* **Algorithme** : Utilisation de la **Régression logistique**.
* **Optimisation** : Correction du déséquilibre de classe via le paramètre `class_weight='balanced'`.
* **Interprétation** : Analyse des **Odds Ratios** pour identifier les facteurs de risque dominants.

---

##  Modélisation et résultats

### Approche mathématique
Le modèle utilise la fonction sigmoïde pour estimer la probabilité de gravité :
$$P(target=1|X) = \frac{1}{1 + e^{-(\beta_0 + \sum \beta_i X_i)}}$$

### Performance du modèle
La priorité a été donnée au **Rappel (Recall)** afin de détecter un maximum d'accidents graves, réduisant ainsi les faux négatifs critiques dans un contexte de sécurité publique.

$$Recall = \frac{TP}{TP + FN}$$

---

##  Éthique et confidentialité
* Les données utilisées sont issues de l'Open Data gouvernemental et sont totalement anonymisées.
* L'analyse statistique (notamment sur le sexe) est menée à des fins de **prévention routière** et ne doit pas servir à des pratiques discriminatoires.

---

##  Installation
1. Cloner le projet :
   ```bash
   git clone [https://github.com/hibahasnaoui963/Accidents_2024.git](https://github.com/hibahasnaoui963/Accidents_2024.git)