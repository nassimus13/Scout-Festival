# 📋 5 Tickets initiaux - Festival Scout IA

> Copiez-collez ces tickets directement dans GitHub pour démarrer le projet.

---

## ⚠️ Phase actuelle : V1 manuelle assistée par IA

**Important :** Nous sommes en **V1 manuelle assistée par IA**. Le pipeline doit d'abord être validé manuellement avec prompts solides et Google Sheet maîtrisés. L'automatisation Make/n8n/API viendra plus tard, après validation complète du workflow.

---

## 📝 Comment les utiliser :

1. Allez sur : `https://github.com/nassimus13/Scout-Festival/issues`
2. Cliquez **"New issue"**
3. **Option A :** Choisissez le template `festival_scout_task` et remplissez avec les infos ci-dessous
4. **Option B :** Copiez-collez directement le contenu
5. Assignez les labels recommandés
6. Cliquez **"Submit new issue"**

---

# 🎯 ISSUE #1 : Définir le workflow GitHub du projet Festival Scout IA

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
- ✅ Règle centrale documentée : "Un ticket ne passe à Ready que si clarifié"
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

# 🎯 ISSUE #2 : Créer le prompt maître de recherche festivals

## 🎯 Objectif

Créer un prompt IA robuste qui, à partir des caractéristiques de **MON FILM**, retourne une liste de **10 à 20 festivals fortement compatibles et vérifiés**.

**Format de sortie :** TSV compatible Google Sheets + version Markdown lisible.

## 🧠 Contexte

