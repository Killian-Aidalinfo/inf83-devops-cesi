---
theme: seriph
colorSchema: light
layout: cover
background: '#ffffff'
title: INF83 - Déploiement continu DevOps
titleTemplate: '%s · CivilisationIT'
info: |
  ## INF83 - Déploiement continu DevOps
  Versionning, culture DevOps, conteneurisation, CI/CD et mise en production automatisée.

  Support de cours - CESI - par CivilisationIT
class: text-left
drawings:
  persist: false
transition: slide-left
mdc: true
fonts:
  sans: Inter
  mono: Fira Code
css: unocss
hideInToc: true
---

<style>
/* ── Cover ─────────────────────────────────────────────────
   Fond blanc comme les autres diapos (frontmatter background: #ffffff).
   Bleu uniquement : fin liseré de marque à gauche + titre dégradé bleu. */
.slidev-layout.cover {
  position: relative;
  overflow: hidden;
}
.slidev-layout.cover::after {
  content: "";
  position: absolute;
  left: 0; top: 0; bottom: 0;
  width: 5px;
  background: linear-gradient(180deg, var(--civit-blue) 0%, var(--civit-fire) 100%);
}
.slidev-layout.cover h1 {
  font-size: 4.2rem;
  line-height: 1.05;
  background: linear-gradient(115deg, var(--civit-blue) 0%, var(--civit-blue-dark) 100%);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
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
  <span class="px-3 py-1 rounded-full civit-callout text-sm">CESI : CDA</span>
</div>

<div class="pt-4 text-sm">
  <a href="https://killian-aidalinfo.github.io/inf83-devops-cesi/tp/" target="_blank" class="text-civit-blue">→ Parcours TP (créneaux libres)</a>
</div>

<div class="abs-bottom-12 left-12 text-sm opacity-70">
  Support pédagogique préparé par <strong>CivilisationIT</strong><br>
  Intervenant CESI
</div>

---
hideInToc: true
---

# Le programme de la semaine 🗓️

<div class="text-lg opacity-60 -mt-1 mb-5">Cinq jours, du premier commit à la mise en production automatisée.</div>

<div class="chapters-grid">
  <div class="ch"><span class="n">1</span> Positionnement du cours</div>
  <div class="ch"><span class="n">2</span> Vue d'ensemble</div>
  <div class="ch"><span class="n">3</span> Culture DevOps</div>
  <div class="ch"><span class="n">4</span> Git — versionning & évolution applicative</div>
  <div class="ch"><span class="n">5</span> Environnements, mise en prod & maintenance</div>
  <div class="ch"><span class="n">6</span> Conteneurisation avec Docker</div>
  <div class="ch"><span class="n">7</span> Pipeline CI/CD</div>
  <div class="ch"><span class="n">8</span> Tests automatisés</div>
  <div class="ch"><span class="n">9</span> Supervision & observabilité</div>
  <div class="ch highlight"><span class="n">10</span> Projet continu 🚀</div>
</div>

<div class="text-sm opacity-60 mt-5">
+ Annexes en fin de support : exercices, antisèches, erreurs fréquentes, glossaire, sources.
</div>

<style>
.chapters-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 0.6rem 1.2rem;
}
.chapters-grid .ch {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.55rem 0.9rem;
  border: 1px solid rgba(14, 165, 233, 0.20);
  border-radius: 12px;
  background: rgba(14, 165, 233, 0.04);
  font-weight: 600;
  color: var(--civit-navy);
}
.chapters-grid .ch .n {
  flex: none;
  width: 1.7rem; height: 1.7rem;
  display: inline-flex; align-items: center; justify-content: center;
  border-radius: 50%;
  background: linear-gradient(135deg, var(--civit-blue), var(--civit-blue-dark));
  color: #fff; font-size: 0.85rem; font-weight: 700;
}
.chapters-grid .highlight {
  border-color: var(--civit-blue);
  background: rgba(14, 165, 233, 0.10);
}
</style>

---
layout: two-cols
class: gap-8
hideInToc: true
---

# Qui suis-je ? 👋

**Killian Stein** — intervenant CESI · fondateur de **CivilisationIT**

**Mon parcours**
- Alternance **TSR**, puis **ASR**, puis **MAALSI**
- **CDI chez Aidalinfo** & autoentrepreneur
- DevOps / SRE / Cloud au quotidien

**Partage & vulgarisation**
- Conférences *Cyberday 2024 & 2025*, *Henri-Poincaré 2025*
- Blog & tutoriels DevOps écrits

::right::

<div class="civit-callout mt-12">

### Au quotidien

- 🐳 Docker, CI/CD, supervision
- ☁️ Cloud (Scaleway, OVH…)
- 🔧 DevOps / SRE / automatisation

</div>

<div class="civit-callout-fire mt-6 text-sm">
🔥 N'hésitez pas à m'interrompre, poser des questions et challenger les exemples : ce cours est aussi le vôtre.
</div>

---
hideInToc: true
---

# Et vous ? Présentez-vous 🎤

<div class="text-xl opacity-60 -mt-1 mb-8">Petit tour de table avant de commencer — chacun en quelques mots.</div>

<div class="intro-grid">
  <div class="q-card">
    <span class="ic">💼</span>
    <div><strong>Vous travaillez ?</strong><br><span class="hint">Où, et en quoi consiste votre poste ?</span></div>
  </div>
  <div class="q-card">
    <span class="ic">🛠️</span>
    <div><strong>Vous faites quoi ?</strong><br><span class="hint">Dev, ops, data, sécurité… ?</span></div>
  </div>
  <div class="q-card">
    <span class="ic">💻</span>
    <div><strong>Votre stack / langage principal ?</strong><br><span class="hint">Node, PHP, Java, Python… ?</span></div>
  </div>
  <div class="q-card">
    <span class="ic">📈</span>
    <div><strong>Votre niveau en DevOps ?</strong><br><span class="hint">(philosophie, Git, conteneurisation, CI/CD)</span></div>
  </div>
  <div class="q-card span-2">
    <span class="ic">✨</span>
    <div><strong>Vos attentes</strong> pour ces 5 jours ?</div>
  </div>
</div>

<style>
.intro-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 0.85rem;
}
.intro-grid .span-2 { grid-column: 1 / -1; }
.intro-grid .q-card {
  display: flex;
  align-items: center;
  gap: 0.9rem;
  padding: 0.95rem 1.15rem;
  border: 1px solid rgba(14, 165, 233, 0.22);
  border-radius: 14px;
  background: linear-gradient(180deg, rgba(14, 165, 233, 0.06), rgba(14, 165, 233, 0.015));
  transition: border-color .2s ease;
}
.intro-grid .ic { font-size: 1.7rem; line-height: 1; flex: none; }
.intro-grid strong { color: var(--civit-navy); font-weight: 700; }
.intro-grid .hint { color: var(--civit-muted); font-size: 0.92em; }
</style>

---
hideInToc: true
---

# Votre projet fil rouge CESI 🎯

<div class="text-lg opacity-60 -mt-1 mb-6">À CESI, vous menez un projet fil rouge à travers les modules — servons-nous-en.</div>

<div class="grid grid-cols-2 gap-6">

<div class="civit-callout">

### Dites-moi
- C'est **quoi** ? (sujet, techno, langage)
- Où en êtes-vous ? (démarré, en cours, à finaliser)
- **Seul ou en équipe** ?
- Déjà sur **Git / GitHub** ?

</div>

<div class="civit-callout-fire">

### On peut s'en servir comme support
- **Conteneuriser** votre vrai projet (perso ou CESI)
- Lui ajouter une **CI/CD** et du **monitoring**
- Sinon : une **petite app** créée dans votre langage

</div>

</div>

<div class="civit-callout mt-6 text-sm">
🎙️ Ça me permet d'<strong>adapter</strong> les TP à vos projets — les compétences DevOps vues ici sont directement réinvestissables dans votre fil rouge CESI.
</div>

---
layout: section
class: civit-section
---

# 1. Positionnement du cours

---
hideInToc: true
---

# Pré-requis et matériel recommandé

Chaque apprenant doit disposer de :

- un terminal utilisable ;
- un éditeur ou IDE ;
- Git installé et configuré ;
- Docker Desktop ou Docker Engine selon l'environnement de formation ;
- un accès à une forge Git, par exemple GitHub ;
- un accès à une solution CI : GitHub Actions, ou instance fournie par l'intervenant ;
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
hideInToc: true
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
hideInToc: true
class: loop-slide
---

# Boucle DevOps : livrer plus vite sans casser la production

<div class="text-base opacity-60 -mt-1">Chaque étape automatisée ; les mesures et le feedback nourrissent la boucle suivante.</div>

