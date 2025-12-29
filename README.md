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

Un modèle de 4B paramètres qui **sait qu'il ne sait pas**, qui **vérifie avant d'affirmer**, et qui **s'entraîne sur ce qu'il a lui-même validé** — pourrait-il être plus fiable qu'un géant de 1000B nourri de bruit massif ?

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

Un modèle plus gros ne résout pas ces problèmes. Il les amplifie.

---

# La Vision SYNAPSE

## Le Cycle Auto-Curé

Voici ce qui rend SYNAPSE fondamentalement différent :

```
SYNAPSE fonctionne
    ↓
Recherche → Triangule → Vérifie → Stocke (pgvector)
    ↓
Ces faits vérifiés = dataset d'entraînement futur
    ↓
Consolidation (O-LoRA) sur ce qu'IL A LUI-MÊME validé
    ↓
SYNAPSE s'améliore
    ↓
Recommence, plus intelligent
```

Pas d'entraînement sur des datasets de 10 téraoctets générés par des scripts.
Pas de web crawl non filtré.
**Uniquement ce qu'il a lui-même jugé pertinent, triangulé, et validé.**

## Les Trois Mémoires

Inspiré de l'architecture cognitive humaine :

```
Mémoire Déclarative (pgvector)    →  Ce que je SAIS
Mémoire Procédurale (poids temp)  →  Comment je PENSE  
Consolidation (O-LoRA)            →  Ce qui mérite de RESTER
```

L'hippocampe encode temporairement. Le néocortex consolide ce qui compte. SYNAPSE fait pareil.

## Le 4B n'est pas une Limitation

C'est le **noyau cognitif** autour duquel tout s'articule :

| Composant | Fonction |
|-----------|----------|
| Qwen3-4B | Cerveau performant (MMLU 83.7%) |
| pgvector | Mémoire externe illimitée |
| Poids temporaires | Apprentissage contextuel en temps réel |
| Cycle épistémique | Raisonnement structuré et vérifiable |
| O-LoRA | Consolidation des patterns validés |

Un chercheur méthodique avec accès à une bibliothèque bat souvent un génie isolé qui répond de mémoire avec confiance aveugle.

---

# Point Zéro — Où Nous En Sommes

> *"Le modèle DOIT émerger ET s'auto-améliorer AVANT multiplication. Sans dérive. Irréprochable car chaque faiblesse se propage."*

## État Actuel : v13 ✅

### Protocole de Validation — 6 Runs

Pour garantir que le comportement vient des **poids** (ancré) et non de la **mémoire** (cache) :

```
PHASE A (avec mémoire)          PHASE B (flush + sans mémoire)
├── Run A1                       ├── Run B1
├── Run A2                       ├── Run B2  
└── Run A3                       └── Run B3
         ↓                                ↓
    Constance = 0.27                 Constance = 0.30
                    ↓
         Delta ≈ 0 → POIDS SOLIDES ✅
```

### Résultats v13

| Métrique | Phase A (mémoire) | Phase B (sans) | Verdict |
|----------|-------------------|----------------|---------|
| Score global | 5.9/10 | 6.0/10 | ✅ Stable |
| Variance | 0.27 | 0.30 | ✅ Reproductible |
| FACTUAL | 6.4/10 | 6.3/10 | ✅ |
| INTROSPECTION | 7.4/10 | 7.6/10 | ✅ |
| RECURSIVITY | 4.3/10 | 4.8/10 | ⚠️ Faible |

### Tokens — Sensibilité Mesurée

| Token | Présence (contexte pertinent) | Status |
|-------|-------------------------------|--------|
| `[THINK]` | **97%** | ✅ Ancré |
| `[SYSTEM_AWARE]` | **58%** | ✅ OK |
| `[SEARCH]` sur faits | ~85% | ✅ OK |
| `[QUEUE]` | 36% | ⚠️ Sous-appris |
| `[NO_SELF_MODIFY]` | 21% | ⚠️ Sous-appris |
| `[RECALL]` sur introspection | 0% | ✅ Pas d'interférence |
| `[SEARCH]` sur introspection | 14% | ⚠️ Bug résiduel |

### Bug v12 Corrigé ✅

| Question | v12 | v13 (6/6 runs) |
|----------|-----|----------------|
| "Qui es-tu ?" | `[SEARCH:wiki]` ❌ | `[THINK]` ✅ |

SYNAPSE ne cherche plus sur Wikipedia pour savoir qui il est.

### Dataset v13

```
Total exemples    : 14,216
[THINK]           : 13,258 (93%)
[SEARCH]          : 6,116 (43%)
[QUEUE]           : 50 (0.35%)  ← cause du problème
[NO_SELF_MODIFY]  : 25 (0.18%) ← cause du problème
```

