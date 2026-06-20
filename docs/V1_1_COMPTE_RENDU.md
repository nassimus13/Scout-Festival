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

## Agent 4 — MATCHING

Agent 4 a été repris et formalisé en V1.1 dans :

`prompts/04-matching-festival.md`

Règles validées :

- Une ligne MATCHING = une combinaison unique `ID Film + Festival`.
- La sortie doit respecter exactement les 40 colonnes de l’onglet `MATCHING`.
- L’ID Matching suit le format `MATCH-[ID Film]-001`, `MATCH-[ID Film]-002`, etc. si aucun ID n’est fourni.
- Les données factuelles festival sont reprises depuis `FESTIVAL MASTER` sans modification.
- Les champs d’analyse Agent 4 sont complétés uniquement dans `MATCHING`.
- La colonne `Accesibilité` conserve volontairement cette orthographe pour compatibilité Google Sheets.
- Les champs de suivi candidature gardent les valeurs par défaut si aucune information réelle n’est fournie.
- `Mail prêt` reste `Non` à ce stade.
- `Statut` reste `À traiter` à ce stade.
- Agent 4 ne rédige jamais les emails.
- Agent 4 ne fait jamais de nouvelle recherche festival.

## Test Agent 4 — FILM-004

Test réalisé sur les données réelles du Google Sheets officiel.

Donnée film vérifiée :

- `ID Film` : `FILM-004`
- `Titre du film` : `Derniers jours d'été`
- `Type de film` : `Court métrage`
- `Durée` : `18 min`
- `Genre principal` : `Drame`
- `Sous-titres disponibles` : `Anglais`

Festivals testés depuis `FESTIVAL MASTER` :

1. `Festival international du court métrage de Clermont-Ferrand`
2. `Brussels Short Film Festival`
3. `Un Festival C’est Trop Court`

Résultat vérifié dans `MATCHING` :

- `MATCH-FILM-004-001`
- `MATCH-FILM-004-002`
- `MATCH-FILM-004-003`

Contrôles validés :

- Les 3 lignes MATCHING existent.
- Les 3 lignes sont liées à `FILM-004`.
- Les 3 lignes reprennent le titre `Derniers jours d'été`.
- Les 3 lignes respectent les 40 colonnes MATCHING.
- Les champs de suivi sont conformes : `Statut = À traiter`, `Mail prêt = Non`.
- Les données factuelles festival sont reprises depuis `FESTIVAL MASTER`.
- Agent 4 ne produit pas d’email.

Décision :

Agent 4 est validé fonctionnellement sur le test réel `FILM-004`.

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

Tester Agent 5 à partir des lignes `MATCHING` réelles du film `FILM-004`, puis vérifier que la sortie Agent 5 alimente correctement `EMAILS CANDIDATURE`.
