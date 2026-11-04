# Fiche de cadrage : Ordonnances incomplètes en pharmacie

> Remplir chaque rubrique en une à trois phrases. Les rubriques marquées (obligatoire) sont vérifiées par `pytest`.

## Besoin en une phrase (obligatoire)

Détecter automatiquement les ordonnances incomplètes afin de faciliter leur vérification avant la délivrance des médicaments.

## Utilisateur final (obligatoire)

Les pharmaciens chargés du contrôle des ordonnances et de la sécurité des patients.

## Approche retenue (obligatoire)

Cocher une seule case :

- [x] Règles métier
- [ ] Machine learning
- [ ] RAG
- [ ] Modèle génératif seul

## Justification (obligatoire, citer au moins deux critères de la grille : (a) données étiquetées, (b) vérifiabilité, (c) coût par requête, (d) conséquence d'une erreur)

(b) Les champs obligatoires sont définis par des règles vérifiables. (d) Une ordonnance incomplète validée à tort peut présenter un risque important pour le patient.

## Données nécessaires et leur origine (obligatoire)

Les champs des ordonnances et les exigences réglementaires applicables, provenant du logiciel de pharmacie et des référentiels officiels.

## Métrique de succès et seuil d'acceptation (obligatoire)

Atteindre un rappel d'au moins 99 % des ordonnances incomplètes sur un jeu de test représentatif.

## Conséquence d'une erreur et validation humaine prévue (obligatoire)

Une anomalie non détectée peut présenter un risque pour le patient. Chaque ordonnance reste soumise à la vérification du pharmacien.

## Risques éthiques ou de confidentialité (obligatoire)

Les ordonnances contiennent des données de santé sensibles qui doivent être protégées et anonymisées pour les tests.

## Approche écartée et pourquoi (facultatif)

Le modèle génératif seul est écarté car il ne garantit pas un contrôle systématique des champs obligatoires.

