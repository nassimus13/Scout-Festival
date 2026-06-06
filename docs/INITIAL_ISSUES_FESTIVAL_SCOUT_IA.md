# 📋 5 Tickets initiaux - Festival Scout IA

> Copiez-collez ces tickets directement dans GitHub pour démarrer le projet.

---

## 📝 Comment les utiliser :

1. Allez sur : `https://github.com/nassimus13/Scout-Festival/issues`
2. Cliquez **"New issue"**
3. **Option A :** Choisissez le template `festival_scout_task` et remplissez avec les infos ci-dessous
4. **Option B :** Copiez-collez directement le contenu
5. Assignez les labels recommandés
6. Cliquez **"Submit new issue"**

---

# 🎫 ISSUE #1 : Définir le workflow GitHub du projet Festival Scout IA

## 🎯 Objectif

Définir clairement et documenter le workflow GitHub qui va piloter le projet Festival Scout IA.

## 🧠 Contexte

Sans un workflow clair, les tickets vont traîner partout, les rôles seront flous et ça va être le chaos. Il faut une seule source de vérité sur :
- Comment un ticket progresse
- Quand est-ce qu'un ticket est "Ready"
- Comment on teste avant de livrer
- Qui valide quoi

## 📦 Sortie attendue

- ✅ Document `GITHUB_WORKFLOW_FESTIVAL_SCOUT_IA.md` complété
- ✅ 9 colonnes Kanban clairement définies avec exemples
- ✅ Règle centrale documentée : "Un ticket ne passe à Ready que si clarificé"
- ✅ Guide d'utilisation du workflow (comment créer, prendre, valider un ticket)

## ✅ Critères d'acceptation

- [ ] Document rédigé et lisible pour un débutant
- [ ] Les 9 colonnes ont une description, un exemple et des actions claires
- [ ] La règle "To refine → Ready" est bien expliquée
- [ ] Les labels recommandés sont listés
- [ ] Bonnes pratiques incluses (faire/ne pas faire)
- [ ] Document commité dans `docs/`

## ❓ Questions avant validation

- [ ] **Q1 :** Le workflow correspond-il vraiment au pipeline du projet ?
  - **Réponse :** À remplir par le créateur du ticket
- [ ] **Q2 :** Faut-il adapter les noms des colonnes ou c'est bon ?
  - **Réponse :** À remplir

## 🔗 Dépendances

- Aucune

## 🏷️ Labels recommandés

- `Documentation`
- `Pipeline`
- `High`
- `À valider`

## 📌 Statut initial

**To refine** → puis passer à **Ready** une fois approuvé

---

# 🎫 ISSUE #2 : Créer le prompt maître de recherche festivals

## 🎯 Objectif

Créer un prompt IA robuste qui prend en entrée les caractéristiques d'un film et retourne une liste de festivals potentiellement compatibles (format : CSV ou JSON avec nom + site + deadline).

## 🧠 Contexte

C'est le premier maillon de la chaîne. Si ce prompt n'est pas bon, tout le reste s'écroule. Besoin d'un prompt qui :
- Prend en entrée : titre, genre, durée, public cible, synopsis court
- Retourne : liste de festivals (min 20, max 100) avec URLs accessibles
- Prioritaire sur la complétude plutôt que la perfection

## 📦 Sortie attendue

- ✅ Prompt rédigé et documenté en Markdown
- ✅ Testé manuellement sur au moins 3 films différents (cinéma + court-métrage)
- ✅ Résultats testés et partagés (Google Doc ou screenshot)
- ✅ Format de sortie clairement défini
- ✅ Limites et améliorations potentielles documentées

## ✅ Critères d'acceptation

- [ ] Prompt écrit et fonctionnel dans ChatGPT ou Claude
- [ ] Testé sur 3 films (genres différents)
- [ ] Retourne entre 15 et 50 festivals par film
- [ ] Les URLs sont valides (au moins 80%)
- [ ] Format de sortie cohérent
- [ ] Documentation avec exemples d'input/output
- [ ] Limites expliquées (festivals régionaux, saisonniers, etc.)

## ❓ Questions avant validation

- [ ] **Q1 :** Quel modèle IA utilise-t-on en priorité ? (ChatGPT 4, Claude, autre ?)
  - **Réponse :** À détailler
- [ ] **Q2 :** Faut-il inclure les festivals en ligne ou juste physiques ?
  - **Réponse :** À détailler
- [ ] **Q3 :** Quel est le délai acceptable d'actualité des festivals (2023 ? 2024 ?) ?
  - **Réponse :** À détailler

## 🔗 Dépendances

- Aucune (peut être fait en parallèle)

## 🏷️ Labels recommandés

- `Prompts IA`
- `Pipeline`
- `High`
- `Prompt`
- `À valider`

## 📌 Statut initial

**To refine** → clarifier les questions → **Ready** → test → **Ready for test**

---

# 🎫 ISSUE #3 : Créer le prompt d'analyse détaillée d'un festival

## 🎯 Objectif

Créer un prompt IA qui prend l'URL d'un festival et extrait intelligemment :
- Dates limite candidature
- Catégories acceptées (types de films)
- Frais de candidature
- Format accepté (DCP, ProRes, MP4, etc.)
- Sélection (blind ou avec crédits ?)
- Palmarès / prix
- Contact principal

## 🧠 Contexte

Une fois qu'on a une liste de festivals, il faut les "analyser" pour savoir s'il vaut la peine de postuler. Ce prompt utilise la vision d'IA pour lire la page et extraire les infos pertinentes (plus rapide que du scraping web classique).

## 📦 Sortie attendue

