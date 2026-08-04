
## Prerequisite Material (beginner)

Read/watch alongside Phase 1, not instead of it. These give you the vocabulary the papers assume you already have.

1. **Stanford CS224N — NLP with Deep Learning** (lecture series, ongoing updates)
   *Why first:* Establishes embeddings, RNNs/attention basics, and evaluation methodology before you hit the Transformer paper.

2. **Stanford CS25 — Transformers United** (lecture series, ongoing updates)
   *Why:* Companion to CS224N; guest lectures from lab researchers contextualize why each paper below mattered at the time.

---

## The LLM Architecture Foundation (2017–2020)

Read in this exact order — each paper assumes the previous one.

1. **"Attention Is All You Need"** — Vaswani et al., 2017
   *The Transformer. Everything after this depends on it. Do not skip or skim.*

2. **"BERT: Pre-training of Deep Bidirectional Transformers"** — Devlin et al., 2018
   *Shows how Transformers are pretrained for language understanding via masked language modeling.*

3. **"Language Models are Few-Shot Learners" (GPT-3)** — Brown et al., 2020
   *Introduces in-context learning — the paradigm that makes prompting possible at all. Read the original GPT-1/GPT-2 papers (Radford et al.) as background only if you want historical depth; GPT-3 is the one that matters for modern practice.*

4. **"Scaling Laws for Neural Language Models"** — Kaplan et al., 2020
   *Explains why bigger models + more data = predictable performance gains. Sets up why Chinchilla (next) was a big deal.*

5. **"Training Compute-Optimal Large Language Models" (Chinchilla)** — Hoffmann et al., 2022
   *Corrects Kaplan et al. — shows most LLMs of the era were undertrained relative to their size. Read immediately after #4 for the contrast.*

---

## Making LLMs Usable: Alignment & Reasoning (2020–2023)

By this point you understand *how LLMs are built*. This phase covers *how they're made to behave usefully*.

6. **"Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks"** — Lewis et al., 2020
   *Read here, not later — RAG was invented before RLHF and is architecturally a "base LLM" concept. This is the paper that coined the term "RAG."*

7. **"REALM: Retrieval-Augmented Language Model Pre-Training"** — Guu et al., 2020
   *Parallel effort to #6 — bakes retrieval into pretraining rather than bolting it on at inference. Read directly after Lewis et al. to see the two competing design philosophies.*

8. **"Dense Passage Retrieval for Open-Domain QA" (DPR)** — Karpukhin et al., 2020
   *The dense retrieval mechanism most modern RAG stacks (including yours) still use under the hood.*

9. **"Training language models to follow instructions with human feedback" (InstructGPT)** — Ouyang et al., 2022
   *RLHF. This is the paper that turned raw next-token predictors into usable assistants like ChatGPT.*

10. **"Constitutional AI: Harmlessness from AI Feedback"** — Bai et al., 2022 (Anthropic)
    *An alternative to human-labeled RLHF — AI feedback guided by a written constitution. Read right after InstructGPT for contrast.*

11. **"Chain-of-Thought Prompting Elicits Reasoning in Large Language Models"** — Wei et al., 2022
    *Shows reasoning can be elicited through prompting alone, no retraining needed.*

12. **"Direct Preference Optimization" (DPO)** — Rafailov et al., 2023
    *A simpler mathematical alternative to RLHF. Read after #9–10 to see how the field simplified alignment over time.*

---

## Advanced RAG (2022–2023)

