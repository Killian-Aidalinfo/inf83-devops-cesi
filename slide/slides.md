---
theme: seriph
colorSchema: light
title: INF83 - Déploiement continu DevOps
titleTemplate: '%s · CivilisationIT'
info: |
  ## INF83 - Déploiement continu DevOps
  Versionning, culture DevOps, conteneurisation, CI/CD et mise en production automatisée.

  Support de cours - CESI - par CivilisationIT (civilisation-it.fr)
class: text-left
drawings:
  persist: false
transition: slide-left
mdc: true
fonts:
  sans: Inter
  mono: Fira Code
css: unocss
---

<style>
.slidev-layout.cover {
  background:
    radial-gradient(circle at 15% 10%, rgba(14, 165, 233, 0.16) 0%, transparent 45%),
    radial-gradient(circle at 85% 90%, rgba(249, 115, 22, 0.12) 0%, transparent 45%),
    #ffffff;
}
</style>

<div class="absolute top-10 right-10 civit-badge">
  <img src="/civilisationit-logo.svg" class="w-8 h-8" />
  <span>Civilisation<span class="fire">IT</span></span>
</div>

# INF83
## Déploiement continu DevOps

Versionning, culture DevOps, conteneurisation, CI/CD<br>et mise en production automatisée

<div class="pt-12">
  <span class="px-3 py-1 rounded-full civit-callout text-sm">CESI · 3e année</span>
  <span class="px-3 py-1 rounded-full civit-callout-fire text-sm ml-2">5 jours · théorie / pratique / projet fil rouge</span>
</div>

<div class="abs-bottom-12 left-12 text-sm opacity-70">
  Support pédagogique préparé par <strong>CivilisationIT</strong> — civilisation-it.fr<br>
  Intervenant CESI
</div>

---
layout: two-cols
class: gap-8
---

# Bienvenue 👋

Ce cours vous accompagne, pas à pas, de votre **premier commit Git** jusqu'à un **déploiement automatisé** en staging via une pipeline CI/CD.

**Public cible**
- Développeurs en 3e année d'études supérieures
- Accompagnement prévu pour celles et ceux qui n'ont jamais pratiqué Git

**Durée indicative**
- 5 jours, alternance théorie / pratique / projet fil rouge

::right::

<div class="civit-callout mt-12">

### Livrables pédagogiques

- Support de cours
- Exercices guidés
- TP fil rouge
- Checklist de déploiement
- Grille d'évaluation formative

</div>

<div class="civit-callout-fire mt-6 text-sm">
🔥 Contenus complémentaires (tutoriels écrits & vidéo DevOps) :<br>
<a href="https://civilisation-it.fr" target="_blank">civilisation-it.fr</a>
</div>

---

# Sommaire du module

<div class="grid grid-cols-2 gap-x-12 pt-6 text-lg">

<ol class="space-y-3">
<li>Positionnement du cours</li>
<li>Vue d'ensemble : de l'idée au déploiement</li>
<li>Versionning et évolution applicative avec Git</li>
<li>DevOps : valeurs, principes et pratiques</li>
<li>Environnements, mise en production et maintenance</li>
<li>Conteneurisation avec Docker</li>
<li>Pipeline CI/CD</li>
</ol>

<ol class="space-y-3" start="8">
<li>TP fil rouge : déployer un projet existant</li>
<li>Exercices courts</li>
<li>Antisèches</li>
<li>Erreurs fréquentes et corrections</li>
<li>Glossaire rapide</li>
<li>Sources et bibliographie</li>
</ol>

</div>

<!--
Schémas originaux créés pour ce support. Les références [S...] sont détaillées en fin de document.
-->

---
layout: section
class: civit-section
---

# 1. Positionnement du cours

---

# Pourquoi ce module ?

Amener les apprenants à **déployer une application de façon automatisée** dans une démarche DevOps :

- gestion de versions avec Git
- valeurs et pratiques **DevOps**
- **conteneurisation** avec Docker
- installation / configuration d'une solution de **CI/CD** <span class="opacity-50 text-sm">[S0]</span>

<v-click>

<div class="civit-callout mt-8">
Un étudiant qui n'a jamais utilisé Git doit pouvoir suivre les premières manipulations, puis comprendre comment <strong>Git devient le point de départ d'un pipeline CI/CD complet</strong>.
</div>

</v-click>

---

# Objectifs pédagogiques opérationnels

À la fin des 5 jours, un apprenant doit être capable de :

<div class="text-sm">

| Objectif | Résultat observable |
|---|---|
| Mettre en place un logiciel de versionning | Créer un dépôt Git, committer proprement, travailler en branche, résoudre un conflit, synchroniser avec un dépôt distant. |
| Documenter les évolutions | Messages de commit utiles, changelog, tags de version, distinguer correction / maintenance / évolution. |
| Expliquer DevOps | CALMS, pratiques CI/CD, environnements de déploiement, métriques de pilotage. |
| Conteneuriser une application | `Dockerfile`, build, run, variables d'environnement, Docker Compose. |
| Automatiser la livraison | Pipeline GitLab CI / Jenkins, tests/build, artefact ou image, staging puis promotion prod. |
| Diagnostiquer un incident | Lire les logs, reproduire un bug, procédure d'escalade, proposer un rollback. |

</div>

---

# Fil conducteur des 5 jours

| Jour | Fil conducteur | Pratique dominante |
|---|---|---|
| **Jour 1** | Versionning, évolution applicative, Git pour débutants, introduction automatisation / conteneurs. | Exercices Git individuels puis binômes. |
| **Jours 2-3** | Culture DevOps, CALMS, CI/CD, environnements, stratégies de déploiement, pratiques de maintenance. | Cartographie d'un flux de livraison et conception de pipeline. |
| **Jours 4-5** | Docker, Docker Compose, GitLab CI / Jenkins, TP de déploiement d'un projet existant. | TP fil rouge : conteneuriser, automatiser, déployer, documenter. |

<div class="civit-callout-fire mt-10">

**Principe pédagogique.** On ne commence pas par « installer un outil ». On commence par le problème : *comment livrer plus souvent, avec moins de stress, plus de traçabilité et moins d'écarts entre les environnements ?*

</div>

---

# Pré-requis et matériel recommandé

Chaque apprenant doit disposer de :

