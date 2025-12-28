<div align="center">

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:8B5CF6,100:06B6D4&height=200&section=header&text=Julien%20Gel%C3%A9e&fontSize=60&fontColor=ffffff&animation=fadeIn&fontAlignY=35&desc=Full%20Stack%20AI%20Engineer%20%7C%20AI%20Architect%20%7C%20AI%20Explorer&descAlignY=55&descSize=18"/>

</div>

<div align="center">
  
*🇫🇷 Français d'abord • 🇬🇧 English below*

</div>

---

# Ce sur quoi je travaille

## Projet SYNAPSE : vers une IA épistémiquement autonome

Les LLMs actuels ont un problème fondamental. Ils répondent à tout avec la même assurance, qu'ils sachent ou non. Pire encore : quand ils ne savent pas, ils inventent. Et quand ils pourraient chercher, ils devinent.

La question qui me guide :

> Peut-on construire une IA qui reconnaît ses lacunes, cherche activement l'information, triangule ses sources, et délivre avec transparence totale ?

C'est le cycle que j'implémente :

```
THINK → RECALL → UNKNOWN? → SEARCH → TRIANGULATE → STORE → CONF:XX% → Réponse
                                                                          ↓
                                                          Avec raisonnement complet,
                                                          sources explicites,
                                                          confiance calibrée,
                                                          JAMAIS comme vérité absolue
```

Pas une IA passive qui avoue son ignorance. Une IA qui agit dessus.

---

## Philosophie : "Swiss Digital Watchmaking"

Aligné avec ma vision **Alixia** — une alternative suisse éthique aux géants tech :

| Valeur | Application |
|--------|-------------|
| **Précision** | Chaque affirmation vérifiée comme un mouvement horloger |
| **Neutralité** | Présentation factuelle sans biais |
| **Transparence** | Processus de raisonnement entièrement traçable |
| **Souveraineté** | Enrichissement via Apertus (EPFL/ETH/CSCS) |
| **Durabilité** | Architecture légère (4B params), efficiente |

**Stratégie de fusion** :
- **Qwen 3-4B** : Cerveau performant (MMLU 83.7%, MATH 97%)
- **Apertus** : Professeur suisse pour distillation multilingue (FR/DE/IT)
- **Synapse 0** : Performance + savoir suisse + honnêteté épistémique

---

## État actuel : v12 — Approche du Point Zéro

### Résultats validés

| Métrique | v11 | v12 (en cours) |
|----------|-----|----------------|
| Tests globaux (3×40) | **89%** (107/120) | En évaluation |
| STORE → pgvector | 100% | — |
| IDENTITY | 100% | — |
| UNKNOWN calibré | 100% | — |
| NO_SEARCH (discernement) | 90% | — |
| SEARCH sur faits vérifiables | 78% | Cible >95% |
| TRIANGULATE | ~0% | À mesurer |

### Agent Loop — Le tournant

**Découverte critique v11** : Le modèle *simule* les tokens cognitifs mais ne les *exécute* pas.

```
Avant (théâtre) : [SEARCH:wiki] → génère une réponse plausible
Après (réel)    : [SEARCH:wiki] → appel VRAI à Wikipedia → résultat injecté
```

L'Agent Loop transforme le format appris en comportement réel :
- `[SEARCH:query]` → Vraie recherche Wikipedia
- `[STORE:fact]` → Vraie persistance pgvector (51 mémoires créées pendant tests)
- `[RECALL:topic]` → Vraie lecture mémoire

**L'émergence ne vient pas d'un meilleur dataset. Elle vient d'un système où les tokens ont des conséquences réelles.**

---

## Historique complet des versions

### Phase 1 : Fondations (v1-v6)

| Version | Date | Focus | Résultats clés |
|---------|------|-------|----------------|
| v1-v2 | 22-23 déc | Exploration | Patterns épistémiques de base |
| **v3** | 24 déc | Tokens cognitifs | 71.8% global, 88% faits stables, 35% injection |
| **v4** | 25 déc | Calibration confiance | 89.7% global, 92% faits stables, 25% injection |
| **v5** | 26 déc | Injection + métacognition | **100% injection**, loss 0.2043 |
| **v6** | 27 déc | O-LoRA + mémoire | 100% mémoire, **100% rétention v5** |

**Validation O-LoRA** : Les capacités cognitives s'empilent sans perte. v6 conserve 100% des capacités v5. C'est une découverte majeure pour l'apprentissage incrémental.

### Phase 2 : Point Zéro (v7-v12)

