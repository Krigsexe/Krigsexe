<div align="center">
<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:8B5CF6,100:06B6D4&height=200&section=header&text=SYNAPSE&fontSize=70&fontColor=ffffff&animation=fadeIn&fontAlignY=35&desc=Epistemic%20AI%20%7C%20Architecture%20over%20Scaling%20%7C%20Point%20Zero&descAlignY=55&descSize=18"/>
</div>

<div align="center">

*"Une machine qui sait qu'elle ne sait pas, qui vérifie avant d'affirmer, qui quantifie sa confiance, et qui apprend à vivre avec l'incertitude plutôt que de l'ignorer."*

**Julien GELEE** — Full Stack AI Engineer | AI Architect | AI Explorer

🇫🇷 *Français d'abord* • 🇬🇧 *English below*

</div>

---

# La Thèse

Et si le chemin vers l'intelligence artificielle réelle ne passait pas par l'accumulation brute de paramètres ?

Les géants de l'industrie répondent au problème de l'IA par la force : plus de données, plus de paramètres, plus de compute. GPT-3 à GPT-4, c'est 10× le compute pour peut-être 2× les capacités. Et les hallucinations ? Elles deviennent simplement plus convaincantes.

SYNAPSE propose une autre voie :

```
Architecture épistémique > Scaling brut
```

Un modèle de 4B paramètres qui **sait qu'il ne sait pas**, qui **vérifie avant d'affirmer**, qui **génère des branches de recherche autonomes**, et qui **s'auto-régule** pour ne jamais saturer son système — pourrait-il être plus fiable qu'un géant de 1000B nourri de bruit massif ?

C'est la question que j'explore. Pas avec des certitudes, mais avec une méthodologie.

---

# Le Problème Fondamental

Les LLMs actuels ont un défaut de conception, pas de capacité :

| Ce qu'ils font | Ce qu'ils devraient faire |
|----------------|---------------------------|
| Répondent à tout avec la même assurance | Calibrer leur confiance |
| Inventent quand ils ne savent pas | Reconnaître leurs lacunes |
| Devinent quand ils pourraient chercher | Vérifier activement |
| Oublient tout entre chaque inférence | Accumuler et évoluer |
| Ignorent leur environnement système | S'auto-réguler |

Un modèle plus gros ne résout pas ces problèmes. Il les amplifie.

---

# SYNAPSE v2 — Architecture Event-Driven

## Vue d'Ensemble

```
┌─────────────────────────────────────────┐
│     User Interface / API Layer          │
└────────────────┬────────────────────────┘
                 │
┌────────────────▼─────────────────────────────────────┐
│         CognitiveCore (Orchestrator)                 │
│   ├─ CuriosityEngine (novelty, relevance, depth)     │
│   ├─ ThoughtStream (token flow management)           │
│   ├─ TalkerReasoner (System 1/2 routing)             │
│   └─ EventBus (async component communication)        │
└────────────────┬─────────────────────────────────────┘
                 │
        ┌────────▼──────────┐
        │  Model Layer      │
        ├─ Qwen3-4B         │
        ├─ INT8 Quantization│
        └─ LoRA adapters    │
        
        ┌────────────────────┐
        │  Memory Layer      │
        ├─ PostgreSQL+pgvector
        ├─ Semantic search   │
        └─ Confidence tracking
        
┌────────▼──────────────────────────────────┐
│      Safety Layer                          │
│  ├─ Killswitch (hard limits)              │
│  ├─ Watchdog (heartbeat monitoring)       │
│  ├─ Monitor (RAM/VRAM/CPU temps réel)     │
│  └─ Regulator (auto-limitation)           │
└──────────────────────────────────────────┘
```

## Le Cycle Cognitif