- un terminal utilisable ;
- un éditeur ou IDE ;
- Git installé et configuré ;
- Docker Desktop ou Docker Engine selon l'environnement de formation ;
- un accès à une forge Git, par exemple GitLab ou GitHub ;
- un accès à une solution CI : GitLab CI, Jenkins, ou instance fournie par l'intervenant ;
- un projet applicatif simple : API, application web, service Node.js, Spring Boot, Python, PHP, .NET, etc.

### Commandes de vérification

```bash
git --version
docker --version
docker compose version
```

---
layout: section
class: civit-section
---

# 2. Vue d'ensemble
## De l'idée au déploiement

---

# Un système, pas seulement un script

Un déploiement continu n'est pas seulement un script. C'est un **système complet** :

- des personnes
- un dépôt Git
- des règles de collaboration
- un pipeline
- des environnements
- des contrôles qualité
- des journaux
- des procédures de retour arrière

---
layout: image
image: /images/schema_01_boucle_devops.png
backgroundSize: contain
---

<div class="absolute bottom-4 left-4 text-xs opacity-70 bg-black bg-opacity-40 px-2 py-1 rounded">
Schéma 1 - Boucle DevOps
</div>

---

# CALMS et métriques DORA

Le modèle DevOps vise à réduire la distance entre **développement**, **exploitation** et **utilisateurs**.

Le cadre **CALMS** résume les dimensions à travailler <span class="opacity-50 text-sm">[S7]</span> :

<div class="flex gap-3 mt-6 text-center">
  <div class="civit-callout flex-1 py-4"><strong class="text-civit-blue">C</strong>ulture</div>
  <div class="civit-callout flex-1 py-4"><strong class="text-civit-blue">A</strong>utomation</div>
  <div class="civit-callout flex-1 py-4"><strong class="text-civit-blue">L</strong>ean</div>
  <div class="civit-callout flex-1 py-4"><strong class="text-civit-blue">M</strong>easurement</div>
  <div class="civit-callout flex-1 py-4"><strong class="text-civit-blue">S</strong>haring</div>
</div>

<v-click>

<div class="civit-callout-fire mt-8">
Les métriques <strong>DORA</strong> aident ensuite à objectiver la performance de livraison : délai commit → production, fréquence de déploiement, temps de récupération après échec <span class="opacity-50 text-sm">[S8]</span>.
</div>

</v-click>

---

# Les mots à maîtriser dès le début (1/2)

<div class="text-sm">

| Terme | Définition courte | Exemple concret |
|---|---|---|
| Dépôt | Espace versionné contenant code, historique et configuration. | Projet GitLab avec `README.md`, `src/`, `Dockerfile`. |
| Commit | Point d'historique décrivant un changement cohérent. | `fix(auth): reject expired token` |
| Branche | Ligne de travail isolée. | `feature/checkout`, `fix/login-500` |
| Merge / Pull request | Demande de fusion avec discussion, revue, CI. | Fusionner une branche dans `main`. |
| Pipeline | Suite automatisée d'étapes. | Installer, tester, construire, scanner, déployer. |
| Artefact | Résultat produit par le pipeline. | Rapport de tests, paquet `.jar`, image Docker. |

</div>

---

# Les mots à maîtriser dès le début (2/2)

<div class="text-sm">

| Terme | Définition courte | Exemple concret |
|---|---|---|
| Image Docker | Modèle immuable d'exécution. | `registry.example.com/app:1.2.0` |
| Conteneur | Processus isolé lancé à partir d'une image. | Service API démarré par `docker run`. |
| Registry | Entrepôt d'images. | Docker Hub, GitLab Container Registry. |
| Environnement | Cible de déploiement avec configuration propre. | `dev`, `test`, `staging`, `prod` |
| Secret | Donnée sensible injectée sans être commitée. | Mot de passe DB, token API. |

</div>

---

# CI, Continuous Delivery, Continuous Deployment

| Pratique | Idée | Question de contrôle |
|---|---|---|
| **CI** - Continuous Integration | Intégrer fréquemment les changements et exécuter des contrôles automatiques. | « Mon code est-il intégrable sans casser le projet ? » |
| **Continuous Delivery** | Le logiciel est toujours dans un état livrable ; la mise en prod reste décidée par un humain. | « Peut-on livrer maintenant si le métier valide ? » |
| **Continuous Deployment** | Chaque changement validé par la pipeline peut être déployé automatiquement en production. | « Le pipeline peut-il aller jusqu'à la prod sans action manuelle ? » |

<div class="civit-callout mt-8">
Dans un contexte pédagogique, on vise souvent d'abord <strong>CI + livraison continue vers staging</strong>, puis une <strong>promotion manuelle</strong> vers production. C'est réaliste, sécurisé et compatible avec des équipes qui découvrent Git ou Docker.
</div>

---
layout: section
class: civit-section
---

# 3. Versionning et évolution applicative avec Git

---

# Pourquoi versionner ?

Git est un système de gestion de versions **distribué**. Il enregistre les changements d'un ensemble de fichiers au fil du temps afin de pouvoir retrouver une version antérieure, comparer des changements et comprendre qui a modifié quoi <span class="opacity-50 text-sm">[S1][S2]</span>.

Sans versioning, une équipe dépend de copies manuelles comme `projet_final_v2_vraiment_final.zip`.

Avec Git, l'équipe obtient :

- une **traçabilité** des changements ;
- un **historique consultable** ;
- des **retours arrière** contrôlés ;
- du **travail parallèle** grâce aux branches ;
- une base technique pour la **revue de code** et la **CI/CD**.

<div class="civit-callout-fire mt-6">
<strong>À retenir.</strong> Dans une démarche DevOps, Git n'est pas seulement l'outil des développeurs. C'est le déclencheur du pipeline, le lieu de revue, la source de vérité de la configuration et le support d'audit.
</div>

---
layout: image-right
image: /images/schema_02_git_lifecycle.png
backgroundSize: contain
---

# Modèle mental Git pour débutants

Git distingue plusieurs zones :

1. **Répertoire de travail** : fichiers visibles dans le dossier projet.
2. **Index / staging area** : sélection des changements qui entreront dans le prochain commit.
3. **Dépôt local** : historique de commits sur la machine.
4. **Dépôt distant** : dépôt partagé sur GitLab, GitHub ou serveur interne.

<div class="text-xs opacity-60 mt-4">Schéma 2 - Cycle de vie Git</div>

---

# Commandes minimales

```bash
# Voir l'état du dépôt
git status

# Ajouter des fichiers à l'index
git add README.md src/

# Créer un commit
git commit -m "docs: add installation steps"

# Envoyer la branche vers le dépôt distant
git push origin main

# Récupérer les nouveautés du dépôt distant
git pull
```