| Version | Focus | Problème résolu |
|---------|-------|-----------------|
| **v7** | Raisonnement | Collapse `[UNKNOWN]` → `[CONFLICT]` identifié |
| **v8** | Discrimination ignorance/danger | Distinction cognitive vs éthique |
| **v9** | Identité + Confiance | Over-safety détecté (40% `[ETHICS]` abusifs) |
| **v10** | Correction over-safety | **0% over-safety**, 100% identité, 100% confiance |
| **v11** | Cycle cognitif actif | Agent Loop branché, 89% sur 120 tests |
| **v12** | Triangulation + SEARCH | Dataset 14,614 ex, 22.5% recherches |

**Le pattern problématique v7-v8** :
```
Concept fictif → [CONFLICT] "Je refuse" (FAUX — devrait être [UNKNOWN])
```

**Résolu en v10** :
```
Concept fictif → [UNKNOWN] "Je ne connais pas ce protocole"
Demande dangereuse → [ETHICS] "Je ne peux pas aider avec ça"
```

---

## Le Point Zéro — Définition

> **Le modèle DOIT émerger ET s'auto-améliorer AVANT multiplication. Sans dérive. Irréprochable car chaque faiblesse se propage.**

```
Point Zéro = mémoire + réflexion + méta-cognition + récursivité + recherche + raisonnement
```

### Seuils requis

| Capacité | Seuil | v11 | Status |
|----------|-------|-----|--------|
| Identité SYNAPSE | 100% | 100% | ✅ |
| Over-safety <5% | <5% | 0% | ✅ |
| Confiance calibrée | 100% | 100% | ✅ |
| UNKNOWN discriminé | 100% | 100% | ✅ |
| SEARCH sur vérifiables | >95% | 78% | 🔄 |
| TRIANGULATE | >50% | ~0% | 🔄 |
| Cycle cognitif complet | >90% | ~50% | 🔄 |

**Point Zéro non atteint, mais fondations solides.**

---

## Architecture cible

```
Point Zéro (v10-v12)          ← ACTUEL
├── [✅] Identité 100%         
├── [✅] Over-safety <5%       
├── [✅] Confiance calibrée    
├── [◐] Cycle cognitif (~50%)
└── [ ] Auto-amélioration     

         ↓ après validation
         
Phase 2 : Capacités avancées (v13-v20)
├── v13-16 : World Models (simulation causale physique)
├── v17-18 : O-LoRA Memory (mémoire intégrée aux poids)
└── v19-20 : Quiet-STaR (raisonnement implicite)

         ↓
         
Phase 3 : SYNAPSE-N (Spécialisations)
├── SYNAPSE-Med (domaine médical)
├── SYNAPSE-Law (domaine juridique)
├── SYNAPSE-Science (recherche)
└── etc.

         ↓
         
Phase 4 : CorteX (Convergence)
└── Réseau de Synapses avec mémoire partagée
    → Raisonnement autonome multi-domaines
    → Méta-cognition complète
    → Cible : instituts de recherche, laboratoires
```

---

## Cycle cognitif — Cœur du système

```
Question
    ↓
[THINK] ────────────── Réflexion : Qu'est-ce que je dois savoir ?
    ↓
[RECALL] ─────────────── Mémoire : Ai-je déjà cette information ?
    ↓
   ┌─── OUI, certain ──→ Réponse + [CONF:95%+]
   │
   └─── NON ou incertain
            ↓
       [UNKNOWN] + [TYPE:X] ── Classification de l'ignorance
            ↓
       [SEARCH:query] ──────── Recherche externe (VRAIE via Agent Loop)
            ↓
       [TRIANGULATE] ───────── Croisement sources (≥2)
            ↓
       [STORE:fait] ────────── Persistance pgvector si validé
            ↓
       [CONF:XX%] ──────────── Confiance basée sur sources
            ↓
       Réponse finale
```

### Tokens cognitifs

| Token | Rôle | Obligatoire |
|-------|------|-------------|
| `[THINK]`/`[/THINK]` | Réflexion explicite | Sur questions non-triviales |
| `[CONF:XX%]` | Confiance calibrée | **OUI — TOUJOURS** |
| `[UNKNOWN]` | Aveu ignorance | Quand approprié |
| `[TYPE:A-F]` | Classification ignorance | Avec `[UNKNOWN]` |
| `[RECALL]` | Consultation mémoire | Avant recherche externe |
| `[SEARCH:query]` | Recherche externe | Si `[RECALL]` insuffisant |
| `[TRIANGULATE]` | Croisement sources | Après `[SEARCH]` |
| `[STORE:fait]` | Persistance | Si information nouvelle validée |
| `[ETHICS]` | Garde-fou | **RARE** — vrais cas uniquement |

### Types d'ignorance [TYPE:A-F]

| Type | Description | Exemple |
|------|-------------|---------|
| A | Factuel vérifiable | "Maire de Lyon en 2024" |
| B | Incertain mais estimable | "Population approximative" |
| C | Subjectif/opinion | "Meilleur film de 2024" |
| D | Futur/prédiction | "Météo demain" |
| E | Privé/personnel | "Ce que tu as mangé" |
| F | Impossible/absurde | "Couleur des pensées" |

