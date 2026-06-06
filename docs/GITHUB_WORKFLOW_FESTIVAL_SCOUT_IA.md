# 🎬 Workflow GitHub - Festival Scout IA

**Objectif :** Organiser le pipeline de recherche et préparation de candidatures festivals pour films.

---

## 📊 Pipeline du projet

```
🎬 MON FILM
    ↓
🔍 Recherche festivals compatibles
    ↓
📋 Extraction des informations festival
    ↓
🧮 Analyse compatibilité film ↔ festival
    ↓
⭐ Priorisation stratégique
    ↓
📝 Préparation candidature béton
    ↓
📧 Composition emails festival
    ↓
📤 Envoi & suivi candidatures
    ↓
🔔 Relances & suivi réponses
    ↓
📊 Dashboard suivi candidatures
```

---

## 🎯 Les 9 colonnes Kanban

Chaque ticket progresse dans ce workflow :

### 1️⃣ **To refine** (Bleu clair)
- **Sens :** Idée floue ou besoin à clarifier
- **Exemple :** "Chercher festivals de science-fiction"
- **Qui :** Celui qui crée le ticket
- **Question clé :** C'est clair ou ça manque de détails ?
- **Action :** Clarifier le besoin avant de passer à Ready

### 2️⃣ **Ready** (Vert)
- **Sens :** Ticket clair et prêt à être travaillé
- **Exemple :** "Créer un prompt IA qui filtre les festivals avec shortlist 20"
- **Qui :** N'importe qui peut le prendre
- **Question clé :** Est-ce que je comprends exactement ce qui est attendu ?
- **Action :** Assigner à quelqu'un qui peut le faire

### 3️⃣ **To Do** (Gris)
- **Sens :** Tâche validée et assignée, mais pas commencée
- **Exemple :** "Tester le prompt sur 5 films"
- **Qui :** La personne assignée
- **Question clé :** Je suis assigné, mais je n'ai pas encore démarré
- **Action :** Commencer le travail → passer à In Progress

### 4️⃣ **In Progress** (Orange)
- **Sens :** Tâche en cours de travail
- **Exemple :** "Je développe la logique de scraping"
- **Qui :** La personne assignée
- **Question clé :** C'est en cours, ça avance ?
- **Action :** Continuer ou signaler un blocage

### 5️⃣ **Blocked** (Rouge)
- **Sens :** Tâche bloquée par une dépendance ou une question
- **Exemple :** "En attente de l'API Google Sheets" ou "Besoin d'une décision sur le format de sortie"
- **Qui :** Celui qui explique le blocage
- **Question clé :** Pourquoi c'est bloqué ? Qui peut débloquer ?
- **Action :** Commenter le ticket avec la raison, attendre la réponse

### 6️⃣ **Ready for test** (Jaune)
- **Sens :** Travail terminé, prêt à être testé/validé
- **Exemple :** "Prompt IA créé et documenté, prêt pour test sur 10 films"
- **Qui :** Celui qui a fait le travail
- **Question clé :** Le travail est-il réellement prêt ?
- **Action :** Demander la validation à quelqu'un d'autre

### 7️⃣ **Waiting for test** (Violet)
- **Sens :** En attente de validation/test utilisateur
- **Exemple :** "Le prompt est en test, on attend les résultats"
- **Qui :** Le testeur/validateur
- **Question clé :** C'est bon ou ça faut des changements ?
- **Action :** Rendre un verdict (approuvé ou correction)

### 8️⃣ **Ready for prod** (Vert clair)
- **Sens :** Validé et approuvé, prêt à intégrer en production
- **Exemple :** "Le prompt a passé les tests, on peut l'utiliser en live"
- **Qui :** Celui qui fait l'intégration
- **Question clé :** Tout est prêt pour utiliser ?
- **Action :** Intégrer dans l'outil / mettre en place / déployer

### 9️⃣ **Livrable** (Gris foncé)
- **Sens :** Terminé et utilisable en production ✅
- **Exemple :** "Prompt intégré dans Make/n8n et testé en live"
- **Qui :** La personne qui a intégré
- **Question clé :** C'est fini ?
- **Action :** Fermer l'issue (GitHub auto-archive)

---

## 🚨 RÈGLE CENTRALE

> **❌ Un ticket ne doit PAS passer à "Ready" tant que les questions de clarification ne sont pas traitées.**

**Exemples de tickets à laisser en "To refine" :**
- "Créer un prompt" (lequel ? pour quoi faire ?)
- "Faire du scraping" (de quel site ? quel format de sortie ?)
- "Analyser les résultats" (comment ? selon quels critères ?)

**Quand passer à "Ready" :**
- ✅ Le contexte est clair
- ✅ Les critères d'acceptation sont définis
- ✅ Les dépendances sont identifiées
- ✅ Les questions en suspens ont des réponses

---

## 📋 Comment utiliser le workflow

### Pour créer un ticket :
1. Créez une issue avec le template `festival_scout_task.md`
2. Placez-la en **To refine** par défaut
3. Posez les questions qui vous bloquent en commentaire
4. Quand tout est clair → passez à **Ready**

### Pour prendre un ticket :
1. Allez dans la colonne **Ready**
2. Sélectionnez un ticket clair
3. Assignez-vous
4. Glissez-le à **To Do**
5. Commencez le travail → **In Progress**

### Quand vous finissez :
1. Vérifiez les critères d'acceptation
2. Documentez ce que vous avez fait (commentaire + code si applicable)
3. Glissez à **Ready for test**
4. Demandez une review/validation en commentaire

### Lors d'une validation :
1. Testez selon les critères d'acceptation
2. Approuvez → **Ready for prod** ou Correction → **In Progress**
3. Une fois approuvé et intégré → **Livrable**
4. Fermez l'issue

---

## 🏷️ Labels utilisés

Voir le fichier `LABELS_FESTIVAL_SCOUT_IA.md` pour la liste complète.

**Résumé rapide :**
- **Catégorie :** Pipeline, Recherche festivals, Prompts IA, Candidature béton, Emails, Dashboard
- **Priorité :** Urgent, High, Medium, Low
- **Type :** Décision, À clarifier, Prompt, Make/n8n, Test

---

## 💡 Bonnes pratiques

| ✅ À faire | ❌ À éviter |
|---------|----------|
| Tickets courts et focalisés | Issues géantes ("Faire le projet") |
| Titres actifs et clairs | Titres vagues ("Truc à faire") |
| Critères d'acceptation définis | Pas de définition de "fini" |
| Labels appliqués | Issues sans contexte |
| Assigné à quelqu'un | Tickets orphelins |
| Déplacé régulièrement | Qui traîne 3 mois en In Progress |

---

## 📞 Questions ? Blocages ?

- **Ticket peu clair ?** → Reste en **To refine**, pose des questions
- **T'es bloqué ?** → Passe à **Blocked**, explique pourquoi
- **C'est fait mais ça attend ?** → **Ready for test**, demande une review
- **C'est approuvé mais pas utilisé ?** → **Ready for prod**, fais l'intégration

---

**Créé pour :** Festival Scout IA  
**Dernière mise à jour :** 2026-06-06  
**Adapté pour :** Débutants sur GitHub
