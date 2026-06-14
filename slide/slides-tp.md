---
theme: seriph
colorSchema: light
layout: cover
background: '#ffffff'
title: INF83 — Parcours TP
titleTemplate: '%s · CivilisationIT'
info: |
  ## INF83 — Parcours TP
  Petits TP qui s'assemblent, à faire sur les créneaux libres (1h / 2h / 3h) des 5 jours.
class: text-left
transition: slide-left
mdc: true
fonts:
  sans: Inter
  mono: Fira Code
css: unocss
hideInToc: true
---

<style>
.slidev-layout.cover { position: relative; overflow: hidden; }
.slidev-layout.cover::after {
  content: ""; position: absolute; left: 0; top: 0; bottom: 0; width: 5px;
  background: linear-gradient(180deg, var(--civit-blue) 0%, var(--civit-fire) 100%);
}
.slidev-layout.cover h1 {
  font-size: 4.2rem; line-height: 1.05;
  background: linear-gradient(115deg, var(--civit-blue) 0%, var(--civit-blue-dark) 100%);
  -webkit-background-clip: text; background-clip: text; color: transparent;
}

/* ── Cartes de créneau ── */
.slots { display: flex; flex-direction: column; gap: 0.6rem; margin-top: 0.4rem; }
.slot {
  display: flex; align-items: stretch; border: 1px solid rgba(14,165,233,0.22);
  border-radius: 14px; overflow: hidden; background: rgba(14,165,233,0.04);
}
.slot .dur {
  flex: none; width: 74px; display: flex; align-items: center; justify-content: center;
  font-weight: 800; font-size: 1.05rem; color: #fff;
  background: linear-gradient(135deg, var(--civit-blue), var(--civit-blue-dark));
}
.slot .body { padding: 0.5rem 0.9rem; }
.slot .tps { font-weight: 700; color: var(--civit-navy); font-size: 0.98rem; }
.slot .todo { font-size: 0.82rem; color: #334155; margin-top: 0.12rem; }
.slot .gain { font-size: 0.82rem; color: var(--civit-blue-dark); font-weight: 600; margin-top: 0.1rem; }
/* Carte bonus (étudiants avancés) */
.slot.bonus { border-color: rgba(249,115,22,0.45); background: rgba(14,165,233,0.04); }
.slot.bonus .dur { background: linear-gradient(135deg, #38bdf8, #1971a0); }
.slot.bonus .tag { display:inline-block; font-size:0.7rem; font-weight:700; color:#0369a1;
  background: rgba(14,165,233,0.14); border-radius:999px; padding:0.05rem 0.5rem; margin-left:0.4rem; vertical-align:middle; }
.daytag {
  display: inline-block; font-size: 0.8rem; font-weight: 700; color: var(--civit-blue-dark);
  background: rgba(14,165,233,0.10); border-radius: 999px; padding: 0.15rem 0.7rem; margin-left: 0.5rem; vertical-align: middle;
}
.tp-slide h1 { font-size: 1.85rem; }
</style>

<div class="absolute top-10 right-10 civit-badge">
  <img src="/civilisationit-logo.svg" class="w-8 h-8" />
  <span>Civilisation<span class="fire">IT</span></span>
</div>

# Parcours TP

## Des petits TP qui s'assemblent

Sur les **créneaux libres** des 5 jours — 1 h / 2 h / 3 h — chaque TP ajoute une brique à **une seule application** — un de vos projets perso, votre fil rouge CESI, ou une petite app créée dans votre langage — qui grandit jusqu'au projet final.

<div class="pt-12">
  <span class="px-3 py-1 rounded-full civit-callout text-sm">CESI : CDA</span>
  <span class="px-3 py-1 rounded-full civit-callout-fire text-sm ml-2">5 jours · créneaux libres</span>
</div>

<div class="pt-4 text-sm">
  <a href="https://killian-aidalinfo.github.io/inf83-devops-cesi/" target="_blank" class="text-civit-blue">← Cours INF83 — Déploiement continu</a>
</div>

---
hideInToc: true
---

# Comment ça marche 🧩

<div class="grid grid-cols-2 gap-6 mt-4">

<div class="civit-callout">

### Le principe
- **Quelle appli ?** un de vos **projets perso** (ou votre fil rouge CESI), sinon une **petite app créée dans votre langage** (Node, PHP, Python, Java…).
- **Une seule appli**, du premier commit au déploiement.
- Chaque créneau = **une brique** branchée sur la précédente.

</div>

<div class="civit-callout-fire">

### Rythme adapté
- **1 h** — 1 à 2 petits TP ciblés.
- **2 h** — un bloc cohérent (ou un *workshop*).
- **3 h** — un *projet final* d'assemblage.
- ⭐ **Les plus à l'aise avec Git prennent de l'avance sur Docker dès le J1.**

</div>

</div>

<div class="civit-callout mt-5 text-sm">
🧵 <strong>Projet continu :</strong> repo + CI → tests → Docker → Compose + BDD → image vers GHCR → déploiement staging → sécurité → supervision → <strong>projet final</strong>.
</div>

---
hideInToc: true
class: tp-slide
---

# Jour 1 <span class="daytag">Git · première CI</span>

<div class="slots">
  <div class="slot">
    <div class="dur">1 h</div>
    <div class="body">
      <div class="tps">CI <code>tp-01 Hello CI</code> + <code>tp-02 déclencheurs</code></div>
      <div class="todo">Créer le dépôt · écrire <code>.github/workflows/ci.yml</code> · déclencher sur <b>push</b>, <b>PR</b> et <code>workflow_dispatch</code> · lire l'onglet Actions</div>
      <div class="gain">→ dépôt GitHub + première CI qui tourne</div>
    </div>
  </div>
  <div class="slot">
    <div class="dur">2 h</div>
    <div class="body">
      <div class="tps">CI <code>tp-03 lint + tests</code> + Tests <code>tp-01 / tp-04 TDD</code></div>
      <div class="todo">Créer l'API Express + tests Jest · enchaîner lint + tests en CI (<code>setup-node</code>) · écrire un test en TDD (red→green→refactor)</div>
      <div class="gain">→ CI verte avec lint et tests unitaires</div>
    </div>
  </div>
  <div class="slot bonus">
    <div class="dur">1 h</div>
    <div class="body">
      <div class="tps">Docker <code>tp-01 → tp-03</code><span class="tag">★ avancés</span></div>
      <div class="todo">Lancer un conteneur · mapper un port <code>-p</code> et des variables <code>-e</code> · lire les logs · inspecter / déboguer</div>
      <div class="gain">→ prennent de l'avance sur Docker (J2 allégé pour eux)</div>
    </div>
  </div>
</div>

---
hideInToc: true
class: tp-slide
---

# Jour 2 <span class="daytag">Docker</span>

<div class="slots">
  <div class="slot">
    <div class="dur">1 h</div>
    <div class="body">
      <div class="tps">Docker <code>tp-01 → tp-03</code> <span class="opacity-60 text-sm">(rattrapage — déjà fait par les avancés)</span></div>
      <div class="todo">run / stop / restart / rm · ports et variables d'env · logs · inspection d'un conteneur</div>
      <div class="gain">→ aisance avec les conteneurs en CLI</div>
    </div>
  </div>
  <div class="slot">
    <div class="dur">2 h</div>
    <div class="body">
      <div class="tps">Docker <code>tp-04 Dockerfile</code> + <code>tp-05 multi-stage</code></div>
      <div class="todo">Écrire un Dockerfile Node/Express + <code>.dockerignore</code> · soigner le cache des couches · multi-stage + utilisateur <b>non-root</b></div>
      <div class="gain">→ l'appli est conteneurisée en image légère</div>
    </div>
  </div>
  <div class="slot">
    <div class="dur">1h30</div>
    <div class="body">
      <div class="tps">Docker <code>tp-08 Compose : app + BDD</code></div>
      <div class="todo">Décrire <code>compose.yaml</code> (app + Postgres) · <b>healthcheck</b> + <code>depends_on: condition</code> · gérer le cycle de vie de la stack</div>
      <div class="gain">→ stack locale qui démarre en une commande</div>
    </div>
  </div>
</div>

---
hideInToc: true
class: tp-slide
---

# Jour 3 <span class="daytag">CI/CD</span>

<div class="slots">
  <div class="slot">
    <div class="dur">2 h</div>
    <div class="body">
      <div class="tps">CI <code>tp-05 secrets</code> + <code>tp-09 image → GHCR</code></div>
      <div class="todo">Créer secrets / variables de dépôt · build & push de l'image avec <code>build-push-action</code> + <code>metadata-action</code> · login via <code>GITHUB_TOKEN</code></div>
      <div class="gain">→ la CI build et publie l'image Docker</div>
    </div>
  </div>
  <div class="slot">
    <div class="dur">2 h</div>
    <div class="body">
      <div class="tps">CI <code>tp-10 déploiement Render</code> <span class="opacity-60 text-sm">(ou <code>tp-08 Pages</code> pour un front statique)</span></div>
      <div class="todo">Créer un web service Render · <b>Deploy Hook</b> stocké en secret · déploiement auto depuis Actions · vérifier la mise en ligne</div>
      <div class="gain">→ déploiement continu automatique en staging</div>
    </div>
  </div>
</div>

---
hideInToc: true
class: tp-slide
---

# Jour 4 <span class="daytag">Sécurité · tests</span>

<div class="slots">
  <div class="slot">
    <div class="dur">1 h</div>
    <div class="body">
      <div class="tps">DevSecOps <code>tp-01 Gitleaks</code> + <code>tp-03 Trivy deps</code></div>
      <div class="todo">Scanner les secrets (Gitleaks + hook pre-commit) · scanner les dépendances (Trivy) · <b>gate bloquant</b> sur CVE HIGH/CRITICAL</div>
      <div class="gain">→ secrets et dépendances sous contrôle</div>
    </div>
  </div>
  <div class="slot">
    <div class="dur">1 h</div>
    <div class="body">
      <div class="tps">DevSecOps <code>tp-07 scan image</code> + <code>tp-08 durcir Dockerfile</code></div>
      <div class="todo">Scanner l'image (Trivy + <b>SBOM</b>) · durcir le Dockerfile étape par étape · vérifier le résultat</div>
      <div class="gain">→ gate de sécurité sur l'image</div>
    </div>
  </div>
  <div class="slot">
    <div class="dur">2 h</div>
    <div class="body">
      <div class="tps">Tests <code>tp-08 intégration</code> + <code>tp-12 tests dans la CI</code></div>
      <div class="todo">Écrire un test d'intégration (base en mémoire) · brancher toute la suite de tests dans la CI</div>
      <div class="gain">→ filet de sécurité complet en CI</div>
    </div>
  </div>
</div>

---
hideInToc: true
class: tp-slide
---

# Jour 5 <span class="daytag">Supervision · synthèse</span>

<div class="slots">
  <div class="slot">
    <div class="dur">2 h</div>
    <div class="body">
      <div class="tps">Docker <code>WS-03 stack web + BDD + cache</code></div>
      <div class="todo">Monter app + Postgres + Redis en une commande · réseau interne · volumes persistants · ajouter la supervision (Grafana / Prometheus)</div>
      <div class="gain">→ stack conteneurisée et supervisée</div>
    </div>
  </div>
  <div class="slot">
    <div class="dur">3 h</div>
    <div class="body">
      <div class="tps">Projet final — Docker <code>tp-12</code> <span class="opacity-60">/</span> CI/CD <code>tp-12</code></div>
      <div class="todo">Assembler la stack 3-tiers (multi-stage, non-root, healthcheck) + le pipeline qualité → image → déploiement multi-env avec approbation prod</div>
      <div class="gain">→ tout est assemblé = le projet continu complet</div>
    </div>
  </div>
</div>

---
hideInToc: true
---

# Logique d'assemblage 🔗

<div class="text-base opacity-60 -mt-1 mb-5">Chaque brique se branche sur la précédente et converge vers le projet continu.</div>

<div class="flex flex-wrap items-center gap-2 text-sm leading-loose">
<span class="civit-callout px-3 py-1">repo + CI</span> →
<span class="civit-callout px-3 py-1">tests</span> →
<span class="civit-callout px-3 py-1">Docker</span> →
<span class="civit-callout px-3 py-1">Compose + BDD</span> →
<span class="civit-callout px-3 py-1">image → GHCR</span> →
<span class="civit-callout px-3 py-1">CD staging</span> →
<span class="civit-callout-fire px-3 py-1">sécurité</span> →
<span class="civit-callout-fire px-3 py-1">supervision</span> →
<span class="civit-callout px-3 py-1 font-bold">🎯 projet continu</span>
</div>

---
hideInToc: true
---

# Variante : workshops autonomes

Pour un créneau **2 h / 3 h**, plutôt qu'enchaîner des petits TP, donne directement un **workshop** (déjà calibré, avec corrigé) :

<div class="text-sm mt-4">

| Durée | Workshop | Pour |
|---|---|---|
| 2 h | Docker `WS-01` conteneuriser une app | mettre une appli en conteneur de A à Z |
| 2 h | CI/CD `WS-02` pipeline de qualité | lint + tests + couverture |
| 2 h 30 | DevSecOps `WS-04` gate de sécurité en CI | bloquer sur vulnérabilité |
| 4 h | `WS-06` de chaque formation | mini-projet complet *(à scinder)* |

</div>

<div class="civit-callout mt-5 text-sm">
📊 <strong>Bonus — Supervision approfondie</strong> (2–3 h) : conteneuriser une stack <strong>Prometheus + Grafana + Loki</strong>, brancher un exporter sur l'app, créer un <em>dashboard</em> et une <em>alerte</em> (service down, latence p95, disque &gt; 80 %).
</div>

<div class="civit-callout-fire mt-3 text-sm">
🚫 <strong>Hors-scope ces 5 jours</strong> (autres bonus possibles) : Ansible, Terraform, Kubernetes, GitOps — orchestration / IaC avancées.
</div>

---
layout: cover
class: civit-section
background: '#ffffff'
hideInToc: true
---

<div class="absolute top-10 right-10 civit-badge">
  <span>Civilisation<span class="fire">IT</span></span>
</div>

# À vous de jouer ! 🚀

## Une appli, neuf briques, un projet continu

<div class="civit-callout mt-12 inline-block text-left">

**Parcours TP préparé par CivilisationIT**

Intervenant CESI — module INF83
</div>
