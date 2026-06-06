# 📚 Tutoriel : Créer un GitHub Project Kanban de A à Z

*Écrit pour les débutants sur GitHub - Parfait pour votre premier projet !*

---

## 📋 Table des matières
1. [Comprendre les concepts](#concepts)
2. [Créer un GitHub Project](#créer-project)
3. [Configurer les colonnes](#colonnes)
4. [Créer des Issues](#issues)
5. [Ajouter des Labels](#labels)
6. [Utiliser votre Kanban](#utiliser)
7. [Astuces & Bonnes pratiques](#astuces)

---

## 🎯 Concepts de base {#concepts}

### Qu'est-ce qu'un GitHub Project ?
- Un **tableau de bord visuel** pour organiser votre travail
- Fonctionne comme un **tableau Kanban** (colonnes + cartes)
- **Lié directement à vos issues** (tickets de travail)

### Les 3 éléments clés :
1. **Project** = Le tableau global
2. **Issues** = Les tickets/tâches individuelles
3. **Labels** = Les étiquettes pour catégoriser

### Notre workflow :
```
To refine → Ready → To Do → In Progress → Blocked
                                    ↓
                          Ready for test → Waiting for test → Ready for prod → Livrable
```

---

## 🚀 Créer un GitHub Project {#créer-project}

### Étape 1 : Accéder aux Projects
1. Allez sur votre repo : `https://github.com/VOTRE_USERNAME/VOTRE_REPO`
2. Cliquez sur l'onglet **"Projects"** (en haut)
3. Cliquez sur le bouton **"New project"** (vert)

### Étape 2 : Configurer le Project
1. **Name** : Entrez un nom (ex: "34 Trucs - Backlog")
2. **Description** : Optionnel (ex: "Suivi du projet Scout Festival")
3. **Project template** : Choisissez **"Table"** ou **"Kanban"**
   - → Recommandé : **"Kanban"** (c'est plus visuel)
4. Cliquez **"Create project"**

### Étape 3 : Vous arrivez sur le board vide
✅ Bravo ! Votre project est créé

---

## 📊 Configurer les colonnes {#colonnes}

### Ajouter des colonnes de statut

Les colonnes Kanban représentent les étapes du workflow.

#### Votre structure (9 colonnes) :

1. **To refine** (Bleu)
   - Tickets qui ont besoin d'être clarifiés

2. **Ready** (Vert)
   - Tickets clairs et prêts à commencer

3. **To Do** (Gris)
   - Tickets à faire, non démarrés

4. **In Progress** (Orange)
   - Actuellement en cours de travail

5. **Blocked** (Rouge)
   - Bloqués, en attente d'autre chose

6. **Ready for test** (Jaune)
   - Développement fini, prêt pour test

7. **Waiting for test** (Violet)
   - En cours de test

8. **Ready for prod** (Vert clair)
   - Testé et approuvé, prêt pour production

9. **Livrable** (Gris foncé)
   - Livré en production ✅

### Comment ajouter une colonne :

1. Cliquez le **"+"** à droite du dernier colonne
2. Entrez le nom de la colonne
3. GitHub propose automatiquement de lier des **Status** (optionnel pour commencer)
4. Cliquez **"Create column"**

**⚠️ Astuce** : Vous pouvez réorganiser les colonnes en les glissant/déposant !

---

## 🎫 Créer des Issues (tickets) {#issues}

Les Issues sont les **tâches individuelles** qui remplissent votre Kanban.

### Créer une Issue directement du repo

#### Méthode 1 : Via l'onglet "Issues"
1. Allez dans l'onglet **"Issues"**
2. Cliquez **"New issue"**
3. Remplissez :
   - **Title** : Titre court et clair
   - **Description** : Détails de la tâche
   - **Labels** : Sélectionnez des catégories
   - **Assignee** : Qui la fait (vous pour l'instant)
4. Cliquez **"Submit new issue"**

#### Méthode 2 : Directement depuis le Project
1. Allez dans votre **Project**
2. Cliquez **"+ Add item"** dans une colonne
3. Cherchez une issue existante OU créez-en une nouvelle
4. L'issue apparaît dans le Kanban

### Exemple de bonne Issue :

```
Title: "Mettre en place la page d'accueil"

Description:
## Objectif
Créer la page d'accueil du site Scout Festival

## Détails
- Header avec logo
- Menu de navigation
- Section hero avec image
- Footer avec liens réseaux

## Critères d'acceptation
- [ ] Page responsive (mobile + desktop)
- [ ] Tous les liens fonctionnent
- [ ] Images optimisées
- [ ] Validation HTML/CSS

## Dépendances
Aucune pour le moment

## Effort estimé
3 jours
```

---

## 🏷️ Ajouter des Labels {#labels}

Les **Labels** catégorisent vos issues. C'est super utile pour filtrer et organiser.

### Labels recommandés pour Scout-Festival :

**Par type :**
- `Feature` = Nouvelle fonctionnalité
- `Bug` = Problème à corriger
- `Documentation` = Docs/README
- `Infra` = Infrastructure/DevOps

**Par priorité :**
- `Urgent` = À faire immédiatement
- `High` = Important
- `Medium` = Normal
- `Low` = Peut attendre

**Par catégorie projet :**
- `Frontend` = Interface utilisateur
- `Backend` = Serveur/API
- `Database` = Base de données
- `Design` = Design/UX

**Autres :**
- `Help wanted` = Cherche aide
- `Good first issue` = Parfait pour débuter
- `Question` = Besoin de clarification

### Créer un Label :

1. Allez dans l'onglet **"Issues"**
2. Sur la gauche, cliquez **"Labels"**
3. Cliquez **"New label"**
4. Remplissez :
   - **Label name** : ex: "Frontend"
   - **Description** : ex: "Travail sur l'interface"
   - **Color** : Choisissez une couleur
5. Cliquez **"Create label"**

### Appliquer un Label à une Issue :

1. Ouvrez l'issue
2. Sur la droite, cliquez **"Labels"**
3. Sélectionnez les labels à ajouter
4. Fermez le menu (auto-save)

---

## 💻 Utiliser votre Kanban {#utiliser}

### Workflow quotidien :

#### 1️⃣ Commencer une tâche
- Prenez une issue dans **"To Do"**
- Glissez-la vers **"In Progress"**
- ✏️ Commentez : "Je commence" (optionnel mais utile)

#### 2️⃣ Pendant le développement
- Travaillez normalement
- Faites des commits réguliers
- Mentionnez l'issue dans vos commits : `git commit -m "Fix navbar - #42"`
  - (42 = le numéro de l'issue)

#### 3️⃣ Quand c'est prêt pour test
- Glissez l'issue vers **"Ready for test"**
- Écrivez un commentaire avec les infos de test

#### 4️⃣ Test & Feedback
- L'issue passe à **"Waiting for test"**
- Si OK : vers **"Ready for prod"**
- Si problème : retour à **"In Progress"**

#### 5️⃣ En production
- Glissez vers **"Livrable"** ✅

### Filtrer et chercher :

**Dans le Kanban :**
- Cliquez la **loupe** en haut
- Cherchez : `is:open`, `label:Frontend`, `assignee:YOUR_USERNAME`
- Résultats en temps réel

---

## 🎨 Astuces & Bonnes pratiques {#astuces}

### ✅ Bonnes pratiques

| ✅ Faire | ❌ Ne pas faire |
|---------|-----------------|
| Issues courtes et focalisées | Issues géantes avec 10 tâches |
| Titres clairs et actifs | Titres vagues ("Truc à faire") |
| Description détaillée | Pas de contexte du tout |
| 1 label min par issue | Pas de labels |
| Assignez-vous (ou quelqu'un) | Issues orphelines |
| Fermez les issues quand c'est fait | Les laisser traîner ouvertes |

### 🚀 Astuces avancées

1. **Automatisation** :
   - GitHub peut auto-déplacer les issues en fonction des événements
   - Exemple : "Issue fermée → passe à Livrable"
   - C'est dans les "Workflows" du Project

2. **Templates d'Issues** :
   - Créez des modèles pour les bugs, features, etc.
   - Les équipes aiment ça !

3. **Mentions & Liens** :
   - Écrivez `#42` pour lier une autre issue
   - Écrivez `@username` pour mentionner quelqu'un
   - Les issues sont liées automatiquement

4. **Vue personnalisée** :
   - Cliquez **"View"** pour changer la présentation
   - Triez par priorité, assigné, etc.

5. **Milestones** (optionnel) :
   - Créez des "phases" : Sprint 1, v1.0, etc.
   - Assignez les issues aux milestones
   - Suivez la progression

---

## 📝 Exemple complet : Créer votre premier ticket

### Scénario : Vous voulez créer la page d'accueil

**Étape 1 : Créer l'Issue**
```
Title: Design & Créer la page d'accueil (index.html)

Description:
## 🎯 Objectif
Développer la page d'accueil (landing page) du site Scout Festival

## 📋 Détails de la tâche
- Créer la structure HTML de base
- Ajouter le header avec logo et navigation
- Créer une section hero avec image de fond
- Ajouter une section "À propos" avec texte
- Intégrer les réseaux sociaux dans le footer
- Rendre responsive (mobile & desktop)

## ✅ Critères d'acceptation
- [ ] Page s'affiche correctement sur tous les écrans
- [ ] Tous les liens sont fonctionnels
- [ ] Images sont optimisées (< 100KB)
- [ ] Code est commenté et propre
- [ ] Pas d'erreurs console

## 🔗 Ressources
- Design : [Lien Figma]
- Inspiration : [Lien site similaire]

## 🏷️ Labels à ajouter
- Frontend
- High priority

## ⏱️ Temps estimé
2 jours
```

**Étape 2 : Ajouter au Kanban**
1. Dans le Project, cliquez **"+ Add item"**
2. Cherchez et sélectionnez l'issue
3. Elle s'ajoute par défaut à la première colonne
4. Glissez-la dans **"Ready"** (ou "To Do" selon votre envie)

**Étape 3 : La faire**
1. Glissez-la vers **"In Progress"**
2. Créez une branche : `git checkout -b feature/homepage`
3. Travaillez normalement
4. Commitez : `git commit -m "Add homepage structure - #1"`
5. Push et faites une PR
6. Une fois mergée : déplacez vers **"Ready for test"**

---

## 🎓 Résumé en une page

```
🔷 PROJECT = Vue globale du travail
    ↓
🎯 COLONNES = Étapes du workflow (9 dans votre cas)
    ↓
🎫 ISSUES = Tickets individuels (détail du travail)
    ↓
🏷️ LABELS = Catégories pour organiser
    ↓
💪 GLISSEZ/DÉPOSEZ = Mouvez les issues entre colonnes
```

---

## ❓ FAQ

**Q: Combien d'issues par projet ?**
A: Autant que vous en avez ! 100, 1000... GitHub gère bien.

**Q: Dois-je fermer une issue quand elle est "Livrable" ?**
A: Oui ! C'est la convention. Fermée = Terminer.

**Q: Puis-je avoir plusieurs Projects sur le même repo ?**
A: Oui ! Un pour le backlog, un pour le sprint actuel, etc.

**Q: Comment collaborer avec d'autres ?**
A: Assignez les issues à des collègues. Ils recevront une notification.

**Q: Mon Kanban est vide, c'est normal ?**
A: Oui ! Vous devez créer les issues d'abord.

---

## 🎉 Bravo !

Vous savez maintenant comment :
- ✅ Créer un GitHub Project Kanban
- ✅ Organiser votre travail en colonnes
- ✅ Créer des issues et des labels
- ✅ Utiliser le workflow quotidien
- ✅ Collaborer efficacement

**Prochaines étapes :**
1. Créez 3-5 issues pour démarrer
2. Mettez-les dans les bonnes colonnes
3. Commencez à les travailler
4. Ajustez votre workflow selon vos besoins

Bon développement ! 🚀

---

*Dernière mise à jour : 2026-06-06*
*Créé pour : nassimus13/Scout-Festival*
