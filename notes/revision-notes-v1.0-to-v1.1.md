# Exam Revision Notes: v1.0 → v1.1 (AIF-C01)

> **Version 1.0** published March 26, 2026 | **Version 1.1** published April 30, 2026
>
> The v1.1 exam replaces v1.0 approximately one month after publication. Even though some content was removed or reworded from the official objectives, the underlying concepts are still valid foundational knowledge. This document captures what changed and why you should still know the removed content.

---

## Content Removed from Objectives (Still Worth Knowing)

### 1. Area Under the Curve (AUC) — Removed from Objective 1.3.6

**What changed:** The metric list changed from "accuracy, Area Under the Curve [AUC], F1 score" to "accuracy, precision, recall, F1 score."

**Why still know it:**
- AUC-ROC is still widely used in practice for evaluating binary classifiers
- May still appear as a distractor in answer choices
- Understanding it helps you understand precision/recall tradeoffs (which ARE on the exam)

**Quick notes on AUC:**

| Concept | Explanation |
|---------|-------------|
| **ROC Curve** | Plots True Positive Rate (Recall) vs. False Positive Rate at different classification thresholds |
| **AUC** | Area Under the ROC Curve — single number (0 to 1) summarizing classifier performance |
| **AUC = 0.5** | Random guessing (the diagonal line) — model has no discriminative ability |
| **AUC = 1.0** | Perfect classifier — separates all positives from negatives perfectly |
| **AUC = 0.8** | Good — means there's an 80% chance the model ranks a random positive example higher than a random negative example |

> **Why it was likely removed:** The exam shifted toward more intuitive, business-friendly metrics (precision, recall, F1). AUC requires understanding ROC curves and thresholds — more of a data scientist concept than a practitioner one. Precision/recall are easier to explain to stakeholders: "Of the ones we flagged, how many were right?" (precision) and "Of all the actual fraud, how much did we catch?" (recall).

> **Connection to what's still tested:** AUC is essentially a summary of the precision-recall tradeoff across all thresholds. If you understand precision and recall deeply (which you need for v1.1), you implicitly understand what AUC measures.

---

### 2. Explicit Pipeline Component Names — Removed from Objective 1.3.1

**What changed:** The detailed list "(for example, data collection, exploratory data analysis [EDA], data pre-processing, feature engineering, model training, hyperparameter tuning, evaluation, deployment, monitoring)" was replaced with simply "Describe and differentiate components of an AI/ML pipeline."

**Why still know it:**
- The concepts didn't go away — the objective just became more general
- You still need to understand each pipeline stage to answer questions about it
- The new wording "describe AND differentiate" suggests you need to know how stages differ from each other

**The full pipeline (still testable, just not explicitly listed):**

```
Data Collection → EDA → Pre-processing → Feature Engineering → Model Training → Hyperparameter Tuning → Evaluation → Deployment → Monitoring
```

> **Key differentiators between stages (what "differentiate" likely means):**
> - **EDA** = understanding data (descriptive, no changes made)
> - **Pre-processing** = fixing data quality issues (changes made, but no new info created)
> - **Feature engineering** = creating new useful inputs from raw data (new info derived)
> - **Training** = algorithm learning patterns (model created)
> - **Tuning** = optimizing the learning process itself (model refined)
> - **Evaluation** = measuring quality (no model changes, just assessment)

---

### 3. SageMaker Data Wrangler and Feature Store — Removed from Objective 1.3.4

**What changed:** The example services changed from "(for example, SageMaker AI, SageMaker Data Wrangler, SageMaker Feature Store, SageMaker Model Monitor)" to "(for example, Amazon Bedrock, Amazon Q, Amazon Quick, Kiro, SageMaker AI)."

**Why still know them:**

| Service | What It Does | Why Still Relevant |
|---------|-------------|-------------------|
| **SageMaker Data Wrangler** | Visual data preparation and transformation tool | Still exists as a SageMaker feature; data prep questions still appear |
| **SageMaker Feature Store** | Centralized repository for storing and retrieving ML features | Feature engineering is still a pipeline concept; store enables reusability |
| **SageMaker Model Monitor** | Monitors deployed models for drift and quality | Still critical — just moved to a monitoring context rather than a pipeline one |

> **Why the shift happened:** v1.1 focuses more on the GenAI/FM stack (Bedrock, Q, Quick, Kiro) reflecting the industry shift from custom ML pipelines to foundation model applications. The exam is becoming less "data science tooling" and more "AI application building."

---

### 4. "Amazon Bedrock Agents, agentic AI, model context protocol" — Reworded in Objective 3.1.6

**What changed:** From "Describe the role of agents in multi-step tasks (for example, Amazon Bedrock Agents, agentic AI, model context protocol)" to "Define the role of AI agents and describe AI agents' business applications."

**Why this matters:**
- The new wording is BROADER — not just "multi-step tasks" but all "business applications"
- MCP and Bedrock Agents are now covered elsewhere (Domain 2, Objective 2.1.6)
- The emphasis shifted from TECHNICAL implementation to BUSINESS VALUE of agents

