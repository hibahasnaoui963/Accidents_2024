# Accidents_2024
Prédiction de la Gravité des Accidents de la Route (France 2024)
Présentation du Projet

Ce projet analyse les facteurs influençant la gravité des accidents corporels de la circulation en France pour l'année 2024. L'objectif est de construire un modèle de Machine Learning capable de prédire si un accident sera Grave (Tué ou Hospitalisé) ou Léger (Indemne ou Blessé léger).

Ce travail démontre ma capacité à gérer un pipeline complet de Data Science : de l'ingénierie des données à l'interprétation statistique des résultats.
Structure du Projet

Le projet est découpé en trois étapes méthodologiques :
1. Préparation des Données (01_import_preparation.ipynb)

    Fusion des tables : Croisement des fichiers "Caractéristiques" et "Usagers" via l'identifiant d'accident.

    Nettoyage : Suppression des colonnes ayant plus de 20% de valeurs manquantes pour garantir la fiabilité statistique.

    Targeting : Création de la variable cible binaire target à partir de la colonne grav.

2. Analyse Exploratoire - EDA (02_analyse_exploratoire.ipynb)

    Visualisation : Étude de l'impact du sexe, de la luminosité et du milieu (agglomération) sur la gravité.

    Validation Statistique : Utilisation du Test du χ2 d'indépendance pour confirmer les corrélations observées (p-value < 0,05).

3. Modélisation (03_modelisation.ipynb)

    Algorithme : Entraînement d'une Régression Logistique.

    Optimisation : Gestion du déséquilibre de classe via le paramètre class_weight='balanced' pour améliorer le Rappel (Recall).

    Interprétation : Calcul des Odds Ratios pour quantifier l'influence de chaque variable.

Résultats et Modélisation Mathématique

Le modèle repose sur la fonction sigmoïde pour estimer la probabilité de gravité :
P(target=1∣X)=1+e−(β0​+∑βi​Xi​)1​
Métrique de performance clé

Pour ce projet de sécurité routière, nous avons privilégié le Recall afin de minimiser les faux négatifs (accidents graves non détectés) :
Recall=TP+FNTP​
Considérations Éthiques

L'analyse des données respecte l'anonymat des usagers conformément au RGPD. Les conclusions sur le profil des usagers (comme le sexe) sont destinées à des fins de prévention ciblée et ne doivent en aucun cas servir à la stigmatisation ou à des pratiques discriminatoires.
Installation et Utilisation

    Cloner le dépôt : git clone https://github.com/hibahasnaoui963/Accidents_2024.git

    Installer les bibliothèques : pip install -r requirements.txt

    Exécuter les notebooks : Ouvrir les fichiers dans VS Code ou Jupyter Lab dans l'ordre numérique.