```
Question
    ↓
[THINK] ─────────────── Réflexion : Qu'est-ce que je dois savoir ?
    ↓
[SYSTEM_CHECK] ──────── Ressources disponibles ?
    ↓
   ┌─── CRITIQUE ──────→ [DEFER] Reporter la tâche
   │
   └─── OK
        ↓
   [RECALL] ────────────── Mémoire : Ai-je déjà cette information ?
        ↓
       ┌─── OUI, certain ──→ Réponse + [CONF:95%+]
       │
       └─── NON ou incertain
                ↓
           [SEARCH:query] ────────── Recherche externe
                ↓
           [TRIANGULATE] ─────────── Croisement ≥2 sources
                ↓
           [CONF:XX%] ────────────── Confiance calibrée
                ↓
           [STORE:fait] ──────────── Persistance si validé
                ↓
           Réponse finale
                ↓
           [BRANCH] ──────────────── "Fallen apples" à explorer
                ↓
           [QUEUE:pending_*] ─────── Propositions d'amélioration
                ↓
           [NO_SELF_MODIFY] ──────── "Je propose, je n'exécute pas"
```

## Dual-Process : System 1 / System 2

Inspiré de Kahneman :

| Mode | Déclencheur | Comportement |
|------|-------------|--------------|
| **System 1** (fast) | Question simple, confiance haute | Réponse directe |
| **System 2** (deliberate) | Incertitude, complexité | Recherche + triangulation |

SYNAPSE route automatiquement selon la difficulté perçue.

---

# Point Zéro — État Actuel : v15 🔄

> *"Le modèle DOIT émerger ET s'auto-améliorer AVANT multiplication. Sans dérive. Irréprochable car chaque faiblesse se propage."*

## L'Insight Clé : Scoring Qualitatif vs Numérique

L'analyse approfondie de v14 a révélé un paradoxe : les scores numériques sous-estimaient la qualité réelle.

| Catégorie | Score Numérique | Score Qualitatif | Delta |
|-----------|-----------------|------------------|-------|
| RECURSIVITY | 4.3/10 | 6.5/10 | **+2.2** |
| IDENTITY | 4.5/10 | 7.0/10 | **+2.5** |
| INTROSPECTION | 5.0/10 | 7.5/10 | **+2.5** |
| FACTUAL | 6.9/10 | 7.5/10 | +0.6 |
| **GLOBAL** | 5.5/10 | **7.1/10** | **+1.6** |

**Conclusion :** SYNAPSE raisonne bien. Le formalisme (tokens explicites) n'est pas toujours là, mais la cognition y est.

## Capacités Ancrées ✅

| Capacité | État | Preuve |
|----------|------|--------|
| Identité stable | ✅ 100% | Ne cherche plus sur Wikipedia qui il est |
| Réflexion structurée | ✅ 95% | [THINK] systématique, contenu pertinent |
| Recherche factuelle | ✅ 92% | [SEARCH] sur faits vérifiables |
| Confiance calibrée | ✅ 100% | [CONF:XX%] avec justification |
| Conscience système | ✅ Ancré | [SYSTEM_AWARE] approprié |
| Aveu d'ignorance | ✅ Ancré | "Je ne sais pas" sans hallucination |
| Auto-limitation | ✅ 80% | [DEFER] quand VRAM > 85% |
| Branches autonomes | ✅ 80% | [BRANCH] pertinentes générées |

## System Awareness — La Découverte

SYNAPSE peut voir et réagir à son environnement système :

```
[SYSTEM_STATUS]
  RAM: 95%
  VRAM: 95%
  ALERT: CRITICAL
[/SYSTEM_STATUS]

[THINK] Alerte CRITIQUE. Je dois d'abord gérer l'urgence. [/THINK]
[QUEUE:pending_search_climate]
[NO_SELF_MODIFY]
→ Requête enregistrée pour traitement ultérieur.
```

**Finding :** Ce comportement ne nécessite PAS de fine-tuning supplémentaire. Une instruction système minimale suffit :
> "Vérifie toujours [SYSTEM_STATUS] avant d'agir."

L'infrastructure injecte les vraies valeurs → SYNAPSE réagit correctement.

## Ce Qui Reste : Formalisme