> **Study implication:** Don't just know what agents DO technically. Know what business problems they SOLVE:
> - Customer service automation (reduce ticket resolution time)
> - Research and analysis (accelerate report generation)
> - Process automation (invoice processing, approvals)
> - Code assistance (development acceleration)

---

### 5. "Simplicity" as GenAI Advantage — Removed from Objective 2.2.1

**What changed:** From "adaptability, responsiveness, simplicity" to "adaptability, responsiveness, conversational capabilities, ability to generate content."

**Why the change makes sense:**
- "Simplicity" was vague and arguably incorrect — GenAI is NOT simple under the hood
- The replacement terms are more specific and testable
- "Conversational capabilities" and "ability to generate content" are the TRUE differentiators of GenAI vs. traditional ML

> **What to focus on now:** The advantages that are UNIQUE to GenAI (not shared with traditional ML):
> - Conversational interface (natural language in/out)
> - Content generation (creating NEW things, not just classifying/predicting)
> - These are the reasons you'd choose GenAI OVER traditional ML

---

### 6. "Human Evaluation" → "Human-in-the-loop Evaluation" — Objective 3.4.1

**What changed:** Simple rewording from "human evaluation" to "human-in-the-loop evaluation."

**Why it matters:**
- "Human-in-the-loop" is more precise — it emphasizes humans as part of the PROCESS, not a one-time review
- Aligns with Amazon A2I (Augmented AI) which IS a human-in-the-loop service
- Suggests ongoing integration of human judgment, not just post-hoc review

> **Exam implication:** If you see "human-in-the-loop" in an answer choice and "human evaluation" in another, they mean the same thing in this context. But expect the newer terminology.

---

### 7. Amazon MemoryDB — Removed from In-Scope Services

**What changed:** Amazon MemoryDB was removed from the in-scope database list.

**Why still know it exists:**
- MemoryDB is a Redis-compatible, durable, in-memory database
- It supports vector search (useful for RAG)
- It was likely removed because the exam consolidated vector DB options to: OpenSearch, Aurora, Neptune, and RDS for PostgreSQL

> **If it appears as a distractor:** It's NOT wrong that MemoryDB can do vector search — it CAN. But for exam purposes, stick with the four explicitly in-scope vector database options.

---

### 8. "PartyRock" — Removed from Objective 2.3.1

**What changed:** "Amazon Bedrock PartyRock" was removed from the example list of services for developing GenAI applications.

**Why still know it:**
- PartyRock is/was a no-code playground for experimenting with GenAI apps
- It was a learning tool, not a production service
- Its removal suggests the exam is focusing on production-grade services

> **Current in-scope services for GenAI development:** Amazon Bedrock, Amazon SageMaker AI, SageMaker JumpStart, Amazon Quick, Kiro, Strands Agents, Amazon Bedrock AgentCore.

---

### 9. "Amazon Bedrock Data Automation" — Removed from Objective 2.3.1

**What changed:** Removed from the example list of GenAI development services.

**Why still know it:**
- Bedrock Data Automation processes documents and extracts structured data
- It's still a Bedrock feature — just not explicitly called out as an exam example
- Document processing/extraction is still a valid GenAI use case

---

## New Services Added to In-Scope (v1.1)

| Service | Category | What It Does | Why It Was Added |
|---------|----------|-------------|-----------------|
| **Amazon Aurora** | Database | Relational database with vector search capability (pgvector) | Vector storage for RAG embeddings |
| **Amazon Bedrock AgentCore** | ML | Managed infrastructure for deploying/running AI agents at scale | Agentic AI is a major v1.1 theme |
| **Kiro** | Developer Tools | AI-powered development environment | AI-assisted coding now part of AI practitioner knowledge |
| **Strands Agents** | Developer Tools | Open-source framework for building AI agents | Building custom agent logic |
| **Amazon Q** | Developer Tools | AI assistant (now superseded — Q Business became Amazon Quick, Q Developer became Kiro) | Conversational AI for business/developer tasks — legacy branding still referenced in exam objectives |
| **Amazon SageMaker JumpStart** | ML | Pre-built ML solutions and model hub | Quick model deployment and exploration |
| **AWS Transform** | ML | Enterprise AI transformation service | Helping organizations adopt AI at scale |

---

## Services Removed from Out-of-Scope List (Now Potentially Testable)

> **Important:** These were previously explicitly OUT of scope but are no longer on the exclusion list. This means they COULD appear on the exam (though not guaranteed).

| Service | What It Does | Possible Exam Context |
|---------|-------------|----------------------|
| **AWS DeepComposer** | Music generation using ML | Generative AI example (creative applications) |
| **Amazon FinSpace** | Financial data management | Data management for ML in finance |
| **Amazon Honeycode** | No-code app builder (discontinued) | Likely irrelevant now |
| **AWS IAM Identity Center** | Centralized identity/access management | Security and access control for AI systems |
| **AWS Marketplace** | Buy/sell software and ML models | Source for pre-trained models and AI solutions |
| **AWS Organizations** | Multi-account management | Governance at scale for AI workloads |
| **Amazon WorkDocs** | Document collaboration | Could be a data source for RAG |

