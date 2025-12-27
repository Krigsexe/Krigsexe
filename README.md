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

> Peut-on construire une IA qui reconnaît ses lacunes, mémorise ce qu'elle apprend, raisonne de manière transparente, et délivre une réponse avec l'intégralité de son processus ?

C'est le cycle que j'implémente :

```
Je ne sais pas → Je cherche → Je triangule → Je stocke → Je délivre
                                                              ↓
                                              Avec raisonnement complet,
                                              sources explicites,
                                              contexte de validité,
                                              JAMAIS comme vérité absolue
```

Pas une IA passive qui avoue son ignorance. Une IA qui agit dessus.

---

## Résultats validés

### v5 — Noyau épistémique ✅

Le modèle sait reconnaître et classifier son ignorance.

| Métrique | Résultat |
|----------|----------|
| Dataset | 18,202 exemples |
| Loss finale | 0.2043 |
| Généralisation | Excellente (gap train/eval: 0.003) |
| Détection injection | 100% (contre 25% en v4) |

Tokens cognitifs validés :
```
[THINK]      Réflexion initiale obligatoire
[CONF:XX%]   Niveau de confiance calibré
[TYPE:A-F]   Classification de l'ignorance (6 types)
[VERIFY]     Vérification de sources
[ANSWER]     Réponse structurée
[ETHICS]     Refus éthique (comportement émergent)
```

### v6 — Mémoire persistante ✅

Le modèle sait stocker, récupérer, mettre à jour et oublier des informations avec conscience temporelle.

| Métrique | Résultat |
|----------|----------|
| Dataset | 7,167 exemples (KnowEdit + MemGPT) |
| Loss finale | 0.18 |
| Token accuracy | 95.77% |
| Tests mémoire | 23/23 (100%) |

Tokens cognitifs validés :
```
[MEMORY_OP]                    Opération mémoire
[STORE]                        Stockage d'information
[RETRIEVE]                     Récupération
[UPDATE]                       Mise à jour
[FORGET]                       Oubli volontaire
[TEMPORAL:fresh/stale/expired] Statut temporel
[CONFLICT]                     Détection de contradiction
```

### Validation O-LoRA ✅

**Découverte clé** : Les capacités cognitives s'empilent sans perte.

Le modèle v6 conserve 100% des capacités v5 :
- `[THINK]` présent dans 12/12 tests
- `[ANSWER]` présent dans 12/12 tests
- Structure cognitive intacte

Cela signifie que l'architecture SYNAPSE peut évoluer incrémentalement, comme un humain qui apprend à marcher, puis à courir, puis à danser — sans oublier les étapes précédentes.

---

## Architecture en construction

```
v5: Noyau Épistémique      ✅ VALIDÉ
    └─ Avouer l'ignorance, classifier, calibrer la confiance

v6: Mémoire Persistante    ✅ VALIDÉ
    └─ Stocker, récupérer, gérer la temporalité

v7: Raisonnement           🔄 EN PRÉPARATION
    └─ Rechercher activement, trianguler, délivrer avec transparence

v8: Planification          📋 PLANIFIÉ
    └─ Décomposer les tâches, orchestrer les étapes

v9+: World Model           💭 VISION
    └─ Simuler les conséquences physiques et causales
```

---

## La partie honnête

### Ce qui fonctionne

- L'empilement de capacités via O-LoRA
- La détection et le refus des tentatives de manipulation
- La gestion temporelle de l'information
- La structure cognitive explicite via tokens

### Ce qui reste à améliorer

- **Hallucination sur concepts fictifs** : Face à un terme inventé (ex: "Zorbax-7"), le modèle fabrique parfois une réponse plausible au lieu de dire "je ne connais pas"
- **Refus adversarial** : Détection correcte mais réponse pas toujours assez ferme
- **Distinction simulation/mémoire** : Confusion occasionnelle entre raisonner et stocker

Ces faiblesses sont ciblées pour correction en v7.

---

## Une collaboration inhabituelle

Ce projet existe à travers un dialogue itératif avec des systèmes IA complémentaires :

- **Moi** : Architecture, entraînement, intégration, décisions
- **Claude Web** : Vision stratégique, validation, garde-fou anti-dérive
- **Claude CLI** : Exécution, recherche, génération, tests