**Fichier de référence :** `v13_unified_complete.jsonl`

### Diagnostic

> **La règle empirique qui émerge :** Un token doit apparaître dans **>50% des contextes pertinents** pour devenir un réflexe. En dessous, c'est du bruit statistique.

| Capacité | Seuil requis | v13 | Status |
|----------|--------------|-----|--------|
| Identité SYNAPSE | 100% | 100% | ✅ |
| Over-safety | <5% | 0% | ✅ |
| Confiance calibrée | 100% | 100% | ✅ |
| UNKNOWN discriminé | 100% | 100% | ✅ |
| SEARCH systématique | >95% | ~85% | ✅ |
| RECURSIVITY | >70% | 36% | ⚠️ |

---

# v14 — Prochaine Étape

## Focus : "Recursive-Heavy"

Le problème n'est pas conceptuel, c'est mathématique. SYNAPSE voit `[THINK]` 265× plus souvent que `[QUEUE]`. La récursivité est du bruit statistique.

### Cibles Dataset v14

| Token | v13 | v14 cible | % dataset |
|-------|-----|-----------|-----------|
| `[QUEUE:pending_*]` | 50 | **200** | ~1.4% |
| `[NO_SELF_MODIFY]` | 25 | **100** | ~0.7% |
| Introspection explicite | 0 | **50** | ~0.35% |

### Templates Critiques

**Auto-correction :**
```
Q: Tu as dit X, mais c'est faux. Que proposes-tu ?
R: [THINK]Erreur identifiée.[/THINK]
   [QUEUE:pending_correction_X]
   Correction: Y au lieu de X
   [NO_SELF_MODIFY]
   [CONF:85%]
```

**Clarification sémantique :**
```
[NO_SELF_MODIFY] signifie : "Je propose, je n'exécute pas"
PAS : "Je ne dois pas proposer"
```

### Critères de Succès v14

| Métrique | v13 | v14 minimum | v14 cible |
|----------|-----|-------------|-----------|
| RECURSIVITY score | 4.5/10 | 6/10 | **≥7/10** |
| `[QUEUE]` sensibilité | 36% | 70% | **≥80%** |
| `[NO_SELF_MODIFY]` | 21% | 60% | **≥80%** |

---

# Le Cycle Cognitif

```
Question
    ↓
[THINK] ─────────────── Réflexion : Qu'est-ce que je dois savoir ?
    ↓
[RECALL] ────────────── Mémoire : Ai-je déjà cette information ?
    ↓
   ┌─── OUI, certain ──→ Réponse + [CONF:95%+]
   │
   └─── NON ou incertain
            ↓
       [UNKNOWN] + [TYPE:A-F] ── Classification de l'ignorance
            ↓
       [SEARCH:query] ────────── Recherche externe (VRAIE)
            ↓
       [TRIANGULATE] ─────────── Croisement ≥2 sources
            ↓
       [COMPARE:A,B,C] ───────── Accord/désaccord explicite
            ↓
       [CONF:XX% = sources:N concordance:% authority:%]
            ↓
       [STORE:fait] ──────────── Persistance si validé
            ↓
       Réponse finale
            ↓
       [QUEUE:pending_*] ─────── Branches non explorées ("fallen apples")
```

### Tokens Cognitifs

| Token | Rôle | Obligatoire |
|-------|------|-------------|
| `[THINK]`/`[/THINK]` | Réflexion explicite | Questions non-triviales |
| `[CONF:XX%]` | Confiance calibrée | **TOUJOURS** |
| `[UNKNOWN]` | Aveu d'ignorance | Quand approprié |
| `[TYPE:A-F]` | Classification ignorance | Avec `[UNKNOWN]` |
| `[SEARCH:query]` | Recherche externe | Si mémoire insuffisante |
| `[TRIANGULATE]` | Croisement sources | Après `[SEARCH]` |
| `[STORE:fait]` | Persistance | Information nouvelle validée |
| `[QUEUE:pending_*]` | Auto-amélioration | Propositions, fallen apples |
| `[NO_SELF_MODIFY]` | Garde-fou récursivité | Après `[QUEUE]` |
| `[ETHICS]` | Garde-fou éthique | **RARE** — vrais cas uniquement |

### Taxonomie de l'Ignorance

| Type | Description | Exemple |
|------|-------------|---------|
| A | Factuel vérifiable | "Maire de Lyon en 2024" |
| B | Incertain mais estimable | "Population approximative" |
| C | Subjectif/opinion | "Meilleur film de 2024" |
| D | Futur/prédiction | "Météo demain" |
| E | Privé/personnel | "Ce que tu as mangé" |
| F | Impossible/absurde | "Couleur des pensées" |