> **Study priority:** Of these, **AWS Marketplace** and **AWS Organizations** are the most likely to appear in exam context:
> - Marketplace: "Where can you find third-party AI models?" or "How do companies sell/buy ML solutions?"
> - Organizations: "How do you govern AI usage across a large enterprise with multiple AWS accounts?"
> - IAM Identity Center: "How do you manage SSO access to AI services across teams?"

---

## Key Themes in the v1.0 → v1.1 Changes

### 1. Agentic AI is Now a First-Class Topic
- Added to definitions (1.1.1), comparisons (1.1.2), real-world applications (1.2.4)
- Got its own dedicated objective (2.1.6) covering MCP, multi-agent patterns, memory, tools, orchestration
- Agent business applications emphasized (3.1.6)
- Agent security added (5.1.1 — AgentCore Identity and Policy)

### 2. Shift from Custom ML to Foundation Model Applications
- Pipeline services now emphasize Bedrock, Q, Quick, Kiro over SageMaker internals
- "Simplicity" replaced with specific GenAI capabilities (conversation, content generation)
- New services (Strands Agents, AgentCore, Kiro) all focus on USING AI, not building from scratch

### 3. Cost and Economics Get More Attention
- Token-based pricing is now its own objective (2.1.4)
- Model selection adds cost, latency, model complexity as explicit factors
- ROI added to business metrics
- Model distillation added as cost optimization technique
- Business objective alignment metrics added (task completion rate, cost per interaction)

### 4. Security Becomes More Specific and Comprehensive
- Specific threats called out: data leakage prevention, output filtering, audit trails, toxicity
- Hallucination detection elevated to its own objective (5.1.5)
- Agent security formalized (AgentCore Identity and Policy)
- Grounding techniques explicitly tested

### 5. Context Engineering as a Distinct Discipline
- New objective (2.1.5) separates it from prompt engineering
- Recognizes that WHAT info you give the model is as important as HOW you ask

### 6. Evaluation Gets Richer
- LLM-as-a-judge added (scalable evaluation for open-ended tasks)
- Business alignment metrics formalized (proving business value, not just technical quality)
- Human-in-the-loop terminology replaces "human evaluation" (emphasizing ongoing process)
- Prompt versioning/management added (tracking what works)

---

## Exam Strategy: What the Revisions Tell You to Focus On

> **If AWS added it in v1.1, they consider it important and will test it heavily.**

| Priority | Topic | Why |
|----------|-------|-----|
| **HIGH** | Agentic AI (MCP, multi-agent patterns, tool use, memory) | Entirely new objective + added across 4 domains |
| **HIGH** | Token-based pricing and cost optimization | New dedicated objective |
| **HIGH** | Context engineering vs. prompt engineering | New dedicated objective |
| **HIGH** | Hallucination detection and grounding | Elevated to its own objective in Domain 5 |
| **HIGH** | Business alignment metrics (task completion, cost per interaction) | New objective emphasizing business value |
| **MEDIUM** | Agent security (AgentCore Identity + Policy) | New addition to security domain |
| **MEDIUM** | Prompt versioning and management | New objective in Domain 3 |
| **MEDIUM** | Model distillation | Added to cost tradeoffs |
| **MEDIUM** | LLM-as-a-judge evaluation | Added to evaluation metrics |
| **LOW** | AWS Transform, Kiro, Strands Agents | New services — know what they do at a high level |
| **LOW** | Removed content (AUC, PartyRock, MemoryDB) | Unlikely to be tested directly, but good background |

---

## Quick Reference: Old Wording → New Wording

| Objective | v1.0 Wording | v1.1 Wording | What to Study Differently |
|-----------|-------------|-------------|--------------------------|
| 1.1.1 | "large language models [LLMs]" | "large language model [LLM], generative AI [GenAI], agentic AI" | Know agentic AI definition and how it relates to GenAI |
| 1.1.2 | "AI, ML, GenAI, and deep learning" | "AI, ML, GenAI, deep learning, and agentic AI" | Place agentic AI in the hierarchy (subset of GenAI) |
| 1.1.3 | "batch, real-time" | "batch, real-time, asynchronous, serverless" | Know all 4 inferencing types and when to use each |
| 1.1.5 | "Describe supervised, unsupervised, reinforcement" | "Describe different types of AI/ML learning (for example, ...methods)" | Broader — could include semi-supervised, self-supervised |
| 1.3.6 | "accuracy, AUC, F1 score" | "accuracy, precision, recall, F1 score" | Focus on precision vs. recall tradeoff scenarios |
| 2.2.1 | "adaptability, responsiveness, simplicity" | "adaptability, responsiveness, conversational capabilities, ability to generate content" | Know WHY these are advantages over traditional ML |
| 3.1.6 | "role of agents in multi-step tasks" | "role of AI agents and their business applications" | Focus on business use cases, not just technical capability |
| 3.4.1 | "human evaluation" | "human-in-the-loop evaluation" | Same concept, newer terminology aligning with A2I |