<div class="loop-wrap">
<svg viewBox="0 0 900 600" class="loop-svg">
<defs>
<linearGradient id="ring" x1="0" y1="0" x2="1" y2="1">
<stop offset="0%" stop-color="#0ea5e9"/><stop offset="100%" stop-color="#1971a0"/></linearGradient>
<filter id="sh" x="-30%" y="-30%" width="160%" height="160%">
<feDropShadow dx="0" dy="3" stdDeviation="4" flood-color="#0ea5e9" flood-opacity="0.16"/></filter>
</defs>
<line x1="450.0" y1="130.0" x2="450.0" y2="65.0" stroke="#0ea5e9" stroke-width="1.6" stroke-dasharray="3 3" opacity="0.65"/>
<line x1="580.8" y1="184.2" x2="696.1" y2="138.2" stroke="#0ea5e9" stroke-width="1.6" stroke-dasharray="3 3" opacity="0.65"/>
<line x1="635.0" y1="315.0" x2="798.0" y2="315.0" stroke="#0ea5e9" stroke-width="1.6" stroke-dasharray="3 3" opacity="0.65"/>
<line x1="580.8" y1="445.8" x2="696.1" y2="491.8" stroke="#0ea5e9" stroke-width="1.6" stroke-dasharray="3 3" opacity="0.65"/>
<line x1="450.0" y1="500.0" x2="450.0" y2="565.0" stroke="#1971a0" stroke-width="1.6" stroke-dasharray="3 3" opacity="0.65"/>
<line x1="319.2" y1="445.8" x2="203.9" y2="491.8" stroke="#1971a0" stroke-width="1.6" stroke-dasharray="3 3" opacity="0.65"/>
<line x1="265.0" y1="315.0" x2="102.0" y2="315.0" stroke="#1971a0" stroke-width="1.6" stroke-dasharray="3 3" opacity="0.65"/>
<line x1="319.2" y1="184.2" x2="203.9" y2="138.2" stroke="#1971a0" stroke-width="1.6" stroke-dasharray="3 3" opacity="0.65"/>
<circle cx="450" cy="315" r="185" fill="none" stroke="url(#ring)" stroke-width="2.5" stroke-dasharray="2 9" stroke-linecap="round" opacity="0.6"/>
<path d="M -5,-5 L 6,0 L -5,5 Z" fill="#94a3b8" transform="translate(520.8,144.1) rotate(22.5)"/>
<path d="M -5,-5 L 6,0 L -5,5 Z" fill="#94a3b8" transform="translate(620.9,244.2) rotate(67.5)"/>
<path d="M -5,-5 L 6,0 L -5,5 Z" fill="#94a3b8" transform="translate(620.9,385.8) rotate(112.5)"/>
<path d="M -5,-5 L 6,0 L -5,5 Z" fill="#94a3b8" transform="translate(520.8,485.9) rotate(157.5)"/>
<path d="M -5,-5 L 6,0 L -5,5 Z" fill="#94a3b8" transform="translate(379.2,485.9) rotate(202.5)"/>
<path d="M -5,-5 L 6,0 L -5,5 Z" fill="#94a3b8" transform="translate(279.1,385.8) rotate(247.5)"/>
<path d="M -5,-5 L 6,0 L -5,5 Z" fill="#94a3b8" transform="translate(279.1,244.2) rotate(292.5)"/>
<path d="M -5,-5 L 6,0 L -5,5 Z" fill="#94a3b8" transform="translate(379.2,144.1) rotate(337.5)"/>
<circle cx="450" cy="315" r="70" fill="#f0f9ff" stroke="#0ea5e9" stroke-width="2" filter="url(#sh)"/>
<text class="hub" x="450" y="309" text-anchor="middle">Feedback</text>
<text class="hsub" x="450" y="329" text-anchor="middle">logs · métriques</text>
<text class="hsub" x="450" y="344" text-anchor="middle">incidents · users</text>
<rect x="376.0" y="51.0" width="148" height="28" rx="9" fill="#f8fafc" stroke="#0ea5e9" stroke-width="1.2" stroke-opacity="0.55"/>
<text class="det" x="450.0" y="65.0" text-anchor="middle" dominant-baseline="central">issues · backlog</text>
<rect x="622.1" y="124.2" width="148" height="28" rx="9" fill="#f8fafc" stroke="#0ea5e9" stroke-width="1.2" stroke-opacity="0.55"/>
<text class="det" x="696.1" y="138.2" text-anchor="middle" dominant-baseline="central">commits · branches</text>
<rect x="724.0" y="301.0" width="148" height="28" rx="9" fill="#f8fafc" stroke="#0ea5e9" stroke-width="1.2" stroke-opacity="0.55"/>
<text class="det" x="798.0" y="315.0" text-anchor="middle" dominant-baseline="central">build · image Docker</text>
<rect x="622.1" y="477.8" width="148" height="28" rx="9" fill="#f8fafc" stroke="#0ea5e9" stroke-width="1.2" stroke-opacity="0.55"/>
<text class="det" x="696.1" y="491.8" text-anchor="middle" dominant-baseline="central">tests · CI</text>
<rect x="376.0" y="551.0" width="148" height="28" rx="9" fill="#f8fafc" stroke="#1971a0" stroke-width="1.2" stroke-opacity="0.55"/>
<text class="det" x="450.0" y="565.0" text-anchor="middle" dominant-baseline="central">registry ghcr.io</text>
<rect x="129.9" y="477.8" width="148" height="28" rx="9" fill="#f8fafc" stroke="#1971a0" stroke-width="1.2" stroke-opacity="0.55"/>
<text class="det" x="203.9" y="491.8" text-anchor="middle" dominant-baseline="central">staging → prod</text>
<rect x="28.0" y="301.0" width="148" height="28" rx="9" fill="#f8fafc" stroke="#1971a0" stroke-width="1.2" stroke-opacity="0.55"/>
<text class="det" x="102.0" y="315.0" text-anchor="middle" dominant-baseline="central">run · scaling</text>
<rect x="129.9" y="124.2" width="148" height="28" rx="9" fill="#f8fafc" stroke="#1971a0" stroke-width="1.2" stroke-opacity="0.55"/>
<text class="det" x="203.9" y="138.2" text-anchor="middle" dominant-baseline="central">logs · alertes</text>
<g filter="url(#sh)"><rect x="380.0" y="107.0" width="140" height="46" rx="13" fill="#fff" stroke="#0ea5e9" stroke-width="2"/>
<circle cx="406.0" cy="130.0" r="13" fill="#0ea5e9"/>
<text class="num" x="406.0" y="130.0" text-anchor="middle" dominant-baseline="central">1</text>
<text class="lbl" x="427.0" y="130.0" dominant-baseline="central">Planifier</text></g>
<g filter="url(#sh)"><rect x="510.8" y="161.2" width="140" height="46" rx="13" fill="#fff" stroke="#0ea5e9" stroke-width="2"/>
<circle cx="536.8" cy="184.2" r="13" fill="#0ea5e9"/>
<text class="num" x="536.8" y="184.2" text-anchor="middle" dominant-baseline="central">2</text>
<text class="lbl" x="557.8" y="184.2" dominant-baseline="central">Coder</text></g>
<g filter="url(#sh)"><rect x="565.0" y="292.0" width="140" height="46" rx="13" fill="#fff" stroke="#0ea5e9" stroke-width="2"/>
<circle cx="591.0" cy="315.0" r="13" fill="#0ea5e9"/>
<text class="num" x="591.0" y="315.0" text-anchor="middle" dominant-baseline="central">3</text>
<text class="lbl" x="612.0" y="315.0" dominant-baseline="central">Construire</text></g>
<g filter="url(#sh)"><rect x="510.8" y="422.8" width="140" height="46" rx="13" fill="#fff" stroke="#0ea5e9" stroke-width="2"/>
<circle cx="536.8" cy="445.8" r="13" fill="#0ea5e9"/>
<text class="num" x="536.8" y="445.8" text-anchor="middle" dominant-baseline="central">4</text>
<text class="lbl" x="557.8" y="445.8" dominant-baseline="central">Tester</text></g>
<g filter="url(#sh)"><rect x="380.0" y="477.0" width="140" height="46" rx="13" fill="#fff" stroke="#1971a0" stroke-width="2"/>
<circle cx="406.0" cy="500.0" r="13" fill="#1971a0"/>
<text class="num" x="406.0" y="500.0" text-anchor="middle" dominant-baseline="central">5</text>
<text class="lbl" x="427.0" y="500.0" dominant-baseline="central">Publier</text></g>
<g filter="url(#sh)"><rect x="249.2" y="422.8" width="140" height="46" rx="13" fill="#fff" stroke="#1971a0" stroke-width="2"/>
<circle cx="275.2" cy="445.8" r="13" fill="#1971a0"/>
<text class="num" x="275.2" y="445.8" text-anchor="middle" dominant-baseline="central">6</text>
<text class="lbl" x="296.2" y="445.8" dominant-baseline="central">Déployer</text></g>
<g filter="url(#sh)"><rect x="195.0" y="292.0" width="140" height="46" rx="13" fill="#fff" stroke="#1971a0" stroke-width="2"/>
<circle cx="221.0" cy="315.0" r="13" fill="#1971a0"/>
<text class="num" x="221.0" y="315.0" text-anchor="middle" dominant-baseline="central">7</text>
<text class="lbl" x="242.0" y="315.0" dominant-baseline="central">Exploiter</text></g>
<g filter="url(#sh)"><rect x="249.2" y="161.2" width="140" height="46" rx="13" fill="#fff" stroke="#1971a0" stroke-width="2"/>
<circle cx="275.2" cy="184.2" r="13" fill="#1971a0"/>
<text class="num" x="275.2" y="184.2" text-anchor="middle" dominant-baseline="central">8</text>
<text class="lbl" x="296.2" y="184.2" dominant-baseline="central">Observer</text></g>
</svg>
</div>