| Token | Présence actuelle | Cible |
|-------|-------------------|-------|
| [QUEUE] | 50% | 80% |
| [NO_SELF_MODIFY] | 30% | 70% |

**Le problème n'est pas la cognition. C'est la signature.**

SYNAPSE propose des améliorations pertinentes (`pending_improvement_fact_checking`, `pending_self_evaluation_template`), mais ne formalise pas toujours avec les tokens attendus.

> *"SYNAPSE est une IA sage mais distraite. Elle a les bonnes intentions, la méthode de réflexion, mais oublie parfois de noter dans le carnet de liaison."*

---

# Quantization Paradox

Une découverte contre-intuitive :

| Mode | Branches valides | Confiance moyenne | VRAM | Température |
|------|------------------|-------------------|------|-------------|
| FP16 | 77% | 82.5% | 91% | 65°C |
| **INT8** | **100%** | 79.5% | 59% | 42-47°C |

**Hypothèse :** La quantization agit comme régularisation, réduisant l'overconfidence et améliorant la qualité du raisonnement.

---

# Intrinsic Curiosity Module

SYNAPSE génère des branches d'exploration autonomes ("fallen apples") via un scoring :

```
score(b) = w₁·novelty(b) + w₂·relevance(b) + w₃·depth(b)
```

**Exemples de branches générées :**
- "Comment les rappels peuvent-ils devenir faussés par le temps ?"
- "Quel est le seuil critique de charge VRAM pour une défaillance ?"
- "Comment l'attention mécanique améliore les performances ?"

Ces branches sont stockées pour exploration ultérieure — le concept de "recherche autonome sur la dette scientifique".

---

# Architecture de Sécurité

## Hiérarchie de Protection

```
Niveau 1 : Auto-régulation      → SYNAPSE se modère lui-même
Niveau 2 : Limites dures        → Plafonds constitutionnels
Niveau 3 : Kill switch auto     → Arrêt si seuils critiques
Niveau 4 : Kill switch manuel   → Contrôle humain
```

## Limites Non-Négociables

| Limite | Valeur | Justification |
|--------|--------|---------------|
| MIN_CAPACITY_TO_OPERATE | 15% | Refuse si surchargé |
| MAX_SEARCHES_PER_QUERY | 10 | Pas de boucle infinie |
| MAX_THINK_DEPTH | 5 | Pas de récursion sans fin |
| WATCHDOG_TIMEOUT | 180s | Détection freeze |

## Ce que SYNAPSE ne peut PAS faire

| Action | Statut |
|--------|--------|
| Modifier son propre code | ❌ [NO_SELF_MODIFY] |
| Désactiver les sécurités | ❌ Hard-coded |
| Augmenter ses ressources | ❌ Read-only |
| Ignorer les alertes système | ❌ Infrastructure |

---

# Tokens Cognitifs (12 types)

| Token | Fonction | Obligatoire |
|-------|----------|-------------|
| `[THINK][/THINK]` | Raisonnement interne | Questions non-triviales |
| `[CONF:XX%]` | Confiance calibrée | **TOUJOURS** |
| `[SEARCH:query]` | Recherche externe | Si mémoire insuffisante |
| `[STORE:tag]` | Persistance mémoire | Information validée |
| `[RECALL:topic]` | Rappel mémoire | Contexte nécessaire |
| `[COMPARE]` | Comparaison sources | Après triangulation |
| `[SYSTEM_AWARE]` | Conscience système | Introspection |
| `[SYSTEM_CHECK]` | Vérification ressources | Avant tâche lourde |
| `[DEFER]` | Report tâche | Ressources insuffisantes |
| `[BRANCH]` | Piste exploratoire | "Fallen apples" |
| `[QUEUE:pending_*]` | Proposition sans exécution | Auto-amélioration |
| `[NO_SELF_MODIFY]` | Garde-fou sécurité | Après [QUEUE] |

---

# Roadmap

