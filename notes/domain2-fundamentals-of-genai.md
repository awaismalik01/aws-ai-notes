# Domain 2: Fundamentals of Generative AI (24% of Exam)

---

## Task 2.1: Basic Concepts of Generative AI

### Foundational GenAI Concepts

| Concept | Definition | Example |
|---------|-----------|---------|
| **Tokens** | The smallest unit of text that an LLM processes. Can be words, subwords, or characters | "unhappiness" → ["un", "happiness"] (2 tokens) |
| **Chunking** | Breaking large documents into smaller pieces for processing or storage in vector databases | Splitting a 50-page PDF into 500-word chunks for RAG |
| **Embeddings** | Numerical vector representations of text/images that capture semantic meaning. Similar concepts have similar vectors | "king" and "queen" are close in embedding space |
| **Vectors** | Arrays of numbers that represent data in multi-dimensional space, used to measure similarity | [0.2, -0.5, 0.8, 0.1] representing a sentence |
| **Prompt Engineering** | The practice of crafting effective inputs (prompts) to guide FM outputs toward desired results | "Summarize this text in 3 bullet points for a C-level audience" |
| **Transformer** | Neural network architecture that uses self-attention mechanisms to process sequences in parallel (basis of modern LLMs) | GPT, BERT, Claude all use transformer architecture |
| **Foundation Models (FMs)** | Large pre-trained models that can be adapted to many downstream tasks without training from scratch | Claude, Amazon Titan, Llama |
| **Multi-modal Models** | Models that can process and generate multiple data types (text, images, audio, video) | Amazon Nova (text + image + video) |
| **Diffusion Models** | Generative models that learn to create data by reversing a gradual noising process | Stable Diffusion, DALL-E (image generation) |

### Deep Explanations — Making These Stick

**Tokens — The Currency of GenAI**

> **Analogy — Scrabble tiles:** Just like Scrabble breaks words into individual letter tiles, LLMs break text into tokens. But tokens aren't always full words — they can be pieces of words.
>
> **Practical rule of thumb:** 1 token ≈ 4 characters ≈ ¾ of a word in English.
> - "Hello world" = 2 tokens
> - "Artificial Intelligence" = 2-3 tokens  
> - A 500-word essay ≈ 375 tokens
>
> **Why it matters for the exam:** Tokens are the BILLING UNIT. Every time you send a prompt (input tokens) and receive a response (output tokens), you're charged. Longer conversations = more tokens = more money. Context window size (e.g., 128K tokens) = maximum "memory" the model can hold at once.

**Chunking — Breaking Documents Into Bite-Sized Pieces**

> **Analogy — Cutting a pizza:** You can't eat a whole pizza in one bite. Similarly, an LLM can't process a 200-page document at once (it exceeds the context window). So you "chunk" it into smaller slices — maybe by paragraph, page, or a fixed number of words.
>
> **Why chunking strategy matters:**
> - **Too small** (50 words) → Loses context, chunks are meaningless fragments
> - **Too large** (5,000 words) → Less precise retrieval, wastes token budget
> - **Just right** (200-500 words) → Captures complete thoughts, efficient retrieval
>
> **Chunking is critical for RAG:** When a user asks a question, you search for the most relevant CHUNKS (not the whole document) and feed only those into the model's prompt.

**Embeddings — Meaning Turned Into Numbers**

> **Analogy — GPS coordinates for meaning:** Just like GPS coordinates tell you where a place is in physical space, embeddings tell you where a concept is in "meaning space." Things that are close in meaning get coordinates that are close together.
>
> **Visual example:**
> ```
> "puppy" → [0.9, 0.8, 0.1]    ← close to "dog"
> "dog"   → [0.9, 0.7, 0.2]    ← close to "puppy"  
> "car"   → [0.1, 0.2, 0.9]    ← far from both
> ```
>
> **Key insight:** Embeddings capture SEMANTIC similarity (meaning), not just word similarity. "Happy" and "joyful" will be close in embedding space even though they share no letters. This is what makes semantic search possible.

**Vectors — The Actual Numbers**

> **Relationship to embeddings:** An embedding IS a vector. "Embedding" is the concept (turning meaning into numbers). "Vector" is the format (an array of numbers). When someone says "store embeddings in a vector database," they mean "store these arrays of numbers that represent meaning."

**Transformers — The Engine Behind Modern AI**