---

# Configuration initiale

```bash
git config --global user.name "Prénom Nom"
git config --global user.email "prenom.nom@example.com"
git config --global init.defaultBranch main

git config --global --list
```

### Bonnes pratiques

- utiliser la même adresse que la forge Git ;
- configurer une clé SSH si l'organisation l'impose ;
- ne jamais committer de mot de passe, token, clé privée ou fichier `.env` réel ;
- créer un `.gitignore` dès le début.

---

# Exemple de `.gitignore` générique

```text
# dépendances
node_modules/
vendor/
.venv/

# build
build/
dist/
target/

# secrets locaux
.env
*.pem
*.key

# IDE / OS
.idea/
.vscode/
.DS_Store
```

---

# TP guidé : premier dépôt

Objectif : créer un dépôt local, produire plusieurs commits lisibles, puis pousser vers un dépôt distant.

```bash
mkdir tp-git-intro
cd tp-git-intro
git init

printf "# TP Git Intro\n" > README.md
git status
git add README.md
git commit -m "docs: add project title"

mkdir src
printf "console.log('hello devops');\n" > src/app.js
git add src/app.js
git commit -m "feat: add hello script"

git log --oneline --graph --decorate
```

---

# Questions de débrief

<div class="civit-callout text-lg space-y-4 mt-8">

- Qu'est-ce qui est versionné ?
- Quelle différence entre `git add` et `git commit` ?
- Pourquoi faire deux commits plutôt qu'un gros commit ?
- Que doit contenir un message de commit utile ?

</div>

---

# Branches, merge et conflits

Workflow simple pour débuter, inspiré de **GitHub Flow** : créer une branche courte, committer, ouvrir une demande de fusion, relire, tester, fusionner vers `main` <span class="opacity-50 text-sm">[S3]</span>.

```bash
# Créer une branche
git switch -c feature/page-status

# Modifier des fichiers, puis committer
git add .
git commit -m "feat(status): add health page"

# Pousser la branche
git push -u origin feature/page-status
```

---

# Cycle de collaboration recommandé

<div class="grid grid-cols-3 gap-3 text-sm pt-4">
<div v-for="(step, i) in steps" :key="i" class="civit-callout py-2 px-3">
{{ i + 1 }}. {{ step }}
</div>
</div>

<script setup>
const steps = [
  "créer une issue ou tâche",
  "créer une branche nommée clairement",
  "faire des commits petits et cohérents",
  "pousser la branche",
  "ouvrir une merge request",
  "laisser la CI s'exécuter",
  "corriger les remarques",
  "fusionner",
  "supprimer la branche",
]
</script>

---

# Résoudre un conflit simple

Un conflit apparaît lorsque Git ne sait pas combiner automatiquement deux modifications concurrentes.

```bash
# Récupérer les changements distants
git fetch origin

# Rejouer ou fusionner selon le workflow choisi
git merge origin/main

# Ouvrir les fichiers en conflit, choisir le contenu final,
# puis marquer comme résolu
git add fichier-en-conflit.md
git commit
```

Dans le fichier, Git montre souvent :

```text
 <<<<<<< HEAD
version locale
=======
version distante
>>>>>>> origin/main
```

L'apprenant doit **supprimer les marqueurs** et conserver le contenu correct.

---

# Messages de commit, versions et changelog

Les messages de commit doivent aider les humains **et** les outils.

- **Conventional Commits** : `type(scope): description`, lisible et exploitable par l'automatisation <span class="opacity-50 text-sm">[S4]</span>
- **SemVer** : une version `MAJOR.MINOR.PATCH` communique l'impact d'une évolution <span class="opacity-50 text-sm">[S5]</span>
- **Keep a Changelog** : un changelog doit être écrit pour les humains, pas un dump de logs Git <span class="opacity-50 text-sm">[S6]</span>

```text
feat(auth): add refresh token endpoint
fix(payment): prevent duplicate invoice creation
docs(readme): document docker compose usage
ci(gitlab): cache node dependencies
refactor(api): split user controller
```

---

# Types de commit pour ce cours

<div class="grid grid-cols-2 gap-x-8 text-sm">

| Type | Quand l'utiliser |
|---|---|
| `feat` | Nouvelle fonctionnalité visible. |
| `fix` | Correction de bug. |
| `docs` | Documentation. |
| `test` | Ajout ou correction de tests. |

| Type | Quand l'utiliser |
|---|---|
| `ci` | Pipeline, GitLab CI, Jenkins, GitHub Actions. |
| `build` | Dépendances, packaging, Dockerfile. |
| `refactor` | Restructuration sans changement fonctionnel. |
| `chore` | Tâches annexes. |

</div>

---

# Tags et changelog

```bash
# Créer un tag annoté
git tag -a v1.0.0 -m "Release v1.0.0"

# Envoyer les tags
git push origin v1.0.0
```

Extrait de `CHANGELOG.md` :

```markdown
# Changelog

## [1.1.0] - 2026-06-12

### Added
- Ajout d'une page de statut `/health`.

### Fixed
- Correction d'un bug de connexion avec token expiré.
```

---

# Maintenance, évolution et procédure bug

Le module demande de distinguer **maintenance** et **évolution applicative** <span class="opacity-50 text-sm">[S0]</span>.

| Catégorie | Définition pratique | Exemple |
|---|---|---|
| Maintenance curative | Corriger un défaut constaté. | Fix d'une erreur 500 en production. |
| Maintenance préventive | Réduire un risque avant incident. | Mise à jour d'une dépendance vulnérable. |
| Maintenance évolutive | Ajouter ou modifier une capacité métier. | Ajout d'un export CSV demandé par les utilisateurs. |
| Maintenance adaptative | Adapter le logiciel à un changement externe. | Changement de version de BDD ou d'API partenaire. |

---

# Modèle de ticket bug reproductible

```markdown
## Résumé
Décrire le problème en une phrase.

## Environnement
- Version applicative : v...
- Environnement : dev / staging / prod
- Navigateur ou client : ...
- Date / heure : ...

## Étapes de reproduction
1. ...
2. ...
3. ...

## Résultat attendu
...

## Résultat obtenu
...

## Logs / captures / traces
...

## Gravité estimée
Bloquant / majeur / mineur
```

---

# Diagnostic de premier niveau

