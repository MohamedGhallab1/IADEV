# TP2 — Entraîner, évaluer et accepter un modèle de sentiment

**Module :** Développement et déploiement d'applications intelligentes  
**Semaine :** 2  
**Projet :** sentiment-app

## 1. Mesures obtenues

Le modèle utilise une représentation TF-IDF et une régression logistique pour classer les avis en deux catégories : positive et negative.

| Indicateur | Démonstration | Allociné |
|---|---:|---:|
| Nombre total d'avis | 290 | 20 000 |
| Avis d'entraînement | 232 | 16 000 |
| Avis de test | 58 | 4 000 |
| Taille du vocabulaire | 316 | 149 529 |
| F1 macro | 0,879 | 0,920 |
| Rappel négatif | 0,931 | 0,911 |
| Erreurs | 7 | 318 |

Le modèle entraîné sur Allociné obtient un meilleur F1 macro que celui entraîné sur les données de démonstration.

## 2. Analyse des erreurs

### Démonstration

Le modèle commet 7 erreurs sur 58 avis : 2 avis négatifs classés positifs et 5 avis positifs classés négatifs.

Les trois erreurs affichées concernent des commentaires contenant des sentiments contradictoires :

1. « Taille trop petite et retour payant au déballage, sauf que ensuite produit conforme… » : positif prédit négatif.
2. « Commande jamais reçue et remboursement en attente au début, sauf que ensuite je recommande… » : positif prédit négatif.
3. « Service impeccable et livraison en avance sur le papier, sauf que ensuite produit cassé… » : négatif prédit positif.

Ces erreurs s'expliquent notamment par la difficulté du modèle à interpréter le retournement du sentiment. TF-IDF représente les mots et les groupes de deux mots, mais ne comprend pas toujours le sens global de la phrase.

### Allociné

Le modèle commet 318 erreurs sur 4 000 avis. Il classe 181 avis négatifs comme positifs et 137 avis positifs comme négatifs.

Les trois erreurs affichées concernent des critiques parlant notamment de grammaire cinématographique, de Yasmina Reza et de Clint Eastwood.

Ces exemples montrent que le modèle peut également se tromper sur des formulations complexes appartenant à son propre domaine d'entraînement.

## 3. Décision d'acceptation

Deux seuils sont examinés :

- Seuil technique : F1 macro supérieur ou égal à 0,85.
- Seuil métier indiqué dans l'énoncé du TP2 : rappel de la classe négative supérieur ou égal à 0,90.

Le modèle de démonstration respecte ces deux seuils : F1 macro de 0,879 et rappel négatif de 0,931.

Le modèle Allociné les respecte également : F1 macro de 0,920 et rappel négatif de 0,911.

**Décision :** les deux modèles sont acceptés pour les objectifs expérimentaux du TP2. Toutefois, ces résultats ne suffisent pas pour autoriser directement une utilisation en production sur des avis e-commerce. Une évaluation sur des avis commerciaux représentatifs reste nécessaire.

## 4. Limites et décalage de domaine

Nous avons testé deux avis commerciaux avec le modèle entraîné sur Allociné.

**Premier avis :** « Livraison rapide, produit conforme, tres satisfait »

- Prédiction obtenue : negative.
- Confiance affichée : 50 %.
- Sentiment attendu : positif.
- Conclusion : prédiction incorrecte, avec une forte incertitude.

**Deuxième avis :** « Produit casse et service injoignable, a fuir »

- Prédiction obtenue : negative.
- Confiance affichée : 75 %.
- Sentiment attendu : négatif.
- Conclusion : prédiction correcte.

Ces observations mettent en évidence un décalage de domaine (*domain shift*). Le modèle a été entraîné sur des critiques cinématographiques, alors que les textes testés concernent des achats et des livraisons.

Un score élevé sur les critiques de films ne garantit pas une performance équivalente sur les avis commerciaux.

Pour améliorer l'application, nous proposons d'utiliser un jeu de données représentatif du commerce électronique, d'analyser davantage les avis mitigés et de prévoir une vérification humaine lorsque le modèle est incertain.

## Conclusion

Le TP2 nous a permis de comprendre le processus d'entraînement, l'évaluation par des métriques adaptées, l'analyse des erreurs et la distinction entre acceptation technique et validation métier.

Les fichiers `models/sentiment.joblib` et `models/metrics.json` ont été générés. Seul le fichier de métriques doit être versionné dans Git.