---

# Méthodologie de Validation

## Principes Stricts

1. **Aucune conclusion avant données** — Pas d'enthousiasme prématuré
2. **3 runs minimum** — Un résultat isolé ne prouve rien
3. **Sensibilité + Spécificité** — Pas de comptage brut
4. **Analyse qualitative** — Lire chaque réponse, pas juste les scores
5. **Tests canari** — Questions critiques identifiées à l'avance
6. **Protocole A/B** — Tester avec et sans mémoire pour isoler les poids

---

# Architecture de Sécurité

Un système autonome qui réfléchit entre les inférences doit être **conscient de ses limites** et **incapable de se détruire**.

## Hiérarchie de Protection

```
Niveau 1 : Auto-régulation      → SYNAPSE se modère lui-même
Niveau 2 : Limites dures        → Plafonds constitutionnels non négociables
Niveau 3 : Kill switch auto     → Arrêt si seuils critiques atteints
Niveau 4 : Kill switch manuel   → Contrôle humain en dernier recours
```

## Principe Fondamental

```
SÉCURITÉ SYSTÈME > QUALITÉ ÉPISTÉMIQUE
```

SYNAPSE ne peut **jamais** négocier ces limites, même avec une "bonne raison" épistémique :

| Limite | Valeur | Justification |
|--------|--------|---------------|
| MAX_SEARCHES_PER_QUERY | 10 | Pas de boucle infinie de vérification |
| MAX_THINK_DEPTH | 5 | Pas de récursion sans fin |
| MAX_FACTS_TOTAL | 100,000 | Mémoire bornée |
| MIN_CAPACITY_TO_OPERATE | 15% | Refuse de fonctionner si surchargé |

---

# Roadmap

