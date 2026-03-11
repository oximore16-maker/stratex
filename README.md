# STRATEX v4.1 🌉 — Le Framework Hybride BMAD × APEX
### Strategic + Execution | La méthode qui combine le meilleur des deux mondes

![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)
![Version](https://img.shields.io/badge/Version-4.1-green.svg)
![Status: Beta](https://img.shields.io/badge/Status-Beta-orange.svg)
![Claude Code](https://img.shields.io/badge/Claude-Code-purple.svg)

---

> **Principe fondateur :**  
> BMAD est le **cerveau stratégique** — il sait *quoi* construire, *pourquoi*, et *pour qui*.  
> Apex est le **moteur d'exécution** — il sait *comment* construire, session par session, sans jamais exploser la fenêtre de contexte.  
> STRATEX est le **câble qui les relie** — le pont, les règles de routage, et la mémoire partagée.

---

## Table des matières

1. [Les trois fondations de STRATEX](#1-les-trois-fondations)
2. [Le problème que STRATEX résout](#2-le-problème)
3. [Architecture globale](#3-architecture)
4. [Installation](#4-installation)
5. [Les 7 agents spécialisés](#5-les-7-agents-spécialisés)
6. [La couche BRIDGE — le cœur de STRATEX](#6-bridge)
7. [Le protocole de routage à 3 niveaux](#7-routage)
8. [CLAUDE.md master template](#8-claude-md)
9. [Les commandes bridge](#9-commandes)
10. [Les hooks d'automatisation](#10-hooks)
11. [Workflow complet de A à Z](#11-workflow)
12. [Résumé des commandes](#12-référence)
13. [Projets inspirants](#13-inspirants)

---

## 1. Les trois fondations de STRATEX

Avant de comprendre STRATEX, il faut connaître les trois méthodes sur lesquelles il est construit. Si tu les connais déjà, tu peux passer directement à la section 2.

---

### Claude Code — l'outil de base

**Claude Code** est un assistant IA d'Anthropic qui travaille directement dans ton terminal, sur ton ordinateur. Contrairement à ChatGPT ou à Claude.ai qu'on utilise dans un navigateur, Claude Code lit tes fichiers, écrit du code, exécute des commandes, et interagit avec ton projet en temps réel.

En résumé : c'est un développeur IA qui s'installe sur ton ordi et travaille avec toi dans tes fichiers.

**Le problème avec Claude Code seul :** quand un projet grossit, Claude Code se perd. Il essaie de tout faire dans un seul contexte surchargé — un peu comme si tu demandais à quelqu'un de retenir 500 pages de notes dans sa tête en même temps. Résultat : il oublie des choses, fait des erreurs, dérive de l'objectif initial.

C'est exactement le problème que BMAD, Apex et AIBlueprint ont chacun cherché à résoudre — à leur façon.

---

### BMAD — le chef de projet IA

**BMAD** (qui signifie "Be My Agile Developer", soit en français "Sois mon développeur agile") est une méthode créée par Nick Baumann. Elle divise le travail de développement en **rôles spécialisés**, exactement comme dans une vraie équipe de développement.

**Les rôles BMAD en français :**

| Nom technique | Ce que c'est en français | Ce qu'il fait |
|---|---|---|
| Analyst | Analyste produit | Comprend le besoin, étudie le marché, clarifie ce qu'on veut construire |
| PM (Product Manager) | Chef de produit | Rédige le document de vision du produit (ce qu'on construit, pourquoi, pour qui) |
| Architect | Architecte technique | Décide comment le produit sera construit techniquement |
| PO (Product Owner) | Responsable du produit | Découpe le document de vision en morceaux exploitables |
| SM (Scrum Master) | Coordinateur | Crée les "stories" — des petites tâches de développement bien décrites |
| Dev | Développeur | Code la feature |
| QA (Quality Assurance) | Testeur | Vérifie que ce qui a été codé fonctionne correctement |

**Un PRD** (Product Requirements Document) c'est le "document de vision du produit" — il décrit en détail ce qu'on construit, pourquoi, pour qui, et comment on saura que c'est réussi. C'est la boussole du projet.

**Une story** (ou user story) c'est une petite unité de travail écrite du point de vue de l'utilisateur. Exemple : *"En tant qu'utilisateur, je veux pouvoir me connecter avec mon email pour accéder à mon compte."* Chaque story contient des critères précis pour savoir si elle est terminée.

**Le problème avec BMAD seul :** BMAD est excellent pour planifier, mais quand vient le moment de coder, l'agent développeur peut se perdre dans la mise en œuvre. Il n'y a pas de mécanisme pour garder le contexte propre et borné pendant les sessions de code.

---

### Apex Spec System — le moteur d'exécution

**Apex** est une méthode créée par Moshe Benavraham. Son idée centrale : ne jamais laisser Claude Code travailler sans une **spec** (une feuille de route détaillée) validée au préalable.

**Comment ça marche :**

Avant de coder quoi que ce soit, Apex oblige à créer deux fichiers :
- Un fichier `spec.md` — qui décrit précisément ce qu'on va faire, pourquoi, et les critères pour savoir si c'est réussi
- Un fichier `tasks.md` — une liste de tâches atomiques (des petites étapes de 15 à 30 minutes chacune, maximum 25 par session)

Ensuite Claude Code travaille tâche par tâche, dans un contexte propre et limité. À la fin, il valide que chaque critère est rempli.

**Une session** c'est une unité de travail bornée — typiquement 2 à 4 heures. Au lieu de demander à Claude Code de "coder toute l'application", tu lui demandes de faire une session précise sur une feature précise.

**CONSIDERATIONS.md** c'est la mémoire du projet — un fichier où Claude Code note les leçons apprises après chaque session. "On a essayé X, ça ne marche pas parce que Y, la prochaine fois faire Z." C'est ce qui évite de refaire les mêmes erreurs.

**Le problème avec Apex seul :** Apex est excellent pour exécuter, mais il ne sait pas *quoi* construire ni dans quel ordre. Sans vision produit, sans architecture formelle, sans quelqu'un pour challenger les décisions, on risque de bien exécuter les mauvaises choses.

---

### AIBlueprint — les patterns avancés

**AIBlueprint** est un projet open source créé par Melvynx. C'est une boîte à outils de configurations avancées pour Claude Code — des agents pré-configurés, des hooks automatiques, des skills qui s'activent selon la situation.

**Les concepts clés :**

**Un hook** c'est un déclencheur automatique. Par exemple : "à chaque fois que tu exécutes une commande bash, vérifie d'abord que c'est sans danger." Le hook s'exécute en arrière-plan sans que tu aies à y penser.

**Un skill** c'est une compétence qu'on donne à Claude Code pour des situations précises. Exemple : le skill `ralph-loop` s'active automatiquement quand les tests échouent en boucle — il analyse l'erreur, identifie la cause, corrige, relance.

**Un agent** c'est une version spécialisée de Claude Code avec un rôle précis, des outils spécifiques, et un modèle d'IA adapté à sa tâche.

AIBlueprint a fourni à STRATEX la philosophie de comment structurer tout ça proprement — avec des agents focalisés, des outputs structurés, et des automatisations intelligentes.

---

### Pourquoi STRATEX combine les trois

Chaque méthode résout une partie du problème :

- **BMAD** sait *quoi* construire — mais pas *comment* garder le contexte propre
- **Apex** sait *comment* exécuter proprement — mais pas *quoi* construire ni dans quel ordre
- **AIBlueprint** sait *comment* automatiser et spécialiser — mais n'est pas une méthode de travail complète

STRATEX est le câble qui les branche ensemble. La section suivante explique exactement quel problème ça résout.

---

## 2. Le problème

BMAD et Apex résolvent deux problèmes *différents* — et si tu les utilises séparément, tu rates l'essentiel.

| Problème | BMAD seul | Apex seul | STRATEX |
|---|---|---|---|
| Pas de plan → code qui dérive | ✅ Résolu | ❌ Inexistant | ✅ |
| Fenêtre de contexte qui explose | ❌ Non géré | ✅ Résolu | ✅ |
| Stories trop vagues pour coder | Partiel | ❌ | ✅ Via `/storify` |
| Leçons apprises perdues entre sprints | ❌ | Partiel | ✅ Bidirectionnel |
| Features simples → too much ceremony | ❌ Lent | ❌ Overkill aussi | ✅ Routing intelligent |
| CI/CD non intégré au cycle | ❌ | ✅ | ✅ |
| État du sprint invisible | Partiel | ❌ | ✅ Via sync automatique |

**BMAD sans Apex** : tes stories BMAD sont excellentes, mais l'agent Dev se perd dans la mise en œuvre car aucun mécanisme ne découpe la story en sessions sûres pour la fenêtre de contexte.

**Apex sans BMAD** : tes sessions sont bien découpées, mais tu construis sans PRD, sans architecture formelle, sans agent PM/Arch pour challenger tes décisions.

**STRATEX** : BMAD planifie jusqu'aux stories → le bridge convertit chaque story en sessions Apex → Apex exécute proprement → les leçons remontent dans BMAD → cycle suivant.

---

## 2. Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                        STRATEX FRAMEWORK                            │
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │                   COUCHE STRATÉGIQUE (BMAD)                  │   │
│  │                                                              │   │
│  │   Analyst ──► PM ──► Architect ──► PO ──► Scrum Master      │   │
│  │      │         │         │          │          │            │   │
│  │  Product    PRD.md   Arch.md    Sharding    Stories/        │   │
│  │   Brief                                     Epics           │   │
│  └──────────────────────────────┬───────────────────────────── ┘   │
│                                 │                                   │
│                    ┌────────────▼────────────┐                     │
│                    │    COUCHE BRIDGE 🌉      │                     │
│                    │                          │                     │
│                    │  /storify    → Converts  │                     │
│                    │  /route      → Dispatche │                     │
│                    │  /sync-sprint → Synchro  │                     │
│                    │  hooks       → Auto      │                     │
│                    └────────────┬────────────┘                     │
│                                 │                                   │
│  ┌──────────────────────────────▼──────────────────────────────┐   │
│  │                  COUCHE EXÉCUTION (APEX)                     │   │
│  │                                                              │   │
│  │  ┌─────────────────────────────────────────┐                │   │
│  │  │  APEX SPEC SYSTEM (Sessions structurées) │                │   │
│  │  │  /nextsession → /sessionspec → /tasks    │                │   │
│  │  │  → /implement → /validate → /updateprd  │                │   │
│  │  └─────────────────────────────────────────┘                │   │
│  │                                                              │   │
│  │  ┌──────────────────────────────────────────┐               │   │
│  │  │  APEX SKILL (Pipeline autonome)          │               │   │
│  │  │  /apex --auto --review --tests [feature] │               │   │
│  │  │  10 steps : branch→analyze→plan→execute  │               │   │
│  │  │             →validate→review→fix→test    │               │   │
│  │  │             →verify→PR                   │               │   │
│  │  └──────────────────────────────────────────┘               │   │
│  │                                                              │   │
│  │  ┌──────────────────────────────────────────┐               │   │
│  │  │  INFRA & CI/CD                           │               │   │
│  │  │  /audit → /pipeline → /infra             │               │   │
│  │  └──────────────────────────────────────────┘               │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘

FLUX DE DONNÉES :
  BMAD → Stories.md ──[/storify]──► .spec_system/PRD/ + sessions
  Apex → CONSIDERATIONS.md ──[/sync-sprint]──► BMAD sprint-status.yaml
  Hooks git commit → auto-update state.json + sprint-status.yaml
```

---

## 3. Installation

### Prérequis

- Claude Code CLI installé
- Abonnement Claude Pro ou Max
- macOS ou Linux

### Installation en une commande

```bash
npx stratex@latest setup
```

La CLI te guide pour choisir les composants et installe tout automatiquement dans `~/.claude/`.

```bash
# Installation complète sans questions
npx stratex@latest setup --skip

# Installation dans un dossier personnalisé
npx stratex@latest setup --folder /mon/projet/.claude
```

### Après l'installation

**1. Personnalise `.claude/CLAUDE.md` avec ta stack :**

```markdown
## WHAT
[Ton projet]

## WHY
[L'objectif métier]

## HOW
[Ta stack — langage, frameworks, outils]
```

**2. Lance Claude Code dans ton projet :**

```bash
cd ton-projet
claude
```

**3. Vérifie que tout est en place :**

```bash
/sprint-dashboard
```

> **Code source de la CLI :** [github.com/oximore16-maker/stratex-cli](https://github.com/oximore16-maker/stratex-cli)

---

---

## 4. Les 7 agents spécialisés

STRATEX v4.1 introduit 7 agents spécialisés invocables via `@nom-agent`. Chaque agent travaille dans son propre contexte isolé et ne retourne que ses conclusions.

| Agent | Modèle | Rôle |
|---|---|---|
| `@stratex-analyst` | Sonnet 🔵 | Brief produit, analyse marché, clarification des besoins |
| `@stratex-architect` | Opus 🔴 | Décisions d'architecture, ADR, choix techniques |
| `@stratex-planner` | Sonnet 🟢 | User stories BMAD, sessions Apex, décomposition des tâches |
| `@stratex-researcher` | Sonnet 🟡 | Deep research autonome sur 8 à 20 sources |
| `@stratex-reviewer` | Opus 🟠 | Code review adversarial en 6 dimensions |
| `@stratex-qa` | Sonnet 🟣 | Tests, validation, critères d'acceptance |
| `@stratex-action` | Haiku ⚡ | Tâches batch légères, renommages, boilerplate |

Chaque agent produit des outputs structurés en XML (`<brief>`, `<adr>`, `<review>`, `<qa-report>`) pour des sorties claires et directement exploitables.

---

## 5. La couche BRIDGE — le cœur de STRATEX

Le bridge repose sur **trois principes** :

### 4.1 La story BMAD est la mère de la session Apex

Une story BMAD produite par le Scrum Master contient déjà :
- Un titre clair
- Des critères d'acceptation (AC)
- Des dépendances
- Une estimation

Le bridge `/storify` transforme ça en `spec.md` + `tasks.md` pour Apex, en injectant automatiquement le contexte de l'architecture BMAD.

```
story-1.1.md (BMAD)
    ↓ /storify
.spec_system/specs/phase01-session01-auth/
    ├── spec.md           (Objectif, scope, approche, fichiers cibles)
    ├── tasks.md          (Checklist de 12-25 tâches atomiques)
    ├── implementation-notes.md
    ├── security-compliance.md
    └── validation.md     (Miroir des ACs BMAD)
```

### 4.2 Les leçons Apex remontent dans BMAD

Chaque session Apex produit un `CONSIDERATIONS.md` avec les leçons apprises. Après chaque session, `/sync-sprint` :
1. Lit `CONSIDERATIONS.md`
2. Met à jour `sprint-status.yaml` (BMAD)
3. Ajoute les insights dans le contexte de l'agent Dev BMAD pour les prochaines stories

### 4.3 L'état est partagé et non dupliqué

Un seul fichier `state.json` Apex est la source de vérité pour l'avancement. `sprint-status.yaml` BMAD est son miroir de haut niveau. Le hook post-commit les maintient en sync automatiquement.

---

## 6. Le protocole de routage à 3 niveaux

Avant toute action, `/route` analyse la complexité de la demande et décide quel outil utiliser :

```
                    ┌─────────────────────────────────────┐
                    │  /route "ma demande"                  │
                    └─────────────┬───────────────────────-┘
                                  │
              ┌───────────────────┼──────────────────────┐
              │                   │                      │
              ▼                   ▼                      ▼
    ┌──────────────────┐ ┌─────────────────┐ ┌──────────────────────┐
    │   NIVEAU 1       │ │   NIVEAU 2      │ │   NIVEAU 3           │
    │   /apex --auto   │ │   APEX SESSION  │ │   BMAD COMPLET       │
    │                  │ │                 │ │                      │
    │ Critères :       │ │ Critères :      │ │ Critères :           │
    │ • 1 composant    │ │ • 2-4 composants│ │ • Nouveau projet     │
    │ • Objectif clair │ │ • Plan nécessaire│ │ • Refonte majeure    │
    │ • Pas d'archi    │ │ • Story existante│ │ • Pas de PRD         │
    │   modifiée       │ │ • < 25 tâches   │ │ • Décision d'archi   │
    │ • < 2h           │ │   estimées      │ │ • Multi-équipe       │
    │                  │ │                 │ │                      │
    │ Temps : 30-90min │ │ Temps : 2-4h    │ │ Temps : 1-3 jours    │
    └──────────────────┘ └─────────────────┘ └──────────────────────┘

    EXEMPLES :
    "Fix le bug du login"         → Niveau 1 (/apex --auto)
    "Ajouter l'auth JWT"          → Niveau 2 (session Apex depuis story)
    "Système de paiement complet" → Niveau 3 (BMAD full pipeline)
```

### Les signaux de complexité utilisés par `/route`

**Réduit le niveau (→ N1) :**
- Mots : "fix", "bug", "rapide", "juste", "petit", "correction"
- Fichier ou composant unique mentionné
- Changement de comportement sans nouvelle interface

**Augmente le niveau (→ N3) :**
- Nouveaux services, APIs, ou bases de données
- Mots : "architecture", "système", "platform", "refonte", "migration"
- Plusieurs équipes impliquées
- Pas de story BMAD existante

---

## 7. CLAUDE.md master template

Ce fichier est à placer à la racine dans `.claude/CLAUDE.md`. Il charge les deux systèmes et définit le comportement par défaut.

```markdown
# STRATEX — Configuration Master

## Framework actif
Ce projet utilise le framework STRATEX (BMAD + Apex Spec System).

## Règle de routage
Avant TOUTE implémentation, évalue la complexité :
- Demande simple (1 composant, objectif clair) → `/apex --auto [feature]`
- Story existante ou feature connue → Flux Apex session (`/storify` si pas encore fait)
- Nouveau projet / refonte / décision d'archi → Flux BMAD complet

## Sources de vérité
1. `docs/prd.md` — PRD maître (BMAD)
2. `docs/architecture.md` — Architecture (BMAD)
3. `.spec_system/state.json` — Avancement des sessions (Apex)
4. `docs/stories/sprint-status.yaml` — Avancement du sprint (BMAD)
5. `.spec_system/CONSIDERATIONS.md` — Leçons apprises (partagé)
6. `.spec_system/CONVENTIONS.md` — Standards de code (partagé)

## Comportement attendu
- Ne jamais implémenter sans spec validée (sauf si /apex --auto en N1)
- Toujours lire CONVENTIONS.md avant d'écrire du code
- Toujours lire CONSIDERATIONS.md pour les patterns connus à éviter
- Après chaque session, appeler `/sync-sprint`
- Les tâches Apex doivent rester atomiques (≤ 30 min chacune)
- Maximum 25 tâches par session
- Ne pas dépasser 40% de la fenêtre de contexte sur une session

## Agents disponibles (BMAD)
- `*analyst` — Analyse et brief produit
- `*pm` — PRD et requirements
- `*architect` — Architecture technique
- `*po` — Product Owner, sharding docs
- `*sm` — Scrum Master, création de stories
- `*dev` — Développeur, implémentation
- `*qa` — Quality Assurance

## Commandes disponibles (Apex)
- `/nextsession` — Prochaine session recommandée
- `/sessionspec` — Spec formelle de la session
- `/tasks` — Checklist de tâches
- `/implement` — Démarrage implémentation
- `/validate` — Validation de complétude
- `/updateprd` — Mise à jour PRD
- `/audit` — Tooling local (lint, types, tests)
- `/pipeline` — CI/CD
- `/carryforward` — Leçons apprises

## Commandes bridge (STRATEX)
- `/route [demande]` — Dispatcher intelligent
- `/storify [story-file]` — Convertit une story BMAD en session Apex
- `/sync-sprint` — Synchronise BMAD sprint-status ↔ Apex state.json

## Structure des documents clés
Quand tu charges une story BMAD pour une session, charge TOUJOURS :
1. `docs/architecture.md` (sections pertinentes uniquement)
2. `.spec_system/CONVENTIONS.md`
3. `.spec_system/CONSIDERATIONS.md`
4. La story elle-même

Ne jamais charger le PRD complet dans une session de dev — trop lourd.
```

---

## 8. Les commandes bridge

### 7.1 `/storify` — Convertit une story BMAD en session Apex

Fichier : `.claude/commands/storify.md`

```markdown
---
name: storify
description: Convertit une story BMAD en spec + tasks Apex. Usage: /storify [chemin-story ou titre]
---

# STORIFY — Bridge BMAD → Apex

## Objectif
Transformer une story BMAD en une session Apex formelle, en injectant le contexte architectural.

## Instructions

1. **Localiser la story**
   - Si un fichier est fourni en argument, le lire directement
   - Sinon, chercher dans `docs/stories/` une story correspondant à l'argument
   - Si aucune story trouvée, indiquer et lister les stories disponibles

2. **Lire le contexte architectural**
   - Lire `.spec_system/CONVENTIONS.md`
   - Lire `.spec_system/CONSIDERATIONS.md`
   - Lire les sections pertinentes de `docs/architecture.md` (composants mentionnés dans la story)

3. **Générer le numéro de session**
   - Lire `.spec_system/state.json`
   - Trouver la prochaine session disponible dans la phase courante
   - Format : `phaseNN-sessionNN-[slug-titre-story]`

4. **Créer la spec Apex** dans `.spec_system/specs/[session-id]/spec.md`
   Structure obligatoire :
   ```
   # Session : [titre de la story]
   
   ## Métadonnées
   - Session ID : [phaseNN-sessionNN]
   - Story source : [chemin story BMAD]
   - Epic parent : [nom epic]
   - Durée estimée : [X heures]
   - Composants cibles : [liste]
   
   ## Objectif
   [Reprendre l'objectif de la story en 2-3 phrases]
   
   ## Critères d'acceptation (depuis la story BMAD)
   [Copier exactement les ACs de la story]
   
   ## Scope (dans cette session)
   [Ce qui EST inclus]
   
   ## Hors scope
   [Ce qui N'EST PAS inclus — important pour rester dans le budget contexte]
   
   ## Approche technique
   [Basée sur docs/architecture.md — décrire l'approche choisie]
   
   ## Fichiers cibles
   [Liste des fichiers qui seront créés ou modifiés]
   
   ## Dépendances
   [Sessions Apex précédentes dont celle-ci dépend]
   
   ## Considérations de sécurité
   [Issues de sécurité spécifiques à cette session]
   ```

5. **Générer les tâches Apex** dans `.spec_system/specs/[session-id]/tasks.md`
   - Décomposer en tâches ATOMIQUES de 15-30 min chacune
   - Maximum 25 tâches (idéalement 15-20)
   - Format checkbox : `- [ ] [verbe d'action] [objet précis]`
   - Grouper par phase : Setup → Core Implementation → Tests → Validation
   - Inclure une tâche "Mise à jour CONSIDERATIONS.md" en fin de session

6. **Mettre à jour state.json**
   - Ajouter la session avec status "pending"
   - Lier à la story BMAD source

7. **Rapport de conversion**
   Afficher :
   - Session créée : [ID]
   - Nombre de tâches : [N]
   - Durée estimée : [X-Y heures]
   - Prochaine étape : `/implement` pour démarrer

## Vérification du budget contextuel
Après génération, vérifier :
- Si tâches > 25 → proposer de splitter en 2 sessions
- Si durée estimée > 4h → proposer de splitter
- Si fichiers cibles > 15 → avertir, proposer scope réduit
```

---

### 7.2 `/route` — Dispatcher intelligent

Fichier : `.claude/commands/route.md`

```markdown
---
name: route
description: Analyse la complexité d'une demande et dispatche vers le bon niveau STRATEX. Usage: /route "description de la demande"
---

# ROUTE — Dispatcher STRATEX

## Objectif
Analyser la demande et décider : Niveau 1 (/apex --auto), Niveau 2 (session Apex), ou Niveau 3 (BMAD complet).

## Processus d'analyse

### Étape 1 : Lire l'état courant
- Lire `.spec_system/state.json` pour connaître la phase/session courante
- Lire `docs/stories/sprint-status.yaml` pour voir les stories actives
- Vérifier si une story BMAD correspondante existe déjà

### Étape 2 : Scorer la complexité (0-10)

**Signaux qui AUGMENTENT le score :**
- Mentionne plusieurs services/APIs/bases de données (+2 par)
- Requiert une décision d'architecture (+3)
- Pas de story BMAD existante pour cette feature (+2)
- Mots : "système", "platform", "refonte", "migration", "architecture" (+2)
- Implique des changements de schéma DB (+2)
- Implique de nouveaux endpoints publics (+1)
- Multi-tenant ou concerns de sécurité complexes (+2)

**Signaux qui DIMINUENT le score :**
- Mots : "fix", "bug", "correction", "petit", "juste", "rapide" (-2)
- Un seul fichier ou composant mentionné (-2)
- Comportement existant à modifier sans nouvelle interface (-1)
- Story BMAD déjà prête et détaillée (-2)
- Session Apex déjà créée pour cette story (-3)

### Étape 3 : Décision de routage

**Score 0-3 → Niveau 1 (Apex Skill)**
```
🚀 NIVEAU 1 — Pipeline autonome
Commande recommandée :
/apex --auto --review --tests "[description]"

Durée estimée : 30-90 minutes
Aucune spec préalable requise.
```

**Score 4-6 → Niveau 2 (Session Apex)**
```
📋 NIVEAU 2 — Session Apex structurée

Story BMAD source : [trouver ou indiquer qu'elle manque]

Si la story existe déjà :
  → /storify [chemin-story]     (si session pas encore créée)
  → /implement                  (si session déjà créée)

Si la story n'existe pas :
  → Créer la story d'abord avec *sm, puis /storify
```

**Score 7-10 → Niveau 3 (BMAD complet)**
```
🏗️ NIVEAU 3 — Flux BMAD complet requis

Raison : [expliquer pourquoi la complexité dépasse une session]

Flux recommandé :
1. *analyst  → Brief produit
2. *pm       → PRD ou mise à jour PRD
3. *architect → Décisions d'archi (si nouvelles)
4. *po       → Sharding des docs
5. *sm       → Création des stories
6. /storify  → Pour chaque story → session Apex
7. /implement → Exécution session par session
```

### Étape 4 : Afficher la décision

Format de sortie :
```
📊 Analyse STRATEX
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Demande : "[demande analysée]"
Score de complexité : X/10
Niveau recommandé : [1 / 2 / 3]

Justification :
+ [signal détecté] (+N)
- [signal détecté] (-N)

Action immédiate :
[commande exacte à exécuter]

Alternative si N1 s'avère trop simple :
[commande de fallback]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```
```

---

### 7.3 `/sync-sprint` — Synchronisation bidirectionnelle

Fichier : `.claude/commands/sync-sprint.md`

```markdown
---
name: sync-sprint
description: Synchronise l'état BMAD sprint-status.yaml ↔ Apex state.json et remonte les leçons apprises.
---

# SYNC-SPRINT — Synchronisation STRATEX

## Objectif
Maintenir la cohérence entre les deux systèmes après chaque session ou commit important.

## Processus

### Étape 1 : Lire les deux sources
- Lire `.spec_system/state.json` (source de vérité Apex)
- Lire `docs/stories/sprint-status.yaml` (source de vérité BMAD)

### Étape 2 : Calculer les deltas

Pour chaque session Apex avec status "completed" :
1. Trouver la story BMAD source (via le lien dans spec.md)
2. Marquer la story comme Done dans sprint-status.yaml
3. Calculer le % de l'epic complété

Pour chaque session Apex avec status "in-progress" :
1. Trouver la story BMAD source
2. Marquer la story comme In Progress dans sprint-status.yaml
3. Indiquer les tâches complétées / total

### Étape 3 : Remonter les leçons apprises

Lire `.spec_system/CONSIDERATIONS.md` :
1. Identifier les entrées ajoutées depuis la dernière sync (comparer avec la date du dernier sync dans state.json)
2. Formater en insights BMAD :
   ```yaml
   # sprint-status.yaml — section insights
   lessons_learned:
     - session: [session-id]
       date: [date]
       insight: "[leçon apprise]"
       impact_on_stories: [liste de stories futures potentiellement affectées]
   ```

### Étape 4 : Mettre à jour les deux fichiers

**Mettre à jour `docs/stories/sprint-status.yaml` :**
```yaml
sprint:
  name: [sprint courant]
  updated_at: [timestamp]
  velocity_actual: [sessions complétées * points]
  
epics:
  - id: E1
    title: [titre epic]
    stories:
      - id: S1.1
        title: [titre story]
        status: [Done | In Progress | Todo]
        session_apex: [session-id]
        completed_at: [date si Done]
      
progress:
  total_stories: N
  done: X
  in_progress: Y
  todo: Z
  percent_complete: XX%

lessons_learned:
  - [...]
```

**Mettre à jour `.spec_system/state.json` :**
Ajouter `last_bmad_sync: [timestamp]`

### Étape 5 : Rapport de sync

```
✅ SYNC-SPRINT STRATEX
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Sessions Apex → BMAD : [N stories mises à jour]
Leçons remontées : [N insights]
Sprint progress : XX% ([X]/[N] stories)

Prochaine story recommandée : [titre]
Commande : /storify docs/stories/[epic]/[story].md
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```
```

---

## 9. Les hooks d'automatisation

### 8.1 Hook post-commit

Fichier : `.claude/hooks/post-commit.sh`

Ce hook s'exécute automatiquement après chaque `git commit` pour maintenir l'état en sync.

```bash
#!/bin/bash
# STRATEX — Post-commit hook
# Maintient la synchronisation BMAD ↔ Apex après chaque commit

STATE_FILE=".spec_system/state.json"
SPRINT_STATUS="docs/stories/sprint-status.yaml"

# Vérifier que les fichiers nécessaires existent
if [ ! -f "$STATE_FILE" ] || [ ! -f "$SPRINT_STATUS" ]; then
  exit 0  # Pas un projet STRATEX, skip silencieusement
fi

# Mettre à jour le timestamp de dernier commit dans state.json
TIMESTAMP=$(date -u +"%Y-%m-%dT%H:%M:%SZ")
COMMIT_MSG=$(git log -1 --pretty=%B | head -1)
COMMIT_HASH=$(git rev-parse --short HEAD)

# Injecter le dernier commit dans state.json
jq --arg ts "$TIMESTAMP" \
   --arg msg "$COMMIT_MSG" \
   --arg hash "$COMMIT_HASH" \
   '.last_commit = {"hash": $hash, "message": $msg, "timestamp": $ts}' \
   "$STATE_FILE" > /tmp/state_tmp.json && mv /tmp/state_tmp.json "$STATE_FILE"

echo "🔄 STRATEX: État synchronisé après commit $COMMIT_HASH"
echo "   Rappel: Exécute /sync-sprint pour une sync complète"
```

### 8.2 Hook de protection du contexte

Fichier : `.claude/hooks/pre-implement.sh`

Vérifie qu'une session ne dépasse pas le budget de contexte avant l'implémentation.

```bash
#!/bin/bash
# STRATEX — Pre-implement context budget check
# Avertit si la session risque de surcharger la fenêtre de contexte

SESSION_DIR=".spec_system/specs/$1"

if [ ! -d "$SESSION_DIR" ]; then
  echo "❌ Session non trouvée: $1"
  exit 1
fi

# Compter les tâches
TASK_COUNT=$(grep -c "^- \[ \]" "$SESSION_DIR/tasks.md" 2>/dev/null || echo 0)
FILE_COUNT=$(grep -c "^-" "$SESSION_DIR/spec.md" 2>/dev/null | head -5 | tail -1 || echo 0)

echo "📊 Budget contextuel pour session $1 :"
echo "   Tâches : $TASK_COUNT (max recommandé : 25)"
echo "   Fichiers cibles : $FILE_COUNT"

if [ "$TASK_COUNT" -gt 25 ]; then
  echo "⚠️  ATTENTION : $TASK_COUNT tâches dépassent le budget recommandé (25)"
  echo "   Envisage de splitter cette session en deux."
  exit 1
fi

echo "✅ Budget OK"
exit 0
```

### 8.3 Configurer les hooks dans Claude Code

Dans `.claude/settings.json` :

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Bash(git commit*)",
        "hooks": [
          {
            "type": "command",
            "command": "bash .claude/hooks/post-commit.sh"
          }
        ]
      }
    ],
    "PreToolUse": [
      {
        "matcher": "Bash(/implement*)",
        "hooks": [
          {
            "type": "command",
            "command": "bash .claude/hooks/pre-implement.sh"
          }
        ]
      }
    ]
  }
}
```

---

## 10. Workflow complet de A à Z

### Scénario : Construction d'une app de gestion de tâches

---

#### PHASE 0 — Bootstrap (une fois)

```bash
# 1. Initialiser le projet
git init mon-projet && cd mon-projet
npx bmad-method install

# 2. Initialiser Apex
/initspec   # Via Claude Code

# 3. Customiser CONVENTIONS.md avec tes standards
# (TypeScript strict, testing avec Vitest, etc.)

# 4. Copier les 3 fichiers bridge dans .claude/commands/
# 5. Copier CLAUDE.md dans .claude/
# 6. Copier les hooks dans .claude/hooks/
```

---

#### PHASE 1 — Planification stratégique (BMAD)

```
# Dans Claude Code, activer l'agent analyst :
*analyst
"Je veux construire une app de gestion de tâches pour équipes"

# → Produit : docs/product-brief.md

*pm
"Créer le PRD depuis ce brief"
# → Produit : docs/prd.md

*architect
"Concevoir l'architecture full-stack"
# → Produit : docs/architecture.md

*po
"Sharder le PRD et l'architecture"
# → Produit : docs shardés, prêts pour les agents Dev

*sm
"Créer les stories pour l'Epic 1 : Authentification"
# → Produit : docs/stories/epic-1/story-1.1.md, story-1.2.md, story-1.3.md
```

---

#### PHASE 2 — Routage et préparation des sessions

```
# Pour chaque feature, commencer par :
/route "Implémenter l'authentification JWT avec refresh tokens"

# Réponse attendue :
# Score: 6/10 → Niveau 2 (Session Apex)
# Story source identifiée: docs/stories/epic-1/story-1.1.md
# Commande: /storify docs/stories/epic-1/story-1.1.md

# Exécuter :
/storify docs/stories/epic-1/story-1.1.md

# Résultat :
# Session créée: phase01-session01-auth-jwt
# Tâches générées: 18 tâches atomiques
# Durée estimée: 2.5-3h
```

---

#### PHASE 3 — Exécution des sessions (Apex)

```
# Démarrer la session
/implement

# Claude lit spec.md, tasks.md, CONVENTIONS.md, CONSIDERATIONS.md
# et commence à coder task par task :
# ✅ Setup des dépendances (jsonwebtoken, bcrypt)
# ✅ Créer AuthService avec generateTokens()
# ✅ Créer le middleware d'authentification
# ✅ Créer POST /auth/login endpoint
# ✅ Créer POST /auth/refresh endpoint
# ✅ Tests unitaires AuthService
# ✅ Tests d'intégration endpoints
# ...

# En fin de session, valider :
/validate

# Mettre à jour le système :
/updateprd

# Synchroniser BMAD :
/sync-sprint
```

---

#### Pour une feature simple (Niveau 1)

```
/route "Corriger le bug où l'email de bienvenue n'est pas envoyé après inscription"

# Réponse : Score 2/10 → Niveau 1
# Commande recommandée :
/apex --auto --review --tests "Fix welcome email not sent after user registration"

# Claude exécute les 10 étapes autonomes :
# 1. init branch: fix/welcome-email
# 2. analyze code: cherche le bug dans UserService et EmailService
# 3. plan fix: identifie la ligne manquante dans le flow d'inscription
# 4. execute: applique le fix
# 5. validate: vérifie le comportement
# 6. review: analyse adversariale
# 7. fix issues: corrige les problèmes trouvés en review
# 8. add tests: écrit un test de régression
# 9. verify tests: confirme que tous les tests passent
# 10. create PR: ouvre la PR avec description complète
```

---

#### Pour une nouvelle feature majeure (Niveau 3)

```
/route "Ajouter un système de notifications en temps réel avec WebSockets"

# Réponse : Score 8/10 → Niveau 3 (BMAD requis)
# Flux recommandé affiché

# On active BMAD pour décider l'architecture :
*architect
"Concevoir le système de notifications temps réel.
Contexte: React frontend, NestJS backend, PostgreSQL.
Contraintes: scalable, < 100ms latency"

# → docs/architecture-notifications.md

*sm
"Créer les stories pour l'Epic Notifications"
# → 4 stories créées

# Puis pour chaque story :
/storify docs/stories/epic-3/story-3.1.md
/implement
/validate
/sync-sprint
# Répéter...
```

---

#### PHASE 4 — Entre les phases (qualité et CI/CD)

```
# Après toutes les sessions d'une phase :
/audit      # Lint, types, tests locaux
/pipeline   # CI/CD : quality gate, build, security scan, integration tests
/infra      # Infrastructure : health, security, backup, deploy

# Carry forward les leçons pour la phase suivante :
/carryforward
```

---

## 10. Référence des commandes

### Commandes STRATEX (bridge)

| Commande | Usage | Quand |
|---|---|---|
| `/route [demande]` | Dispatcher intelligent | Avant toute action |
| `/storify [story]` | Story BMAD → Session Apex | Après *sm, avant /implement |
| `/sync-sprint` | Sync BMAD ↔ Apex | Après chaque session |

### Commandes BMAD (agents)

| Agent | Invocation | Produit |
|---|---|---|
| Analyst | `*analyst [brief]` | `docs/product-brief.md` |
| PM | `*pm` | `docs/prd.md` |
| Architect | `*architect` | `docs/architecture.md` |
| PO | `*po shard documents` | Docs shardés |
| Scrum Master | `*sm create stories for [epic]` | `docs/stories/epic-N/` |
| Dev | `*dev` | Implémentation (Niveau 3 seulement) |
| QA | `*qa` | Review et tests |

### Commandes Apex (session workflow)

| Commande | Usage | Quand |
|---|---|---|
| `/nextsession` | Prochaine session recommandée | Début de journée |
| `/sessionspec` | Spec formelle | Si /storify pas utilisé |
| `/tasks` | Checklist de tâches | Après /sessionspec |
| `/implement` | Démarrer le code | Après /tasks |
| `/validate` | Vérifier la complétude | Fin de session |
| `/updateprd` | Marquer done, sync PRD | Après /validate |
| `/carryforward` | Leçons apprises | Entre phases |
| `/audit` | Lint, types, tests | Entre phases |
| `/pipeline` | CI/CD | Entre phases |
| `/infra` | Infrastructure | Entre phases |

### Commandes Apex Skill (pipeline autonome)

| Commande | Usage |
|---|---|
| `/apex --auto --review --tests [feature]` | Pipeline complet (N1) |
| `/apex --auto [feature]` | Pipeline rapide (N1 minimal) |

---

## Conclusion

STRATEX n'est pas une troisième méthode qui vient compliquer les choses. C'est la reconnaissance que BMAD et Apex sont complémentaires par nature :

**BMAD** donne de la *direction* : où on va, pourquoi, dans quel ordre, avec quelle architecture.  
**Apex** donne de la *discipline* : comment on y va, session par session, sans jamais se perdre dans un contexte surchargé.

Le bridge est intentionnellement minimal — trois commandes, deux hooks — pour ne pas introduire de complexité inutile. L'objectif est de laisser chaque système faire ce qu'il fait le mieux, en les faisant parler le même langage.

```
BMAD parle en : Epic → Story → Acceptance Criteria
Apex parle en : Phase → Session → Task
STRATEX traduit : Story ↔ Session, AC ↔ Validation.md, Sprint ↔ State.json
```

Le résultat final : un projet où tu ne peux jamais te perdre — ni au niveau stratégique (BMAD t'indique où tu en es), ni au niveau de l'implémentation (Apex garde le contexte propre et les sessions bornées).

---

*Framework STRATEX v4.1 — conçu pour Claude Code avec BMAD, Apex Spec System et AIBlueprint**

---

## 12. Projets inspirants

STRATEX n'existerait pas sans ces projets :

- **[BMAD Method](https://github.com/bmadcode/bmad-agent)** — la méthode agile pour Claude Code
- **[Apex Spec System](https://github.com/moshehbenavraham/apex-spec-system)** — l'implémentation guidée par la spec
- **[AIBlueprint par Melvynx](https://github.com/Melvynx/aiblueprint)** — la référence pour les configs Claude Code avancées
- **[Claude Code Docs](https://docs.anthropic.com/claude-code)** — la documentation officielle

---

## Statut honnête

**Ce framework a été conçu par raisonnement**, en combinant des approches que j'admirais, sans avoir lancé Claude Code moi-même. C'est exactement pour ça que je le partage ici plutôt que de le présenter comme un produit fini.

Si tu testes STRATEX, ces questions m'intéressent :
- Les agents s'invoquent-ils correctement avec `@stratex-nom` ?
- Le workflow `/route` → `/apex` est-il fluide en pratique ?
- Qu'est-ce qui plante en premier ?
- Quel est le coût réel en tokens sur une session ?

Tous les retours sont bienvenus — issues GitHub ou communauté Renaud Dékode.

---

## Licence

**CC BY-NC 4.0** — Copyright (c) 2026 Oximore

Tu peux utiliser, modifier et partager STRATEX librement, à condition de :
- **Citer Oximore** comme auteur avec un lien vers ce repo
- **Ne pas vendre** STRATEX ni l'intégrer dans un produit commercial

→ [Lire la licence complète](LICENSE) | [Résumé CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.fr)

---

*Fait avec curiosité, partagé avec humilité. Tous les retours sont les bienvenus.*