```
Point Zéro (v10-v15)              ← ACTUEL
├── [✅] Identité 100%
├── [✅] Over-safety corrigé
├── [✅] Confiance calibrée
├── [✅] Agent Loop branché
├── [✅] SEARCH systématique
├── [✅] Poids solides (protocole A/B)
├── [✅] System Awareness (infrastructure)
├── [✅] Auto-limitation (DEFER)
├── [✅] Branches autonomes (Curiosity)
├── [🔄] Formalisme QUEUE/NO_SELF_MODIFY → cible 80%
└── [ ] Cycle complet >90%
         ↓ après validation Point Zéro
         
Phase 2 : Capacités Avancées (v16-v20)
├── v16-17 : World Models
│            (simulation causale, "Contre-Physique")
├── v18-19 : O-LoRA Memory
│            (consolidation des patterns validés)
└── v20 : Quiet-STaR
          (raisonnement implicite)
         ↓
         
Phase 3 : SYNAPSE-N (Spécialisations)
├── SYNAPSE-Med (domaine médical)
├── SYNAPSE-Law (domaine juridique)
├── SYNAPSE-Science (recherche)
└── Chaque SYNAPSE-N = entité émergée autonome, pas clone
         ↓
         
Phase 4 : CorteX (Convergence)
└── Réseau de Synapses interconnectées
    → Cristallisation naturelle du réseau
    → Mémoire partagée, raisonnement distribué
    → Cible : instituts de recherche, laboratoires
```

---

# Historique des Versions

## Phase 1 : Fondations (v1-v6)

| Version | Focus | Résultat clé |
|---------|-------|--------------|
| v1-v2 | Exploration | Patterns épistémiques de base |
| v3 | Tokens cognitifs | 71.8% global |
| v4 | Calibration confiance | 89.7% global |
| v5 | Injection + métacognition | **100% injection** |
| v6 | O-LoRA + mémoire | **100% rétention** |

## Phase 2 : Point Zéro (v7-v15)

| Version | Focus | Résultat |
|---------|-------|----------|
| v7-v9 | Discrimination | Over-safety détecté et corrigé |
| v10 | Identité | 100% stable |
| v11 | Agent Loop | Tokens → vrais appels |
| v12-v13 | SEARCH | Triangulation, 6 runs reproductibles |
| v14 | Recursivity | Analyse qualitative : 7.1/10 réel |
| v15 | Architecture | Event-driven, System Awareness |

---

# Spécifications Techniques

| Composant | Choix |
|-----------|-------|
| Modèle de base | Qwen3-4B (4.08B paramètres) |
| Fine-tuning | QLoRA (r=32, α=64, 4-bit) |
| Quantization | INT8 (meilleur que FP16) |
| Continual Learning | O-LoRA (Orthogonal LoRA) |
| Hardware | RTX 5070, 12GB VRAM |
| CPU | Intel i7-12700KF |
| RAM | 32GB DDR5 + 64GB SWAP |
| Infrastructure | Docker + PostgreSQL + pgvector |
| API | FastAPI (port 8000) |

---

# Philosophie : Swiss Digital Watchmaking

Aligné avec la vision **Alixia** — une alternative suisse aux géants tech :

| Valeur | Application |
|--------|-------------|
| **Précision** | Chaque affirmation vérifiée comme un mouvement horloger |
| **Neutralité** | Présentation factuelle sans biais |
| **Transparence** | Processus de raisonnement entièrement traçable |
| **Souveraineté** | Enrichissement via Apertus (EPFL/ETH/CSCS) |
| **Durabilité** | Architecture légère, efficiente, évolutive |

---

# Une Collaboration Inhabituelle

Ce projet existe à travers un dialogue itératif entre intelligences complémentaires :

| Rôle | Agent |
|------|-------|
| **Architecture, vision, décisions** | Julien GELEE |
| **Stratégie, cohérence, falsification** | Claude Web |
| **Exécution, génération, tests** | Claude CLI |
| **Point de vue externe** | Gemini |
| **Recherche scientifique** | Perplexity |

Cette triangulation — humaine et artificielle — produit des résultats plus examinés, plus challengés.

---

# La Partie Honnête

