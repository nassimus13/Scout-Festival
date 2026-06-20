# Compte rendu V1.1 — Festival Scout IA

## Date

Reprise après validation V1.

## Statut général

La V1 est considérée comme terminée.

La V1.1 vise à fiabiliser le pipeline complet après l’arrivée d’un film dans l’onglet MON FILM.

## État vérifié

- Le projet utilise le fichier Google Sheets officiel `Festival Scout AI DATABASE`.
- Les onglets de travail sont :
  - `MON FILM`
  - `FESTIVAL MASTER`
  - `MATCHING`
  - `EMAILS CANDIDATURE`
- Les anciens onglets de test sont conservés en archive.

## Pipeline cible V1.1

1. Un film est ajouté dans `MON FILM`.
2. Des festivals compatibles sont préparés dans `FESTIVAL MASTER`.
3. Les lignes de matching sont générées dans `MATCHING`.
4. Les emails de candidature sont générés dans `EMAILS CANDIDATURE`.

## Règle Agent 5 validée

L’Agent 5 doit toujours générer un email complet en brouillon, même lorsque certaines informations manquent.

Règles de sortie :

- `Mail prêt = Non` tant que le contact programmation, le lien de visionnage ou le mot de passe manquent.
- `Statut email = Brouillon` par défaut.
- `Contact programmation = À vérifier` si le contact n’est pas connu.
- Ne jamais inventer de contact, de sélection, de prix ou de projection.

## Point de vigilance

Les informations du film doivent rester cohérentes entre `MON FILM`, `MATCHING` et `EMAILS CANDIDATURE`.

Une attention particulière doit être portée aux champs :

- Sous-titres disponibles
- Lien de visionnage
- Mot de passe
- Contact programmation

## Prochaine étape

Formaliser et tester Agent 4 — MATCHING, puis vérifier que la sortie Agent 4 alimente correctement Agent 5.