C'est le premier maillon de la chaîne. Si ce prompt n'est pas bon, tout le reste s'écroule. Le prompt doit :
- Prendre en entrée : titre, genre, durée, public cible, synopsis, ADN du film
- Retourner : **SEULEMENT** 10-20 festivals réellement compatibles (pas d'invention)
- Vérifier les informations via sources officielles
- Respecter les priorités du projet

## 📦 Sortie attendue

- ✅ Prompt rédigé et documenté en Markdown
- ✅ Testé sur **MON FILM** + 2 variantes de recherche (ex: "angle auteur" vs "angle commercial")
- ✅ Résultats testés et partagés (Google Sheet ou fichier TSV)
- ✅ Format de sortie clairement défini : **TSV avec colonnes** = Nom | Site | Deadline | Catégories acceptées | Frais | Priorité
- ✅ Limites et améliorations documentées
- ✅ **Règles de vérification documentées**

## ✅ Critères d'acceptation

- [ ] Prompt écrit et fonctionnel dans ChatGPT ou Claude
- [ ] **Testé sur MON FILM** avec au moins 2 variantes de recherche
- [ ] **Retourne 10-20 festivals** (ni plus, ni moins)
- [ ] **AUCUNE donnée inventée :**
  - ❌ Jamais inventer deadline
  - ❌ Jamais inventer frais
  - ❌ Jamais inventer contact
  - ❌ Jamais inventer durée max
  - ❌ Jamais inventer condition de première
- [ ] **Informations vérifiées via sources officielles :**
  - Site officiel du festival
  - Règlement officiel
  - FilmFreeway ou Festhome
  - Shortfilmdepot (pour courts métrages)
- [ ] Format TSV lisible et importable dans Google Sheets
- [ ] Documentation avec exemples d'input/output
- [ ] **Priorités respectées :**
  - Festivals courts métrages
  - Cinéma auteur
  - Festivals méditerranéens, arabes, africains
  - Festivals francophones
  - Drame familial, thriller social / polar intime
- [ ] Cas manquants clairement marqués "à vérifier"

## ❓ Questions avant validation

- [ ] **Q1 :** Quel modèle IA utilise-t-on en priorité ? (ChatGPT 4, Claude, autre ?)
  - **Réponse :** À détailler
- [ ] **Q2 :** Faut-il inclure les festivals en ligne ou juste physiques ?
  - **Réponse :** À détailler
- [ ] **Q3 :** Comment vérifier les infos si le site festival n'existe plus ou est mort ?
  - **Réponse :** À détailler

## 🔗 Dépendances

- Aucune (peut être fait en parallèle)

## 🏷️ Labels recommandés

- `Prompts IA`
- `Recherche festivals`
- `High`
- `Prompt`
- `À valider`

## 📌 Statut initial

**To refine** → clarifier les questions → **Ready** → test → **Ready for test**

---

# 🎯 ISSUE #3 : Créer le prompt d'analyse détaillée d'un festival

## 🎯 Objectif

Créer un prompt IA capable d'analyser les informations d'un festival (page web, règlement, bloc de texte copié-collé) et produire une **fiche d'analyse enrichie compatible avec FESTIVALS MASTER**.

## 🧠 Contexte

Une fois qu'on a une liste de festivals, il faut les "analyser" pour comprendre vraiment si c'est pertinent pour MON FILM. Ce prompt fonctionne avec du copier-coller de règlements (pas d'API Vision obligatoire).

## 📦 Sortie attendue

- ✅ Prompt documenté pour analyser les infos festivals
- ✅ Testé sur 3 pages de festivals différentes (structures différentes)
- ✅ Sortie structurée et compatible FESTIVALS MASTER
- ✅ Champs enrichis avec analyse stratégique
- ✅ Documentation avec exemple

## ✅ Critères d'acceptation

- [ ] Prompt fonctionne avec texte copié-collé (SANS API Vision obligatoire)
- [ ] Extrait les infos clés : deadline, catégories, frais, conditions
- [ ] **Ajoute une analyse de compatibilité pour MON FILM :**
  - ADN Festival : quelle est la personnalité du festival ?
  - Pourquoi compatible ? (avec MON FILM spécifiquement)
  - Pourquoi risqué ? (les raisons de ne pas sélectionner)
  - Angle de candidature : quelle facette de MON FILM mettre en avant ?
  - Accessibilité : quelle est la vraie sélectivité ?
  - Potentiel réseau : peut-on faire des contacts ?
  - Priorité : ranking de 1-5
  - Stratégie diffusion : si on est sélectionné, ça nous sert à quoi ?
  - Action suivante : que faire concrètement ?
- [ ] **Règle stricte :** Si l'info manque → écrire **"à vérifier"** (jamais inventer)
- [ ] Format clair et lisible (Markdown ou tableau)
- [ ] Cas d'erreur gérés (page vide, infos manquantes, texte pourri)
- [ ] Testé sur 3 festivals

## ❓ Questions avant validation

- [ ] **Q1 :** Doit-on analyser AUSSI les avis des créateurs sur le festival ? (networking, réputation)
  - **Réponse :** À détailler
- [ ] **Q2 :** Comment gérer les festivals qui n'ont pas de règlement en ligne ?
  - **Réponse :** À détailler

## 🔗 Dépendances

- Issue #2 (besoin d'avoir une liste de festivals d'abord)

## 🏷️ Labels recommandés

- `Prompts IA`
- `Analyse festivals`
- `High`
- `Prompt`
- `À valider`

## 📌 Statut initial

**To refine** → **Ready** → test → **Ready for test**

---

# 🎯 ISSUE #4 : Créer le prompt de préparation candidature béton

## 🎯 Objectif

Créer un prompt IA qui prépare une **candidature personnalisée et solide** pour MON FILM selon le festival cible.

Le prompt doit adapter l'angle candidature selon le type de festival et produire une **checklist des assets** avant envoi.

## 🧠 Contexte

Une fois qu'on sait À QUEL FESTIVAL candidater, faut préparer une candidature béton. Ce prompt doit :
- Générer un angle candidature adapté au festival
- Produire un texte de candidature personnalisé (pas du copier-coller)
- Générer un mail de candidature prêt à envoyer
- Produire une checklist des assets nécessaires

C'est du templating intelligent + génération IA pour la V1 manuelle.

## 📦 Sortie attendue

- ✅ Prompt rédigé et testé
- ✅ Testé sur **MON FILM × 3 festivals cibles** (types différents : auteur, méditerranéen, social)
- ✅ Pour chaque test : angle candidature + texte personnalisé + mail + checklist
- ✅ Format Markdown structuré
- ✅ Prêt à être copié-collé dans un email ou un formulaire

## ✅ Critères d'acceptation

- [ ] Prompt prend en entrée : infos MON FILM + infos festival cible + fiche analyse
- [ ] **Génère l'angle candidature adapté :**
  - Pour festival auteur : mets en avant la démarche créative
  - Pour festival méditerranéen/arabe : angle culturel/géographique
  - Pour festival social/thriller : angle message social / pertinence actuelle
  - Pour festival francophone : références/connections françaises
- [ ] **Génère un texte de candidature :**
  - Personnalisé au festival (pas générique)
  - Longueur adaptée (200-500 mots selon le festival)
  - Tone adapté (formel, créatif, etc.)
- [ ] **Génère un mail de candidature :**
  - Sujet attractif et personnalisé
  - Corps de mail personnalisé
  - Signature propre
- [ ] **Génère une checklist des assets :**
  - Affiche (format/taille requis)
  - Trailer/teaser (durée max)
  - Photos de tournage (nombre/format)
  - Bande sonore (si awards spéciaux)
  - Sous-titres (langues demandées)
  - DCP ou lien privé Vimeo
  - Certificat international (si nécessaire)
- [ ] **Testé sur 3 combinaisons :**
  - MON FILM × Festival auteur
  - MON FILM × Festival méditerranéen/arabe
  - MON FILM × Festival social/thriller
- [ ] Résultats documentés et révisables
- [ ] Format prêt pour envoi

## ❓ Questions avant validation

- [ ] **Q1 :** Doit-on faire des templates distincts par type de festival ou un seul prompt intelligent ?
  - **Réponse :** À détailler
- [ ] **Q2 :** À quel point personnaliser le mail ? Combien de recherche sur le festival ?
  - **Réponse :** À détailler

## 🔗 Dépendances

- Issue #2 et #3 (besoin des infos film + infos festival d'abord)

## 🏷️ Labels recommandés

- `Prompts IA`
- `Candidature béton`
- `High`
- `Prompt`
- `À valider`

## 📌 Statut initial

**To refine** → **Ready** → test → **Ready for test**

---

# 🎯 ISSUE #5 : Valider et affiner le template standard des tickets GitHub

## 🎯 Objectif

Tester et affiner le template d'issue `.github/ISSUE_TEMPLATE/festival_scout_task.md` pour que tous les **futurs tickets du pipeline** soient structurés et compréhensibles.

## 🧠 Contexte

On a créé un template mais faut le tester "en live" avec des vrais tickets. L'objectif est de s'assurer que :
- La structure est claire et utile
- Chaque section aide à la clarification
- Les critères d'acceptation sont bien définis
- Le template fonctionne pour tous les types de tickets (prompts, documentation, etc.)

## 📦 Sortie attendue

- ✅ Template testé avec au moins 2 tickets réels (issues #2, #3 ou #4)
- ✅ Feedback: sections inutiles supprimées, sections manquantes ajoutées
- ✅ Exemples dans le template mieux précisés
- ✅ Template final validé et documenté
- ✅ Guide d'utilisation du template rédigé

## ✅ Critères d'acceptation

- [ ] 2 issues créées avec le template (ex: issues #2 et #3)
- [ ] Template testable par n'importe quel débutant
- [ ] Sections inutiles identifiées et supprimées
- [ ] Sections manquantes ajoutées si besoin
- [ ] Exemples clairs et réalistes
- [ ] Document "Comment utiliser le template" rédigé
- [ ] Template final commité

## ❓ Questions avant validation

- [ ] **Q1 :** Faut-il d'autres sections ? (Timeline ? Budget ? Ressources ?)
  - **Réponse :** À détailler
- [ ] **Q2 :** Les critères d'acceptation doivent-ils toujours être en checkbox ?
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

## 📋 Résumé des 5 issues

| # | Titre | Catégorie | Priorité | État initial |
|---|-------|-----------|----------|--------------|
| 1 | Définir le workflow GitHub | Documentation | High | To refine |
| 2 | Créer prompt recherche festivals | Prompts IA | High | To refine |
| 3 | Créer prompt analyse festival | Prompts IA | High | To refine |
| 4 | Créer prompt candidature béton | Prompts IA | High | To refine |
| 5 | Valider le template d'issue | Documentation | Medium | To refine |

---

## 🚀 Prochaine étape

Créer ces 5 issues et les mettre dans la colonne **To refine** du Project Kanban.

---

**Phase :** V1 manuelle assistée par IA  
**Prochaine étape après validation :** Automatisation Make/n8n après validation complète  
**Créé pour :** Festival Scout IA (Projet perso)  
**Dernière mise à jour :** 2026-06-06
