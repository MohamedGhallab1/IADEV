# Fiche de cadrage : Priorisation des avis négatifs

> Remplir chaque rubrique en une à trois phrases. Les rubriques marquées (obligatoire) sont vérifiées par `pytest`.

## Besoin en une phrase (obligatoire)

Classer automatiquement les avis négatifs selon leur niveau d'urgence pour améliorer le traitement des réclamations.

## Utilisateur final (obligatoire)

Les agents du service client et les responsables de la satisfaction client.

## Approche retenue (obligatoire)

Cocher une seule case :

- [ ] Règles métier
- [x] Machine learning
- [ ] RAG
- [ ] Modèle génératif seul

## Justification (obligatoire, citer au moins deux critères de la grille : (a) données étiquetées, (b) vérifiabilité, (c) coût par requête, (d) conséquence d'une erreur)

(a) Les avis peuvent être étiquetés selon leur priorité pour entraîner un classifieur. (c) Le machine learning permet de traiter de nombreux avis à faible coût.

## Données nécessaires et leur origine (obligatoire)

Les avis clients historiques et leurs niveaux de priorité attribués par le service client.

## Métrique de succès et seuil d'acceptation (obligatoire)

Atteindre un F1 macro d'au moins 0,85 et un rappel de 0,95 pour les avis urgents.

## Conséquence d'une erreur et validation humaine prévue (obligatoire)

Une réclamation urgente mal classée peut être traitée trop tard. Les agents pourront corriger les priorités proposées.

## Risques éthiques ou de confidentialité (obligatoire)

Les avis peuvent contenir des informations personnelles qui doivent être anonymisées avant l'entraînement.

## Approche écartée et pourquoi (facultatif)

Le RAG est écarté car le besoin principal est de classer des avis et non de rechercher des informations documentaires.

