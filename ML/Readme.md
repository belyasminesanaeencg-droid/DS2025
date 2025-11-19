# Compte rendu – Analyse des données (Wine Quality)

## 1. Objectif de l’analyse
L’objectif est d'explorer et comprendre le dataset *Wine Quality* avant d’entraîner un modèle de classification.  
L’analyse permet de :
- examiner la structure des données,
- étudier la variable cible,
- identifier les relations entre les variables,
- préparer la transformation en classification binaire.

---

## 2. Exploration du dataset

### 2.1 Chargement et résumé
Le dataset contient :
- **4898 échantillons**
- **11 variables explicatives**
- **1 variable cible : `quality`**

Le résumé (`df.info()`) montre :
- aucune valeur manquante,
- uniquement des types numériques,
- un dataset propre.

### 2.2 Aperçu des premières lignes
L’affichage de `df.head()` confirme :
- la cohérence des colonnes,
- des valeurs réalistes,
- l’absence d’anomalies visibles.

---

## 3. Analyse de la variable cible

### 3.1 Distribution des qualités
L’analyse via `value_counts()` montre :
- une majorité de vins notés **5, 6 ou 7**,
- très peu d’échantillons extrêmes,
- une distribution **déséquilibrée**.

### 3.2 Transformation en binaire
Règle appliquée :
- `0` → mauvaise qualité (quality ≤ 5)
- `1` → bonne qualité (quality ≥ 6)

Cette transformation :
- simplifie le problème,
- équilibre partiellement les classes,
- facilite l’utilisation d’un modèle comme k-NN.

---

## 4. Analyse statistique des variables

### 4.1 Statistiques descriptives
À partir des boxplots :
- distributions souvent **asymétriques**,
- valeurs aberrantes sur certaines variables (sucre résiduel, alcool),
- échelles très différentes entre variables  
  → nécessité de **normaliser** pour k-NN.

### 4.2 Matrice de corrélation
La heatmap révèle :
- forte corrélation entre :
  - densité ↔ sucre résiduel  
  - densité ↔ chlorures
- faible corrélation directe entre variables et qualité

Implications :
- présence de redondance dans les données,
- la qualité n’est pas linéairement prédite par une seule variable,
- un modèle basé sur distances ou non linéaire est pertinent.

---

## 5. Conclusion de l’analyse
- Le dataset est propre et prêt pour la modélisation.
- Les variables ont des échelles différentes → normalisation obligatoire.
- Certaines variables sont fortement corrélées → redondance dans les mesures.
- La cible est déséquilibrée → justification du passage à une classification binaire.
- Les observations motivent l'utilisation :
  - d’un découpage stratifié,
  - de la normalisation,
  - d’un modèle comme k-NN pour la suite.

---

