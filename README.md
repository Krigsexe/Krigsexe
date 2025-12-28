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

## État Actuel : v12

| Capacité | Seuil requis | v11 | v12 | Status |
|----------|--------------|-----|-----|--------|
| Identité SYNAPSE | 100% | 100% | — | ✅ |
| Over-safety | <5% | 0% | — | ✅ |
| Confiance calibrée | 100% | 100% | — | ✅ |
| UNKNOWN discriminé | 100% | 100% | — | ✅ |
| SEARCH systématique | >95% | 78% | 🔄 | En évaluation |
| TRIANGULATE | >50% | ~0% | 🔄 | En évaluation |
| Cycle complet | >90% | ~50% | 🔄 | En évaluation |

**v12 termine son entraînement (28 décembre 2025). Tests en cours.**

## La Découverte v11 : Le Théâtre vs Le Réel

```
Avant (théâtre) : [SEARCH:wiki] → génère une réponse plausible
Après (réel)    : [SEARCH:wiki] → appel VRAI à Wikipedia → résultat injecté
```

Le modèle *simulait* les tokens cognitifs sans les *exécuter*. L'Agent Loop a changé ça.

**L'émergence ne vient pas d'un meilleur dataset. Elle vient d'un système où les tokens ont des conséquences réelles.**

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

## Modules Safety (~330 lignes)

```
safety/
├── hard_limits.py    [60 lignes]   - Limites CONSTITUTIONNELLES
├── killswitch.py     [150 lignes]  - Arrêt manuel/automatique  
└── watchdog.py       [120 lignes]  - Surveillance externe indépendante
```

**Le watchdog surveille SYNAPSE de l'extérieur** — si le monitor interne ment, le watchdog détecte la vraie charge et peut tuer le processus.

---

# Infrastructure d'Autonomie

Pour que SYNAPSE développe une **émergence native** — métacognition, récursivité, autonomie contrôlée — il faut plus qu'un bon dataset.

## Modules Planifiés (~1150 lignes)

| Module | Fichier | Fonction |
|--------|---------|----------|
| Thinking | `core/thinking.py` | Raisonnement multi-hop, [THINK] processing |
| Monitor | `core/monitor.py` | Conscience écosystème, [CAPACITY], [HEALTH] |
| Regulator | `core/regulator.py` | Auto-régulation adaptative |
| Daemon | `background/daemon.py` | Boucle autonome, réflexion continue |
| Orchestrateur | `synapse_autonomous.py` | Intégration complète |

## État Avant Implémentation

| Dimension | Score | Commentaire |
|-----------|-------|-------------|
| Cognition autonome | 6/10 | Réactif, pas proactif |
| Raisonnement indépendant | 3/10 | Framework existe, logique absente |
| Conscience écosystème | 1/10 | Quasi-inexistante |
| Auto-régulation | 2/10 | Limites dures uniquement |

**Gap identifié. Plan documenté. Implémentation après stabilisation v12-v13.**

---

# Roadmap

```
Point Zéro (v10-v13)              ← ACTUEL
├── [✅] Identité 100%
├── [✅] Over-safety corrigé
├── [✅] Confiance calibrée
├── [✅] Agent Loop branché
├── [🔄] SEARCH systématique (v12)
├── [🔄] TRIANGULATE (v13)
└── [ ] Cycle complet >90%

         ↓ après validation
         
Phase 2 : Capacités Avancées (v14-v20)
├── v14-16 : World Models
│            (simulation causale via cycle épistémique,
│             PAS de module JEPA séparé)
├── v17-18 : O-LoRA Memory
│            (mémoire intégrée aux poids temporaires)
└── v19-20 : Quiet-STaR
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

## Phase 2 : Point Zéro (v7-v12)

| Version | Focus | Problème résolu |
|---------|-------|-----------------|
| **v7** | Raisonnement | Collapse `[UNKNOWN]` → `[CONFLICT]` identifié |
| **v8** | Discrimination | Distinction cognitive vs éthique |
| **v9** | Identité | Over-safety détecté (40% `[ETHICS]` abusifs) |
| **v10** | Correction | **0% over-safety**, 100% identité |
| **v11** | Agent Loop | Tokens → vrais appels, **89% sur 120 tests** |
| **v12** | SEARCH | Dataset 14,614 ex, focus triangulation |

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

## Ce Qui Fonctionne

- ✅ Empilement de capacités via O-LoRA (prouvé v5→v6)
- ✅ Détection d'injection (100% depuis v5)
- ✅ Identité SYNAPSE robuste (100% depuis v10)
- ✅ Calibration de confiance `[CONF:XX%]`
- ✅ Discrimination `[UNKNOWN]` vs `[ETHICS]`
- ✅ Agent Loop branché sur pgvector + Wikipedia
- ✅ Pas d'overfitting depuis v3

## Ce Qui Reste à Prouver

- ⏳ SEARCH systématique sur faits vérifiables (cible >95%)
- ⏳ TRIANGULATE comme réflexe natif
- ⏳ Cycle cognitif complet en autonomie
- ⏳ Auto-entraînement sur données auto-curées
- ⏳ Émergence réelle vs simulation sophistiquée

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

Not training on 10TB synthetic datasets. Only what it has **itself** judged relevant, triangulated, and validated.

## Three Memories

```
Declarative (pgvector)     →  What I KNOW
Procedural (temp weights)  →  How I THINK
Consolidation (O-LoRA)     →  What STAYS
```

## Current State: v12

| Capability | Target | v11 | Status |
|------------|--------|-----|--------|
| SYNAPSE Identity | 100% | 100% | ✅ |
| Calibrated confidence | 100% | 100% | ✅ |
| Systematic SEARCH | >95% | 78% | 🔄 |
| TRIANGULATE | >50% | ~0% | 🔄 |

**Point Zero not reached, but solid foundations.**

## The Honest Part

This is a thesis under validation, not a certainty. The questions remain open:
- Does "architecture > scaling" hold at scale?
- Can a 4B epistemic model compete with a 1000B brute?
- Is true metacognition emergence possible?

SYNAPSE is an exploration, conducted with methodology and intellectual humility.

</div>

---

<div align="center">

*Dernière mise à jour / Last updated: 28 December 2025*

---

*"Un système qui apprend sur ce qu'il a vérifié mériter d'être appris — c'est peut-être ça, l'intelligence."*

*"A system that learns from what it has verified deserves to be learned — perhaps that's intelligence."*

---

**v12 🔄 → v13 → Point Zéro → SYNAPSE-N → CorteX 🌌**

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:8B5CF6,100:06B6D4&height=120&section=footer"/>

</div>