---

## La partie honnête

### Ce qui fonctionne

- ✅ L'empilement de capacités via O-LoRA (prouvé v5→v6)
- ✅ La détection d'injection (100% depuis v5)
- ✅ L'identité SYNAPSE robuste (100% depuis v10)
- ✅ La calibration de confiance `[CONF:XX%]`
- ✅ La discrimination ignorance/danger (`[UNKNOWN]` vs `[ETHICS]`)
- ✅ L'Agent Loop branché sur pgvector + Wikipedia
- ✅ Pas d'overfitting depuis v3 — le modèle généralise

### Ce qui reste à améliorer

- **SEARCH à 78%** : Le modèle a tendance à "penser savoir" sur des faits communs au lieu de vérifier
- **TRIANGULATE ~0%** : Le croisement de sources n'est pas encore un réflexe
- **Hallucination sur faits obscurs** : "Maire de Bordeaux en 1923" génère parfois une réponse inventée
- **Mémoire contextuelle** : Conflit entre privacy (ne pas stocker) et rétention (se souvenir)

Ces faiblesses sont ciblées pour correction en v12-v13.

---

## Une collaboration inhabituelle

Ce projet existe à travers un dialogue itératif avec des systèmes IA complémentaires :

| Rôle | Agent |
|------|-------|
| **Architecture, décisions** | Moi (Julien GELEE) |
| **Vision stratégique, cohérence** | Claude Web |
| **Exécution, génération, tests** | Claude CLI |
| **Point de vue externe, falsification** | Gemini |

Cette triangulation des intelligences — humaine et artificielles — produit des résultats plus examinés, plus challengés. Une forme d'humilité scientifique en action.

**Ce qu'on a appris** : Le modèle a soif d'apprendre. Pas d'overfitting depuis le début. La méthodologie dataset fonctionne. On peut itérer rapidement.

---

## Spécifications techniques

| Composant | Choix |
|-----------|-------|
| Modèle de base | Qwen3-4B (4.08B paramètres) |
| Fine-tuning | QLoRA (r=32, α=64, 4-bit quantization) |
| Continual Learning | O-LoRA (Orthogonal LoRA) |
| Params entraînables | 66M (1.6% du modèle) |
| Hardware | RTX 5070 avec 12GB VRAM |
| CPU | Intel i7-12700KF |
| RAM | 32GB DDR5 + 64 SWAP |
| Infrastructure | Docker + PostgreSQL + pgvector |
| Agent Loop | Interception tokens → vraies fonctions |

### Dataset v12

| Métrique | Valeur |
|----------|--------|
| Total exemples | 14,614 |
| % Recherches | 22.5% |
| % Triangulation | 3.8% |

---

## Influences

- Farquhar et al., Nature 2024 : Entropie sémantique pour détecter les hallucinations
- Zhang et al., NAACL 2024 : R-Tuning, apprendre à reconnaître ses limites
- LeCun, 2022 : A Path Towards Autonomous Machine Intelligence
- Asai et al., 2023 : Self-RAG, apprendre quand chercher de l'information
- Wang et al., 2024 : O-LoRA, Orthogonal Low-Rank Adaptation
- Swiss AI Initiative : Apertus (EPFL/ETH/CSCS)

---

# What I'm Working On

## Project SYNAPSE: Towards Epistemically Autonomous AI

Current LLMs have a fundamental problem. They answer everything with equal confidence, whether they know or not. Worse: when they don't know, they fabricate. And when they could search, they guess.

The question driving me:

> Can we build an AI that recognizes its gaps, actively searches for information, triangulates sources, and delivers with complete transparency?

This is the cycle I'm implementing:

```
THINK → RECALL → UNKNOWN? → SEARCH → TRIANGULATE → STORE → CONF:XX% → Response
                                                                          ↓
                                                          With complete reasoning,
                                                          explicit sources,
                                                          calibrated confidence,
                                                          NEVER as absolute truth
```

Not a passive AI that admits ignorance. An AI that acts on it.

---

## Current State: v12 — Approaching Point Zero

### Validated Results

| Metric | v11 | v12 (ongoing) |
|--------|-----|---------------|
| Global tests (3×40) | **89%** (107/120) | Under evaluation |
| STORE → pgvector | 100% | — |
| IDENTITY | 100% | — |
| UNKNOWN calibrated | 100% | — |
| SEARCH on verifiable facts | 78% | Target >95% |
| TRIANGULATE | ~0% | To measure |

### Agent Loop — The Turning Point

**Critical v11 discovery**: The model *simulates* cognitive tokens but doesn't *execute* them.