<div class="grid grid-cols-2 gap-4 pt-6">
<div v-for="(step, i) in steps" :key="i" class="civit-callout py-3 px-4 text-sm">
<span class="text-civit-blue font-bold">{{ i + 1 }}.</span> {{ step }}
</div>
</div>

<script setup>
const steps = [
  "Reproduire le bug ou constater qu'il n'est pas reproductible.",
  "Identifier la version déployée : tag Git, image Docker, commit SHA.",
  "Lire les logs applicatifs et ceux du pipeline.",
  "Vérifier les variables d'environnement et dépendances externes.",
  "Comparer avec le dernier changement connu.",
  "Décider : correction, rollback, hotfix, escalade.",
]
</script>

---
layout: section
class: civit-section
---

# 4. DevOps
## Valeurs, principes et pratiques

---

# CALMS comme grille de lecture

<div class="text-sm">

| Pilier | Question à poser à l'équipe | Exemple de pratique |
|---|---|---|
| **C**ulture | Développeurs, ops, QA et métier partagent-ils la responsabilité du service ? | Post-mortem sans blâme, revues croisées. |
| **A**utomation | Qu'est-ce qui est encore manuel, répétitif ou fragile ? | Pipeline CI/CD, tests automatiques, déploiement scripté. |
| **L**ean | Où sont les attentes, gaspillages et retours tardifs ? | Petits lots, branches courtes, feedback rapide. |
| **M**easurement | Comment sait-on que l'on s'améliore ? | DORA, taux d'échec, temps de restauration, couverture utile. |
| **S**haring | Comment circule la connaissance ? | README, runbook, démonstrations, documentation vivante. |

</div>

DevOps n'est pas uniquement un rôle ou un outil : c'est une démarche de collaboration qui fluidifie le passage de l'idée à la valeur livrée, tout en maintenant la stabilité opérationnelle.

---

# Métriques DORA en pratique

Les métriques DORA ne servent pas à classer les personnes, mais à comprendre un **système de livraison** <span class="opacity-50 text-sm">[S8]</span>.

| Métrique | Sens | Exemple de mesure débutante |
|---|---|---|
| Lead time for changes | Temps entre commit et déploiement. | Date du commit jusqu'au déploiement staging. |
| Deployment frequency | Fréquence de déploiement. | Nombre de déploiements staging par semaine. |
| Change failure rate | Part des déploiements qui provoquent un incident. | Déploiements ayant nécessité rollback ou hotfix. |
| Failed deployment recovery time | Temps pour récupérer après un échec. | Durée entre incident et restauration du service. |

<div class="civit-callout-fire mt-4 text-sm">
<strong>Attention pédagogique.</strong> Une équipe débutante ne doit pas chercher « tout automatiser » le premier jour. Elle doit d'abord rendre visible son flux.
</div>

---

# Pratiques DevOps attendues dans ce module

<div class="grid grid-cols-2 gap-3 text-sm pt-4">

- **Versionner** le code, les scripts, la documentation et la configuration non sensible.
- **Intégrer souvent** via des branches courtes et une CI systématique.
- **Tester automatiquement** ce qui peut l'être : unitaires, intégration, lint, smoke tests.
- **Construire une fois, déployer plusieurs fois** : même artefact ou image vers staging puis prod.
- **Paramétrer par environnement** : variables, secrets, endpoints, volumes.
- **Observer** : logs, métriques, traces, santé applicative.
- **Prévoir le rollback** avant de déployer.
- **Documenter** : README, runbook, changelog, procédure de diagnostic.

</div>

---

# Application 12-Factor : repères utiles

La méthodologie **Twelve-Factor App** propose des principes pour rendre une application déployable et portable <span class="opacity-50 text-sm">[S9]</span>.

<div class="text-sm">

| Principe utile | Traduction opérationnelle |
|---|---|
| Codebase unique | Un dépôt par application ou service, versionné dans Git. |
| Dépendances explicites | Déclarer `package.json`, `requirements.txt`, `pom.xml`, etc. |
| Config dans l'environnement | Ne pas hardcoder les mots de passe ni URL de production. |
| Build / release / run séparés | Construire une image puis l'exécuter avec une configuration. |
| Processus stateless | Éviter de stocker l'état applicatif dans le conteneur. |
| Logs en flux | Écrire sur stdout/stderr, agréger ensuite. |
| Parité dev/prod | Limiter les différences entre local, staging et prod. |

</div>

---
layout: section
class: civit-section
---

# 5. Environnements, mise en production et maintenance

---

# Environnements classiques

Le déploiement est le passage d'une version livrable vers un environnement cible. Il faut choisir une **stratégie**, maîtriser la **configuration**, connaître le **plan de rollback** et vérifier que le service fonctionne.

| Environnement | But | Règles habituelles |
|---|---|---|
| Local | Développer vite. | Données factices, logs verbeux, Docker Compose possible. |
| Intégration | Assembler les contributions. | CI systématique, données non sensibles. |
| Test / QA | Valider fonctionnellement. | Jeux de tests maîtrisés, version proche de staging. |
| Staging / préproduction | Répéter la production. | Configuration proche prod, validation release. |
| Production | Servir les utilisateurs. | Accès restreint, observabilité, sauvegardes, rollback. |

---
layout: image
image: /images/schema_05_strategies_deploiement.png
backgroundSize: contain
---

<div class="absolute bottom-4 left-4 text-xs opacity-70 bg-black bg-opacity-40 px-2 py-1 rounded">
Schéma 5 - Stratégies de déploiement
</div>

---

# Stratégies de déploiement

<div class="text-sm">

| Stratégie | Principe | Avantages | Limites |
|---|---|---|---|
| Go live / big bang | Toute la nouvelle version est activée d'un coup. | Simple à comprendre. | Risque élevé, rollback parfois lent. |
| Site pilote | Déploiement sur un périmètre restreint. | Retour utilisateur réel limité. | Gérer plusieurs populations. |
| Rolling | Remplacement progressif des instances. | Moins d'interruption, courant avec orchestration. | Deux versions peuvent cohabiter. |
| Blue/green | Deux environnements identiques ; bascule du trafic. | Rollback rapide par rebascule <span class="opacity-50">[S20]</span>. | Coût d'infra et synchronisation. |
| Canary | Une petite part du trafic reçoit v2, puis extension <span class="opacity-50">[S21]</span>. | Réduit l'impact d'un bug, favorise la mesure. | Besoin de routage et observabilité solides. |

</div>