> **Analogy — A really smart reader:** Imagine reading a sentence where the word "bank" appears. Is it a river bank or a financial bank? A transformer uses "self-attention" to look at ALL other words in the sentence simultaneously to figure out the right meaning. It doesn't read left-to-right like older models — it considers everything at once.
>
> **Why transformers revolutionized AI:**
> - **Before transformers (RNNs):** Read one word at a time, left to right. By the time it reached the end of a long sentence, it had "forgotten" the beginning. Slow because each word depends on the previous.
> - **After transformers:** Read ALL words simultaneously. Can relate any word to any other word regardless of distance. Massively parallelizable = much faster training.
>
> **The "T" in GPT, BERT, etc. stands for Transformer.**

**Foundation Models — The Pre-Built Base**

> **Analogy — A university graduate:** A foundation model is like a person who completed a broad university education. They know a lot about many things (pre-training). Now you can give them a specific job (fine-tuning) or just ask them questions (prompting) without sending them back to school.
>
> **Why "foundation"?** Because it's the BASE upon which you build specific applications. One foundation model can power a chatbot, a summarizer, a translator, and a code generator — all without retraining.

**Diffusion Models — Creating Images From Noise**

> **Analogy — Sculpting from marble:** A sculptor starts with a block of marble (noise) and gradually removes material until a statue (image) emerges. Diffusion models work similarly:
> 1. **Training:** Take real images, gradually add random noise until they become pure static
> 2. **Generation:** Start with pure random noise, gradually remove noise to create a realistic image
>
> **This is how Stable Diffusion and DALL-E create images from text descriptions.**


### How Transformers Work (Simplified)

```
Input Text → Tokenization → Embeddings → Self-Attention Layers → Output Prediction
```

- **Self-Attention**: Allows the model to weigh the importance of different parts of the input when generating each output token
- **Key advantage**: Processes all tokens in parallel (unlike older RNNs that process sequentially)
- **Result**: Better at capturing long-range dependencies in text

> **Self-attention example:** In the sentence "The cat sat on the mat because it was tired," self-attention helps the model understand that "it" refers to "the cat" (not "the mat"). It does this by calculating attention scores between every pair of words.

### Potential Use Cases for GenAI Models

| Category | Use Cases | Real-World Example |
|----------|-----------|-------------------|
| **Content Generation** | Blog posts, marketing copy, reports, emails | Marketing team generates 50 product descriptions in minutes |
| **Image Generation** | Product mockups, artwork, design concepts | E-commerce creates product images without photoshoots |
| **Video/Audio Generation** | Synthetic media, voice synthesis, video editing | Training videos with AI-generated narration |
| **Summarization** | Document condensation, meeting notes, research digests | Lawyers summarize 100-page contracts into 2-page briefs |
| **AI Assistants** | Customer support, internal knowledge assistants | IT helpdesk bot answering employee questions 24/7 |
| **Translation** | Multi-language content, localization | Global company translates docs into 20 languages instantly |
| **Code Generation** | Writing, debugging, explaining, and documenting code | Developer uses Kiro to auto-generate unit tests |
| **Customer Service Agents** | Automated support with contextual understanding | Airline chatbot handles rebooking, refunds, and complaints |
| **Search** | Semantic search across documents and knowledge bases | Employee searches "vacation policy for part-time workers" in natural language |
| **Recommendation Engines** | Personalized content and product suggestions | Streaming service recommends shows based on viewing history |

### The FM Lifecycle

```
Data Selection → Model Selection → Pre-training → Fine-tuning → Evaluation → Deployment → Feedback
       ↑                                                                                    |
       └────────────────────── Continuous improvement loop ─────────────────────────────────┘
```

| Stage | Description | Analogy |
|-------|-------------|---------|
| **Data Selection** | Choosing high-quality, diverse, representative training data | Selecting textbooks for a student's education |
| **Model Selection** | Choosing architecture, size, and base model appropriate for the task | Choosing the right vehicle for the journey (sedan vs. truck vs. sports car) |
| **Pre-training** | Training the model on massive general datasets (most expensive phase) | Getting a 4-year university degree (broad education) |
| **Fine-tuning** | Adapting the pre-trained model to specific tasks/domains | Getting specialized job training after university |
| **Evaluation** | Measuring performance against benchmarks and human judgment | Taking the certification exam |
| **Deployment** | Making the model available for inference in production | Starting the actual job |
| **Feedback** | Collecting user feedback and performance data for improvement | Annual performance reviews leading to professional development |


### Token-Based Pricing Model

**How it works:**
- You pay per token processed (both input and output tokens)
- Input tokens = your prompt (context + instructions)
- Output tokens = the model's generated response
- Longer prompts and responses = higher cost

> **Analogy — Pay-per-word telegram:** In the old days, telegrams charged per word. You'd write concisely to save money. Token-based pricing works the same way — every word (token) costs money, both what you SEND and what you RECEIVE back.
>
> **Critical exam knowledge:**
> - Input tokens are usually CHEAPER than output tokens
> - A long system prompt sent with every request adds up fast (100 requests × 1,000-token system prompt = 100,000 input tokens billed)
> - Prompt caching helps: if you send the same system prompt repeatedly, caching avoids re-processing it

