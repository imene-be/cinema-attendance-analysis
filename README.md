# Analyse de la fréquentation des cinémas français

Quel est l'impact du nombre d'écrans et de fauteuils sur la fréquentation d'un cinéma ? Ce projet d'analyse de données explore la question sur les cinémas français (2018 à 2022) et construit un modèle prédictif des entrées annuelles.

## Objectifs

- Nettoyer et explorer les données des cinémas
- Comparer les régions selon les entrées par fauteuil
- Mesurer la corrélation entre infrastructures (écrans, fauteuils) et fréquentation
- Entraîner un modèle de régression pour estimer les entrées annuelles
- Formuler des recommandations pour une commune donnée

## Démarche

1. **Nettoyage** : chargement du CSV avec pandas, remplacement des valeurs manquantes d'`entrees_annuelles` par la moyenne de la région, suppression des valeurs aberrantes (zéro écran ou zéro fauteuil).
2. **Analyse** : entrées moyennes par fauteuil et par région, graphiques des meilleures et des moins bonnes régions.
3. **Corrélations** : relation entre écrans et entrées, puis entre fauteuils et entrées, avec nuages de points et droite de régression.
4. **Modélisation** : régression linéaire avec scikit-learn. Variables explicatives : `ecrans`, `fauteuils`, `population_commune`. Variable cible : `entrees_annuelles`. Évaluation par le R² et l'erreur absolue moyenne.
5. **Recommandations** : simulation sur une commune fictive pour comparer plusieurs scénarios d'équipement.

## Résultats

- Corrélation écrans et entrées : **0,89**
- Corrélation fauteuils et entrées : **0,86**
- Modèle prédictif : **R² de 0,92**, erreur absolue moyenne d'environ 25 000 entrées

Le nombre d'écrans pèse donc légèrement plus sur la fréquentation que le nombre de fauteuils.

## Données

Le fichier source n'est pas inclus dans le dépôt. Il est attendu dans `data/cinemas.csv`, séparateur `;`, avec les colonnes suivantes : `region`, `commune`, `population_commune`, `ecrans`, `fauteuils`, `annee`, `entrees_annuelles`, `label_art_et_essai`.

## Structure

```
src/
  nettoyage.py      chargement et nettoyage des données
  analyse.py        calculs statistiques et graphiques
  modelisation.py   entraînement et évaluation du modèle
  utilitaires.py    préparation des données
  main.py           enchaînement de l'analyse
test_*.py           tests du nettoyage, de l'analyse, de la modélisation et du processus complet
requirements.txt    dépendances Python
```

## Installation

```bash
git clone https://github.com/imene-be/cinema-attendance-analysis.git
cd cinema-attendance-analysis
python3 -m venv venv
source venv/bin/activate
pip install pandas matplotlib scikit-learn seaborn
```

`tkinter` est déjà fourni avec Python : il ne s'installe pas avec pip.

## Technologies

Python, pandas, matplotlib, seaborn, scikit-learn

---

Réalisé par [Imène Bentifraouine](https://imenebe.fr).