Les rolling updates remplacent progressivement les instances, par exemple dans Kubernetes <span class="opacity-50 text-sm">[S22]</span>.

---

# Checklist de mise en production — Avant

<div class="civit-callout space-y-2 mt-4">

- La version est identifiée par un tag Git et/ou un tag d'image.
- Les tests critiques sont verts.
- Les migrations de base de données sont préparées et réversibles si possible.
- Les variables d'environnement sont connues et documentées.
- Le plan de rollback est écrit.
- Les parties prenantes savent quoi vérifier après déploiement.

</div>

---

# Checklist de mise en production — Pendant / Après

<div class="grid grid-cols-2 gap-6 pt-4">

<div>

### Pendant

<div class="civit-callout space-y-2 text-sm">

- Suivre les logs de déploiement.
- Vérifier la santé du service : endpoint `/health`, statut conteneur, réponse HTTP.
- Surveiller erreurs, latence, consommation CPU/RAM.
- Noter l'heure exacte et la version déployée.

</div>
</div>

<div>

### Après

<div class="civit-callout-fire space-y-2 text-sm">

- Exécuter un smoke test.
- Mettre à jour le changelog ou la release note.
- Créer un ticket d'incident si un contournement a été nécessaire.
- Débriefer les irritants du déploiement.

</div>
</div>

</div>

---
layout: section
class: civit-section
---

# 6. Conteneurisation avec Docker

---

# Pourquoi Docker ?

La conteneurisation permet de **packager une application et son environnement d'exécution** dans une image.

- Docker documente conteneur, image, registry, Dockerfile, couches et Compose dans son parcours de démarrage <span class="opacity-50 text-sm">[S11]</span>
- La CNCF rattache les conteneurs à l'approche **cloud native** : systèmes résilients, observables et automatisables <span class="opacity-50 text-sm">[S10]</span>

---
layout: image-right
image: /images/schema_04_conteneurisation.png
backgroundSize: contain
---

# Image, conteneur, registry

| Concept | À retenir | Commande typique |
|---|---|---|
| Image | Modèle immuable construit à partir d'un Dockerfile. | `docker build -t app:dev .` |
| Conteneur | Processus isolé lancé depuis une image. | `docker run app:dev` |
| Registry | Entrepôt d'images taguées. | `docker push registry/app:1.0.0` |
| Volume | Stockage persistant séparé du conteneur. | `docker volume create data` |
| Réseau | Communication entre conteneurs. | `docker network create app-net` |

<div class="text-xs opacity-60 mt-4">
Docker décrit un conteneur comme un processus isolé avec son propre système de fichiers, réseau et arbre de processus <span class="opacity-50">[S15]</span>.
</div>

---

# Commandes Docker essentielles

```bash
# Télécharger une image
docker pull nginx:alpine

# Lancer un conteneur en arrière-plan
docker run -d --name web -p 8080:80 nginx:alpine

# Voir les conteneurs
docker ps

# Lire les logs
docker logs web

# Entrer dans un conteneur
docker exec -it web sh

# Arrêter et supprimer
docker stop web
docker rm web
```

---

# Écrire un Dockerfile propre

Un `Dockerfile` est un fichier texte qui liste les instructions nécessaires à la construction d'une image <span class="opacity-50 text-sm">[S12]</span>.

Instructions courantes :

<div class="flex gap-2 flex-wrap mt-4">
<span v-for="kw in keywords" :key="kw" class="civit-callout px-3 py-1 font-mono text-sm">{{ kw }}</span>
</div>

<script setup>
const keywords = ["FROM", "RUN", "COPY", "ENV", "EXPOSE", "CMD", "ENTRYPOINT", "USER", "WORKDIR"]
</script>

---

# Exemple Node.js multi-stage (1/2)

```dockerfile
# syntax=docker/dockerfile:1

FROM node:22-alpine AS deps
WORKDIR /app
COPY package*.json ./
RUN npm ci

FROM node:22-alpine AS build
WORKDIR /app
COPY --from=deps /app/node_modules ./node_modules
COPY . .
RUN npm test
RUN npm run build
```

---

# Exemple Node.js multi-stage (2/2)

```dockerfile
FROM node:22-alpine AS runtime
WORKDIR /app
ENV NODE_ENV=production
COPY --from=build /app/dist ./dist
COPY package*.json ./
RUN npm ci --omit=dev
USER node
EXPOSE 3000
CMD ["node", "dist/server.js"]
```

<div class="civit-callout mt-6 text-sm">
Docker recommande les <strong>builds multi-stage</strong> pour réduire la taille de l'image finale et séparer la construction de l'exécution <span class="opacity-50">[S13]</span>.
</div>

---

# Bonnes pratiques Dockerfile

<div class="grid grid-cols-2 gap-6">

<div class="text-sm space-y-2">

- commencer par une image de base officielle et maintenue ;
- copier les fichiers de dépendances avant le code pour profiter du cache ;
- utiliser `.dockerignore` ;
- éviter de lancer l'application en `root` quand c'est possible ;
- exposer le port attendu ;
- ne pas mettre de secrets dans l'image ;
- taguer l'image avec une version ou un commit SHA ;
- ajouter un healthcheck applicatif.

</div>

<div>

### Exemple `.dockerignore`

```text
.git
node_modules
dist
coverage
.env
*.log
```

</div>

</div>

---

# Docker Compose pour les dépendances locales

Docker Compose permet de définir et lancer des applications multi-conteneurs via un fichier YAML <span class="opacity-50 text-sm">[S14]</span>.

```yaml
services:
  api:
    build: .
    ports:
      - "3000:3000"
    environment:
      NODE_ENV: development
      DATABASE_URL: postgres://app:app@db:5432/app
    depends_on:
      - db

  db:
    image: postgres:16-alpine
    environment:
      POSTGRES_USER: app
      POSTGRES_PASSWORD: app
      POSTGRES_DB: app
    volumes:
      - db-data:/var/lib/postgresql/data

volumes:
  db-data:
```

---

# Commandes Docker Compose

```bash
# Construire et démarrer
docker compose up --build

# Démarrer en arrière-plan
docker compose up -d

# Voir les logs
docker compose logs -f api

# Arrêter
docker compose down

# Supprimer aussi les volumes de données locales
docker compose down -v
```

---

# Sécurité minimale des conteneurs

L'OWASP DevSecOps Guideline encourage l'intégration de contrôles de sécurité dans les pipelines et la culture **shift-left** <span class="opacity-50 text-sm">[S23]</span>.