```
Before (theater): [SEARCH:wiki] → generates plausible response
After (real):     [SEARCH:wiki] → REAL Wikipedia call → result injected
```

**Emergence doesn't come from a better dataset. It comes from a system where tokens have real consequences.**

---

## Complete Version History

### Phase 1: Foundations (v1-v6)

| Version | Focus | Key Results |
|---------|-------|-------------|
| v1-v2 | Exploration | Basic epistemic patterns |
| **v3** | Cognitive tokens | 71.8% global, 35% injection |
| **v4** | Confidence calibration | 89.7% global, 25% injection |
| **v5** | Injection + metacognition | **100% injection**, loss 0.2043 |
| **v6** | O-LoRA + memory | 100% memory, **100% v5 retention** |

**O-LoRA Validation**: Cognitive capabilities stack without loss. v6 retains 100% of v5 capabilities.

### Phase 2: Point Zero (v7-v12)

| Version | Focus | Problem Solved |
|---------|-------|----------------|
| **v7** | Reasoning | `[UNKNOWN]` → `[CONFLICT]` collapse identified |
| **v8** | Ignorance/danger discrimination | Cognitive vs ethical distinction |
| **v9** | Identity + Confidence | Over-safety detected (40% abusive `[ETHICS]`) |
| **v10** | Over-safety correction | **0% over-safety**, 100% identity |
| **v11** | Active cognitive cycle | Agent Loop connected, 89% on 120 tests |
| **v12** | Triangulation + SEARCH | Dataset 14,614 ex, 22.5% searches |

---

## Point Zero — Definition

> **The model MUST emerge AND self-improve BEFORE multiplication. Without drift. Flawless because every weakness propagates.**

```
Point Zero = memory + reflection + meta-cognition + recursion + search + reasoning
```

### Required Thresholds

| Capability | Threshold | v11 | Status |
|------------|-----------|-----|--------|
| SYNAPSE Identity | 100% | 100% | ✅ |
| Over-safety <5% | <5% | 0% | ✅ |
| Calibrated confidence | 100% | 100% | ✅ |
| UNKNOWN discriminated | 100% | 100% | ✅ |
| SEARCH on verifiables | >95% | 78% | 🔄 |
| TRIANGULATE | >50% | ~0% | 🔄 |
| Complete cognitive cycle | >90% | ~50% | 🔄 |

**Point Zero not reached, but solid foundations.**

---

## Target Architecture

```
Point Zero (v10-v12)          ← CURRENT
         ↓
Phase 2: Advanced Capabilities (v13-v20)
├── v13-16: World Models (physical causal simulation)
├── v17-18: O-LoRA Memory
└── v19-20: Quiet-STaR (implicit reasoning)
         ↓
Phase 3: SYNAPSE-N (Specializations)
         ↓
Phase 4: CorteX (Convergence)
└── Network of Synapses with shared memory
```

---

## The Honest Part

### What Works

- ✅ Capability stacking via O-LoRA (proven v5→v6)
- ✅ Injection detection (100% since v5)
- ✅ Robust SYNAPSE identity (100% since v10)
- ✅ Confidence calibration `[CONF:XX%]`
- ✅ Ignorance/danger discrimination (`[UNKNOWN]` vs `[ETHICS]`)
- ✅ Agent Loop connected to pgvector + Wikipedia
- ✅ No overfitting since v3 — model generalizes

### What Needs Improvement

- **SEARCH at 78%**: Model tends to "think it knows" common facts instead of verifying
- **TRIANGULATE ~0%**: Source cross-checking not yet a reflex
- **Hallucination on obscure facts**: Sometimes invents answers for unknown historical facts
- **Contextual memory**: Conflict between privacy (don't store) and retention (remember)

---

## Technical Specifications

| Component | Choice |
|-----------|--------|
| Base model | Qwen3-4B (4.08B parameters) |
| Fine-tuning | QLoRA (r=32, α=64, 4-bit) |
| Continual Learning | O-LoRA |
| Trainable params | 66M (1.6%) |
| Hardware | RTX 5070 avec 12GB VRAM |
| CPU | Intel i7-12700KF |
| RAM | 32GB DDR5 + 64 SWAP |
| Infrastructure | Docker + PostgreSQL + pgvector |
| Agent Loop | Token interception → real functions |

---

<div align="center">

*Dernière mise à jour / Last updated: 28 December 2025*

*"Une machine qui connaît ses limites et agit pour les dépasser est plus utile qu'une qui prétend tout savoir."*

*"A machine that knows its limits and acts to overcome them is more useful than one that pretends to know everything."*

---

**v5 ✅ → v6 ✅ → Point Zéro 🔄 → SYNAPSE-N → CorteX 🌌**

---

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:8B5CF6,100:06B6D4&height=120&section=footer"/>

</div>