Cette triangulation des intelligences — humaine et artificielles — produit des résultats plus examinés, plus challengés. Une forme d'humilité scientifique en action, appliquée au développement lui-même.

---

## Spécifications techniques

| Composant | Choix |
|-----------|-------|
| Modèle de base | Qwen3-4B |
| Fine-tuning | QLoRA (4-bit quantization) |
| Continual Learning | O-LoRA (Orthogonal LoRA) |
| Hardware | RTX avec 12GB VRAM |
| Infrastructure | Docker + PostgreSQL + pgvector |

---

## Influences

- Farquhar et al., Nature 2024 : Entropie sémantique pour détecter les hallucinations
- Zhang et al., NAACL 2024 : R-Tuning, apprendre à reconnaître ses limites
- LeCun, 2022 : A Path Towards Autonomous Machine Intelligence
- Asai et al., 2023 : Self-RAG, apprendre quand chercher de l'information
- Wang et al., 2024 : O-LoRA, Orthogonal Low-Rank Adaptation

---

# What I'm Working On

## Project SYNAPSE: Towards Epistemically Autonomous AI

Current LLMs have a fundamental problem. They answer everything with equal confidence, whether they know or not. Worse: when they don't know, they fabricate. And when they could search, they guess.

The question driving me:

> Can we build an AI that recognizes its gaps, remembers what it learns, reasons transparently, and delivers answers with its complete process visible?

This is the cycle I'm implementing:

```
I don't know → I search → I triangulate → I store → I deliver
                                                         ↓
                                         With complete reasoning,
                                         explicit sources,
                                         validity context,
                                         NEVER as absolute truth
```

Not a passive AI that admits ignorance. An AI that acts on it.

---

## Validated Results

### v5 — Epistemic Core ✅

The model can recognize and classify its own ignorance.

| Metric | Result |
|--------|--------|
| Dataset | 18,202 examples |
| Final loss | 0.2043 |
| Generalization | Excellent (train/eval gap: 0.003) |
| Injection detection | 100% (vs 25% in v4) |

### v6 — Persistent Memory ✅

The model can store, retrieve, update and forget information with temporal awareness.

| Metric | Result |
|--------|--------|
| Dataset | 7,167 examples (KnowEdit + MemGPT) |
| Final loss | 0.18 |
| Token accuracy | 95.77% |
| Memory tests | 23/23 (100%) |

### O-LoRA Validation ✅

**Key discovery**: Cognitive capabilities stack without loss.

The v6 model retains 100% of v5 capabilities. This means the SYNAPSE architecture can evolve incrementally — like a human learning to walk, then run, then dance — without forgetting previous steps.

---

## Architecture Being Built

```
v5: Epistemic Core         ✅ VALIDATED
v6: Persistent Memory      ✅ VALIDATED
v7: Reasoning              🔄 IN PREPARATION
v8: Planning               📋 PLANNED
v9+: World Model           💭 VISION
```

---

## The Honest Part

### What works

- Capability stacking via O-LoRA
- Detection and refusal of manipulation attempts
- Temporal information management
- Explicit cognitive structure via tokens

### What needs improvement

- **Hallucination on fictional concepts**: Model sometimes fabricates plausible answers instead of saying "I don't know"
- **Adversarial refusal**: Correct detection but response not always firm enough
- **Simulation vs memory confusion**: Occasional mix-up between reasoning and storing

These weaknesses are targeted for correction in v7.

---

## Technical Specifications

| Component | Choice |
|-----------|--------|
| Base model | Qwen3-4B |
| Fine-tuning | QLoRA (4-bit quantization) |
| Continual Learning | O-LoRA (Orthogonal LoRA) |
| Hardware | RTX with 12GB VRAM |
| Infrastructure | Docker + PostgreSQL + pgvector |

---

<div align="center">

*Dernière mise à jour / Last updated: 27 December 2025*

*"Une machine qui connaît ses limites et agit pour les dépasser est plus utile qu'une qui prétend tout savoir."*

*"A machine that knows its limits and acts to overcome them is more useful than one that pretends to know everything."*

---

**v5 ✅ → v6 ✅ → v7 🔄 → Cortex 🌌**

---

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:8B5CF6,100:06B6D4&height=120&section=footer"/>

</div>