Pour ce module, appliquer au minimum :

<div class="civit-callout-fire space-y-2 mt-6">

- ne jamais committer de secrets ;
- scanner les dépendances et images quand l'outil est disponible ;
- utiliser des variables protégées/masquées dans la CI ;
- limiter les droits du runner et du conteneur ;
- tracer l'image déployée : tag, digest, commit ;
- corriger les vulnérabilités critiques avant mise en production.

</div>

---
layout: section
class: civit-section
---

# 7. Pipeline CI/CD

---
layout: image
image: /images/schema_03_pipeline_cicd.png
backgroundSize: contain
---

<div class="absolute bottom-4 left-4 text-xs opacity-70 bg-black bg-opacity-40 px-2 py-1 rounded">
Schéma 3 - Pipeline CI/CD
</div>

---

# Stages recommandés pour le TP

La pipeline CI/CD est la chaîne automatisée qui transforme un changement Git en résultat vérifié : rapport, artefact, image, déploiement.

<div class="text-sm">

| Stage | But | Exemple |
|---|---|---|
| `validate` | Vérifier format, lint, configuration. | `npm run lint`, `mvn validate`. |
| `test` | Exécuter tests automatisés. | Unitaires, intégration légère. |
| `build` | Construire artefact ou image. | `docker build`. |
| `security` | Scanner dépendances ou image. | Trivy, npm audit, OWASP Dependency-Check. |
| `package` | Publier artefact ou image. | Push vers registry. |
| `deploy:staging` | Déployer en préproduction. | SSH + Docker Compose, Kubernetes, PaaS. |
| `deploy:prod` | Promotion contrôlée. | Job manuel protégé. |

</div>

---

# Exemple GitLab CI — structure

GitLab CI démarre avec un fichier `.gitlab-ci.yml` à la racine du projet, qui définit stages, jobs et scripts <span class="opacity-50 text-sm">[S16]</span>. Les pipelines peuvent être déclenchés par push, merge request, schedule ou manuellement <span class="opacity-50 text-sm">[S17][S18]</span>.

```yaml
stages:
  - validate
  - test
  - build
  - deploy

variables:
  IMAGE_TAG: "$CI_REGISTRY_IMAGE:$CI_COMMIT_SHORT_SHA"
```

Les **variables CI/CD** permettent de passer de la configuration et des secrets aux jobs <span class="opacity-50 text-sm">[S16]</span>.

---

# Exemple GitLab CI — validate & test

```yaml
lint:
  stage: validate
  image: node:22-alpine
  script:
    - npm ci
    - npm run lint

unit_tests:
  stage: test
  image: node:22-alpine
  script:
    - npm ci
    - npm test
  artifacts:
    when: always
    paths:
      - coverage/
    expire_in: 1 week
```

---

# Exemple GitLab CI — build de l'image

```yaml
build_image:
  stage: build
  image: docker:27
  services:
    - docker:27-dind
  script:
    - docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD" "$CI_REGISTRY"
    - docker build -t "$IMAGE_TAG" .
    - docker push "$IMAGE_TAG"
```

---

# Exemple GitLab CI — déploiement

```yaml
staging:
  stage: deploy
  image: alpine:3.20
  environment: staging
  needs:
    - build_image
  script:
    - echo "Déployer $IMAGE_TAG vers staging"
  rules:
    - if: '$CI_COMMIT_BRANCH == "main"'

production:
  stage: deploy
  image: alpine:3.20
  environment: production
  when: manual
  script:
    - echo "Promotion contrôlée vers production"
  rules:
    - if: '$CI_COMMIT_BRANCH == "main"'
```

---

# Points à faire commenter aux apprenants

<div class="civit-callout space-y-3 text-lg mt-8">

- un job doit **échouer** si le test échoue ;
- une image doit être **taguée par commit**, pas seulement `latest` ;
- les variables sensibles doivent être définies dans **l'interface CI**, pas dans Git ;
- la **production peut rester manuelle** pour respecter la gouvernance.

</div>

---

# Exemple Jenkinsfile

Dans Jenkins, un `Jenkinsfile` versionné avec le code décrit la pipeline : revue de code de la pipeline, trace d'audit, source unique de vérité <span class="opacity-50 text-sm">[S19]</span>.

```groovy
pipeline {
  agent any
  environment {
    IMAGE_TAG = "registry.example.com/team/app:${env.GIT_COMMIT.take(8)}"
  }
  stages {
    stage('Checkout') { steps { checkout scm } }
    stage('Install')  { steps { sh 'npm ci' } }
    stage('Test') {
      steps { sh 'npm test' }
      post { always { junit 'reports/junit.xml' } }
    }
    stage('Build image') { steps { sh 'docker build -t $IMAGE_TAG .' } }
    stage('Deploy staging') { steps { sh './deploy/staging.sh $IMAGE_TAG' } }
  }
}
```

---

# Choisir un outil CI pour le cours

<div class="text-sm">

| Outil | Points forts | Points d'attention |
|---|---|---|
| GitLab CI | Intégré à GitLab, `.gitlab-ci.yml`, runners, registry, variables. | Nécessite de comprendre YAML et runners. |
| Jenkins | Très flexible, plugins, Jenkinsfile, self-hosted. | Administration plus lourde, plugins à maintenir. |
| GitHub Actions | Pratique si dépôt GitHub, marketplace d'actions. | YAML spécifique, attention aux secrets et permissions. |
| Travis CI | Connu historiquement, simple pour certains projets open source. | Moins central que GitLab/GitHub/Jenkins aujourd'hui. |

</div>

---

# Pipeline-as-code : règles de qualité

<div class="civit-callout-fire space-y-2 mt-6">

- La pipeline est **versionnée** dans le dépôt.
- Elle est **revue** comme du code applicatif.
- Elle **évite les secrets en clair**.
- Elle produit des **logs compréhensibles**.
- Elle sépare **build, test et déploiement**.
- Elle **échoue vite** en cas de problème.
- Elle garde une **trace** de ce qui a été déployé.
- Elle permet de **relancer ou diagnostiquer** sans dépendre d'une personne.

</div>

---
layout: section
class: civit-section
---

# 8. TP fil rouge
## Déployer un projet existant

---

# Sujet proposé

**Mission.** Votre équipe reçoit une application existante. Vous devez la rendre **déployable de façon reproductible et automatisée** <span class="opacity-50 text-sm">[S0]</span>.

### Livrables attendus