<div class="loop-legend">
  <span><i style="background:#0ea5e9"></i> Dev — planifier → tester</span>
  <span><i style="background:#1971a0"></i> Ops — publier → observer</span>
</div>

<style>
.loop-slide h1 { font-size: 1.8rem; line-height: 1.12; }
.loop-wrap { display:flex; justify-content:center; }
.loop-svg { width:100%; max-width:600px; height:auto; display:block; }
.loop-svg .lbl { font-size:15px; font-weight:700; fill:#0b1220; font-family:Inter,sans-serif; }
.loop-svg .num { font-size:14px; font-weight:700; fill:#fff; font-family:Inter,sans-serif; }
.loop-svg .hub { font-size:21px; font-weight:800; fill:#0b1220; font-family:Inter,sans-serif; }
.loop-svg .hsub { font-size:11px; fill:#64748b; font-family:Inter,sans-serif; }
.loop-svg .det { font-size:11.5px; fill:#475569; font-family:Inter,sans-serif; }
.loop-legend { position:absolute; left:2.5rem; top:50%; transform:translateY(-50%); display:flex; flex-direction:column; gap:0.7rem; align-items:flex-start; font-size:0.85rem; color:var(--civit-navy); }
.loop-legend i { display:inline-block; width:0.8rem; height:0.8rem; border-radius:50%; margin-right:0.4rem; vertical-align:middle; }
.loop-legend .muted { color:var(--civit-muted); }
</style>

---
hideInToc: true
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
hideInToc: true
---

# Les mots à maîtriser dès le début (1/2)

<div class="text-sm">

| Terme | Définition courte | Exemple concret |
|---|---|---|
| Dépôt | Espace versionné contenant code, historique et configuration. | Projet GitHub avec `README.md`, `src/`, `Dockerfile`. |
| Commit | Point d'historique décrivant un changement cohérent. | `fix(auth): reject expired token` |
| Branche | Ligne de travail isolée. | `feature/checkout`, `fix/login-500` |
| Merge / Pull request | Demande de fusion avec discussion, revue, CI. | Fusionner une branche dans `main`. |
| Pipeline | Suite automatisée d'étapes. | Installer, tester, construire, scanner, déployer. |
| Artefact | Résultat produit par le pipeline. | Rapport de tests, paquet `.jar`, image Docker. |

</div>

---
hideInToc: true
---

# Les mots à maîtriser dès le début (2/2)

<div class="text-sm">

| Terme | Définition courte | Exemple concret |
|---|---|---|
| Image Docker | Modèle immuable d'exécution. | `registry.example.com/app:1.2.0` |
| Conteneur | Processus isolé lancé à partir d'une image. | Service API démarré par `docker run`. |
| Registry | Entrepôt d'images. | Docker Hub, GitHub Container Registry (`ghcr.io`). |
| Environnement | Cible de déploiement avec configuration propre. | `dev`, `test`, `staging`, `prod` |
| Secret | Donnée sensible injectée sans être commitée. | Mot de passe DB, token API. |

</div>

---
hideInToc: true
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

# 3. DevOps
## Valeurs, principes et pratiques

---
hideInToc: true
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
hideInToc: true
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
hideInToc: true
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
hideInToc: true
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
hideInToc: true
---

# Roadmap DevOps 🗺️

Le DevOps couvre un **écosystème vaste** (cf. *roadmap.sh*). Ce module en prend une **tranche concrète** — le socle du déploiement continu :

<div class="grid grid-cols-3 gap-3 mt-4 text-sm">
  <div class="rm on">Git & forge</div>
  <div class="rm on">Conteneurs · Docker</div>
  <div class="rm on">CI/CD</div>
  <div class="rm on">Tests</div>
  <div class="rm on">Supervision</div>
  <div class="rm">Langage de programmation</div>
  <div class="rm">Cloud</div>
  <div class="rm">IaC (Terraform / Ansible)</div>
  <div class="rm">Orchestration (Kubernetes)</div>
</div>

<div class="civit-callout-fire mt-5 text-sm">
🎯 Le DevOps a aussi donné naissance à des <strong>métiers spécialisés</strong> : DevSecOps, FinOps, MLOps… — ce module pose le <strong>socle commun</strong>.
</div>

<style>
.rm { border:1px solid rgba(14,165,233,0.22); border-radius:10px; padding:0.55rem 0.85rem; background:rgba(14,165,233,0.04); color:var(--civit-muted); }
.rm.on { border-color:var(--civit-blue); background:rgba(14,165,233,0.12); color:var(--civit-navy); font-weight:700; }
.rm.on::before { content:"✓ "; color:var(--civit-blue-dark); }
</style>

---
hideInToc: true
---

# Open source & DevOps 🔓

La culture DevOps est **étroitement liée à l'open source** : elles partagent les mêmes valeurs — **transparence, collaboration, partage**.

<div class="grid grid-cols-2 gap-5 mt-4">

<div class="civit-callout">

### Pourquoi c'est essentiel
- **Innovation rapide** et transparence
- **Collaboration** entre communautés → des outils qui évoluent en continu
- **Interopérabilité**, pas de dépendance à un seul fournisseur (*no vendor lock-in*)
- Des infrastructures plus **flexibles, maîtrisables et durables**

</div>

<div class="civit-callout-fire">

### Dans ce cours
Presque tous nos outils sont **open source** :

**Git · Docker · Trivy · Prometheus · Grafana · K6**

<div class="text-sm opacity-70 mt-2">⚠️ <strong>GitHub Actions</strong>, lui, est <strong>propriétaire</strong> — mais il orchestre des outils open source.</div>

</div>

</div>

---
layout: section
class: civit-section
---

# 4. Versionning et évolution applicative avec Git

---
hideInToc: true
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

<div class="civit-callout-fire mt-3">
<strong>À retenir.</strong> En DevOps, Git n'est pas que l'outil des développeurs : c'est le déclencheur du pipeline, le lieu de revue et la source de vérité de la configuration.
</div>

---
layout: image-right
image: /images/schema_02_git_lifecycle.png
backgroundSize: contain
hideInToc: true
---

# Modèle mental Git pour débutants

Git distingue plusieurs zones :

1. **Répertoire de travail** : fichiers visibles dans le dossier projet.
2. **Index / staging area** : sélection des changements qui entreront dans le prochain commit.
3. **Dépôt local** : historique de commits sur la machine.
4. **Dépôt distant** : dépôt partagé sur GitHub ou un serveur interne.

<div class="text-xs opacity-60 mt-4">Schéma 2 - Cycle de vie Git</div>

---
hideInToc: true
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
hideInToc: true
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
hideInToc: true
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
hideInToc: true
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
hideInToc: true
---

# Questions de débrief

<div class="civit-callout text-lg space-y-4 mt-8">

- Qu'est-ce qui est versionné ?
- Quelle différence entre `git add` et `git commit` ?
- Pourquoi faire deux commits plutôt qu'un gros commit ?
- Que doit contenir un message de commit utile ?

</div>

---
hideInToc: true
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
hideInToc: true
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
  "ouvrir une pull request",
  "laisser la CI s'exécuter",
  "corriger les remarques",
  "fusionner",
  "supprimer la branche",
]
</script>

---
hideInToc: true
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
hideInToc: true
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
ci(actions): cache node dependencies
refactor(api): split user controller
```

---
hideInToc: true
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
| `ci` | Pipeline CI : GitHub Actions. |
| `build` | Dépendances, packaging, Dockerfile. |
| `refactor` | Restructuration sans changement fonctionnel. |
| `chore` | Tâches annexes. |

</div>

---
hideInToc: true
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
hideInToc: true
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
hideInToc: true
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
hideInToc: true
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

# 5. Environnements, mise en production et maintenance

---
hideInToc: true
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
title: Schéma — Stratégies de déploiement
hideInToc: true
---

<div class="absolute bottom-4 left-4 text-xs opacity-70 bg-black bg-opacity-40 px-2 py-1 rounded">
Schéma 5 - Stratégies de déploiement
</div>

---
hideInToc: true
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
hideInToc: true
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
hideInToc: true
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
hideInToc: true
---

# Pourquoi Docker ?

La conteneurisation permet de **packager une application et son environnement d'exécution** dans une image.

- Docker documente conteneur, image, registry, Dockerfile, couches et Compose dans son parcours de démarrage <span class="opacity-50 text-sm">[S11]</span>
- La CNCF rattache les conteneurs à l'approche **cloud native** : systèmes résilients, observables et automatisables <span class="opacity-50 text-sm">[S10]</span>

<div class="civit-callout-fire mt-6 text-sm">
Une machine virtuelle embarque un <strong>OS invité complet</strong> (lourd, lent à démarrer). Un conteneur partage le <strong>noyau de l'hôte</strong> et n'isole que le nécessaire : il démarre en quelques secondes et pèse souvent quelques dizaines de Mo.
</div>

---
hideInToc: true
---

# Une brève histoire de la conteneurisation

Le conteneur n'est pas né avec Docker : c'est l'aboutissement de 30 ans d'isolation système <span class="opacity-50 text-sm">[S15]</span>.

<div class="text-sm">

| Année | Étape | Apport |
|---|---|---|
| **1979** | `chroot` | Première isolation : un processus voit un autre répertoire racine. |
| **2006** | `cgroups` + `namespaces` (Linux) | **Limiter** les ressources (CPU, RAM) et **isoler** les espaces réseau / FS / processus. |
| **2013** | **Docker** | Démocratisation : images + `Dockerfile` + `registry`, expérience développeur ultra-simple. |
| **2015** | **OCI** + **Kubernetes** | Standardisation des formats et industrialisation de l'orchestration à grande échelle. |

</div>

<div class="civit-callout mt-6 text-sm">
Un conteneur, techniquement = des <strong>namespaces</strong> (ce que le processus <em>voit</em>) + des <strong>cgroups</strong> (ce qu'il <em>consomme</em>). Docker n'a rien inventé de ce socle : il l'a rendu utilisable.
</div>

---
layout: image-right
image: /images/schema_04_conteneurisation.png
backgroundSize: contain
class: img-table
hideInToc: true
---

# Image, conteneur, registry

<div class="text-sm">

| Concept | À retenir | Commande typique |
|---|---|---|
| Image | Modèle immuable issu d'un Dockerfile. | `docker build -t app:dev .` |
| Conteneur | Processus isolé lancé depuis une image. | `docker run app:dev` |
| Registry | Entrepôt d'images taguées. | `docker push registry/app:1.0.0` |
| Volume | Stockage persistant hors conteneur. | `docker volume create data` |
| Réseau | Communication entre conteneurs. | `docker network create app-net` |

</div>

<div class="text-xs opacity-60 mt-3">
Un conteneur = un processus isolé avec son propre FS, réseau et arbre de processus <span class="opacity-50">[S15]</span>.
</div>

<style>
.img-table h1 { font-size: 1.9rem; line-height: 1.1; margin-bottom: 0.6rem; }
.img-table table { font-size: 0.82rem; }
.img-table td, .img-table th { padding: 0.32em 0.6em; }
.img-table code { font-size: 0.92em; }
</style>

---
hideInToc: true
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
hideInToc: true
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
hideInToc: true
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
hideInToc: true
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
hideInToc: true
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
hideInToc: true
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
hideInToc: true
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
hideInToc: true
---

# Les réseaux Docker

Docker fournit plusieurs pilotes réseau ; chacun répond à un besoin d'isolation ou d'exposition différent.

<div class="text-sm">

| Pilote | Principe | Quand l'utiliser |
|---|---|---|
| **bridge** (défaut) | Réseau NAT interne ; les conteneurs communiquent et sortent via l'hôte, on expose avec `-p`. | Cas le plus courant, un hôte unique. |
| **host** | Le conteneur utilise directement le réseau de l'hôte, sans isolation. | Performance maximale, pas d'isolation réseau. |
| **overlay** | Relie des conteneurs répartis sur plusieurs machines. | Docker Swarm, cluster multi-hôtes. |
| **macvlan / ipvlan** | Donne au conteneur une IP (et MAC) sur le réseau physique. | Le conteneur doit apparaître comme une machine du LAN. |
| **none** | Aucun réseau, conteneur totalement isolé. | Traitement hors-ligne, sécurité maximale. |

</div>

<div class="civit-callout mt-4 text-sm">
Compose crée automatiquement un réseau <strong>bridge</strong> dédié : les services s'y joignent par leur nom (<code>db</code>, <code>api</code>…) sans exposer de port vers l'extérieur.
</div>

---
hideInToc: true
---

# Sécurité minimale des conteneurs

L'OWASP DevSecOps Guideline encourage l'intégration de contrôles de sécurité dans les pipelines et la culture **shift-left** <span class="opacity-50 text-sm">[S23]</span>.

Pour ce module, appliquer au minimum :

<div class="civit-callout-fire space-y-2 mt-6">

- ne jamais committer de secrets ;
- scanner les dépendances et images quand l'outil est disponible ;
- utiliser des variables protégées/masquées dans la CI ;
- limiter les droits du runner et du conteneur (`USER`, capabilities) ;
- tracer l'image déployée : tag, digest, commit ;
- corriger les vulnérabilités critiques avant mise en production.

</div>

---
hideInToc: true
---

# Scanner une image avec Trivy

**Trivy** analyse une image (ou un dépôt) à la recherche de vulnérabilités connues (CVE) dans l'OS et les dépendances applicatives. C'est un excellent candidat pour un stage `security` du pipeline.

```bash
# Scanner une image construite localement
trivy image mon-app:dev

# Échouer le pipeline si une faille HIGH ou CRITICAL est trouvée
trivy image --severity HIGH,CRITICAL --exit-code 1 mon-app:dev
```

<div class="civit-callout mt-6 text-sm">
Autres outils du même esprit : <code>npm audit</code> / <code>pip-audit</code> pour les dépendances, <strong>SonarQube</strong> pour la qualité du code, <strong>Snyk</strong> et <strong>OWASP Dependency-Check</strong> pour les bibliothèques.
</div>

---
hideInToc: true
---

# Exposer proprement : reverse proxy

En production, on ne publie pas chaque conteneur sur un port brut. Un **reverse proxy** (Traefik, Nginx, Caddy) centralise l'entrée du trafic :

<div class="grid grid-cols-2 gap-6 text-sm mt-4">

<div class="civit-callout space-y-2">

**Rôle du reverse proxy**
- routage par nom de domaine ;
- terminaison **TLS / HTTPS** (certificats Let's Encrypt) ;
- répartition de charge entre instances ;
- point unique d'observation et de journalisation.

</div>

<div class="civit-callout-fire space-y-2">

**⚠️ Piège Docker + pare-feu**
- Docker insère ses propres règles `iptables` ;
- un port publié avec `-p` peut **contourner** une règle UFW ;
- ne pas croire qu'un `ufw deny 8080` suffit ;
- préférer n'exposer que le reverse proxy.

</div>

</div>

---
hideInToc: true
---

# Et après Docker : l'orchestration

Docker Compose suffit sur **un** hôte. Dès qu'il faut de la **haute disponibilité**, de la **montée en charge** automatique ou des **mises à jour sans interruption**, on passe à un orchestrateur.

<div class="text-sm">

| Outil | Positionnement |
|---|---|
| **Docker Swarm** | Orchestration native Docker, simple, syntaxe Compose. |
| **Kubernetes (K8s)** | Standard de l'industrie : self-healing, rolling updates, autoscaling. <span class="opacity-50">[S22]</span> |
| **Rancher / OpenShift** | Distributions et plateformes facilitant l'exploitation de K8s. |

</div>

<div class="civit-callout mt-4 text-sm">
L'orchestrateur prend en charge automatiquement ce qu'on faisait à la main : redémarrer un conteneur mort, répartir la charge, déployer en <strong>rolling update</strong>. Pour ce module, on reste sur Compose, mais il faut savoir où mène la suite.
</div>

---
layout: section
class: civit-section
---

# 7. Pipeline CI/CD

---
hideInToc: true
class: pipe-slide
---

# Pipeline CI/CD : du commit au déploiement contrôlé

<div class="text-base opacity-60 -mt-1">Chaque étape valide la précédente ; un échec arrête la chaîne et renvoie corriger dans Git.</div>

<div class="pipe-wrap">
<svg viewBox="0 0 1160 350" class="pipe-svg">
<defs><marker id="ad" markerWidth="9" markerHeight="9" refX="6" refY="3" orient="auto"><path d="M0,0 L6,3 L0,6 Z" fill="#475569"/></marker><marker id="ab" markerWidth="9" markerHeight="9" refX="6" refY="3" orient="auto"><path d="M0,0 L6,3 L0,6 Z" fill="#2563eb"/></marker><marker id="ar" markerWidth="9" markerHeight="9" refX="6" refY="3" orient="auto"><path d="M0,0 L6,3 L0,6 Z" fill="#ef4444"/></marker></defs>
<line x1="156" y1="95" x2="176" y2="95" stroke="#475569" stroke-width="2" marker-end="url(#ad)"/>
<line x1="316" y1="95" x2="336" y2="95" stroke="#475569" stroke-width="2" marker-end="url(#ad)"/>
<line x1="476" y1="95" x2="496" y2="95" stroke="#475569" stroke-width="2" marker-end="url(#ad)"/>
<line x1="636" y1="95" x2="656" y2="95" stroke="#475569" stroke-width="2" marker-end="url(#ad)"/>
<line x1="796" y1="95" x2="816" y2="95" stroke="#475569" stroke-width="2" marker-end="url(#ad)"/>
<line x1="956" y1="95" x2="976" y2="95" stroke="#475569" stroke-width="2" marker-end="url(#ad)"/>
<rect x="18" y="58" width="138" height="74" rx="12" fill="#dbeafe" stroke="#3b82f6" stroke-width="2"/>
<text x="87" y="95" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:14px;font-weight:700" fill="#0b1220">Commit + PR</text>
<rect x="178" y="58" width="138" height="74" rx="12" fill="#f3f4f6" stroke="#94a3b8" stroke-width="2"/>
<text x="247" y="86" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:14px;font-weight:700" fill="#0b1220">Installer</text><text x="247" y="105" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:14px;font-weight:700" fill="#0b1220">les dépendances</text>
<rect x="338" y="58" width="138" height="74" rx="12" fill="#d1fae5" stroke="#10b981" stroke-width="2"/>
<text x="407" y="95" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:14px;font-weight:700" fill="#0b1220">Lint + tests</text>
<rect x="498" y="58" width="138" height="74" rx="12" fill="#ffedd5" stroke="#f97316" stroke-width="2"/>
<text x="567" y="95" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:14px;font-weight:700" fill="#0b1220">Build image</text>
<rect x="658" y="58" width="138" height="74" rx="12" fill="#fee2e2" stroke="#ef4444" stroke-width="2"/>
<text x="727" y="95" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:14px;font-weight:700" fill="#0b1220">Scan sécurité</text>
<rect x="818" y="58" width="138" height="74" rx="12" fill="#ede9fe" stroke="#8b5cf6" stroke-width="2"/>
<text x="887" y="95" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:14px;font-weight:700" fill="#0b1220">Registry</text>
<rect x="978" y="58" width="138" height="74" rx="12" fill="#fef3c7" stroke="#f59e0b" stroke-width="2"/>
<text x="1047" y="86" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:14px;font-weight:700" fill="#0b1220">Déploiement</text><text x="1047" y="105" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:14px;font-weight:700" fill="#0b1220">staging</text>
<path d="M 567,132 C 567,195 570,195 570,248" fill="none" stroke="#475569" stroke-width="2" marker-end="url(#ad)"/>
<rect x="445" y="248" width="250" height="56" rx="10" fill="#f8fafc" stroke="#94a3b8" stroke-width="1.5"/>
<text x="570" y="276" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:13px;font-weight:600" fill="#334155">Artefacts : rapports, logs, image taguée</text>
<path d="M 1047,132 C 1047,200 918,200 918,248" fill="none" stroke="#2563eb" stroke-width="2.2" marker-end="url(#ab)"/>
<rect x="812" y="248" width="212" height="56" rx="10" fill="#eff6ff" stroke="#3b82f6" stroke-width="1.8"/>
<text x="918" y="267" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:12.5px;font-weight:600" fill="#1e3a8a">Validation manuelle</text><text x="918" y="286" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:12.5px;font-weight:600" fill="#1e3a8a">ou règle de promotion</text>
<line x1="1024" y1="276" x2="1049" y2="276" stroke="#2563eb" stroke-width="2.2" marker-end="url(#ab)"/>
<rect x="1052" y="248" width="88" height="56" rx="10" fill="#d1fae5" stroke="#10b981" stroke-width="2"/>
<text x="1096" y="276" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:15px;font-weight:700" fill="#065f46">Prod</text>
<path d="M 407,132 C 407,205 116,195 116,248" fill="none" stroke="#ef4444" stroke-width="2" stroke-dasharray="5 4" marker-end="url(#ar)"/>
<text x="262" y="210" text-anchor="middle" style="font-family:Inter,sans-serif;font-size:11px;font-weight:400" fill="#ef4444">si une étape échoue</text>
<rect x="18" y="248" width="196" height="56" rx="10" fill="#fee2e2" stroke="#ef4444" stroke-width="1.8"/>
<text x="116" y="276" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:12.5px;font-weight:700" fill="#991b1b">Échec : le pipeline s'arrête</text>
<line x1="214" y1="276" x2="229" y2="276" stroke="#475569" stroke-width="2" marker-end="url(#ad)"/>
<rect x="232" y="248" width="182" height="56" rx="10" fill="#dbeafe" stroke="#3b82f6" stroke-width="1.8"/>
<text x="323" y="276" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:13px;font-weight:700" fill="#1e3a8a">Correction dans Git</text>
</svg>
</div>

<style>
.pipe-slide h1 { font-size: 1.75rem; line-height: 1.1; }
.pipe-wrap { display:flex; justify-content:center; margin-top:0.8rem; }
.pipe-svg { width:100%; max-width:1040px; height:auto; display:block; }
</style>

---
hideInToc: true
class: flow-slide
---

# Deux flux : `dev` → staging, `main` → prod

<div class="text-base opacity-60 -mt-1">La branche de travail déploie en staging ; la fusion sur <code>main</code> déclenche le build et la mise en production.</div>

<div class="flow-wrap">
<svg viewBox="0 0 760 320" class="flow-svg">
<defs><marker id="ad" markerWidth="9" markerHeight="9" refX="6" refY="3" orient="auto"><path d="M0,0 L6,3 L0,6 Z" fill="#475569"/></marker><marker id="ap" markerWidth="9" markerHeight="9" refX="6" refY="3" orient="auto"><path d="M0,0 L6,3 L0,6 Z" fill="#8b5cf6"/></marker></defs>
<rect x="50" y="80" width="150" height="64" rx="12" fill="#dbeafe" stroke="#3b82f6" stroke-width="2"/>
<text x="125" y="103" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:12.5px;font-weight:600" fill="#1e3a8a">branche</text>
<text x="125" y="123" text-anchor="middle" dominant-baseline="central" style="font-family:Fira Code,monospace;font-size:16px;font-weight:700" fill="#1e3a8a">dev</text>
<line x1="200" y1="112" x2="254" y2="112" stroke="#475569" stroke-width="2" marker-end="url(#ad)"/>
<text x="227" y="100" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:11px;font-weight:500" fill="#64748b">push</text>
<rect x="262" y="80" width="196" height="64" rx="12" fill="#f3f4f6" stroke="#94a3b8" stroke-width="2"/>
<text x="360" y="112" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:13.5px;font-weight:600" fill="#334155">CI : lint · tests · build</text>
<line x1="458" y1="112" x2="514" y2="112" stroke="#475569" stroke-width="2" marker-end="url(#ad)"/>
<text x="486" y="100" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:11px;font-weight:500" fill="#64748b">déploie</text>
<rect x="522" y="80" width="150" height="64" rx="12" fill="#ccfbf1" stroke="#14b8a6" stroke-width="2"/>
<text x="597" y="112" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:16px;font-weight:700" fill="#0f766e">Staging</text>
<text x="597" y="158" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:10.5px;font-weight:500" fill="#94a3b8">préprod · validation</text>
<rect x="50" y="210" width="170" height="64" rx="12" fill="#ede9fe" stroke="#8b5cf6" stroke-width="2"/>
<text x="135" y="233" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:12.5px;font-weight:600" fill="#5b21b6">merge sur</text>
<text x="135" y="253" text-anchor="middle" dominant-baseline="central" style="font-family:Fira Code,monospace;font-size:16px;font-weight:700" fill="#5b21b6">main</text>
<line x1="220" y1="242" x2="274" y2="242" stroke="#475569" stroke-width="2" marker-end="url(#ad)"/>
<text x="247" y="230" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:11px;font-weight:500" fill="#64748b">build</text>
<rect x="282" y="210" width="196" height="64" rx="12" fill="#f3f4f6" stroke="#94a3b8" stroke-width="2"/>
<text x="380" y="242" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:13.5px;font-weight:600" fill="#334155">Build image + release</text>
<line x1="478" y1="242" x2="534" y2="242" stroke="#475569" stroke-width="2" marker-end="url(#ad)"/>
<text x="506" y="230" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:10.5px;font-weight:500" fill="#64748b">validation</text>
<rect x="542" y="210" width="150" height="64" rx="12" fill="#d1fae5" stroke="#10b981" stroke-width="2"/>
<text x="617" y="242" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:16px;font-weight:700" fill="#065f46">Prod</text>
<text x="617" y="288" text-anchor="middle" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:10.5px;font-weight:500" fill="#94a3b8">trafic réel</text>
<path d="M 125,144 C 125,180 135,180 135,210" fill="none" stroke="#8b5cf6" stroke-width="2.2" stroke-dasharray="5 4" marker-end="url(#ap)"/>
<text x="150" y="177" text-anchor="start" dominant-baseline="central" style="font-family:Inter,sans-serif;font-size:11px;font-weight:600" fill="#7c3aed">Pull Request mergée</text>
</svg>
</div>

<style>
.flow-slide h1 { font-size: 1.8rem; line-height: 1.12; }
.flow-slide h1 code { color: var(--civit-blue-dark); }
.flow-wrap { display:flex; justify-content:center; margin-top:1.4rem; }
.flow-svg { width:100%; max-width:820px; height:auto; display:block; }
</style>

---
hideInToc: true
---

# Exemple GitHub Actions — structure

GitHub Actions démarre avec un fichier dans `.github/workflows/` (ex. `ci.yml`), qui définit des **jobs** composés d'**étapes** (`steps`) <span class="opacity-50 text-sm">[S16]</span>. Les workflows se déclenchent sur push, pull request, schedule ou manuellement (`workflow_dispatch`) <span class="opacity-50 text-sm">[S17][S18]</span>.

```yaml
name: CI/CD
on:
  push:
    branches: [main]
  pull_request:
  workflow_dispatch:

env:
  IMAGE_TAG: ghcr.io/${{ github.repository }}:${{ github.sha }}
```

Les **secrets et variables** (définis dans *Settings → Secrets and variables*) sont passés aux jobs via `${{ secrets.X }}` <span class="opacity-50 text-sm">[S16]</span>.

---
hideInToc: true
---

# Exemple GitHub Actions — validate & test

```yaml
jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with: { node-version: 22 }
      - run: npm ci
      - run: npm run lint

  unit-tests:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with: { node-version: 22 }
      - run: npm ci
      - run: npm test
      - uses: actions/upload-artifact@v4
        if: always()
        with:
          name: coverage
          path: coverage/
          retention-days: 7
```

---
hideInToc: true
---

# Exemple GitHub Actions — build de l'image

```yaml
  build-image:
    runs-on: ubuntu-latest
    needs: [lint, unit-tests]
    permissions:
      contents: read
      packages: write          # pour pousser sur ghcr.io
    steps:
      - uses: actions/checkout@v4
      - uses: docker/login-action@v3
        with:
          registry: ghcr.io
          username: ${{ github.actor }}
          password: ${{ secrets.GITHUB_TOKEN }}
      - run: docker build -t "$IMAGE_TAG" .
      - run: docker push "$IMAGE_TAG"
```

<div class="civit-callout mt-4 text-sm">
Les runners GitHub ont déjà Docker : pas besoin de <code>docker:dind</code>. Le <code>GITHUB_TOKEN</code> est fourni automatiquement.
</div>

---
hideInToc: true
---

# Exemple GitHub Actions — scan de sécurité

Le job `scan-image` analyse l'image **réellement construite** et bloque sur les failles critiques.

```yaml
  scan-image:
    runs-on: ubuntu-latest
    needs: build-image
    steps:
      - name: Scan Trivy
        uses: aquasecurity/trivy-action@master
        with:
          image-ref: ${{ env.IMAGE_TAG }}
          severity: HIGH,CRITICAL
          exit-code: '1'   # une faille critique fait échouer le job
```

<div class="civit-callout mt-6 text-sm">
On place le scan <strong>après le build</strong> et <strong>avant le déploiement</strong> : inutile de promouvoir une image vulnérable. Pour démarrer en douceur, on peut mettre <code>exit-code: '0'</code> (ou <code>continue-on-error: true</code>) et durcir progressivement.
</div>

---
hideInToc: true
---

# Exemple GitHub Actions — déploiement

```yaml
  staging:
    runs-on: ubuntu-latest
    needs: build-image
    if: github.ref == 'refs/heads/main'
    environment: staging
    steps:
      - run: echo "Déployer $IMAGE_TAG vers staging"

  production:
    runs-on: ubuntu-latest
    needs: staging
    if: github.ref == 'refs/heads/main'
    environment: production   # protégée → validation manuelle requise
    steps:
      - run: echo "Promotion contrôlée vers production"
```

<div class="civit-callout mt-4 text-sm">
La <strong>promotion manuelle</strong> se gère via un <em>Environment</em> protégé (<em>Settings → Environments</em>) avec <em>required reviewers</em> : le job <code>production</code> attend une validation.
</div>

---
hideInToc: true
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

# 8. Tests automatisés
## Livrer vite **sans** livrer des bugs

---
hideInToc: true
---

# Pourquoi tester (et tester automatiquement) ?

Sans tests, chaque déploiement est un pari. Les tests sont le **filet de sécurité** qui autorise à livrer souvent et avec confiance — c'est le « **T** » implicite de toute pipeline CI.

<div class="grid grid-cols-2 gap-6 mt-6">

<div class="civit-callout space-y-2 text-sm">

**Ce que les tests apportent**
- détecter une régression avant l'utilisateur ;
- documenter le comportement attendu ;
- permettre de refactorer sans peur ;
- rendre la pipeline **bloquante** sur un échec.

</div>

<div class="civit-callout-fire space-y-2 text-sm">

**Le coût du bug grandit avec le temps**
- corrigé en local : quelques minutes ;
- corrigé en revue : quelques heures ;
- corrigé en production : incident, rollback, confiance.

→ principe **shift-left** : tester au plus tôt.

</div>

</div>

---
hideInToc: true
---

# La pyramide des tests

On cherche **beaucoup** de tests rapides à la base et **peu** de tests lents au sommet <span class="opacity-50 text-sm">[S28]</span>.

<div class="flex flex-col items-center gap-1 mt-6 text-sm">
  <div class="civit-callout-fire text-center" style="width: 30%">🖥️ <strong>E2E / UI</strong> — peu nombreux, lents, fragiles</div>
  <div class="civit-callout text-center" style="width: 55%">🔗 <strong>Intégration</strong> — moyens, vérifient les interactions</div>
  <div class="civit-callout text-center" style="width: 80%">🧩 <strong>Unitaires</strong> — nombreux, rapides, isolés</div>
</div>

<div class="civit-callout mt-8 text-sm">
Anti-pattern courant : le <strong>cône de glace</strong> (beaucoup de tests E2E lents, peu d'unitaires). Résultat : une pipeline lente, instable, que l'équipe finit par ignorer.
</div>

---
hideInToc: true
---

# Panorama des types de tests (1/2)

<div class="text-sm">

| Type | À quoi ça sert | Exemple d'outil |
|---|---|---|
| **Unitaire** | Vérifier une fonction / un composant isolé, sans dépendance externe. | Jest, Vitest, JUnit, pytest |
| **Intégration** | Vérifier que plusieurs composants fonctionnent ensemble (API + BDD). | Supertest, Testcontainers, pytest |
| **Fonctionnel / E2E** | Rejouer un parcours utilisateur complet dans un vrai navigateur. | Cypress, Playwright, Selenium |
| **Smoke test** | Vérifier en quelques secondes qu'un service répond après déploiement. | `curl /health`, script léger |

</div>

---
hideInToc: true
---

# Panorama des types de tests (2/2)

<div class="text-sm">

| Type | À quoi ça sert | Exemple d'outil |
|---|---|---|
| **Régression** | S'assurer qu'un bug corrigé ne revient pas (test ajouté avec le `fix`). | Le test ajouté à la suite existante |
| **Performance / charge** | Mesurer latence et débit sous trafic, trouver le point de rupture. | **K6**, Gatling, JMeter, Locust |
| **Sécurité** | Détecter vulnérabilités et dépendances à risque. | Trivy, OWASP ZAP, Snyk, `npm audit` |
| **API / contrat** | Vérifier le format et le comportement d'une API. | Postman, Newman, Pact |

</div>

<div class="civit-callout-fire mt-4 text-sm">
On ne cherche pas <strong>tout</strong> tester : on teste ce qui est <strong>risqué</strong>, ce qui <strong>change</strong> souvent et ce qui <strong>coûte cher</strong> en cas de panne.
</div>

---
hideInToc: true
---

# Les tests dans le pipeline

Chaque type de test trouve sa place à un moment précis de la chaîne CI/CD.

<div class="text-sm">

| Moment | Tests exécutés | Pourquoi là |
|---|---|---|
| À chaque commit / MR | Lint, unitaires, intégration légère | Feedback en quelques minutes, bloquant. |
| Avant le build d'image | Couverture, audit des dépendances | Ne pas empaqueter du code cassé. |
| Sur l'image construite | Scan de sécurité (Trivy) | Vérifier l'artefact réellement livré. |
| Après déploiement staging | Smoke test, E2E, performance | Valider dans un environnement proche prod. |

</div>

<div class="civit-callout mt-4 text-sm">
Règle d'or : <strong>un test qui échoue doit faire échouer le job</strong>. Un test « informatif » que personne ne regarde ne protège de rien.
</div>

---
hideInToc: true
---

# Exemple : test de performance avec K6

K6 décrit un scénario de charge **en code**, versionnable et exécutable en CI. Idéal pour relier **tests** et **supervision**.

```javascript
import http from 'k6/http';
import { check, sleep } from 'k6';

export const options = {
  vus: 50,              // 50 utilisateurs virtuels en parallèle
  duration: '30s',
  thresholds: {
    http_req_duration: ['p(95)<500'], // 95% des requêtes < 500 ms
    http_req_failed: ['rate<0.01'],   // moins de 1% d'erreurs
  },
};

export default function () {
  const res = http.get('https://staging.example.com/api/health');
  check(res, { 'status 200': (r) => r.status === 200 });
  sleep(1);
}
```

<div class="civit-callout-fire mt-2 text-sm">
Les <strong>thresholds</strong> transforment une mesure en verdict : si le p95 dépasse 500 ms, le test échoue. On peut ensuite <strong>envoyer ces métriques vers la stack de supervision</strong>.
</div>

---
layout: section
class: civit-section
---

# 9. Supervision et observabilité
## Savoir ce qui se passe **en production**

---
hideInToc: true
---

# Superviser : monitoring vs observabilité

Déployer ne suffit pas : il faut **savoir si le service va bien** et **pourquoi** quand il va mal. C'est le « **M**easurement » de CALMS et la base du métier **SRE** <span class="opacity-50 text-sm">[S29]</span>.

<div class="grid grid-cols-2 gap-6 mt-6 text-sm">

<div class="civit-callout space-y-2">

**Monitoring**
Surveiller des indicateurs **connus à l'avance** et alerter.
→ « Le CPU dépasse-t-il 80% ? Le service répond-il ? »

</div>

<div class="civit-callout-fire space-y-2">

**Observabilité**
Pouvoir **poser de nouvelles questions** sur le système sans le redéployer, pour comprendre l'inattendu.
→ « Pourquoi cette requête précise est-elle lente ? »

</div>

</div>

<div class="civit-callout mt-6 text-sm">
On supervise pour <strong>détecter</strong> (alerte), <strong>diagnostiquer</strong> (logs/traces) et <strong>améliorer</strong> (métriques DORA, capacité). C'est le prolongement direct de la fiche de diagnostic d'incident.
</div>

---
hideInToc: true
---

# Les 3 piliers de l'observabilité

<div class="grid grid-cols-3 gap-4 mt-6 text-sm">

<div class="civit-callout space-y-2 py-4">

### 📜 Logs
Événements horodatés, textuels.
*« Quoi s'est passé ? »*

- erreurs, requêtes, audit
- écrire sur **stdout/stderr** (12-Factor)
- agréger : Loki, ELK, Graylog

</div>

<div class="civit-callout space-y-2 py-4">

### 📊 Métriques
Valeurs numériques dans le temps.
*« Combien ? Quelle tendance ? »*

- CPU, RAM, latence, taux d'erreur
- légères, idéales pour alerter
- Prometheus + Grafana

</div>

<div class="civit-callout space-y-2 py-4">

### 🔍 Traces
Chemin d'une requête entre services.
*« Où est passé le temps ? »*

- utile en microservices
- relie les appels distribués
- Jaeger, Tempo, OpenTelemetry

</div>

</div>

---
hideInToc: true
---

# Les 4 signaux d'or (Golden Signals)

Pour superviser n'importe quel service, Google SRE recommande de suivre **quatre signaux** avant tout le reste <span class="opacity-50 text-sm">[S29]</span> :

<div class="grid grid-cols-2 gap-4 mt-6 text-sm">

<div class="civit-callout py-3"><strong class="text-civit-blue">Latence</strong> — temps de réponse (et distinguer réponses OK / en erreur).</div>
<div class="civit-callout py-3"><strong class="text-civit-blue">Trafic</strong> — demande adressée au service (req/s, connexions).</div>
<div class="civit-callout py-3"><strong class="text-civit-blue">Erreurs</strong> — taux de requêtes qui échouent (5xx, timeouts).</div>
<div class="civit-callout py-3"><strong class="text-civit-blue">Saturation</strong> — à quel point les ressources sont remplies (CPU, RAM, disque, file d'attente).</div>

</div>

<div class="civit-callout-fire mt-6 text-sm">
Ces signaux sont aussi des bons candidats à <strong>alerte</strong> : ils détectent un problème <em>côté utilisateur</em> avant qu'on n'ouvre les logs.
</div>

---
hideInToc: true
---

# SLI, SLO, SLA : mesurer la qualité de service

<div class="text-sm">

| Sigle | Définition | Exemple |
|---|---|---|
| **SLI** — *Service Level Indicator* | La **mesure** brute d'un aspect du service. | % de requêtes < 300 ms sur 30 jours. |
| **SLO** — *Service Level Objective* | La **cible** interne qu'on se fixe sur un SLI. | 99,5 % des requêtes < 300 ms. |
| **SLA** — *Service Level Agreement* | L'**engagement contractuel** envers le client (avec pénalités). | 99,9 % de dispo / mois, sinon pénalités. |

</div>

<div class="civit-callout mt-6 text-sm">
La marge entre l'objectif et 100 % est le <strong>budget d'erreur</strong> : il autorise à <em>prendre des risques de déploiement</em> tant qu'on le respecte. C'est ce qui réconcilie « livrer vite » (Dev) et « rester stable » (Ops).
</div>

---
hideInToc: true
---

# Une stack de supervision typique

Beaucoup d'outils open source structurent l'écosystème — souvent assemblés dans une même stack <span class="opacity-50 text-sm">[S30]</span>.

<div class="text-sm">

| Rôle | Outils courants |
|---|---|
| **Métriques** | Prometheus (collecte + alerting), VictoriaMetrics |
| **Tableaux de bord** | **Grafana** (visualise métriques, logs et traces) |
| **Logs** | Loki, ELK (Elasticsearch / Logstash / Kibana), OpenSearch, Graylog, Fluentd |
| **Disponibilité (uptime)** | Uptime Kuma, Blackbox Exporter |
| **Traces** | Jaeger, Tempo, OpenTelemetry |
| **Tout-en-un (SaaS)** | Datadog, Zabbix, Grafana Cloud |

</div>

<div class="civit-callout-fire mt-4 text-sm">
Combinaison de référence pour débuter : <strong>Prometheus + Grafana + Loki + Uptime Kuma</strong>, le tout déployé… en Docker Compose.
</div>

---
hideInToc: true
---

# Healthcheck, alerte et auto-remédiation

La supervision boucle avec le reste du cours : healthcheck déployé, alerte déclenchée, action automatique — l'esprit **SRE**.

```yaml
# Healthcheck Docker Compose : le conteneur se déclare "healthy" ou non
services:
  api:
    build: .
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:3000/health"]
      interval: 30s
      timeout: 3s
      retries: 3
```

<div class="grid grid-cols-2 gap-4 mt-4 text-sm">

<div class="civit-callout space-y-1">

**Une alerte utile** décrit :
- le **symptôme** (pas la cause supposée) ;
- la **gravité** et qui prévenir ;
- le **runbook** : quoi faire.

</div>

<div class="civit-callout-fire space-y-1">

**Exemple SRE (TP)** : disque > 80 %
1. métrique collectée par Prometheus ;
2. règle d'alerte déclenchée ;
3. script de `cleanup` lancé automatiquement.

</div>

</div>

---
hideInToc: true
---

# De l'alerte au pilotage

La supervision ne sert pas qu'à éteindre des incendies : elle **alimente les métriques DORA** et nourrit l'amélioration continue.

<div class="grid grid-cols-2 gap-4 pt-4">
<div v-for="(step, i) in supervisionSteps" :key="i" class="civit-callout py-3 px-4 text-sm">
<span class="text-civit-blue font-bold">{{ i + 1 }}.</span> {{ step }}
</div>
</div>

<div class="civit-callout-fire mt-6 text-sm">
Une bonne supervision réduit le <strong>temps de restauration</strong> (DORA) : on détecte plus vite, on diagnostique plus vite, on décide plus vite (rollback / hotfix).
</div>

<script setup>
const supervisionSteps = [
  "Détecter : une alerte se déclenche sur un signal d'or.",
  "Diagnostiquer : logs, métriques et traces corrélés dans Grafana.",
  "Décider : rollback, hotfix ou montée en charge.",
  "Apprendre : post-mortem sans blâme, nouvelle alerte ou nouveau test.",
]
</script>

---
layout: section
class: civit-section
---

# 10. Projet continu
## Déployer un projet existant

---
hideInToc: true
---

# Sujet proposé

**Mission.** Votre équipe reçoit une application existante. Vous devez la rendre **déployable de façon reproductible et automatisée** <span class="opacity-50 text-sm">[S0]</span>.

### Livrables attendus

<div class="livrables text-sm">

1. dépôt Git propre
2. branches et pull requests
3. `README.md` d'installation locale
4. `Dockerfile`
5. `docker-compose.yml` si dépendance externe
6. pipeline CI avec tests et build
7. déploiement staging automatisé ou semi-automatisé
8. `CHANGELOG.md`
9. procédure de mise en production et rollback
10. fiche de diagnostic d'incident
11. tests automatisés + scan de sécurité dans la CI
12. healthcheck et supervision minimale (logs + une alerte)

</div>

<style>
.livrables ol { columns: 2; column-gap: 3rem; margin-top: 0.3rem; }
.livrables li { margin: 0.18em 0; break-inside: avoid; }
</style>

---
hideInToc: true
---

# Architecture de dépôt recommandée

```text
mon-application/
|-- .github/
|   `-- workflows/
|       `-- ci.yml            # pipeline CI/CD GitHub Actions
|-- .gitignore
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
|-- monitoring/               # supervision : prometheus, grafana, alertes
|   `-- docker-compose.yml
|-- src/
|-- tests/                    # unitaires, intégration
`-- perf/
    `-- load-test.js          # scénario K6
```

---
hideInToc: true
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
hideInToc: true
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
hideInToc: true
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
hideInToc: true
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
hideInToc: true
---

# Étape E — Pipeline CI

```bash
git switch -c ci/pipeline
# Ajouter le workflow .github/workflows/ci.yml
git add .github/workflows/ci.yml
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
hideInToc: true
---

# Étape F — Tests automatisés

Ajouter un filet de sécurité avant d'automatiser le déploiement.

```bash
git switch -c test/suite
# Écrire au moins : quelques tests unitaires + un test d'intégration
git add tests/ perf/
git commit -m "test: add unit, integration and k6 load test"
```

### Attendus

<div class="civit-callout space-y-1 text-sm mt-4">

- au moins un test **unitaire** et un test **d'intégration** exécutés en CI ;
- un **scan de sécurité** de l'image (Trivy ou `npm audit`) ;
- un **smoke test** post-déploiement (`curl /health`) ;
- bonus : un test de **charge K6** avec un seuil (`p95`).

</div>

---
hideInToc: true
---

# Étape G — Déploiement staging

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
hideInToc: true
---

# Étape H — Supervision minimale

Rendre le service **observable** une fois déployé.

```bash
git switch -c ops/monitoring
# Ajouter un endpoint /health et une stack monitoring/ (compose)
docker compose -f monitoring/docker-compose.yml up -d
git add monitoring/ src/
git commit -m "ops(monitoring): add healthcheck and supervision stack"
```

### Attendus

<div class="civit-callout space-y-1 text-sm mt-4">

- un endpoint `/health` et un `healthcheck` dans le Compose ;
- les logs applicatifs sur **stdout**, consultables ;
- au moins **une métrique** visualisée (Grafana / Uptime Kuma) ;
- au moins **une alerte** décrite (ex. service down ou disque > 80 %).

</div>

---
hideInToc: true
---

# Étape I — Rollback

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
hideInToc: true
---

# Grille d'évaluation formative

<div class="text-sm">

| Critère | Points | Observables |
|---|---:|---|
| Git et collaboration | 15 | Branches, commits lisibles, MR, résolution de conflit, historique propre. |
| Documentation | 10 | README, changelog, procédures déploiement/incident, variables documentées. |
| Conteneurisation | 20 | Dockerfile fonctionnel, image reproductible, Compose si nécessaire, pas de secrets. |
| Pipeline CI/CD | 20 | Stages cohérents, tests bloquants, image/artefact produit, variables sécurisées. |
| Tests et sécurité | 10 | Tests unitaires/intégration en CI, scan d'image, smoke test, seuils K6. |
| Supervision | 10 | Healthcheck, logs accessibles, une métrique visualisée, une alerte décrite. |
| Déploiement et rollback | 10 | Staging déployé, smoke test, rollback décrit ou testé. |
| Compréhension DevOps | 5 | Capacité à expliquer CALMS, CI/CD, environnement, métriques et risques. |

</div>

<div class="text-right font-bold mt-4 text-civit-blue">Total : 100 points</div>

---
layout: section
class: civit-section
---

# 11. Exercices courts à insérer pendant le cours

---
hideInToc: true
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
hideInToc: true
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
hideInToc: true
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
hideInToc: true
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

# 12. Antisèches

---
hideInToc: true
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
hideInToc: true
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
hideInToc: true
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

# 13. Erreurs fréquentes et corrections

---
hideInToc: true
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
hideInToc: true
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

# 14. Glossaire rapide

---
hideInToc: true
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
hideInToc: true
---

# Glossaire (2/2)

<div class="text-sm">

| Terme | Définition |
|---|---|
| Image digest | Identifiant immuable du contenu d'une image. |
| Infrastructure immuable | Remplacer plutôt que modifier manuellement une instance déployée. |
| Pull request | Demande de fusion avec revue, discussions et pipeline. |
| Registry | Entrepôt d'images Docker. |
| Rollback | Retour à une version précédente connue comme stable. |
| Runner / agent | Machine ou processus exécutant les jobs de CI. |
| Smoke test | Test rapide confirmant que le service répond après déploiement. |
| Staging | Environnement de préproduction proche de la production. |

</div>

---
hideInToc: true
---

# Glossaire (3/3) — tests & supervision

<div class="text-sm">

| Terme | Définition |
|---|---|
| Pyramide des tests | Beaucoup de tests unitaires rapides, peu de tests E2E lents. |
| Test E2E | Test de bout en bout rejouant un parcours utilisateur complet. |
| Couverture (coverage) | Part du code exécutée par les tests. |
| Observabilité | Capacité à comprendre l'état interne d'un système via ses sorties. |
| Métrique / Log / Trace | Les 3 piliers : valeur chiffrée / événement texte / chemin d'une requête. |
| Golden signals | Latence, trafic, erreurs, saturation (Google SRE). |
| SLI / SLO / SLA | Indicateur mesuré / objectif interne / engagement contractuel. |
| Healthcheck | Sonde indiquant si un service est en bonne santé. |

</div>

---
layout: section
class: civit-section
---

# 15. Sources et bibliographie

---
hideInToc: true
---

# Sources principales

Les schémas de ce support sont **originaux** et ne reprennent pas d'images propriétaires.

<div class="sources text-xs">

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
- **[S16][S17][S18]** GitHub Docs, *GitHub Actions*
- **[S20]** AWS, *Deployment strategies*
- **[S21]** Google Cloud, *Canary deployment*
- **[S22]** Kubernetes Docs, *Rolling Update*
- **[S23]** OWASP, *DevSecOps Guideline*
- **[S24][S25][S26]** OpenClassrooms
- **[S27]** ScholarVox, *Learning DevOps*
- **[S28]** M. Fowler, *Test Pyramid* / *Practical Test Pyramid*
- **[S29]** Google, *Site Reliability Engineering* (Golden Signals, SLI/SLO)
- **[S30]** Prometheus, Grafana, Grafana Loki & K6 Docs

</div>

<style>
.sources ul { columns: 2; column-gap: 2.2rem; }
.sources li { break-inside: avoid; margin: 0.12em 0; list-style: none; }
</style>

---
layout: cover
class: civit-section
background: '#ffffff'
hideInToc: true
---

<div class="absolute top-10 right-10 civit-badge">
  <span>Civilisation<span class="fire">IT</span></span>
</div>

# Merci !

## Questions, pratique, et place au projet continu 🚀

<div class="civit-callout mt-12 inline-block text-left">

**Support préparé par CivilisationIT**

Intervenant CESI — module INF83
</div>
