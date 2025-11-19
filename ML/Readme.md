Compte rendu – TP : Introduction à la classification (Wine Quality)
🎯 Objectif

L’objectif de ce TP est d'apprendre un modèle prédictif permettant de déterminer la qualité d’un vin blanc (bonne ou mauvaise) à partir de caractéristiques physico-chimiques.
Le dataset provient de l'UCI Machine Learning Repository (Wine Quality).

1. 📊 Analyse des données
1.1 Chargement et résumé du dataset

Le jeu de données est chargé depuis l’URL fournie, puis résumé via pandas.
On obtient :

Nombre d’échantillons : 4898

Nombre de variables d’entrée : 11

Variable cible : quality

1.2 Variables d’entrée (X) et sortie (Y)

X : ensemble des caractéristiques physico-chimiques

Y : qualité du vin (score 0–10)

Répartition des qualités : affichée via value_counts().

1.3 Transformation en classification binaire

Une nouvelle variable cible est créée :

mauvaise qualité (0) si qualité ≤ 5

bonne qualité (1) sinon

La distribution des deux classes est rééquilibrée.

1.4 Analyse statistique

Une analyse descriptive est réalisée :

Boîtes à moustaches → distribution, valeurs extrêmes

Matrice de corrélation → redondance entre certaines variables (par ex. densité ↔ sucre résiduel)

2. 🤖 Classification
2.1 Séparation du dataset

Les données sont scindées en trois ensembles :

Entraînement (Da)

Validation (Dv)

Test (Dt)

Avec stratification sur les classes pour conserver les proportions.
Pourquoi ?

éviter un déséquilibre dans les classes

assurer une bonne représentativité

améliorer la généralisation

2.2 Méthode des k plus proches voisins (k-NN)
2.2.1 Première expérimentation : k = 3

Entraînement sur Da

Prédiction sur Dv

Calcul de l’erreur :

error rate
=
1
−
accuracy
error rate=1−accuracy
2.2.2 Étude des performances selon k

Pour plusieurs valeurs de k (1 à 40) :

Calcul de l’erreur sur :

entraînement → détecte le sur-apprentissage

validation → choix du meilleur compromis

Observation attendue :

k faible → fort sur-apprentissage

k trop grand → sur-lissage, perte de précision

2.2.3 Choix optimal de k

Le meilleur k est celui minimisant l'erreur de validation.

𝑘
∗
=
arg
⁡
min
⁡
𝑘
(
error
𝑣
𝑎
𝑙
)
k
∗
=arg
k
min
	​

(error
val
	​

)
2.2.4 Performance sur l’ensemble test

On évalue l’erreur finale avec le modèle utilisant 
𝑘
∗
k
∗
.
Discussion : performance cohérente ou non, écart entre validation et test.

2.3 Normalisation des données
2.3.1 Pourquoi normaliser ?

k-NN est sensible :

aux différences d'échelle entre variables
→ une variable à grande variance domine la distance euclidienne.

Le code applique :

sc = StandardScaler(with_mean=True, with_std=True)
sc = sc.fit(Xa)
Xa_n = sc.transform(Xa)
Xv_n = sc.transform(Xv)


Remarque :
La normalisation est apprise sur Da uniquement, ce qui évite une fuite d’information.
→ C’est la bonne pratique.

2.3.2 Répétition des expériences

Les performances sont recalculées avec données normalisées.

Résultat attendu :

amélioration significative des performances

meilleure stabilité pour la recherche de k

réduction du sur-apprentissage

2.3.3 Comment rendre les modèles moins sensibles au découpage des données ?

utiliser la validation croisée (k-fold)

répéter plusieurs splits aléatoires

augmenter les données si possible

✔ Conclusion

Ce TP a permis de :

manipuler un dataset réel et analyser ses caractéristiques

transformer un problème multi-classe en binaire

mettre en œuvre le classifieur k-NN

comprendre l’impact crucial :

du choix de k

de la normalisation

du découpage stratifié des données

Le modèle k-NN, malgré sa simplicité, fournit de bons résultats si les données sont correctement normalisées et que le choix de k est guidé par la validation.