<div class="grid grid-cols-2 gap-x-8 text-sm pt-2">

1. dépôt Git propre
2. branches et merge requests
3. `README.md` d'installation locale
4. `Dockerfile`
5. `docker-compose.yml` si dépendance externe

6. pipeline CI avec tests et build
7. déploiement staging automatisé ou semi-automatisé
8. `CHANGELOG.md`
9. procédure de mise en production et rollback
10. fiche de diagnostic d'incident

</div>

---

# Architecture de dépôt recommandée

```text
mon-application/
|-- .gitignore
|-- .gitlab-ci.yml            # ou Jenkinsfile
|-- CHANGELOG.md
|-- Dockerfile
|-- README.md
|-- docker-compose.yml
|-- deploy/
|   |-- staging.sh
|   `-- rollback.sh
|-- docs/
|   |-- procedure-deploiement.md
|   `-- procedure-incident.md
|-- src/
`-- tests/
```

---

# Étape A — Audit initial

<div class="civit-callout space-y-2 text-lg mt-6">

- Le projet démarre-t-il localement ?
- Quelle commande lance les tests ?
- Quelle version du runtime est nécessaire ?
- Quelles variables d'environnement existent ?
- Où sont les logs ?
- Y a-t-il un fichier de dépendances ?
- Quelles données ne doivent jamais être versionnées ?

</div>

---

# Étape B — Git et documentation

```bash
git switch -c docs/bootstrap
# Créer ou compléter README.md, CHANGELOG.md, docs/
git add README.md CHANGELOG.md docs/
git commit -m "docs: document local bootstrap"
git push -u origin docs/bootstrap
```

---

# Étape C — Conteneurisation

```bash
git switch -c build/dockerfile
# Ajouter Dockerfile et .dockerignore
docker build -t mon-app:dev .
docker run --rm -p 3000:3000 mon-app:dev
git add Dockerfile .dockerignore
git commit -m "build(docker): containerize application"
```

---

# Étape D — Compose local

```bash
git switch -c build/compose
# Ajouter docker-compose.yml
docker compose up --build
# Vérifier l'application et les logs
docker compose logs -f
git add docker-compose.yml
git commit -m "build(compose): add local stack"
```

---

# Étape E — Pipeline CI

```bash
git switch -c ci/pipeline
# Ajouter .gitlab-ci.yml ou Jenkinsfile
git add .gitlab-ci.yml
git commit -m "ci: add validation and image build pipeline"
git push -u origin ci/pipeline
```

### Critères de réussite

<div class="civit-callout space-y-1 text-sm mt-4">

- la pipeline démarre automatiquement ;
- un échec de test bloque le pipeline ;
- les logs indiquent clairement l'étape en erreur ;
- un artefact ou une image est produit ;
- les secrets ne sont pas dans le dépôt.

</div>

---

# Étape F — Déploiement staging

Version simple par SSH + Docker Compose, à adapter au contexte :

```bash
#!/usr/bin/env sh
set -eu

IMAGE_TAG="$1"
APP_DIR="/opt/mon-app"

ssh deploy@staging.example.com <<EOF
  set -eu
  cd "$APP_DIR"
  export IMAGE_TAG="$IMAGE_TAG"
  docker compose pull
  docker compose up -d
  docker compose ps
EOF
```

Smoke test minimal :

```bash
curl -fsS https://staging.example.com/health
```

---

# Étape G — Rollback

Un rollback doit être prévu **avant** le déploiement.

<div class="grid grid-cols-2 gap-4 pt-6">
<div v-for="(step, i) in steps" :key="i" class="civit-callout py-3 px-4 text-sm">
<span class="text-civit-blue font-bold">{{ i + 1 }}.</span> {{ step }}
</div>
</div>

<script setup>
const steps = [
  "identifier la dernière version stable",
  "relancer le déploiement avec l'ancien tag d'image",
  "vérifier /health",
  "vérifier les logs",
  "créer un incident et documenter la cause",
  "décider hotfix ou retour au backlog",
]
</script>

---

# Grille d'évaluation formative

<div class="text-sm">

| Critère | Points | Observables |
|---|---:|---|
| Git et collaboration | 20 | Branches, commits lisibles, MR, résolution de conflit, historique propre. |
| Documentation | 15 | README, changelog, procédures déploiement/incident, variables documentées. |
| Conteneurisation | 20 | Dockerfile fonctionnel, image reproductible, Compose si nécessaire, pas de secrets. |
| Pipeline CI/CD | 25 | Stages cohérents, tests bloquants, image/artefact produit, variables sécurisées. |
| Déploiement et rollback | 15 | Staging déployé, smoke test, rollback décrit ou testé. |
| Compréhension DevOps | 5 | Capacité à expliquer CALMS, CI/CD, environnement, métriques et risques. |

</div>

<div class="text-right font-bold mt-4 text-civit-blue">Total : 100 points</div>

---
layout: section
class: civit-section
---

# 9. Exercices courts à insérer pendant le cours

---

# Quiz Git de 10 minutes

<div class="civit-callout space-y-3 text-lg mt-6">

1. Quelle commande montre les fichiers modifiés ?
2. Quelle différence entre `git add` et `git commit` ?
3. Pourquoi éviter de travailler directement sur `main` ?
4. Qu'est-ce qu'un conflit ?
5. Que contient un bon message de commit ?
6. Pourquoi un tag est-il utile pour un déploiement ?

</div>

---

# Atelier conflit Git

**En binômes :**

<div class="grid grid-cols-2 gap-4 pt-6">
<div v-for="(step, i) in steps" :key="i" class="civit-callout py-3 px-4 text-sm">
<span class="text-civit-blue font-bold">{{ i + 1 }}.</span> {{ step }}
</div>
</div>

<div class="civit-callout-fire mt-8 text-sm">
Débrief : comment éviter les conflits longs ?
</div>

<script setup>
const steps = [
  "Les deux apprenants modifient la même ligne d'un fichier.",
  "L'un pousse sa modification.",
  "L'autre tente de pousser, récupère, observe le conflit.",
  "Le binôme résout le conflit ensemble.",
]
</script>

---

# Atelier pipeline cassée

L'intervenant fournit une pipeline volontairement cassée :

<div class="civit-callout-fire space-y-2 text-lg mt-6">

- nom de stage incorrect ;
- dépendance manquante ;
- test qui échoue ;
- variable non définie ;
- image Docker non taguée.

</div>

<div class="civit-callout mt-6">
<strong>Objectif :</strong> diagnostiquer à partir des logs, proposer une correction, créer un commit <code>fix(ci): ...</code>
</div>

---

# Atelier incident

**Scénario** : la version `v1.2.0` déployée en staging répond `500` sur `/api/orders`.

### Travail demandé

<div class="civit-callout space-y-2 text-lg mt-4">

- reproduire ;
- identifier le commit et l'image ;
- consulter les logs ;
- décider rollback ou hotfix ;
- rédiger un ticket d'incident ;
- proposer une amélioration de pipeline pour détecter plus tôt.

</div>

---
layout: section
class: civit-section
---

# 10. Antisèches

---

# Antisèche Git

```bash
# Initialiser / cloner
git init
git clone git@example.com:team/app.git