**Effect on Cost:**
| Factor | Cost Impact | Optimization Strategy |
|--------|-------------|----------------------|
| Longer prompts (more context) | Higher input token cost | Be concise; only include relevant context |
| Longer generated responses | Higher output token cost | Set max_tokens appropriately |
| Larger/more capable models | Higher per-token price | Use smallest model that meets quality needs |
| Prompt caching | Reduces cost for repeated context | Design prompts with cacheable prefixes |
| Shorter, focused prompts | Lower cost | Remove unnecessary instructions/examples |

**Effect on Performance:**
| Factor | Performance Impact | Explanation |
|--------|-------------------|-------------|
| More context tokens | Better quality answers (up to context limit) | More info = better answers, but diminishing returns |
| More output tokens allowed | More detailed responses | Model won't cut off mid-thought |
| Context window limit | Maximum tokens model can process at once | 128K window ≈ a 300-page book |
| Token budget exhaustion | Response gets cut off | Model stops generating mid-sentence |

**Pricing tiers on AWS Bedrock:**

| Tier | How It Works | Best For | Analogy |
|------|-------------|----------|---------|
| **On-demand** | Pay per token, no commitment | Variable/unpredictable workloads | Pay-per-ride taxi |
| **Provisioned throughput** | Reserved capacity, lower per-token cost | Predictable, high-volume workloads | Monthly bus pass |
| **Batch inference** | Discounted pricing for non-real-time processing | Large bulk jobs that can wait | Shipping by freight (slower but cheaper) |

### Context Engineering

**Definition:** The practice of strategically designing and managing the information (context) provided to a foundation model to optimize its outputs.

> **Analogy — Briefing a consultant:** When you hire a consultant, the quality of their advice depends on the quality of the briefing you give them. Context engineering is about being an excellent "briefer" — giving the AI exactly the right information, in the right structure, at the right time.

**Key aspects:**
- **What context to include** — Selecting the most relevant information for the task
- **How to structure it** — Organizing context for optimal model comprehension
- **When to refresh it** — Updating context as conversations evolve
- **How much to provide** — Balancing completeness with token limits and cost

**Difference from Prompt Engineering:**

| Prompt Engineering | Context Engineering |
|-------------------|-------------------|
| Focuses on the instruction/question | Focuses on the background information |
| "How you ask" | "What information you provide" |
| Techniques like chain-of-thought | Techniques like RAG, memory management |
| "Please summarize in 3 bullets" | Providing the right documents TO summarize |

> **Exam distinction:** If a question asks about HOW to instruct the model (chain-of-thought, few-shot) → Prompt Engineering. If it asks about WHAT information to give the model (RAG, knowledge bases, memory) → Context Engineering.

**Context engineering strategies:**
- **RAG** — Retrieve relevant documents and inject into the prompt
- **Conversation memory management** — Summarize old messages, keep recent ones
- **System prompts with role/rules** — Set persistent behavior guidelines
- **Dynamic context selection** — Choose different context based on the query
- **Summarizing previous context** — Compress long conversations to fit token limits

> **Real-world scenario:** A customer support bot has a 128K token context window. After a long conversation (50+ messages), the window fills up. Context engineering decides: which messages to keep verbatim? which to summarize? which to drop? This is memory management.


### Foundational Agentic AI Concepts

**What is Agentic AI?**
AI systems that can autonomously plan, reason, and execute multi-step tasks using tools and external systems.

> **Analogy — A personal assistant vs. a search engine:**
> - **Regular GenAI (non-agentic):** Like asking a librarian a question. They give you an answer from what they know. If they don't know, they say so. They can't go DO things for you.
> - **Agentic AI:** Like a personal assistant. You say "Book me a flight to London next week under $500." They search flights, compare prices, check your calendar, book the ticket, and send you the confirmation. They PLAN, DECIDE, and ACT autonomously.

**Key Components:**

| Component | Description | Example | Analogy |
|-----------|-------------|---------|---------|
| **Planning** | Breaking complex goals into subtasks | Agent decides to search, then summarize, then email | Project manager creating a task list |
| **Reasoning** | Logical thinking about next actions | Determining which tool to use based on the task | Detective deciding which lead to follow |
| **Tool Usage** | Calling external APIs, databases, or functions | Querying a database, calling a weather API | Worker picking the right tool from a toolbox |
| **Memory Management** | Retaining information across interactions | Short-term (conversation) and long-term (stored) memory | Person using sticky notes (short-term) and a filing cabinet (long-term) |
| **Workflow Orchestration** | Coordinating sequence of actions | Managing dependencies between subtasks | Orchestra conductor coordinating musicians |