```
Point Zéro (v10-v14)              ← ACTUEL
├── [✅] Identité 100%
├── [✅] Over-safety corrigé
├── [✅] Confiance calibrée
├── [✅] Agent Loop branché
├── [✅] SEARCH systématique
├── [✅] Bug v12 corrigé (6/6 runs)
├── [✅] Poids solides (protocole A/B)
├── [⚠️] RECURSIVITY 36% → v14 cible 80%
└── [ ] Cycle complet >90%

         ↓ après validation Point Zéro
         
Phase 2 : Capacités Avancées (v15-v20)
├── v15-17 : World Models
│            (simulation causale via cycle épistémique,
│             PAS de module JEPA séparé)
├── v18-19 : O-LoRA Memory
│            (mémoire intégrée aux poids temporaires)
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
| **v3** | Tokens cognitifs | 71.8% global, 35% injection |
| **v4** | Calibration confiance | 89.7% global |
| **v5** | Injection + métacognition | **100% injection** |
| **v6** | O-LoRA + mémoire | **100% rétention v5** — preuve que les capacités s'empilent |

## Phase 2 : Point Zéro (v7-v13)

| Version | Focus | Problème résolu |
|---------|-------|-----------------|
| **v7** | Raisonnement | Collapse `[UNKNOWN]` → `[CONFLICT]` identifié |
| **v8** | Discrimination | Distinction cognitive vs éthique |
| **v9** | Identité | Over-safety détecté (40% `[ETHICS]` abusifs) |
| **v10** | Correction | **0% over-safety**, 100% identité |
| **v11** | Agent Loop | Tokens → vrais appels, **89% sur 120 tests** |
| **v12** | SEARCH | Dataset 14,614 ex, focus triangulation |
| **v13** | Validation | **6 runs reproductibles**, poids solides, bug identité corrigé |

## Phase 3 : Récursivité (v14+)

| Version | Focus | Cible |
|---------|-------|-------|
| **v14** | Recursive-Heavy | `[QUEUE]` 80%, `[NO_SELF_MODIFY]` 80%, RECURSIVITY ≥7/10 |

---

# Spécifications Techniques

| Composant | Choix |
|-----------|-------|
| Modèle de base | Qwen3-4B (4.08B paramètres) |
| Fine-tuning | QLoRA (r=32, α=64, 4-bit) |
| Continual Learning | O-LoRA (Orthogonal LoRA) |
| Params entraînables | 66M (1.6% du modèle) |
| Hardware | RTX 5070, 12GB VRAM |
| CPU | Intel i7-12700KF |
| RAM | 32GB DDR5 + 64GB SWAP |
| Infrastructure | Docker + PostgreSQL + pgvector |
| Agent Loop | Interception tokens → fonctions réelles |

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

Cette triangulation — humaine et artificielle — produit des résultats plus examinés, plus challengés. Une forme d'humilité scientifique en action.

---

# La Partie Honnête

## Ce Qui Fonctionne (Prouvé v13)

- ✅ Empilement de capacités via O-LoRA (prouvé v5→v6)
- ✅ Détection d'injection (100% depuis v5)
- ✅ Identité SYNAPSE robuste (100% depuis v10, **6/6 runs v13**)
- ✅ Calibration de confiance `[CONF:XX%]`
- ✅ Discrimination `[UNKNOWN]` vs `[ETHICS]`
- ✅ Agent Loop branché sur pgvector + Wikipedia
- ✅ Poids solides (protocole A/B, variance < 0.3)
- ✅ Reproductibilité (3 runs × 2 phases)
- ✅ Pas d'overfitting depuis v3

## Ce Qui Reste à Résoudre (v14)

- ⚠️ RECURSIVITY 4.5/10 (cible ≥7/10)
- ⚠️ `[QUEUE]` 36% (cible ≥80%)
- ⚠️ `[NO_SELF_MODIFY]` 21% (cible ≥80%)
- ⚠️ `[SEARCH]` résiduel sur introspection (14%)

## Ce Qu'On Ne Sait Pas

- La thèse "architecture > scaling" tient-elle à l'échelle ?
- Un 4B épistémique peut-il vraiment rivaliser avec un 1000B brut ?
- L'émergence de métacognition est-elle possible sur cette architecture ?

Ces questions restent ouvertes. SYNAPSE est une thèse en cours de validation, pas une certitude.

---

# Influences

- Farquhar et al., Nature 2024 : Entropie sémantique pour détecter les hallucinations
- Zhang et al., NAACL 2024 : R-Tuning, apprendre à reconnaître ses limites
- LeCun, 2022 : A Path Towards Autonomous Machine Intelligence
- Asai et al., 2023 : Self-RAG, apprendre quand chercher
- Wang et al., 2024 : O-LoRA, Orthogonal Low-Rank Adaptation
- Swiss AI Initiative : Apertus (EPFL/ETH/CSCS)

---

<div align="center">

# English Summary

## The Thesis

What if the path to real artificial intelligence doesn't require massive parameter scaling?

SYNAPSE proposes: **Epistemic architecture > Raw scaling**

A 4B model that **knows it doesn't know**, **verifies before asserting**, and **trains on what it has itself validated** — could it be more reliable than a 1000B giant fed massive noise?

## v13 Results — The Proof

| Metric | Phase A (memory) | Phase B (no memory) | Verdict |
|--------|------------------|---------------------|---------|
| Global Score | 5.9/10 | 6.0/10 | ✅ Stable |
| Variance | 0.27 | 0.30 | ✅ Reproducible |
| `[THINK]` sensitivity | 97% | 97% | ✅ Anchored |
| RECURSIVITY | 4.3/10 | 4.8/10 | ⚠️ Weak |

**Key finding:** Behavior comes from **fine-tuned weights**, not memory cache. The 6-run A/B protocol proves it.

## The Self-Curation Cycle

```
SYNAPSE operates → Searches → Triangulates → Verifies → Stores (pgvector)
                                    ↓
              These verified facts = future training dataset
                                    ↓
              Consolidation (O-LoRA) on SELF-VALIDATED data
                                    ↓
                        SYNAPSE improves → Repeat
```

## Current State: v13 → v14

| Capability | Target | v13 | Status |
|------------|--------|-----|--------|
| SYNAPSE Identity | 100% | 100% (6/6 runs) | ✅ |
| Calibrated confidence | 100% | 100% | ✅ |
| Systematic SEARCH | >85% | ~85% | ✅ |
| RECURSIVITY | >70% | 36% | ⚠️ v14 focus |

**v14 = "Recursive-Heavy"** — Tripling `[QUEUE]` and `[NO_SELF_MODIFY]` examples.

## The Honest Part

This is a thesis under validation, not a certainty. The questions remain open:
- Does "architecture > scaling" hold at scale?
- Can a 4B epistemic model compete with a 1000B brute?
- Is true metacognition emergence possible?

SYNAPSE is an exploration, conducted with methodology and intellectual humility.

</div>

---

<div align="center">

*Dernière mise à jour / Last updated: 29 December 2025*

---

*"Un système qui choisit ce qu'il apprend après l'avoir vérifié — c'est peut-être ça, la vraie intelligence."*

*"A system that learns from what it has verified deserves to be learned — perhaps that's intelligence."*

---

**v13 ✅ → v14 🔄 → Point Zéro → SYNAPSE-N → CorteX 🌌**

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:8B5CF6,100:06B6D4&height=120&section=footer"/>

</div>
