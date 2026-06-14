# JSON Schemas V1 — Festival Scout IA

## Objectif

Ce document définit le format JSON attendu pour les futures automatisations Make/n8n du projet Festival Scout IA.

Le format JSON servira à écrire automatiquement les résultats des agents IA dans les bons onglets Google Sheets.

## Règle générale

Le format manuel avec séparateur `|` reste utilisé pour les tests humains dans Google Sheets.

Le format JSON sera utilisé plus tard pour l’automatisation Make/n8n.

## Structure commune JSON

Chaque agent devra produire une réponse JSON avec la structure suivante :

```json
{
  "schema_version": "FSIA_JSON_V1",
  "agent": "AGENT_X",
  "target_sheet": "NOM_DE_L_ONGLET",
  "rows": [],
  "warnings": [],
  "errors": []
}
```

## Signification des champs

### schema_version

Version du schéma JSON utilisé.

Valeur V1 :

```text
FSIA_JSON_V1
```

### agent

Nom de l’agent qui produit la sortie.

Valeurs prévues :

```text
AGENT_1
AGENT_2
AGENT_3
AGENT_4
AGENT_5
```

### target_sheet

Nom exact de l’onglet Google Sheets cible.

Valeurs prévues :

```text
MON FILM
FESTIVAL MASTER
MATCHING
EMAILS CANDIDATURE
```

### rows

Liste des lignes à écrire dans Google Sheets.

Règle :

```text
1 objet dans rows = 1 ligne Google Sheets
```

Les clés présentes dans chaque objet doivent correspondre exactement aux noms des colonnes de l’onglet cible.

### warnings

Liste des alertes non bloquantes.

Exemples :

```text
Contact programmation manquant
Deadline à confirmer
Données festival à vérifier
```

### errors

Liste des erreurs bloquantes.

Exemples :

```text
ID Film manquant
target_sheet inconnu
nombre de colonnes incompatible
```

## Mapping agents vers onglets

### Agent 1

```text
Agent : AGENT_1
Onglet cible : MON FILM
Objectif : produire une ou plusieurs lignes film
```

### Agent 2

```text
Agent : AGENT_2
Onglet cible : FESTIVAL MASTER
Objectif : produire une ou plusieurs lignes festival
```

### Agent 3

```text
Agent : AGENT_3
Onglet cible : FESTIVAL MASTER
Objectif : reformater des festivals vers FESTIVAL MASTER
```

### Agent 4

```text
Agent : AGENT_4
Onglet cible : MATCHING
Objectif : produire les résultats personnalisés film + festival
```

### Agent 5

```text
Agent : AGENT_5
Onglet cible : EMAILS CANDIDATURE
Objectif : produire des brouillons d’emails à partir de MATCHING
```

## Règle importante

Les noms de clés dans `rows` doivent correspondre exactement aux colonnes Google Sheets.

Exemples :

```text
ID Film
Titre du film
Festival
Contact programmation
Résultat final
```

Ne pas renommer les colonnes.
Ne pas traduire les colonnes.
Ne pas abréger les colonnes.

## Statut

Version V1 documentaire.

Cette documentation prépare la future automatisation Make/n8n, mais ne crée pas encore d’automatisation.