# Observer
git status
git diff
git log --oneline --graph --decorate --all

# Committer
git add .
git commit -m "feat: add feature"

# Branches
git branch
git switch -c feature/name
git switch main

# Synchroniser
git fetch
git pull
git push

# Annuler prudemment
git restore file.txt
git revert <commit_sha>
```

---

# Antisèche Docker

```bash
# Images
docker build -t app:dev .
docker images
docker image inspect app:dev

# Conteneurs
docker run --rm -p 3000:3000 app:dev
docker ps
docker logs <container>
docker exec -it <container> sh

# Nettoyage
docker stop <container>
docker rm <container>
docker system df

# Compose
docker compose up --build
docker compose ps
docker compose logs -f
docker compose down
```

---

# Questions à se poser avant de merger

<div class="civit-callout space-y-2 text-lg mt-6">

- Le code est-il testé ?
- La pipeline est-elle verte ?
- Le changement est-il documenté ?
- Le rollback est-il possible ?
- Les secrets sont-ils absents du diff ?
- Le changement modifie-t-il une API publique ?
- Faut-il incrémenter la version ?
- Faut-il prévenir les utilisateurs ou l'exploitation ?

</div>

---
layout: section
class: civit-section
---

# 11. Erreurs fréquentes et corrections

---

# Erreurs fréquentes et corrections (1/2)

<div class="text-sm">

| Problème | Symptôme | Correction |
|---|---|---|
| Secret committé | Token visible dans Git. | Révoquer le secret, purger si nécessaire, utiliser variables CI. |
| Image `latest` partout | Impossible de savoir ce qui est déployé. | Taguer avec version ou commit SHA. |
| Pipeline trop lente | Les développeurs l'ignorent. | Cache, étapes parallèles, tests ciblés, images adaptées. |
| Dockerfile non reproductible | Build différent selon la machine. | Dépendances lockées, image de base taguée, `.dockerignore`. |

</div>

---

# Erreurs fréquentes et corrections (2/2)

<div class="text-sm">

| Problème | Symptôme | Correction |
|---|---|---|
| Déploiement manuel non documenté | Une seule personne sait livrer. | Script + runbook + revue. |
| Tests uniquement locaux | La MR semble bonne mais casse après merge. | Exécuter les tests en CI. |
| Environnements trop différents | « Ça marche chez moi ». | Docker Compose, variables documentées, parité staging/prod. |
| Rollback improvisé | Incident plus long. | Procédure rollback testée avant production. |

</div>

---
layout: section
class: civit-section
---

# 12. Glossaire rapide

---

# Glossaire (1/2)

<div class="text-sm">

| Terme | Définition |
|---|---|
| Artefact | Fichier produit par le build : paquet, rapport, archive, image. |
| Build | Transformation du code source en livrable. |
| CD | Livraison ou déploiement continu selon le niveau d'automatisation. |
| CI | Intégration continue, vérification automatique des changements. |
| Commit SHA | Identifiant unique d'un commit Git. |
| Feature flag | Interrupteur logiciel pour activer/désactiver une fonctionnalité. |
| Hotfix | Correction rapide d'un incident, souvent prioritaire. |

</div>

---

# Glossaire (2/2)

<div class="text-sm">

| Terme | Définition |
|---|---|
| Image digest | Identifiant immuable du contenu d'une image. |
| Infrastructure immuable | Remplacer plutôt que modifier manuellement une instance déployée. |
| Merge request | Demande de fusion avec revue, discussions et pipeline. |
| Registry | Entrepôt d'images Docker. |
| Rollback | Retour à une version précédente connue comme stable. |
| Runner / agent | Machine ou processus exécutant les jobs de CI. |
| Smoke test | Test rapide confirmant que le service répond après déploiement. |
| Staging | Environnement de préproduction proche de la production. |

</div>

---
layout: section
class: civit-section
---

# 13. Sources et bibliographie

---

# Sources principales

Les schémas de ce support sont **originaux** et ne reprennent pas d'images propriétaires.

<div class="text-xs grid grid-cols-2 gap-x-6 gap-y-1">

- **[S0]** CESI, *Fiche module INF83*, cahier des charges 2025
- **[S1][S2]** Git SCM, *Pro Git book*
- **[S3]** GitHub Docs, *GitHub flow*
- **[S4]** Conventional Commits 1.0.0
- **[S5]** Semantic Versioning 2.0.0
- **[S6]** Keep a Changelog 1.1.0
- **[S7]** Atlassian, *CALMS Framework*
- **[S8]** DORA, *Software delivery performance metrics*
- **[S9]** The Twelve-Factor App
- **[S10]** CNCF, *Cloud Native Definition*
- **[S11][S12][S13][S14][S15]** Docker Docs
- **[S16][S17][S18]** GitLab Docs, *CI/CD*
- **[S19]** Jenkins Docs, *Jenkinsfile*
- **[S20]** AWS, *Deployment strategies*
- **[S21]** Google Cloud, *Canary deployment*
- **[S22]** Kubernetes Docs, *Rolling Update*
- **[S23]** OWASP, *DevSecOps Guideline*
- **[S24][S25][S26]** OpenClassrooms
- **[S27]** ScholarVox, *Learning DevOps*

</div>

---
layout: cover
class: civit-section
---

<div class="absolute top-10 right-10 civit-badge">
  <span>Civilisation<span class="fire">IT</span></span>
</div>

# Merci !

## Questions, pratique, et place au TP fil rouge 🚀

<div class="civit-callout mt-12 inline-block text-left">

**Support préparé par CivilisationIT**
Tutoriels DevOps écrits & vidéo : <a href="https://civilisation-it.fr" target="_blank">civilisation-it.fr</a>

Intervenant CESI — module INF83
</div>
