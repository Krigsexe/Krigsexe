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

> Peut-on construire une IA qui reconnaît ses lacunes, va chercher l'information par elle-même, la vérifie, puis seulement alors répond ?

C'est le cycle que j'essaie d'implémenter :

```
Je ne sais pas → Je cherche → Je vérifie → Je comprends → Maintenant je sais
```

Pas une IA passive qui avoue son ignorance. Une IA qui agit dessus.

---

## L'architecture en construction

Le cœur du projet repose sur des tokens cognitifs, des marqueurs explicites qui structurent le raisonnement :

```
[THINK]      Réflexion initiale. Qu'est-ce que je sais vraiment sur ce sujet ?
[CONF:73%]   Niveau de confiance calibré. Pas une impression, une estimation.
[TYPE:C]     Classification de l'incertitude. Ici : information potentiellement obsolète.
[SEARCH]     Déclenchement d'une recherche externe. Je ne devine pas, j'investigue.
[VERIFY]     Croisement des sources. Une seule source ne suffit jamais.
[SIMULATE]   Simulation causale. Si X alors Y. Quels risques ? Quelles alternatives ?
```

La v6 introduit le World Model : avant de répondre à "que se passe-t-il si je pousse ce verre ?", le modèle doit simuler mentalement les conséquences physiques. Plus de réponses déconnectées du réel.

---

## État des lieux

| Composant | Statut | Notes |
|-----------|--------|-------|
| Noyau épistémique (v5) | En cours, ~26% | 18K exemples, calibration de confiance |
| World Model (v6) | Construction du dataset | Simulation causale, physique newtonienne |
| Infrastructure mémoire | Opérationnelle | PostgreSQL + pgvector |
| Release publique | Pas encore | Le projet reste expérimental |

Une découverte inattendue : le modèle a spontanément appris à détecter les tentatives de manipulation. Comportement émergent, non entraîné explicitement. L'investigation continue.

---

## Une collaboration inhabituelle

Ce projet existe à travers un dialogue itératif avec des systèmes IA :

- Moi : architecture, entraînement, intégration, questionnements
- Claude (Anthropic) : analyse technique, documentation, revue critique
- Gemini (Google) : validation stratégique, ancrage physique pour le World Model
- Les travaux de Yann LeCun : la fondation théorique vers laquelle je reviens constamment

Est-ce étrange de développer de l'IA avec de l'IA ? Les idées qui émergent de cette boucle semblent plus examinées, plus challengées. Une forme d'humilité scientifique en action.

---

## La partie honnête

Je ne sais pas si ça va marcher.

L'hypothèse pourrait être fausse. Un modèle 4B pourrait manquer de capacité pour un vrai raisonnement épistémique. L'approche pourrait être naïve.

Mais c'est ça, la recherche. On forme une hypothèse, on teste, on apprend. Chaque doute devient une opportunité de progresser.

Ce que je sais : construire des IA qui hallucinent avec assurance n'est pas suffisant. Nous avons besoin de systèmes qui traitent l'incertitude comme le point de départ d'une action, pas comme une fin en soi.

---

## Influences

- Farquhar et al., Nature 2024 : Entropie sémantique pour détecter les hallucinations
- Zhang et al., NAACL 2024 : R-Tuning, apprendre à reconnaître ses limites
- LeCun, 2022 : A Path Towards Autonomous Machine Intelligence
- Asai et al., 2023 : Self-RAG, apprendre quand chercher de l'information

---

# What I'm Working On

## Project SYNAPSE: Towards Epistemically Autonomous AI

Current LLMs have a fundamental problem. They answer everything with equal confidence, whether they know or not. Worse: when they don't know, they fabricate. And when they could search, they guess.

The question driving me:

> Can we build an AI that recognizes its gaps, goes searching for information on its own, verifies it, and only then responds?

This is the cycle I'm trying to implement:

```
I don't know → I search → I verify → I understand → Now I know
```

Not a passive AI that admits ignorance. An AI that acts on it.

---

## The Architecture Being Built

The core relies on cognitive tokens, explicit markers that structure reasoning:

```
[THINK]      Initial reflection. What do I actually know about this?
[CONF:73%]   Calibrated confidence level. Not a feeling, an estimate.
[TYPE:C]     Uncertainty classification. Here: potentially stale information.
[SEARCH]     External search trigger. I don't guess, I investigate.
[VERIFY]     Source cross-referencing. One source is never enough.
[SIMULATE]   Causal simulation. If X then Y. What risks? What alternatives?
```

Version 6 introduces the World Model: before answering "what happens if I push this glass?", the model must mentally simulate the physical consequences. No more answers disconnected from reality.

---

## Current State

| Component | Status | Notes |
|-----------|--------|-------|
| Epistemic core (v5) | Training, ~26% | 18K examples, confidence calibration |
| World Model (v6) | Building dataset | Causal simulation, Newtonian physics |
| Memory infrastructure | Operational | PostgreSQL + pgvector |
| Public release | Not yet | Project remains experimental |

An unexpected discovery: the model spontaneously learned to detect manipulation attempts. Emergent behavior, not explicitly trained. Investigation ongoing.

---

## An Unusual Collaboration

This project exists through iterative dialogue with AI systems:

- Me: architecture, training, integration, questioning
- Claude (Anthropic): technical analysis, documentation, critical review
- Gemini (Google): strategic validation, physics grounding for World Model
- Yann LeCun's work: the theoretical foundation I keep returning to

Is it strange to develop AI with AI? Ideas emerging from this loop feel more examined, more challenged. Scientific humility in action.

---

## The Honest Part

I don't know if this will work.

The hypothesis might be wrong. A 4B model might lack capacity for genuine epistemic reasoning. The approach might be naive.

But that's research. You form a hypothesis, you test, you learn. Every doubt becomes an opportunity to progress.

What I do know: building AI that confidently hallucinates isn't good enough. We need systems that treat uncertainty as the starting point for action, not an end in itself.

---

## What's Next

- Finish v5 training
- Validate the World Model dataset
- Test: can the model simulate physical consequences before answering?
- Open-source release, when ready

---

<div align="center">

*Dernière mise à jour / Last updated: December 2025*

*"Une machine qui connaît ses limites et agit pour les dépasser est plus utile qu'une qui prétend tout savoir."*

*"A machine that knows its limits and acts to overcome them is more useful than one that pretends to know everything."*

---

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:8B5CF6,100:06B6D4&height=120&section=footer"/>

</div>
