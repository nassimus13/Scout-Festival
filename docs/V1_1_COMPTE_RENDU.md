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

## Agent 2 — FESTIVAL MASTER

Agent 2 a été relu dans :

`prompts/02-recherche-festivals.md`

Règles validées :

- Agent 2 prépare uniquement la base neutre `FESTIVAL MASTER`.
- Agent 2 ne produit pas `MATCHING`.
- Agent 2 ne rédige pas d’emails.
- Agent 2 ne doit pas écrire d’analyse personnalisée liée à un film précis dans `FESTIVAL MASTER`.
- Les champs réservés à `MATCHING` doivent rester à `À compléter dans MATCHING` dans `FESTIVAL MASTER`.
- Les informations inconnues doivent rester `Information manquante` ou `À vérifier`.
- Les URL, emails et réseaux sociaux doivent rester en texte brut.
- La sortie cible respecte exactement les 37 colonnes `FESTIVAL MASTER`.

## Test Agent 2 — FESTIVAL MASTER

Test réalisé sur les 3 festivals actuellement présents dans le Google Sheets officiel :

1. `Festival international du court métrage de Clermont-Ferrand`
2. `Brussels Short Film Festival`
3. `Un Festival C’est Trop Court`

Anomalie détectée :

- Les colonnes personnalisées réservées à `MATCHING` contenaient encore de l’analyse film + festival dans `FESTIVAL MASTER`.

Correction appliquée dans le Drive :

Les colonnes suivantes ont été neutralisées dans `FESTIVAL MASTER` pour les 3 festivals :

- `Pourquoi compatible`
- `Angle de candidature`
- `Accesibilité`
- `Compatibilité du film`
- `Potentiel Réseau`
- `Priorité`
- `Stratégie diffusion`

Nouvelle valeur appliquée :

`À compléter dans MATCHING`

Contrôles validés après correction :

- `FESTIVAL MASTER` contient bien 37 colonnes.
- Les 3 festivals existent toujours.
- Les champs factuels et éditoriaux neutres restent présents.
- Les champs personnalisés liés au film sont maintenant réservés à `MATCHING`.
- Les champs de suivi restent conformes : `Statut = À traiter`, `Mail prêt = Non`.
- Les analyses personnalisées sont conservées dans `MATCHING` et non dans `FESTIVAL MASTER`.

Décision :

Agent 2 est validé fonctionnellement sur la structure `FESTIVAL MASTER` après correction de neutralité.

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

## Agent 5 — EMAILS CANDIDATURE

Agent 5 est formalisé dans :

`prompts/05-emails-candidature.md`

Règles validées :

- L’Agent 5 génère une ligne `EMAILS CANDIDATURE` par ligne `MATCHING`.
- L’Agent 5 doit toujours générer un email complet en brouillon, même lorsque certaines informations manquent.
- `Mail prêt = Non` tant que le contact programmation, le lien de visionnage ou le mot de passe manquent.
- `Statut email = Brouillon` par défaut.
- `Contact programmation = À vérifier` si le contact n’est pas connu.
- Ne jamais inventer de contact, de sélection, de prix ou de projection.

## Test Agent 5 — FILM-004

Test réalisé à partir des 3 lignes `MATCHING` réelles :

- `MATCH-FILM-004-001`
- `MATCH-FILM-004-002`
- `MATCH-FILM-004-003`

Résultat vérifié dans `EMAILS CANDIDATURE` :

- `EMAIL-FILM-004-001`
- `EMAIL-FILM-004-002`
- `EMAIL-FILM-004-003`

Contrôles validés :

- Les 3 emails existent.
- Chaque email est lié au bon ID Matching.
- Chaque email est lié au bon ID Film.
- Les objets mails sont remplis.
- Les emails personnalisés sont complets.
- `Mail prêt = Non`.
- `Statut email = Brouillon`.
- Les contacts programmation ne sont pas inventés.
- Les notes email signalent les éléments à compléter.
- Aucun prix, sélection ou projection n’est inventé.

Décision :

Agent 5 est validé fonctionnellement sur le test réel `FILM-004`.

## Point de vigilance

Les informations du film doivent rester cohérentes entre `MON FILM`, `MATCHING` et `EMAILS CANDIDATURE`.

Une attention particulière doit être portée aux champs :

- Sous-titres disponibles
- Lien de visionnage
- Mot de passe
- Contact programmation
- Champs réservés à `MATCHING` dans `FESTIVAL MASTER`

## Prochaine étape

Poursuivre la V1.1 avec le contrôle de l’Agent 3 — reformatage Google Sheets — afin de garantir que les sorties Agents 2, 4 et 5 restent copiables, structurées et compatibles avec les onglets cibles.