Now that you understand base RAG (#6–8) and reasoning (#11), this phase covers the techniques on **Advanced RAG Pipeline** project.

13. **"HyDE: Precise Zero-Shot Dense Retrieval without Relevance Labels"** — Gao et al., 2022
    *Hypothetical Document Embeddings — generate a fake answer first, embed that for retrieval. A now-common trick in advanced pipelines.*

14. **"In-Context Retrieval-Augmented Language Models"** — Ram et al., 2023 (AI21)
    *Simpler retrieval-at-inference approach — read as a contrast to Lewis et al.'s heavier architecture.*

15. **"Lost in the Middle: How Language Models Use Long Contexts"** — Liu et al., 2023
    *Explains why retrieved documents placed in the middle of a long context get ignored — the core justification for reranking.*

16. **"Self-RAG: Learning to Retrieve, Generate, and Critique through Self-Reflection"** — Asai et al., 2023
    *The model decides *when* to retrieve and critiques its own output — directly relevant to your hybrid retrieval + reranking design.*

17. **RAGAS: "Automated Evaluation of Retrieval Augmented Generation"** — Es et al., 2023
    *Read last in this phase — you now understand every failure mode RAGAS's metrics (faithfulness, answer relevancy, context precision/recall) are designed to catch.*

---

## Agentic AI Foundations (2022–2023)

This is the conceptual base for your **LangGraph Multi-Agent Research Assistant**. Read Phase 2's reasoning papers (#11) before starting here.

18. **"MRKL Systems: A modular, neuro-symbolic architecture..."** — Karpas et al., 2022 (AI21)
    *Early "modular reasoning + knowledge + language" framework — precursor to modern tool-routing agent designs.*

19. **"ReAct: Synergizing Reasoning and Acting in Language Models"** — Yao et al., 2022
    *The foundational agent paper. Interleaving thought → action → observation is the loop nearly every agent framework, including LangGraph, still implements. Read this carefully.*

20. **"Toolformer: Language Models Can Teach Themselves to Use Tools"** — Schick et al., 2023 (Meta)
    *Models learning to self-supervise tool invocation, rather than being explicitly prompted with tool schemas.*

21. **"Reflexion: Language Agents with Verbal Reinforcement Learning"** — Shinn et al., 2023
    *Agents that critique and revise their own past trajectories — the precursor to multi-agent self-correction loops.*

22. **"Generative Agents: Interactive Simulacra of Human Behavior"** — Park et al., 2023 (Stanford, "Smallville")
    *Less directly applicable to a research-assistant agent, but foundational for memory + planning architecture design. Read for architectural literacy, not implementation.*

23. **AutoGPT / BabyAGI** (open-source projects, 2023 — no formal paper)
    *Historically important: popularized fully autonomous agentic loops, even though the underlying architecture was fairly naive by today's standards. Read the repo READMEs, not the code, purely for historical context.*

---

## Applied / Practitioner Resources (read throughout, not sequentially)

These aren't papers — they're the "how do I actually build this" layer. Dip into them as you implement each phase above rather than reading front-to-back.

- **Lilian Weng — "LLM Powered Autonomous Agents"** (blog, posted while at OpenAI)
  *Functions as an informal literature review of Phase 4 — read this right after #19–21 to consolidate.*

- **Anthropic Engineering Blog — "Building Effective Agents"**
  *A practical taxonomy of agent patterns (prompt chaining, routing, orchestrator-worker, evaluator-optimizer). Read once you've finished Phase 4 — it will map cleanly onto the papers you just read.*

- **Chip Huyen — *Designing Machine Learning Systems*** (book)
  *Production/systems-design lens on ML pipelines generally, including RAG. Good for portfolio-write-up credibility.*

- **Eugene Yan — eugeneyan.com** (blog)
  *Practitioner-level writing specifically on RAG evaluation and agent design patterns. Read alongside Phase 3 and Phase 4.*

- **DeepLearning.AI short courses** (Andrew Ng, built with LangChain team):
  - "Building and Evaluating Advanced RAG" → pairs with Phase 3
  - "AI Agents in LangGraph" → pairs with Phase 4
  - "LangChain for LLM Application Development" → general implementation companion

- **LangChain / LangGraph cookbook repos** (GitHub)
  *Read the actual graph-construction code for supervisor / hierarchical / swarm multi-agent patterns — this teaches more about real agent architecture than most papers. Read last, once Phase 4 concepts are solid.*

- **Hugging Face Daily Papers** (ongoing)
  *For tracking anything published after this list — check periodically once you've finished Phases 1–4.*