**Multi-Agent System Patterns:**

| Pattern | Description | Use Case | Analogy |
|---------|-------------|----------|---------|
| **Supervisor** | One agent coordinates and delegates to specialist agents | Complex research with search + analysis + writing agents | Manager delegating tasks to team members |
| **Sequential** | Agents pass work in a chain | Document → Summarize → Translate → Format | Assembly line in a factory |
| **Parallel** | Multiple agents work simultaneously | Running multiple analyses at once | Multiple chefs working on different dishes at same time |
| **Hierarchical** | Layered delegation with sub-supervisors | Enterprise-scale workflows | Corporate org chart (CEO → VPs → Directors → Teams) |

**Model Context Protocol (MCP):**

> **Analogy — USB for AI:** Before USB, every device had its own proprietary connector (printer cable, camera cable, phone cable). USB standardized connections so any device works with any computer. MCP does the same for AI agents — it standardizes how agents connect to ANY external tool or data source.

- An open standard for connecting AI agents to external systems (tools, data sources, services)
- Provides a standardized interface so agents can discover and use tools
- Enables interoperability between different AI agents and tool providers
- Without MCP, every agent-tool connection requires custom integration code

**Multi-Agent Communication Patterns:**

| Pattern | How It Works | Analogy |
|---------|-------------|---------|
| **Direct messaging** | Agents communicate directly with each other | Sending a DM to a coworker |
| **Shared memory** | Agents read/write to a common workspace | Team whiteboard everyone can see and edit |
| **Event-driven** | Agents react to events published by other agents | Slack notifications — you react when you see a relevant message |
| **Blackboard** | Agents post intermediate results to a shared board | Scientists posting findings on a research bulletin board |

---

## Task 2.2: Capabilities and Limitations of GenAI

### Advantages of GenAI

| Advantage | Explanation | Why It Matters for Business |
|-----------|-------------|---------------------------|
| **Adaptability** | Can be applied to diverse tasks without task-specific training | One model investment, many applications |
| **Responsiveness** | Provides immediate, contextual answers in real-time | 24/7 availability, no wait times |
| **Conversational capabilities** | Natural dialogue interface, understands context and nuance | No training needed for end users |
| **Ability to generate content** | Creates novel text, images, code, and multimedia at scale | Massive productivity gains |
| **Few-shot learning** | Can learn new tasks from just a few examples in the prompt | No retraining needed for new tasks |
| **Multi-lingual** | Many models support dozens of languages natively | Global reach without separate systems per language |

### Disadvantages/Limitations of GenAI

| Limitation | Description | Mitigation | Exam Scenario |
|-----------|-------------|------------|---------------|
| **Hallucinations** | Model generates plausible but factually incorrect information | RAG, grounding, fact-checking, citations | "The AI cited a law that doesn't exist" |
| **Interpretability** | Difficult to understand WHY a model produced a specific output | Model cards, explainability tools | "We can't explain to regulators why the AI denied the claim" |
| **Inaccuracy** | Outputs may contain errors, especially for specialized domains | Human review, domain fine-tuning | "The medical AI recommended the wrong dosage" |
| **Nondeterminism** | Same input can produce different outputs each time | Lower temperature, seed parameters | "The report looks different every time we generate it" |
| **Bias** | Models reflect biases present in training data | Guardrails, diverse training data | "The chatbot responds differently to names associated with different ethnicities" |
| **Knowledge cutoff** | Models don't know about events after training date | RAG with current data sources | "The AI doesn't know about last month's product update" |
| **Cost** | Token-based pricing can be expensive at scale | Prompt optimization, caching, smaller models | "Our monthly AI bill is $50K for customer support" |