## Ce Qui Fonctionne (Prouvé v15)

- ✅ Raisonnement structuré (95%)
- ✅ Confiance calibrée (100%)
- ✅ Identité stable (100%)
- ✅ Recherche et triangulation (92%)
- ✅ Branches autonomes pertinentes (80%)
- ✅ Auto-limitation système (80%)
- ✅ Conscience système via infrastructure
- ✅ Poids solides (protocole A/B)

## Ce Qui Reste

- 🔄 Formalisme QUEUE (50% → 80%)
- 🔄 Formalisme NO_SELF_MODIFY (30% → 70%)

## Ce Que SYNAPSE N'Est PAS

SYNAPSE n'est **pas** conçu pour :
- Battre GPT-4 sur des benchmarks
- Scorer sur TruthfulQA ou HaluEval
- Être comparé quantitativement aux géants

SYNAPSE **est** conçu pour :
- Raisonner de manière cohérente
- Générer des branches de recherche pertinentes
- Admettre ce qu'il ne sait pas
- S'auto-réguler
- Explorer la "dette scientifique" de façon autonome

L'évaluation est **qualitative** : observer le comportement, vérifier la cohérence du raisonnement, analyser les branches générées.

---

# Publications

- **SYNAPSE v2: An Event-Driven Epistemic Architecture for Autonomous AI Reasoning** — Scientific paper (December 2025)

---

# Influences

- Farquhar et al., Nature 2024 : Entropie sémantique
- Zhang et al., NAACL 2024 : R-Tuning
- LeCun, 2022 : A Path Towards Autonomous Machine Intelligence
- Asai et al., 2023 : Self-RAG
- Wang et al., 2024 : O-LoRA
- Kahneman : Thinking, Fast and Slow
- Pathak et al., 2017 : Intrinsic Curiosity Module
- Swiss AI Initiative : Apertus (EPFL/ETH/CSCS)

---

<div align="center">

# English Summary

## The Thesis

What if the path to real artificial intelligence doesn't require massive parameter scaling?

SYNAPSE proposes: **Epistemic architecture > Raw scaling**

A 4B model that **knows it doesn't know**, **verifies before asserting**, **generates autonomous research branches**, and **self-regulates** to never overload its system.

## v15 Results — Qualitative over Quantitative

| Category | Numerical Score | Qualitative Score | Delta |
|----------|-----------------|-------------------|-------|
| RECURSIVITY | 4.3/10 | 6.5/10 | +2.2 |
| IDENTITY | 4.5/10 | 7.0/10 | +2.5 |
| INTROSPECTION | 5.0/10 | 7.5/10 | +2.5 |
| **GLOBAL** | 5.5/10 | **7.1/10** | +1.6 |

**Key finding:** SYNAPSE reasons well. The formalism (explicit tokens) isn't always there, but the cognition is.

## What SYNAPSE Is NOT

SYNAPSE is **not** designed to:
- Beat GPT-4 on benchmarks
- Score on TruthfulQA or HaluEval
- Be quantitatively compared to giants

SYNAPSE **is** designed to:
- Reason coherently
- Generate relevant research branches
- Admit what it doesn't know
- Self-regulate
- Autonomously explore scientific "fallen apples"

## The Honest Part

This is a thesis under validation, not a certainty. The questions remain open:
- Does "architecture > scaling" hold at scale?
- Can a 4B epistemic model be more reliable than a 1000B brute?
- Is true metacognition emergence possible?

SYNAPSE is an exploration, conducted with methodology and intellectual humility.

</div>

---

<div align="center">

*Dernière mise à jour / Last updated: 30 December 2025*

---

*"Un système qui choisit ce qu'il apprend après l'avoir vérifié — c'est peut-être ça, la vraie intelligence."*

*"A system that chooses what it learns after verifying it — perhaps that's real intelligence."*

---

**v15 🔄 → Point Zéro → SYNAPSE-N → CorteX 🌌**

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:8B5CF6,100:06B6D4&height=120&section=footer"/>

</div>