- ✅ Prompt documenté pour l'API Vision (OpenAI ou Claude)
- ✅ Testé sur au moins 3 pages de festivals différentes
- ✅ Format de sortie en JSON structuré
- ✅ Cas d'erreur gérés (page pas chargée, infos manquantes, etc.)
- ✅ Documentation avec exemple

## ✅ Critères d'acceptation

- [ ] Prompt utilise Vision API correctement
- [ ] Teste sur 3 festivals (structure différente)
- [ ] JSON output bien structuré et validé
- [ ] Extraction réussie à > 80%
- [ ] Cas d'erreur documentés
- [ ] Format cohérent avec le reste du pipeline
- [ ] Commented in code

## ❓ Questions avant validation

- [ ] **Q1 :** Quel provider Vision utilise-t-on ? (OpenAI, Claude, Google ?)
  - **Réponse :** À détailler
- [ ] **Q2 :** Comment gérer les festivals sans page web (dead link ou trop basiques) ?
  - **Réponse :** À détailler

## 🔗 Dépendances

- Peut être fait en parallèle avec Issue #2
- Utile une fois qu'on a une liste de festivals

## 🏷️ Labels recommandés

- `Prompts IA`
- `Pipeline`
- `High`
- `Prompt`
- `À valider`

## 📌 Statut initial

**To refine** → **Ready** → test → **Ready for test**

---

# 🎫 ISSUE #4 : Créer le prompt de préparation candidature béton

## 🎯 Objectif

Créer un prompt IA qui, à partir des infos de festival + characteristics du film, génère une première version du texte de candidature (synopsis court, arguments de vente, format spécifique au festival).

## 🧠 Contexte

Une fois qu'on sait à quel festival candidater, faut préparer la candidature. Ce prompt génère une première version de la "candidature béton" qu'on peut ensuite affiner manuellement. C'est du templating + génération IA.

## 📦 Sortie attendue

- ✅ Prompt rédigé et testé
- ✅ Testé sur 2 films × 2 festivals (4 combinaisons)
- ✅ Génère du texte adapté au festival (pas du copier-coller)
- ✅ Format Markdown structuré
- ✅ Inclut une checklist de révision manuelle

## ✅ Critères d'acceptation

- [ ] Prompt prend en entrée : infos film + infos festival
- [ ] Génère texte cohérent et spécifique au festival
- [ ] Longueur adaptée (200-500 mots selon le festival)
- [ ] Incluable dans un email ou un formulaire
- [ ] Testé sur 4 combinaisons film/festival
- [ ] Structuré en sections claires (synopsi + arguments + format)
- [ ] Checklist de révision fournie

## ❓ Questions avant validation

- [ ] **Q1 :** Faut-il personnaliser par genre de festival ou générique ?
  - **Réponse :** À détailler
- [ ] **Q2 :** Tone : formel, créatif, ou équilibre ?
  - **Réponse :** À détailler

## 🔗 Dépendances

- Issue #2 et #3 (utile d'avoir les infos film + festival d'abord)

## 🏷️ Labels recommandés

- `Prompts IA`
- `Candidature béton`
- `High`
- `Prompt`
- `À valider`

## 📌 Statut initial

**To refine** → **Ready** → test → **Ready for test**

---

# 🎫 ISSUE #5 : Créer le template standard des tickets GitHub

## 🎯 Objectif

Valider et affiner le template d'issue `.github/ISSUE_TEMPLATE/festival_scout_task.md` pour que tous les tickets créés soient structurés et compréhensibles.

## 🧠 Contexte

On a créé un template mais faut le tester "en live" avec des vrais tickets. L'objectif est de s'assurer que :
- La structure est claire
- Chaque section a du sens
- Les sections aident à la clarification
- Les critères d'acceptation sont bien définis

## 📦 Sortie attendue

- ✅ Template testé avec au moins 2 tickets réels
- ✅ Feedback: sections inutiles supprimées, sections manquantes ajoutées
- ✅ Exemples dans le template mieux précisés
- ✅ Template final validé et documenté
- ✅ Guide d'utilisation du template rédigé

## ✅ Critères d'acceptation

- [ ] 2 issues créées avec le template
- [ ] Template testable par n'importe quel débutant
- [ ] Sections inutiles identifiées et supprimées
- [ ] Sections manquantes ajoutées si besoin
- [ ] Exemples clairs et réalistes
- [ ] Document "Comment utiliser le template" rédigé
- [ ] Template final commité

## ❓ Questions avant validation

- [ ] **Q1 :** Faut-il d'autres sections ? (Timeline ? Budget ? Ressources ?)
  - **Réponse :** À détailler
- [ ] **Q2 :** Les critères d'acceptation doivent-ils être toujours en checkbox ?
  - **Réponse :** À détailler

## 🔗 Dépendances

- Issue #1 (besoin du workflow compris)

## 🏷️ Labels recommandés

- `Documentation`
- `Pipeline`
- `Medium`
- `À valider`

## 📌 Statut initial

**To refine** → **Ready** → test avec 2 tickets → **Ready for test**

---

## 📌 Résumé des 5 issues

| # | Titre | Catégorie | Priorité | État initial |
|---|-------|-----------|----------|---------------|
| 1 | Définir le workflow GitHub | Documentation | High | To refine |
| 2 | Créer prompt recherche festivals | Prompts IA | High | To refine |
| 3 | Créer prompt analyse festival | Prompts IA | High | To refine |
| 4 | Créer prompt candidature béton | Prompts IA | High | To refine |
| 5 | Valider le template d'issue | Documentation | Medium | To refine |

---

**Prochaine étape :** Créer ces 5 issues et les mettre dans la colonne **To refine** du Project Kanban.