> **The #1 exam topic in limitations: HALLUCINATIONS**
>
> **What makes hallucinations dangerous:** The model doesn't say "I'm making this up." It presents fabricated information with the same confidence as factual information. A model might cite a research paper that doesn't exist, complete with a plausible title, author name, and journal.
>
> **Why they happen:** The model is predicting the most likely NEXT TOKEN, not checking facts. "The capital of Australia is..." → the model picks the statistically likely next word, which might be "Sydney" (wrong — it's Canberra) because Sydney appears more frequently with "Australia" in training data.
>
> **How to mitigate (know all of these):**
> 1. **RAG** — Give the model real documents to reference
> 2. **Guardrails** — Bedrock Guardrails can check grounding
> 3. **Temperature = 0** — Reduces creativity/randomness
> 4. **"Only answer from provided context"** instruction
> 5. **Human-in-the-loop** — Expert reviews before delivery
> 6. **Source citations** — Force the model to cite where it got information


### Factors for Selecting GenAI Models

> **Decision framework — Think "CPCC-CCLM" (Cost, Performance, Capabilities, Constraints, Compliance, Cost, Latency, Model complexity):**

| Factor | Key Question | Example Decision |
|--------|-------------|-----------------|
| **Model types** | What modalities do I need? | Need image generation → multi-modal model |
| **Performance requirements** | How accurate must outputs be? | Medical advice needs highest accuracy → largest model |
| **Capabilities** | What can the model do? | Need 200K context window → rules out smaller models |
| **Constraints** | What can't I do? | Data must stay in EU → limits region/model choices |
| **Compliance** | What regulations apply? | HIPAA → need BAA-eligible service |
| **Cost** | What's my budget? | Startup budget → smaller model, on-demand pricing |
| **Latency** | How fast must responses be? | Live chat → low latency required → smaller/faster model |
| **Model complexity** | How sophisticated does it need to be? | Simple FAQ bot → small model sufficient; legal analysis → complex model |

> **Exam insight:** Questions often present a scenario and ask you to pick the right model. Look for these clues:
> - "Cost-effective" or "budget" → Smaller model, on-demand
> - "Fastest response" or "real-time" → Smaller model, provisioned throughput
> - "Highest quality" or "complex reasoning" → Larger model
> - "Must handle images and text" → Multi-modal model
> - "Data cannot leave the region" → Check regional availability

### Business Value and Metrics for GenAI

| Metric | What It Measures | Example |
|--------|-----------------|---------|
| **Cross-domain performance** | How well the AI performs across different business areas | Same model handles sales, support, AND HR queries |
| **ROI** | Return on investment from GenAI implementation | $200K investment saves $800K in labor annually |
| **Efficiency** | Time saved, process acceleration | Report generation reduced from 4 hours to 5 minutes |
| **Conversion rate** | % of users/leads taking desired action | AI recommendations increase purchases by 15% |
| **Average revenue per user** | Revenue impact per customer | Personalized upselling adds $12/customer/month |
| **Accuracy** | Correctness of AI-generated outputs | 94% of AI-generated summaries rated "accurate" by reviewers |
| **Customer lifetime value** | Long-term revenue impact from improved customer experience | Better support → 20% higher retention → more lifetime revenue |

> **Exam tip:** AWS loves to test whether you understand that business metrics (ROI, efficiency) are just as important as technical metrics (accuracy, latency). A model with 99% accuracy that costs $1M/month might have worse ROI than a 92% accurate model costing $10K/month.

---

## Task 2.3: AWS Infrastructure and Technologies for GenAI

### AWS Services for GenAI Development

| Service | Description | When to Use | Memory Trick |
|---------|-------------|-------------|--------------|
| **Amazon Bedrock** | Fully managed service to access FMs via API | Building GenAI apps without managing infrastructure | "Bedrock" = foundation/base → foundation models |
| **Amazon SageMaker AI** | Complete ML platform for building, training, and deploying models | Custom model training, fine-tuning, MLOps | "Sage" = wise → full ML wisdom/platform |
| **SageMaker JumpStart** | Pre-built ML solutions and model hub with one-click deployment | Quick model exploration and deployment | "JumpStart" = quick start → pre-built solutions |
| **Amazon Quick** | AI-powered business intelligence, analytics, and enterprise knowledge assistant (replaced Amazon Q Business) | Data visualization, business reporting, enterprise knowledge Q&A, document summarization | "Quick" = fast insights → BI + enterprise AI assistant |
| **Kiro** | AI-powered development environment (replaced Amazon Q Developer) | AI-assisted coding, debugging, code transformation, spec-driven development | Code-focused AI IDE — the developer counterpart to Amazon Quick |
| **Strands Agents** | Framework for building AI agents | Creating autonomous multi-step AI agents | "Strands" = weaving together → agent orchestration |
| **Amazon Bedrock AgentCore** | Managed infrastructure for deploying and running AI agents at scale | Production agent deployment with security and observability | "AgentCore" = core infrastructure for agents |

> **The big distinction — Bedrock vs. SageMaker:**
>
> | | Amazon Bedrock | Amazon SageMaker AI |
> |--|--------------|-------------------|
> | **Primary use** | ACCESS pre-trained FMs via API | BUILD/TRAIN custom models |
> | **Skill level** | Application developers | Data scientists/ML engineers |
> | **Infrastructure** | Fully managed, serverless | You configure compute (though managed) |
> | **Model source** | Third-party FMs (Claude, Titan, Llama) | Your own models + pre-trained |
> | **Analogy** | Renting a car (use as-is) | Building a custom car (full control) |
>
> **Exam shortcut:** If the question says "without managing infrastructure" or "quickly build an app" → Bedrock. If it says "train a custom model" or "MLOps pipeline" → SageMaker.

### Amazon Bedrock — Key Features

| Feature | Description | When You'd Use It |
|---------|-------------|-------------------|
| **Model choice** | Access to multiple FMs (Claude, Titan, Llama, AI21, Cohere, Stability AI) | Compare models for your specific task |
| **Knowledge Bases** | RAG implementation with automatic chunking, embedding, and retrieval | Ground responses in your company's documents |
| **Agents** | Build autonomous agents that can plan, reason, and take actions | Automate multi-step customer workflows |
| **Guardrails** | Content filtering, topic restrictions, PII detection | Ensure safe, compliant outputs |
| **Model Evaluation** | Compare model performance on your specific tasks | Choose the best model for your use case |
| **Fine-tuning** | Customize models with your domain data | Teach the model your industry's terminology |
| **Prompt Management** | Version and manage prompts across environments | Track which prompts work best, deploy consistently |
| **Data Automation** | Process documents and extract structured data | Turn invoices into database records |

> **Bedrock is the "Swiss Army knife" for GenAI on AWS** — one service that handles model access, RAG, agents, safety, evaluation, fine-tuning, and prompt management. If an exam question involves GenAI on AWS and doesn't specifically mention custom training, Bedrock is likely the answer.


### Amazon Quick & Kiro — AI Assistants for Business and Developers

> **AWS has two AI assistants — one for business users, one for developers. Know the split:**

| Product | Target User | What It Does | Analogy |
|---------|-------------|-------------|---------|
| **Amazon Quick** | Business users (non-technical) | BI dashboards, enterprise knowledge Q&A, document summarization, content generation from internal data (replaced Amazon Q Business) | A smart executive assistant who has read every company document AND can make charts |
| **Kiro** | Software developers | AI-powered IDE with code generation, debugging, spec-driven development, and agentic coding (replaced Amazon Q Developer) | A pair-programming partner who also knows all of AWS |

> **Key history:** Amazon Q was AWS's original AI assistant brand, split into Q Business (for enterprise users) and Q Developer (for coders). Both have been superseded:
> - **Amazon Q Business → Amazon Quick** — combines BI/analytics with enterprise knowledge assistant capabilities
> - **Amazon Q Developer (IDE) → Kiro** — evolved into a full agentic AI development environment
> - **AWS Chatbot → Amazon Q Developer (in chat applications)** — DevOps/cloud management alerts in Slack and Teams (this one KEPT the Q Developer name)

**Amazon Quick (replaced Amazon Q Business) — Deep Dive:**

| Capability | Description | Example |
|-----------|-------------|---------|
| **Business intelligence** | AI-powered dashboards, visualizations, and natural language querying of data | "Show me revenue by region for Q3" → auto-generates chart |
| **Enterprise knowledge Q&A** | Connects to company data sources and answers employee questions | "What is our parental leave policy?" (answers from HR docs) |
| **Document summarization** | Summarizes long documents, emails, meeting notes | "Summarize last week's board meeting notes" |
| **Content generation** | Creates drafts based on internal knowledge | "Write a customer FAQ about our new product using our product specs" |
| **Data source connectors** | Integrates with enterprise sources (S3, SharePoint, Confluence, Slack, Salesforce, databases, etc.) | Searches across ALL company data — not just one system |
| **Access control** | Respects existing permissions — users only see answers from data they're authorized to access | Marketing team can't see HR-only documents through Quick |
| **Admin controls & guardrails** | Admins configure topics to block, define response behavior | Block answers about confidential M&A plans |

> **Key exam point about Amazon Quick:** It combines **business intelligence** (dashboards, analytics) with **enterprise knowledge assistant** capabilities (Q&A over company documents). Think of it as BI + managed RAG in one product.
>
> **Amazon Quick vs. Bedrock Knowledge Bases:**
> - **Amazon Quick** = full end-to-end assistant + BI experience (chat UI, dashboards, access control, connectors) for business users
> - **Bedrock Knowledge Bases** = RAG building block for DEVELOPERS to integrate into their own custom applications

**Kiro (replaced Amazon Q Developer) — Deep Dive:**

| Capability | Description | Example |
|-----------|-------------|---------|
| **Code generation** | Generates code from natural language descriptions | "Write a Lambda function that processes S3 events" |
| **Code explanation** | Explains existing code in plain language | "What does this function do?" |
| **Debugging** | Identifies and suggests fixes for bugs | "Why is this test failing?" |
| **Code transformation** | Upgrades/migrates code (e.g., Java 8 → Java 17) | Automated language version upgrades |
| **Spec-driven development** | Structured workflow: requirements → design → implementation tasks | Define what you want built, Kiro implements it step by step |
| **Agentic coding** | Autonomous task execution — reads code, makes changes, runs tests, iterates | "Add pagination to the /users endpoint" → Kiro does it end-to-end |
| **Hooks** | Automated triggers that run commands/prompts on events (file save, task completion) | Auto-lint on save, run tests after implementing a task |
| **Security scanning** | Detects vulnerabilities in code | Finds insecure dependencies, hardcoded secrets |

> **Kiro vs. Amazon Q Developer — Why the change matters for the exam:**
> - Kiro is an **agentic** AI development environment — it doesn't just suggest code, it autonomously completes multi-step tasks
> - This aligns with the v1.1 exam's heavy emphasis on agentic AI
> - Kiro supports MCP (Model Context Protocol) for connecting to external tools — another v1.1 topic

> **Note — "Amazon Q Developer in chat applications" (formerly AWS Chatbot):**
> - AWS Chatbot was renamed to **Amazon Q Developer in chat applications**
> - It handles **DevOps and cloud management alerts** in Slack and Microsoft Teams
> - Sends notifications for CloudWatch alarms, AWS Health events, Security Hub findings, etc.
> - Allows running AWS CLI commands directly from chat channels
> - This is a DIFFERENT product from Kiro — don't confuse them:
>   - **Kiro** = AI-powered IDE for writing code (replaced Q Developer the coding assistant)
>   - **Amazon Q Developer in chat applications** = ChatOps tool for DevOps alerts and cloud management in Slack/Teams (renamed from AWS Chatbot)

> **Exam scenario shortcuts:**
> - "Employees need to ask questions about internal company documents" → **Amazon Quick**
> - "Developers need AI-powered coding assistance in their IDE" → **Kiro**
> - "Need to build a custom AI-powered Q&A app for customers" → **Amazon Bedrock** (Knowledge Bases + custom app)
> - "Need to search across SharePoint, Confluence, and S3 with one interface" → **Amazon Quick** (enterprise connectors)
> - "Autonomous AI that reads code, makes changes, and runs tests" → **Kiro** (agentic development)
> - "Need BI dashboards with natural language querying" → **Amazon Quick**


### Advantages of Using AWS GenAI Services

| Advantage | Description | Analogy |
|-----------|-------------|---------|
| **Accessibility** | No need for deep ML expertise to build GenAI applications | Don't need to be a mechanic to drive a car |
| **Lower barrier to entry** | Pre-built APIs, managed infrastructure, pay-as-you-go | Renting an apartment vs. building a house |
| **Efficiency** | Faster development with managed services and pre-trained models | Using pre-made ingredients vs. growing your own food |
| **Cost-effectiveness** | No upfront investment in hardware/training, pay for what you use | Uber vs. buying a car for occasional trips |
| **Speed to market** | Rapid prototyping and deployment with managed endpoints | Food truck (quick to start) vs. full restaurant (months of setup) |
| **Ability to meet business objectives** | Enterprise-grade reliability, SLAs, and support | Professional kitchen (consistent quality) vs. home cooking |

### Benefits of AWS Infrastructure for GenAI

| Benefit | Description | How AWS Delivers It |
|---------|-------------|-------------------|
| **Security** | Encryption, VPC isolation, IAM, PrivateLink | Data encrypted at rest and in transit; private network access |
| **Compliance** | SOC, ISO, HIPAA, FedRAMP certifications | AWS Artifact provides compliance documentation |
| **Responsibility** | Shared responsibility model | AWS secures infrastructure; you secure data and access |
| **Safety** | Guardrails, content filtering, model evaluation | Bedrock Guardrails filters harmful content automatically |

### Cost Tradeoffs of AWS GenAI Services

| Option | Tradeoff | When to Choose | Analogy |
|--------|----------|---------------|---------|
| **On-demand (token-based)** | Flexible, no commitment, but higher per-token cost | Unpredictable or low-volume usage | Pay-per-ride taxi |
| **Provisioned throughput** | Lower cost per token, but requires commitment and capacity planning | High-volume, predictable workloads | Monthly subway pass |
| **Custom models** | Highest capability for your domain, but expensive to train | Unique needs no existing model serves | Custom-built car |
| **Smaller models** | Cheaper and faster, but potentially lower quality | Simple tasks, cost-sensitive | Economy car |
| **Larger models** | Higher quality, but more expensive and slower | Complex reasoning, high-stakes outputs | Luxury sedan |
| **Regional coverage** | Some models only in certain regions | Data residency requirements | Some stores only in certain cities |
| **Prompt caching** | Reduces cost for repeated context, but requires compatible design | Repeated system prompts across requests | Buying in bulk vs. per item |

> **Cost optimization mental model:**
> 1. Start with the SMALLEST model that gives acceptable quality
> 2. Use ON-DEMAND pricing until you understand your usage patterns
> 3. Switch to PROVISIONED THROUGHPUT once usage is predictable and high
> 4. Use BATCH for anything that doesn't need real-time responses
> 5. Enable PROMPT CACHING for repeated context (system prompts)
> 6. Consider FINE-TUNING a small model instead of always using a large one

### Bedrock – Cost Savings Cheat Sheet

> **What DOES and DOESN'T affect your Bedrock bill:**

| Factor | Impact on Cost | Details |
|--------|---------------|---------|
| **Number of Input/Output Tokens** | **Main cost driver** | More tokens = more money. Every word in your prompt (input) and response (output) is billed. This is the #1 lever for cost control. |
| **Model size** | High impact | Smaller models (e.g., Haiku) are significantly cheaper per token than larger models (e.g., Sonnet, Opus). Use the smallest model that meets your quality bar. |
| **Pricing mode (On-Demand)** | No discount, maximum flexibility | Great for unpredictable workloads. No long-term commitment. Pay per token as you go. |
| **Pricing mode (Batch)** | **Up to 50% discount** | Submit jobs that don't need real-time responses. AWS processes them when capacity is available. Best cost-saving option for bulk work. |
| **Pricing mode (Provisioned Throughput)** | Usually NOT a cost-saving measure | Designed to **reserve capacity** and guarantee throughput — not primarily to save money. Choose when you need consistent performance, not lower bills. |
| **Temperature** | **No impact on pricing** | Changing temperature does NOT change cost. It only affects output quality/creativity. |
| **Top K** | **No impact on pricing** | Inference parameter only — does not affect token count or billing. |
| **Top P** | **No impact on pricing** | Inference parameter only — does not affect token count or billing. |

> **Critical exam distinction:**
> - "Need to save money on large batch processing jobs?" → **Batch inference** (up to 50% off)
> - "Need guaranteed capacity for a high-traffic app?" → **Provisioned Throughput** (not about saving money — about reserving capacity)
> - "Unpredictable usage, just getting started?" → **On-Demand** (flexible, no commitment)
>
> **Common exam trap:** A question may present Provisioned Throughput as a cost-saving measure. It's NOT — it's about performance guarantees and capacity reservation. Batch is the cost-saving option.

> **What to optimize to reduce costs:**
> 1. Reduce token count (shorter prompts, concise instructions, limit output length with max_tokens)
> 2. Use batch inference for non-urgent workloads (up to 50% savings)
> 3. Choose a smaller model when possible
> 4. Use prompt caching for repeated system prompts
> 5. DON'T bother adjusting temperature/top_k/top_p for cost — they have zero effect on pricing

---

## Key Exam Tips for Domain 2

1. **Tokens** are the billing unit — both input AND output tokens cost money. 1 token ≈ ¾ of a word.
2. **Embeddings** = meaning as numbers; **Vectors** = the number arrays themselves. They enable semantic search.
3. **Hallucinations** are THE #1 cited limitation — know all mitigation strategies (RAG, grounding, guardrails, low temperature, citations)
4. **Nondeterminism** = same prompt, different results each time. Fix with temperature = 0 or seed parameter.
5. **Amazon Bedrock** = access FMs via API (the go-to service for GenAI apps). **SageMaker** = build/train custom models.
6. **Context engineering** ("what info to provide") is BROADER than prompt engineering ("how to ask"). RAG is a context engineering technique.
7. **MCP (Model Context Protocol)** = USB for AI agents. Standardizes tool connections so any agent works with any tool.
8. **Agentic AI** = autonomous planning + reasoning + tool use + memory. Services: Bedrock Agents, Strands Agents, AgentCore.
9. **Token-based pricing**: On-demand (flexible/expensive) vs. Provisioned (committed/cheaper) vs. Batch (delayed/cheapest).
10. **Multi-agent patterns**: Supervisor (boss delegates), Sequential (assembly line), Parallel (simultaneous), Hierarchical (org chart).
11. **Transformers** process all tokens in PARALLEL using self-attention — this is why they're faster and better than older RNN architectures.
12. **Diffusion models** = image generation by reversing a noising process (noise → image). Used by Stable Diffusion, DALL-E.
13. **Foundation Model lifecycle**: Data Selection → Model Selection → Pre-training → Fine-tuning → Evaluation → Deployment → Feedback (continuous loop).
